BASE_URL:						Base URL to be placed in ENDPOINT
SERVICE:						Configured to drive. Can be set to bike or foot
URI_ROUTE:						URI for Route Service 
URI_NEAREST:					URI for Nearest Service 
URI_TRIP:						URI for Trip Service 
URI_TABLE:						URI for Table Service
MAX_RESPONSE_TIME:				Constant for Max Response time
RESPONSE_CODE_OK:				Constant for OK message
longitudeP0:					Longitude for P0. Used in ENDPOINTS
latitudeP0:						Latitude for P0. Used in ENDPOINTS
nameP0:							Address Name for P0 
longitudeP1:					Longitude for P1. Used in ENDPOINTS
latitudeP1:						Latitude for P1. Used in ENDPOINTS
nameP1:							Address Name for P1
invalidLongitudeP0: 			Longitude for an invalid location 
invalidLatitudeP0:				Latitude for an invalid location
invalidOverseasLongitude:		Longitude of an overseas located. Used to try to get route between overseas points
invalidOverseasLatitude:		Latitude of an overseas located. Used to try to get route between overseas points
POINTS_NUMBER:					Manipulated during the tests to count Points Number
NEAREST_POINTS:     			Manipulated during the tests to build the Nearest Service ENDPOINT 
WAY_POINTS_NUMBER				Manipulated during tests to build requests
tableSourceNumber:				Manipulated during the Table Service tests 
tableDestinationNumber:			Manipulated during the Table Service tests

#####Variables to store functions#####	
commonResponseValidations: 		Functions to validate Response codes 
commonRouteStepsValidation:		Functions to validate Route Step values
common2WayPointsValidation: 	Functions to validate Waypoints between 2 routes
commonNearestTests:				Functions to validate Nearest Waypoints 
commonInvalidCoordinates:		Functions to validate Invalid coordinates. Used on most negative tests 
commonWayPointsValidation:		Function to validade N Waypoints between routes
commomRoutesInputValidation:	Functions to validade Invalid Route inputs
commonTripWayPointsValidation: 	Functions to validate all TRIP waypoints
commonTripStepsValidation:		Functions to validate the TRIP steps 
commomInputValidation:			Functions to validate requests input
inputValidationSourceFirstDestinationLast: Functions to validade forced source and destination
validateSourceToDestination:	Functions to validate Source to Destination informations 
validateMultipleSourcesAndDestinations: Functions to validade N number of Sources to Destinations 