require(roperators)
require(stringr)


CCipher <- function(string, shift, CircularNr = FALSE){
  
  if (is.numeric(shift) == FALSE | is.character(string) == FALSE){stop("Key must be numerical or string must be of character type")
  } else if (CircularNr == TRUE) { 
    
    # If key 0, nothing has been done and function returns original alphabet. If key
    # is negative it will shift alphabet forward by number of steps chosen. If key is 
    # positive the function will shift alphabet backwards the number of steps chosen.
    # If it is larger or smaller than [-25,25] respectively, it is either shifted back
    # to original state of position or to another state already defined since this 
    # is a loop. Example, key=-26 = key=26 = key=0 or key=-30 = key=-4. If key is not
    # and integer it will terminate directly. The function returns a CIRCUALR ARRAY.
    CircularNr <- function(shift){
      if (shift == 0) {return(letters)
       } else if (shift < -25 | shift > 25) {
         stop("Stop, alphabet reversed back to original state or reiterated")
        } else if (isFALSE(shift%%1 == 0) == TRUE){
          stop("Stop, input must of integer form")
         } else if (shift < 0 & shift >= -25) {
            return(c(letters[(length(letters)+shift+1) : length(letters)], letters[1 : (length(letters)+shift)]))
             } else {
              return(c(letters[(1+shift) : (length(letters))], letters[1 : shift]))
         }
    } 
    return(CircularNr(shift))
  } else {
    
    Clean_String <- function(string){
      # Make text as lower case letters and clean up numbers or elements which are not letters
      Lower <- str_replace_all(tolower(string), "[^a-zA-z\\s]", " ")
      # If text contains more than one whitespace due to typeos we clean it up
      temp <- str_replace_all(Lower,"[\\s]+", " ")
      return(temp)
    }
    cleantext <- Clean_String(string)
      
    result <- ""
    for (i in 1:nchar(cleantext)) {
      char <- cleantext[i]
      
      # This uses E(x) = (x+n) mod 26 where intToUtf8(97) = "a" = utf8ToInt("a") = 97
      # Note that "%+=% overwrites current value with current value plus a new value. 
      result %+=% intToUtf8((utf8ToInt(char) + shift - 97) %% length(letters) + 97) 
    }
    res <- unlist(strsplit(result, split = "")) # Split up each letter
     res <- res[1:nchar(string)]  # NA may appear at end of string, do not select
    
      hm <- as.numeric(str_locate_all(cleantext," ")[[1]]) # Find original positions of white spaces
       hm <-  hm[1:(length(hm)/2)]  # Gives two identical columns, select only one
        res[hm] <- "!"  # Use this trick to make words concatenate with correct spacing
    return(paste(gsub('!', ' ', res),collapse=""))
    }
}
