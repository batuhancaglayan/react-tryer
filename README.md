### FetchRequestHelper usage

A simple request helper written for React using Fetch. It uses 5 parameter;;

- url => url of service
- method => http method (GET, POST, PUT, DELETE ...)
- succesHandler => the method that will call when the request completes successfully
- errorHandler => the method that will call when an error occured
- headerValues => reqeust header object, if it is null default value is    

	    {
          'Accept': 'application/json',
          'Content-Type': 'application/json'
        }



#### - Import FetchRequestHelper jsx to your component

> import * as fetchRequest from 'DIR_PATH/FetchRequestHelper.jsx';
  
#### - Create request object
 
> let requestGet = new myRequest.init("URL", "GET", "SUCCESS_HANDLER_METHOD", "ERROR_HANDLER_METHOD");

> let requestPost = new myRequest.init("URL", "POST", "SUCCESS_HANDLER_METHOD", "ERROR_HANDLER_METHOD");
  
#### - Trigger call function

  > requestGet.call();
  
   > let data = {
       id : 1,
       name : "person_name_1"
       surname : "person_surname_1",
       age: 28
   }
  
  > requestPost.call(data);
  
  
#### - Simple Component

    import React, { Component } from 'react'; '''
    import * as fetchRequest from 'DIR_PATH/FetchRequestHelper.jsx'; 
    
    class MyButton extends React.Component {
      constructor(props) {
         super(props);
      };
      updateState() {
         let requestGet = new myRequest.init("URL", "GET", "SUCCESS_HANDLER_METHOD", "ERROR_HANDLER_METHOD");
         requestGet.call()
      }
      requestSuccess(data){
        // use data in this handler
      }
      requestError(error){
        // manage error in this handler
      }
      render() {
         return (
            <div>
               <button onClick = {this.updateState}>CLICK</button>
               <h4>{this.state.data}</h4>
            </div>
         );
      }
    }
    
    export default MyButton;

