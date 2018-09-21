---
title: Kompilacja schematu a klasa XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7b6ea782020dde83aa7d59be8ec3058a27075ad
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46479510"
---
# <a name="xmlschemacollection-schema-compilation"></a>Kompilacja schematu a klasa XmlSchemaCollection
**Użyciu klasy XmlSchemaCollection** pamięci podręcznej lub biblioteki, gdzie danych XML (XDR) i schematu XML schematów języka (XSD) definicji mogą być przechowywane i zweryfikowane. **Użyciu klasy XmlSchemaCollection** zwiększa wydajność, buforowanie schematów w pamięci, a nie dostępu do nich z pliku lub adres URL.  
  
> [!NOTE]
>  Mimo że **użyciu klasy XmlSchemaCollection** klasa przechowuje schematy XDR i schematów XML, wszystkie metody i właściwości, która przyjmuje i zwraca **XmlSchema** obiekt obsługuje tylko schematów XML.  
  
> [!IMPORTANT]
>  <xref:System.Xml.Schema.XmlSchemaCollection> Klasa jest obecnie przestarzały i został zastąpiony <xref:System.Xml.Schema.XmlSchemaSet> klasy. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaSet> , zobacz klasę [klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).  
  
## <a name="add-schemas-to-the-collection"></a>Dodaj schematy do kolekcji  
 Schematy są załadowane do kolekcji przy użyciu **Dodaj** metody **użyciu klasy XmlSchemaCollection**, co jest skojarzony z identyfikatora URI obszaru nazw schematu. Dla schematów XML identyfikator URI przestrzeni nazw będzie zazwyczaj docelowego obszaru nazw dla schematu. Schematy XDR, aby uzyskać identyfikator URI przestrzeni nazw jest przestrzeń nazw określona, jeśli schemat został dodany do kolekcji.  
  
## <a name="check-for-a-schema-in-the-collection"></a>Sprawdź, czy schemat w kolekcji  
 Można sprawdzić, czy schemat jest w kolekcji przy użyciu **zawiera** metody. **Zawiera** metoda przyjmuje albo **XmlSchema** obiektu (dla tylko schematy XML) lub ciąg reprezentujący identyfikator URI przestrzeni nazw skojarzone ze schematem (dla schematów XML, schematy i XDR).  
  
## <a name="retrieve-a-schema-from-the-collection"></a>Pobieranie schematu z kolekcji  
 Można pobrać schematu z kolekcji za pomocą **elementu** właściwości. **Elementu** właściwość przyjmuje ciąg reprezentujący przestrzeń nazw identyfikator URI skojarzony ze schematem, zwykle jego docelowego obszaru nazw i zwraca **XmlSchema** obiektu. **Elementu** właściwość dotyczy tylko schematów XML. Wartość zwracana jest zawsze odwołanie o wartości null dla schematów XDR, ponieważ nie mają model obiektów, które jest dostępne.  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>Sprawdź poprawność dokumentów XML za pomocą użyciu klasy XmlSchemaCollection  
 Sprawdzanie poprawności XML wystąpienie dokumentu za pomocą **użyciu klasy XmlSchemaCollection** , tworząc **użyciu klasy XmlSchemaCollection** obiektu, dodając swoje schematy do kolekcji i ustawienie **schematów**  właściwość **elementu XmlValidatingReader** można przypisać utworzony **użyciu klasy XmlSchemaCollection** do **elementu XmlValidatingReader**.  
  
### <a name="improved-performance"></a>Lepsza wydajność  
 Jest to zalecane, Jeśli zatwierdzasz więcej niż jeden dokument względem tego samego schematu, że używasz **użyciu klasy XmlSchemaCollection** ponieważ zapewnia lepszą wydajność, buforując schematów w pamięci.  
  
 Poniższy przykład kodu tworzy **użyciu klasy XmlSchemaCollection** obiektu, schematy są dodawane do kolekcji i ustawia **schematów** właściwości.  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a>Zobacz także

- [Weryfikacja XDR przy użyciu klasy XmlSchemaCollection](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
- [Weryfikacja schematu XML (XSD) przy użyciu klasy XmlSchemaCollection](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
