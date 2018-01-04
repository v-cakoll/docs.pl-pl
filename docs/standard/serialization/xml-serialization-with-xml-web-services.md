---
title: "Serializacja XML z usługami sieci Web XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML Web services, XML serialization
- XML serialization, XML Web services
- SOAP, XML serialization
- asmx files
- serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- .asmx files
- encoded XML serialization
- literal XML serialization
- serialization, attributes
ms.assetid: a416192f-8102-458e-bc0a-0b8f3f784da9
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2b3846e1c932ed23c61d3102d19ed3a039284aa4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xml-serialization-with-xml-web-services"></a>Serializacja XML z usługami sieci Web XML
Serializacji XML jest źródłowego transportu mechanizm używany w architekturze usług sieci Web XML przez <xref:System.Xml.Serialization.XmlSerializer> klasy. Aby kontrolować XML wygenerowanych przez usługi XML sieci Web, możesz zastosować atrybuty wymienione w obu [atrybuty że formant serializacji XML](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md) i [atrybuty że formant zakodowane SOAP serializacji](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md) do klasy, zwracanych wartości parametrów i pól plik używany do tworzenia usługi XML sieci Web (.asmx). Aby uzyskać więcej informacji na temat tworzenia usługi XML sieci Web, zobacz [ASP.NET przy użyciu usługi sieci Web XML budynku](http://msdn.microsoft.com/en-us/01dfc27c-c68e-4910-a0aa-5e4c2a766b0c).  
  
## <a name="literal-and-encoded-styles"></a>Literał i zakodowany stylów  
 XML wygenerowanych przez usługi XML sieci Web mogą być sformatowanych w jeden z dwóch sposobów albo literał lub zakodowane, zgodnie z objaśnieniem w [Dostosowywanie wiadomości SOAP](http://msdn.microsoft.com/en-us/1d777288-c0d9-4e6a-b638-f010da031952). Dlatego są dwóch zestawów atrybutów, które kontrolują serializacji XML. Atrybuty wymienione w [atrybuty że formant serializacji XML](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md) są przeznaczone do sterowania styl literału XML. Atrybuty wymienione w [atrybuty że formant zakodowane SOAP serializacji](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md) sterujące zakodowanego stylem. Stosując selektywnie tych atrybutów, można dostosować aplikację do zwrócenia jedną lub obie te style. Ponadto te atrybuty mogą dotyczyć (odpowiednio) zwracać wartości i parametry.  
  
### <a name="example-of-using-both-styles"></a>Przykład użycia obu style  
 Podczas tworzenia usługi sieci Web XML, można użyć obu zestawów atrybutów na metody. W poniższym przykładzie kodu klasy o nazwie `MyService` zawiera dwie metody usług XML sieci Web, `MyLiteralMethod` i `MyEncodedMethod`. Obie metody wykonywania tej samej funkcji: zwrócenia wystąpienia `Order` klasy. W `Order` klasy <xref:System.Xml.Serialization.XmlTypeAttribute> i <xref:System.Xml.Serialization.SoapTypeAttribute> atrybuty zostaną zastosowane do `OrderID` pola i oba atrybuty ich `ElementName` właściwość o różnych wartościach.  
  
 Aby uruchomić przykład, Wklej kod do pliku z rozszerzeniem .asmx i umieścić go w katalogu wirtualnego zarządzanego przez Internet Information Services (IIS). Z przeglądarki HTML, takie jak program Internet Explorer wpisz nazwę komputera, katalogu wirtualnego i pliku.  
  
```vb  
<%@ WebService Language="VB" Class="MyService" %>  
Imports System  
Imports System.Web.Services  
Imports System.Web.Services.Protocols  
Imports System.Xml.Serialization  
Public Class Order  
    ' Both types of attributes can be applied. Depending on which type  
    ' the method used, either one will affect the call.  
    <SoapElement(ElementName:= "EncodedOrderID"), _  
    XmlElement(ElementName:= "LiteralOrderID")> _  
    public OrderID As String  
End Class  
  
Public Class MyService  
    <WebMethod, SoapDocumentMethod> _  
    public Function MyLiteralMethod() As Order   
        Dim myOrder As Order = New Order()  
        return myOrder  
    End Function  
    <WebMethod, SoapRpcMethod> _  
    public Function MyEncodedMethod() As Order   
        Dim myOrder As Order = New Order()  
        return myOrder  
    End Function  
End Class  
```  
  
```csharp  
<%@ WebService Language="C#" Class="MyService" %>  
using System;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using System.Xml.Serialization;  
public class Order{  
    // Both types of attributes can be applied. Depending on which type  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
public class MyService{  
    [WebMethod][SoapDocumentMethod]  
    public Order MyLiteralMethod(){  
        Order myOrder = new Order();  
        return myOrder;  
    }  
    [WebMethod][SoapRpcMethod]  
    public Order MyEncodedMethod(){  
        Order myOrder = new Order();  
        return myOrder;  
    }  
}  
```  
  
 Poniższy kod przykładowy wywołania `MyLiteralMethod`. Nazwa elementu jest zmieniana na "LiteralOrderID".  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethodResponse xmlns="http://tempuri.org/">  
            <MyLiteralMethodResult>  
                <LiteralOrderID>string</LiteralOrderID>  
            </MyLiteralMethodResult>  
        </MyLiteralMethodResponse>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 Poniższy kod przykładowy wywołania `MyEncodedMethod`. Nazwa elementu jest "EncodedOrderID".  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" xmlns:tns="http://tempuri.org/" xmlns:types="http://tempuri.org/encodedTypes" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body soap:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
        <tns:MyEncodedMethodResponse>  
            <MyEncodedMethodResult href="#id1" />  
        </tns:MyEncodedMethodResponse>  
        <types:Order id="id1" xsi:type="types:Order">  
            <EncodedOrderID xsi:type="xsd:string">string</EncodedOrderID>  
        </types:Order>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### <a name="applying-attributes-to-return-values"></a>Stosowanie atrybutów, aby zwrócić wartości  
 Można także zastosować dla atrybutów, aby zwrócić wartości do kontrolowania obszaru nazw, nazwę elementu i tak dalej. Poniższy przykład kodu dotyczy `XmlElementAttribute` atrybutu wartość zwracaną `MyLiteralMethod` metody. Ten sposób pozwala na kontrolowanie nazwa przestrzeni nazw i elementu.  
  
```vb  
<WebMethod, SoapDocumentMethod> _  
public Function MyLiteralMethod() As _  
<XmlElement(Namespace:="http://www.cohowinery.com", _  
ElementName:= "BookOrder")> _  
Order   
    Dim myOrder As Order = New Order()  
    return myOrder  
End Function  
```  
  
```csharp  
[return: XmlElement(Namespace = "http://www.cohowinery.com",  
ElementName = "BookOrder")]  
[WebMethod][SoapDocumentMethod]  
public Order MyLiteralMethod(){  
    Order myOrder = new Order();  
    return myOrder;  
}  
```  
  
 Po wywołaniu, kod zwraca XML, podobny do następującego.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethodResponse xmlns="http://tempuri.org/">  
            <BookOrder xmlns="http://www.cohowinery.com">  
                <LiteralOrderID>string</LiteralOrderID>  
            </BookOrder>  
        </MyLiteralMethodResponse>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### <a name="attributes-applied-to-parameters"></a>Atrybuty parametrów  
 Również można zastosować atrybutów do parametrów, aby określić przestrzeń nazw, nazwę elementu i tak dalej. Poniższy przykładowy kod dodaje parametr do `MyLiteralMethodResponse` metody i stosuje `XmlAttributeAttribute` atrybutu parametru. Nazwa elementu i przestrzeni nazw są ustawione dla parametru.  
  
```vb  
<WebMethod, SoapDocumentMethod> _  
public Function MyLiteralMethod(<XmlElement _  
("MyOrderID", Namespace:="http://www.microsoft.com")>ID As String) As _  
<XmlElement(Namespace:="http://www.cohowinery.com", _  
ElementName:= "BookOrder")> _  
Order   
    Dim myOrder As Order = New Order()  
    myOrder.OrderID = ID  
    return myOrder  
End Function  
```  
  
```csharp  
[return: XmlElement(Namespace = "http://www.cohowinery.com",  
ElementName = "BookOrder")]  
[WebMethod][SoapDocumentMethod]  
public Order MyLiteralMethod([XmlElement("MyOrderID",   
Namespace="http://www.microsoft.com")] string ID){  
    Order myOrder = new Order();  
    myOrder.OrderID = ID;  
    return myOrder;  
}   
```  
  
 Żądanie protokołu SOAP będzie wyglądać w następujący sposób.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethod xmlns="http://tempuri.org/">  
            <MyOrderID xmlns="http://www.microsoft.com">string</MyOrderID>  
        </MyLiteralMethod>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### <a name="applying-attributes-to-classes"></a>Stosowanie atrybutów do klas  
 Jeśli potrzebujesz do kontrolowania obszaru nazw elementów, które odnoszą się do klasy, możesz zastosować `XmlTypeAttribute`, `XmlRootAttribute`, i `SoapTypeAttribute`, gdzie to właściwe. Poniższy przykład kodu dotyczy wszystkich trzech do `Order` klasy.  
  
```vb  
<XmlType("BigBookService"), _  
SoapType("SoapBookService"), _  
XmlRoot("BookOrderForm")> _  
Public Class Order  
    ' Both types of attributes can be applied. Depending on which  
    ' the method used, either one will affect the call.  
    <SoapElement(ElementName:= "EncodedOrderID"), _  
    XmlElement(ElementName:= "LiteralOrderID")> _  
    public OrderID As String  
End Class  
```  
  
```csharp  
[XmlType("BigBooksService", Namespace = "http://www.cpandl.com")]  
[SoapType("SoapBookService")]  
[XmlRoot("BookOrderForm")]  
public class Order{  
    // Both types of attributes can be applied. Depending on which  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
```  
  
 Wyniki zastosowania `XmlTypeAttribute` i `SoapTypeAttribute` są widoczne podczas badania opisu usługi, jak pokazano w poniższym przykładzie kodu.  
  
```xml  
    <s:element name="BookOrderForm" type="s0:BigBookService" />   
- <s:complexType name="BigBookService">  
- <s:sequence>  
    <s:element minOccurs="0" maxOccurs="1" name="LiteralOrderID" type="s:string" />   
    </s:sequence>  
  
- <s:schema targetNamespace="http://tempuri.org/encodedTypes">  
- <s:complexType name="SoapBookService">  
- <s:sequence>  
    <s:element minOccurs="1" maxOccurs="1" name="EncodedOrderID" type="s:string" />   
    </s:sequence>  
    </s:complexType>  
    </s:schema>  
```  
  
 Efekt `XmlRootAttribute` również zostanie wyświetlona w wynikach HTTP GET i HTTP POST w następujący sposób.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<BookOrderForm xmlns="http://tempuri.org/">  
    <LiteralOrderID>string</LiteralOrderID>  
</BookOrderForm>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [Atrybuty kontrolujące zakodowaną serializację SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 [Instrukcje: Serializacja obiektu jako kodowanego strumienia XML protokołu SOAP](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 [Instrukcje: Przesłanianie zakodowanej serializacji XML protokołu SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 [Wprowadzenie do serializacji XML](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [Instrukcje: Serializacja obiektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Instrukcje: Deserializacja obiektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
