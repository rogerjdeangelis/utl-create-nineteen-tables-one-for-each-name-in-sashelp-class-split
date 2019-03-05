# utl-create-nineteen-tables-one-for-each-name-in-sashelp-class-split
Create nineteen tables one for each name in sashelp class split
    Create nineteen tables one for each name in sashelp class split                                                
                                                                                                                   
    SAS Forum                                                                                                      
    https://communities.sas.com/t5/SAS-Programming/how-to-create-data-sets/m-p/540381                              
                                                                                                                   
    github                                                                                                         
    https://tinyurl.com/y3h8apg2                                                                                   
    https://github.com/rogerjdeangelis/utl-create-nineteen-tables-one-for-each-name-in-sashelp-class-split         
                                                                                                                   
    github                                                                                                         
    https://tinyurl.com/y6uzqbm2                                                                                   
    https://github.com/rogerjdeangelis/utl_thirteen_algorithms_to_split_a_table_based_on_groups_of_data            
                                                                                                                   
    *_                   _                                                                                         
    (_)_ __  _ __  _   _| |_                                                                                       
    | | '_ \| '_ \| | | | __|                                                                                      
    | | | | | |_) | |_| | |_                                                                                       
    |_|_| |_| .__/ \__,_|\__|                                                                                      
            |_|                                                                                                    
    ;                                                                                                              
                                                                                                                   
                                                                                                                   
    p to 40 obs from SASHELP.CLASS total obs=19                                                                    
                                                                                                                   
    bs    NAME       SEX    AGE    HEIGHT    WEIGHT                                                                
                                                                                                                   
     1    Alfred      M      14     69.0      112.5                                                                
     2    Alice       F      13     56.5       84.0                                                                
     3    Barbara     F      13     65.3       98.0                                                                
     4    Carol       F      14     62.8      102.5                                                                
    ...                                                                                                            
                                                                                                                   
    *            _               _                                                                                 
      ___  _   _| |_ _ __  _   _| |_                                                                               
     / _ \| | | | __| '_ \| | | | __|                                                                              
    | (_) | |_| | |_| |_) | |_| | |_                                                                               
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                              
                    |_|                                                                                            
    ;                                                                                                              
                                                                                                                   
                                                                                                                   
    WORK.LOG total obs=19                                                                                          
                                                                                                                   
    Obs    NAME                  STATUS                                                                            
                                                                                                                   
      1    Alfred     work dataset Alfred created                                                                  
      2    Alice      work dataset Alice created                                                                   
      3    Barbara    work dataset Barbara created                                                                 
    ....                                                                                                           
     16    Robert     work dataset Robert created                                                                  
     17    Ronald     work dataset Ronald created                                                                  
     18    Thomas     work dataset Thomas created                                                                  
     19    William    work dataset William created                                                                 
                                                                                                                   
                                                                                                                   
    19 work datasets one for each name                                                                             
                                                                                                                   
    WORK.ALFRED total obs=1                                                                                        
                                                                                                                   
    Obs     NAME     SEX    AGE    HEIGHT    WEIGHT                                                                
                                                                                                                   
     1     Alfred     M      14      69       112.5                                                                
                                                                                                                   
    WORK.ALICE total obs=1                                                                                         
                                                                                                                   
    Obs    NAME     SEX    AGE    HEIGHT    WEIGHT                                                                 
                                                                                                                   
     1     Alice     F      13     56.5       84                                                                   
                                                                                                                   
    ....                                                                                                           
                                                                                                                   
                                                                                                                   
    WORK.WILLIAM total obs=1                                                                                       
                                                                                                                   
    Obs     NAME      SEX    AGE    HEIGHT    WEIGHT                                                               
                                                                                                                   
     1     William     M      15     66.5       112                                                                
                                                                                                                   
    *          _       _   _                                                                                       
     ___  ___ | |_   _| |_(_) ___  _ __                                                                            
    / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                           
    \__ \ (_) | | |_| | |_| | (_) | | | |                                                                          
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                          
                                                                                                                   
    ;                                                                                                              
                                                                                                                   
    data log;                                                                                                      
                                                                                                                   
      set sashelp.class;                                                                                           
      call symputx('name',name);                                                                                   
                                                                                                                   
      rc=dosubl('                                                                                                  
         data &name;                                                                                               
           set sashelp.class(where=(name="&name"));                                                                
         run;quit;                                                                                                 
         %let cc=&syserr;                                                                                          
      ');                                                                                                          
                                                                                                                   
      if symgetn("cc")=0 then status=catx(" ","work dataset",name,"created");                                      
      else status=catx(" ","work dataset",name,"failed");                                                          
      keep name status;                                                                                            
                                                                                                                   
    run;quit;                                                                                                      
                                                                                                                   
                                                                                                                   
