# utl-rolling-moving-sum-and-count-over-3-day-window-by-id
Rolling moving sum and count over 3 day window by id  
    Rolling moving sum and count over 3 day window by id                                                                                
                                                                                                                                        
    github                                                                                                                              
    https://tinyurl.com/yaahouu7                                                                                                        
    https://github.com/rogerjdeangelis/utl-rolling-moving-sum-and-count-over-3-day-window-by-id                                         
                                                                                                                                        
                                                                                                                                        
    related repos                                                                                                                       
    https://github.com/rogerjdeangelis?tab=repositories&q=rolling&type=&language=                                                       
    https://github.com/rogerjdeangelis?tab=repositories&q=moving&type=&language=                                                        
                                                                                                                                        
    I used a 3 day window for ease of verification.                                                                                     
    Just chane 3 to 100 in the R script                                                                                                 
                                                                                                                                        
    SAS Forum                                                                                                                           
    https://tinyurl.com/y9g934qt                                                                                                        
    https://communities.sas.com/t5/SAS-Data-Management/Compute-the-number-of-observations-and-sum-in-a-moving-window/m-p/668471         
                                                                                                                                        
         Method                                                                                                                         
             1. Generate all the days between the dates ny ID                                                                           
                group_by(ID)                                                                                                            
                complete(DTE = seq(min(DTE), max(DTE), by = "day"));                                                                    
             2. Fill the missing amount and count with 0                                                                                
             3. Apply the rollsum funtion with window=3 by ID                                                                           
     /*                   _                                                                                                             
    (_)_ __  _ __  _   _| |_                                                                                                            
    | | `_ \| `_ \| | | | __|                                                                                                           
    | | | | | |_) | |_| | |_                                                                                                            
    |_|_| |_| .__/ \__,_|\__|                                                                                                           
            |_|                                                                                                                         
    */                                                                                                                                  
    options validvarname=upcase;                                                                                                        
    libname sd1 "d:/sd1";                                                                                                               
    data sd1.have;                                                                                                                      
     input id$ dte amt ;                                                                                                                
     informat dte mmddyy10. ;                                                                                                           
     format dte mmddyy10. ;                                                                                                             
     cnt=1;                                                                                                                             
    cards ;                                                                                                                             
    a 01/01/96 8                                                                                                                        
    a  1/03/96 5                                                                                                                        
    a  1/06/96 6                                                                                                                        
    a  1/08/96 7                                                                                                                        
    a  1/10/96 4                                                                                                                        
    b  2/10/97 3                                                                                                                        
    b  2/12/97 9                                                                                                                        
    b  2/15/97 5                                                                                                                        
    b  2/18/97 6                                                                                                                        
    ;;;;                                                                                                                                
    ;;;;                                                                                                                                
    run;quit;                                                                                                                           
                                                                                                                                        
    /*           _               _                                                                                                      
      ___  _   _| |_ _ __  _   _| |_                                                                                                    
     / _ \| | | | __| `_ \| | | | __|                                                                                                   
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                    
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                   
                    |_|                                                                                                                 
    */                                                                                                                                  
                                                                                                                                        
    ROLLING 3 DAY SUM AND COUNT JUST CHAGE 3 TO 100                                                                                     
                                                                                                                                        
    WANT total obs=19                                                                                                                   
                                             | RULES                                                                                    
    Obs    ID       DTE         AMT     CNT  |                                                                                          
                                             |                                                                                          
      1    a     01/01/1996     0.00    0.00 |                                                                                          
      2    a     01/02/1996     0.00    0.00 | Prime the pump                                                                           
                                             |                                                                                          
      3    a     01/03/1996    13.00    2.00 | 1/1/ - 1/3 = 8+5 = 13 and 2 amounts                                                      
      4    a     01/04/1996     5.00    1.00 | 1/2  - 1/4 = 5 and 1 amount                                                              
      5    a     01/05/1996     5.00    1.00 | 1/3  - 1/5 = 5 and 1 amount                                                              
      6    a     01/06/1996     6.00    1.00 | 1/4  - 1/6 = 6 amd 1 amount                                                              
      7    a     01/07/1996     6.00    1.00 | 1/5  - 1/7 = 6 amd 1 amount                                                              
      8    a     01/08/1996    13.00    2.00 | 1/6  - 1/8 = 6+7 = 13 amd 2 amounts                                                      
      9    a     01/09/1996     7.00    1.00 |                                                                                          
     10    a     01/10/1996    11.00    2.00                                                                                            
    |                                                                                                                                   
     11    b     02/10/1997     0.00    0.00 | Prime again                                                                              
     12    b     02/11/1997     0.00    0.00 |                                                                                          
                                                                                                                                        
     13    b     02/12/1997    12.00    2.00 |                                                                                          
     14    b     02/13/1997     9.00    1.00 |                                                                                          
     15    b     02/14/1997     9.00    1.00 |                                                                                          
     16    b     02/15/1997     5.00    1.00 |                                                                                          
     17    b     02/16/1997     5.00    1.00 |                                                                                          
     18    b     02/17/1997     5.00    1.00 |                                                                                          
     19    b     02/18/1997     6.00    1.00 |                                                                                          
                                                                                                                                        
    /*                                                                                                                                  
     _ __  _ __ ___   ___ ___  ___ ___                                                                                                  
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|                                                                                                 
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                                 
    | .__/|_|  \___/ \___\___||___/___/                                                                                                 
    |_|                                                                                                                                 
    */                                                                                                                                  
                                                                                                                                        
    %utl_submit_r64('                                                                                                                   
    library(haven);                                                                                                                     
    library(dplyr);                                                                                                                     
    library(tidyr);                                                                                                                     
    library(zoo);                                                                                                                       
    library(SASxport);                                                                                                                  
    library(lubridate);                                                                                                                 
    have<-read_sas("d:/sd1/have.sas7bdat");                                                                                             
    filday <- have %>%                                                                                                                  
      group_by(ID) %>%                                                                                                                  
      complete(DTE = seq(min(DTE), max(DTE), by = "day"));                                                                              
    filday[is.na(filday)] <- 0;                                                                                                         
    myfun = function(x) rollsum(x, k = 3, fill = 0, align = "right");                                                                   
    filday %>%                                                                                                                          
       group_by(ID) %>%                                                                                                                 
       mutate_each(funs(myfun), AMT, CNT)                                                                                               
       -> want;                                                                                                                         
    want<-as.data.frame(want);                                                                                                          
    write.xport(want,file="d:/xpt/want.xpt");                                                                                           
    ');                                                                                                                                 
                                                                                                                                        
    libname xpt xport "d:/xpt/want.xpt";                                                                                                
    data want ;                                                                                                                         
      retain id;                                                                                                                        
      format dte mmddyy10. amt cnt 6.2;                                                                                                 
      set xpt.want;                                                                                                                     
    run;quit;                                                                                                                           
    libname xpt clear;                                                                                                                  
                                                                                                                                        
                                                                                                                                        
