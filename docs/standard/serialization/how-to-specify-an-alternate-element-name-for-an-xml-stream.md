---
title: "Porady: Określ nazwę elementu alternatywnego strumienia XML"
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
- XML serialization, overriding
- serialization, overriding
- XML stream, specifying alternate element name for
- overriding XML serialization
- classes, overriding
- overriding classes
ms.assetid: 5cc1c0b0-f94b-4525-9a41-88a582cd6668
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a41dbd6dd145e0dcd90ffb67106be9902ebc1721
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-specify-an-alternate-element-name-for-an-xml-stream"></a><span data-ttu-id="92b40-102">Porady: Określ nazwę elementu alternatywnego strumienia XML</span><span class="sxs-lookup"><span data-stu-id="92b40-102">How to: Specify an Alternate Element Name for an XML Stream</span></span>
[<span data-ttu-id="92b40-103">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="92b40-103">Code Example</span></span>](#cpconoverridingserializationofclasseswithxmlattributeoverridesclassanchor1)  
  
 <span data-ttu-id="92b40-104">Przy użyciu [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx), można wygenerować więcej niż jeden strumień XML przy użyciu tych samych klas.</span><span class="sxs-lookup"><span data-stu-id="92b40-104">Using the [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx), you can generate more than one XML stream with the same set of classes.</span></span> <span data-ttu-id="92b40-105">Można to zrobić, ponieważ na tym samym podstawowe informacje o różnice tylko nieznaczne wymaga dwóch różnych usług sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="92b40-105">You might want to do this because two different XML Web services require the same basic information, with only slight differences.</span></span> <span data-ttu-id="92b40-106">Załóżmy na przykład dwie usługi XML sieci Web, które przetwarzają zamówienia książki i w związku z tym wymaga ISBN cyfry.</span><span class="sxs-lookup"><span data-stu-id="92b40-106">For example, imagine two XML Web services that process orders for books, and thus both require ISBN numbers.</span></span> <span data-ttu-id="92b40-107">Jedna usługa używa tagu \<ISBN > a drugi używa tagu \<BookID >.</span><span class="sxs-lookup"><span data-stu-id="92b40-107">One service uses the tag \<ISBN> while the second uses the tag \<BookID>.</span></span> <span data-ttu-id="92b40-108">Masz klasę o nazwie `Book` zawiera pole o nazwie `ISBN`.</span><span class="sxs-lookup"><span data-stu-id="92b40-108">You have a class named `Book` that contains a field named `ISBN`.</span></span> <span data-ttu-id="92b40-109">Jeśli wystąpienie `Book` klasy jest serializowane, będzie domyślnie używać nazwy składowej (ISBN) jako nazwy elementu tag.</span><span class="sxs-lookup"><span data-stu-id="92b40-109">When an instance of the `Book` class is serialized, it will, by default, use the member name (ISBN) as the tag element name.</span></span> <span data-ttu-id="92b40-110">W przypadku pierwszego usługi sieci Web XML jest zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="92b40-110">For the first XML Web service, this is as expected.</span></span> <span data-ttu-id="92b40-111">Ale wysyłania strumień XML do drugiego usługi sieci Web XML, konieczne jest przesłonięcie serializacji tak, aby nazwy elementu znacznika `BookID`.</span><span class="sxs-lookup"><span data-stu-id="92b40-111">But to send the XML stream to the second XML Web service, you must override the serialization so that the tag's element name is `BookID`.</span></span>  
  
### <a name="to-create-an-xml-stream-with-an-alternate-element-name"></a><span data-ttu-id="92b40-112">Aby utworzyć strumień XML zawierających nazwę elementu alternatywny</span><span class="sxs-lookup"><span data-stu-id="92b40-112">To create an XML stream with an alternate element name</span></span>  
  
1.  <span data-ttu-id="92b40-113">Utworzenie wystąpienia <xref:System.Xml.Serialization.XmlElementAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="92b40-113">Create an instance of the <xref:System.Xml.Serialization.XmlElementAttribute> class.</span></span>  
  
2.  <span data-ttu-id="92b40-114">Ustaw <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> z <xref:System.Xml.Serialization.XmlElementAttribute> do "BookID".</span><span class="sxs-lookup"><span data-stu-id="92b40-114">Set the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> of the <xref:System.Xml.Serialization.XmlElementAttribute> to "BookID".</span></span>  
  
3.  <span data-ttu-id="92b40-115">Utworzenie wystąpienia <xref:System.Xml.Serialization.XmlAttributes> klasy.</span><span class="sxs-lookup"><span data-stu-id="92b40-115">Create an instance of the <xref:System.Xml.Serialization.XmlAttributes> class.</span></span>  
  
4.  <span data-ttu-id="92b40-116">Dodaj `XmlElementAttribute` do kolekcji udostępniane za pośrednictwem <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> właściwości <xref:System.Xml.Serialization.XmlAttributes> .</span><span class="sxs-lookup"><span data-stu-id="92b40-116">Add the `XmlElementAttribute` object to the collection accessed through the <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> property of <xref:System.Xml.Serialization.XmlAttributes> .</span></span>  
  
5.  <span data-ttu-id="92b40-117">Utworzenie wystąpienia <xref:System.Xml.Serialization.XmlAttributeOverrides> klasy.</span><span class="sxs-lookup"><span data-stu-id="92b40-117">Create an instance of the <xref:System.Xml.Serialization.XmlAttributeOverrides> class.</span></span>  
  
6.  <span data-ttu-id="92b40-118">Dodaj `XmlAttributes` do <xref:System.Xml.Serialization.XmlAttributeOverrides>, przekazując typ obiektu do zastępowania i nazwę elementu zastępowaniu.</span><span class="sxs-lookup"><span data-stu-id="92b40-118">Add the `XmlAttributes` to the <xref:System.Xml.Serialization.XmlAttributeOverrides>, passing the type of the object to override and the name of the member being overridden.</span></span>  
  
7.  <span data-ttu-id="92b40-119">Utworzenie wystąpienia `XmlSerializer` klasy z `XmlAttributeOverrides`.</span><span class="sxs-lookup"><span data-stu-id="92b40-119">Create an instance of the `XmlSerializer` class with `XmlAttributeOverrides`.</span></span>  
  
8.  <span data-ttu-id="92b40-120">Utworzenie wystąpienia `Book` klasy, a serializacji lub deserializacji go.</span><span class="sxs-lookup"><span data-stu-id="92b40-120">Create an instance of the `Book` class, and serialize or deserialize it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92b40-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="92b40-121">Example</span></span>  
  
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
  
 <span data-ttu-id="92b40-122">Strumień XML może wyglądać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="92b40-122">The XML stream might resemble the following.</span></span>  
  
```xml  
<Book>  
    <BookID>123456789</BookID>  
</Book>  
```  
  
## <a name="see-also"></a><span data-ttu-id="92b40-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92b40-123">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlElementAttribute>  
 <xref:System.Xml.Serialization.XmlAttributes>  
 <xref:System.Xml.Serialization.XmlAttributeOverrides>  
 [<span data-ttu-id="92b40-124">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="92b40-124">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [<span data-ttu-id="92b40-125">Element XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="92b40-125">XmlSerializer</span></span>](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx)  
 [<span data-ttu-id="92b40-126">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="92b40-126">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="92b40-127">Instrukcje: Deserializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="92b40-127">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [<span data-ttu-id="92b40-128">Instrukcje: Deserializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="92b40-128">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
