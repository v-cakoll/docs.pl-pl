---
title: 'Porady: Określanie alternatywnej nazwy elementu dla Stream XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, overriding
- serialization, overriding
- XML stream, specifying alternate element name for
- overriding XML serialization
- classes, overriding
- overriding classes
ms.assetid: 5cc1c0b0-f94b-4525-9a41-88a582cd6668
ms.openlocfilehash: 8cb6a66f9fc7a67ae99574e783fd889537b9b11a
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339076"
---
# <a name="how-to-specify-an-alternate-element-name-for-an-xml-stream"></a>Porady: Określanie alternatywnej nazwy elementu dla Stream XML
[Przykładowy kod](#cpconoverridingserializationofclasseswithxmlattributeoverridesclassanchor1)  
  
 Za pomocą [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx), można wygenerować więcej niż jeden strumień XML z tego samego zestawu klas. Można to zrobić, ponieważ na tym samym podstawowe informacje o różnice tylko nieznaczne wymaga dwóch różnych usług sieci Web XML. Załóżmy, dwie usługi XML sieci Web, które przetwarzają zamówienia dla książki, a w związku z tym obu wymagają ISBN liczb. Jedna usługa taga \<ISBN > gdy druga taga \<BookID >. Masz klasę o nazwie `Book` zawiera pole o nazwie `ISBN`. Jeśli wystąpienie `Book` klasy jest serializowane, będzie domyślnie używać nazwy składowej (ISBN) jako nazwy elementu tag. W przypadku pierwszego usługi sieci Web XML jest zgodnie z oczekiwaniami. Ale wysyłania strumień XML do drugiego usługi sieci Web XML, konieczne jest przesłonięcie serializacji tak, aby nazwy elementu znacznika `BookID`.  
  
### <a name="to-create-an-xml-stream-with-an-alternate-element-name"></a>Aby utworzyć strumień XML zawierających nazwę elementu alternatywny  
  
1.  Utworzenie wystąpienia <xref:System.Xml.Serialization.XmlElementAttribute> klasy.  
  
2.  Ustaw <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> z <xref:System.Xml.Serialization.XmlElementAttribute> do "BookID".  
  
3.  Utworzenie wystąpienia <xref:System.Xml.Serialization.XmlAttributes> klasy.  
  
4.  Dodaj `XmlElementAttribute` do kolekcji udostępniane za pośrednictwem <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> właściwości <xref:System.Xml.Serialization.XmlAttributes> .  
  
5.  Utworzenie wystąpienia <xref:System.Xml.Serialization.XmlAttributeOverrides> klasy.  
  
6.  Dodaj `XmlAttributes` do <xref:System.Xml.Serialization.XmlAttributeOverrides>, przekazując typ obiektu do zastępowania i nazwę elementu zastępowaniu.  
  
7.  Utworzenie wystąpienia `XmlSerializer` klasy z `XmlAttributeOverrides`.  
  
8.  Utworzenie wystąpienia `Book` klasy, a serializacji lub deserializacji go.  
  
## <a name="example"></a>Przykład  
  
```vb  
Public Class SerializeOverride()  
    ' Creates an XmlElementAttribute with the alternate name.  
    Dim myElementAttribute As XmlElementAttribute = _  
    New XmlElementAttribute()  
    myElementAttribute.ElementName = "BookID"  
    Dim myAttributes As XmlAttributes = New XmlAttributes()  
    myAttributes.XmlElements.Add(myElementAttribute)  
    Dim myOverrides As XmlAttributeOverrides = New XmlAttributeOverrides()  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes)  
    Dim mySerializer As XmlSerializer = _  
    New XmlSerializer(GetType(Book), myOverrides)  
    Dim b As Book = New Book()  
    b.ISBN = "123456789"  
    ' Creates a StreamWriter to write the XML stream to.  
    Dim writer As StreamWriter = New StreamWriter("Book.xml")  
    mySerializer.Serialize(writer, b);  
End Class  
```  
  
```csharp  
public class SerializeOverride()  
{  
    // Creates an XmlElementAttribute with the alternate name.  
    XmlElementAttribute myElementAttribute = new XmlElementAttribute();  
    myElementAttribute.ElementName = "BookID";  
    XmlAttributes myAttributes = new XmlAttributes();  
    myAttributes.XmlElements.Add(myElementAttribute);  
    XmlAttributeOverrides myOverrides = new XmlAttributeOverrides();  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes);  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(Book), myOverrides)  
    Book b = new Book();  
    b.ISBN = "123456789"  
    // Creates a StreamWriter to write the XML stream to.  
    StreamWriter writer = new StreamWriter("Book.xml");  
    mySerializer.Serialize(writer, b);  
}  
```  
  
 Strumień XML może wyglądać w następujący sposób.  
  
```xml  
<Book>  
    <BookID>123456789</BookID>  
</Book>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Serialization.XmlElementAttribute>  
- <xref:System.Xml.Serialization.XmlAttributes>  
- <xref:System.Xml.Serialization.XmlAttributeOverrides>  
- [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
- [Element XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx)  
- [Instrukcje: Serializacja obiektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [Instrukcje: Deserializacja obiektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
- [Instrukcje: Deserializacja obiektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
