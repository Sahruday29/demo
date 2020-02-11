#[{'international' : java.util.Map<String,String>[], 'domestic' : java.util.Map<String,String>[]}]

for (order : flowVars.'orders') 
{
	if (order.location == 'international') {
		payload.'international'.add(order);
	} else {
		payload.'domestic'.add(order);
	}
}

#[[{'orderID':444, 'location':'international','price':14.01}, {'orderID':444, 'location':'international','price':14.01}, {'orderID':555, 'location':'domestic','price':14.01}]]

<?xml version='1.0' encoding='UTF-8'?>
<ns0:provisionOrderResponse xmlns:ns0="http://soap.training.mulesoft.com/">
<return>
<location>international</location>
<price>2</price>
<orderID>123E</orderID>
</return>
<return>
<location>domestic</location>
<price>2</price>
<orderID>123E</orderID>
</return>
</ns0:provisionOrderResponse>

payload.ns0#provisionOrderResponse.*return

http.query.params
#[{'range' : '*'}]

ws:consumer
#[getResource('orderResponse.xml').asString()]
UTF-8
text/xml
