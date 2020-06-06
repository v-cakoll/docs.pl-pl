---
title: Serializacja XML z usługami internetowymi XML
description: Więcej informacji na temat serializacji XML jest mechanizmem transportu używanym w architekturze usług sieci Web XML. Serializacja kodu XML jest wykonywana przez klasę XmlSerializer.
ms.date: 03/30/2017
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
ms.openlocfilehash: b03c25f745df9aa4afe44075506983cb14ed3da7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "84288956"
---
# <a name="xml-serialization-with-xml-web-services"></a>Serializacja XML z usługami internetowymi XML
Serializacji XML jest źródłowego transportu mechanizm używany w architekturze usług sieci Web XML przez <xref:System.Xml.Serialization.XmlSerializer> klasy. Aby sterować XML wygenerowanym przez usługę sieci Web XML, można zastosować atrybuty wymienione w obu [atrybutach, które kontrolują serializacji XML](attributes-that-control-xml-serialization.md) i atrybuty kontrolujące [ZAKODOWANĄ serializację protokołu SOAP](attributes-that-control-encoded-soap-serialization.md) do klas, wartości zwracanych, parametrów i pól pliku używanego do tworzenia usługi sieci Web XML (. asmx). Aby uzyskać więcej informacji na temat tworzenia usługi sieci Web XML, zobacz [usługi sieci Web XML przy użyciu ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ba0z6a33(v=vs.100)).  
  
## <a name="literal-and-encoded-styles"></a>Literał i zakodowany stylów  
 KOD XML wygenerowany przez usługę sieci Web XML można sformatować na jeden z dwóch sposobów, albo literał lub zakodowany, zgodnie z opisem w temacie [Dostosowywanie formatowania komunikatów protokołu SOAP](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dkwy2d72(v=vs.100)). Dlatego są dwóch zestawów atrybutów, które kontrolują serializacji XML. Atrybuty wymienione w [atrybutach, które kontrolują serializacji XML,](attributes-that-control-xml-serialization.md) są przeznaczone do sterowania XML stylu literału. Atrybuty wymienione w [atrybutach kontrolujących kodowanie zakodowanej serializacji protokołu SOAP](attributes-that-control-encoded-soap-serialization.md) w stylu kodowanym. Wybiórczo stosując te atrybuty, można dostosować aplikację w celu zwrócenia obu tych stylów lub obu. Ponadto te atrybuty mogą być stosowane (odpowiednio) do zwracania wartości i parametrów.  
  
### <a name="example-of-using-both-styles"></a>Przykład użycia obu stylów  
 Podczas tworzenia usługi sieci Web XML, można użyć obu zestawów atrybutów na metody. W poniższym przykładzie kodu Klasa o nazwie `MyService` zawiera dwie metody usługi sieci Web XML `MyLiteralMethod` i `MyEncodedMethod` . Obie metody wykonywania tej samej funkcji: zwrócenia wystąpienia `Order` klasy. W `Order` klasie, <xref:System.Xml.Serialization.XmlTypeAttribute> i <xref:System.Xml.Serialization.SoapTypeAttribute> atrybuty są stosowane do `OrderID` pola, a oba atrybuty mają `ElementName` ustawioną inną wartość.  
  
 Aby uruchomić przykład, wklej kod do pliku z rozszerzeniem. asmx i umieść plik w katalogu wirtualnym zarządzanym przez Internet Information Services (IIS). W przeglądarce HTML, takiej jak Internet Explorer, wpisz nazwę komputera, katalogu wirtualnego i pliku.  
  
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
public class Order {  
    // Both types of attributes can be applied. Depending on which type  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
public class MyService {  
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
  
 Poniższy przykładowy kod wywołuje `MyLiteralMethod` . Nazwa elementu jest zmieniana na "LiteralOrderID".  
  
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
  
 Poniższy przykładowy kod wywołuje `MyEncodedMethod` . Nazwa elementu jest "EncodedOrderID".  
  
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
  
### <a name="applying-attributes-to-return-values"></a>Stosowanie atrybutów do zwracanych wartości  
 Można również zastosować atrybuty do zwracanych wartości, aby kontrolować przestrzeń nazw, nazwę elementu i tak dalej. Poniższy przykład kodu stosuje `XmlElementAttribute` atrybut do wartości zwracanej przez `MyLiteralMethod` metodę. Ten sposób pozwala na kontrolowanie nazwa przestrzeni nazw i elementu.  
  
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
  
### <a name="attributes-applied-to-parameters"></a>Atrybuty zastosowane do parametrów  
 Można również zastosować atrybuty do parametrów, aby określić przestrzeń nazw, nazwę elementu i tak dalej. Poniższy przykład kodu dodaje parametr do `MyLiteralMethodResponse` metody i stosuje `XmlAttributeAttribute` atrybut do parametru. Nazwa elementu i przestrzeni nazw są ustawione dla parametru.  
  
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
 Jeśli potrzebujesz kontrolować przestrzeń nazw elementów, które są skorelowane z klasami, możesz zastosować `XmlTypeAttribute` , `XmlRootAttribute` i `SoapTypeAttribute` , zgodnie z potrzebami. Poniższy przykład kodu stosuje wszystkie trzy do `Order` klasy.  
  
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
public class Order {  
    // Both types of attributes can be applied. Depending on which  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
```  
  
 Wyniki zastosowania `XmlTypeAttribute` i `SoapTypeAttribute` mogą być widoczne podczas badania opisu usługi, jak pokazano w poniższym przykładzie kodu.  
  
```xml
<s:element name="BookOrderForm" type="s0:BigBookService" />
<s:complexType name="BigBookService">
  <s:sequence>
    <s:element minOccurs="0" maxOccurs="1" name="LiteralOrderID" type="s:string" />
  </s:sequence>

  <s:schema targetNamespace="http://tempuri.org/encodedTypes">
    <s:complexType name="SoapBookService">
      <s:sequence>
        <s:element minOccurs="1" maxOccurs="1" name="EncodedOrderID" type="s:string" />
      </s:sequence>
    </s:complexType>
  </s:schema>
</s:complexType>
```
  
 Efekt `XmlRootAttribute` również zostanie wyświetlona w wynikach HTTP GET i HTTP POST w następujący sposób.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<BookOrderForm xmlns="http://tempuri.org/">  
    <LiteralOrderID>string</LiteralOrderID>  
</BookOrderForm>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
- [Atrybuty kontrolujące zakodowaną serializację protokołu SOAP](attributes-that-control-encoded-soap-serialization.md)
- [Instrukcje: Serializacja obiektu jako kodowanego strumienia XML protokołu SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [Instrukcje: Przesłanianie zakodowanej serializacji XML protokołu SOAP](how-to-override-encoded-soap-xml-serialization.md)
- [Wprowadzenie do serializacji XML](introducing-xml-serialization.md)
- [Instrukcje: Serializacja obiektu](how-to-serialize-an-object.md)
- [Instrukcje: Deserializacja obiektu](how-to-deserialize-an-object.md)
