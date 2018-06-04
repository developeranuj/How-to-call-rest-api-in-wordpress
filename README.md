# How-to-call-rest-api-in-wordpress



$url = BOOKER_API_URL.'customer/appointment/create';
  $body = array (
         
         'ItineraryTimeSlotList' =>
         array (
         0 =>
         array (
           'StartDateTime' => '/Date(1524223609000)/',
           'IsPackage' => false,
           'TreatmentTimeSlots' =>
           array (
           0 =>
           array (
             'TreatmentID' => 2117109,
             'StartDateTime' => '/Date(1524223609000)/',
             'EmployeeWasRequested' => false,
           ),
           ),
         ),
         ),
         'LocationID' => $_SESSION['locations'],
         'Customer' => array (
         'ID' => $_SESSION['customerId'],
         'FirstName' => $_SESSION['customer']['FirstName'],
         'LastName' => $_SESSION['customer']['LastName'],
         'Email' => $_SESSION['customer']['Email'],
                   'SendEmail' => true,
         'HomePhone'=> '1234567890',        
         'MobilePhone'=> '1234567890',        
         'RequireCustomerPhone' => true,
         'RequireCustomerAddress' => false
         ),
         // 'AppointmentPayment' =>
         // array (
         // 'PaymentItem' =>
         // array (
         //   'Method' =>
         //   array (
         //   'ID' => 1,
         //   ),
         //   'CreditCard' =>
         //   array (
         //   'NameOnCard' => rgar( $entry, '1' ),
         //   'Number' => rgar( $entry, '3' ),
         //   'Type' =>
         //   array (
         //     'ID' => rgar( $entry, '2' ),
         //   ),
         //   'ExpirationDate' => '/Date('.$dateTimestamp.')/',
         //   ),
         // ),
         // ),
         'Notes' => 'string',
         'RefCode' => 'string',
         'access_token' => $_SESSION['login_token'],
       );

    $bodyRequest = 
        array(
            "headers"=>array(
                'Content-Type' => 'application/json',
                'Ocp-Apim-Subscription-Key' => BOOKER_SUBSCRIPTION_KEY
            ),
            "body"=>json_encode($body)
        
        );
        // echo "<pre>";
        // print_r($bodyRequest);
    $api_response = wp_remote_post($url,$bodyRequest);    
    echo "<pre>";
    var_dump(json_decode($api_response));
