---
title: Kompilacja schematu kolekcji XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d64443f213603b1f5db9c256acc88e998e3f009a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xmlschemacollection-schema-compilation"></a>Kompilacja schematu kolekcji XmlSchemaCollection
**Kolekcji XmlSchemaCollection** pamięci podręcznej lub biblioteki, gdzie schematy języka (XSD) definicji XML danych (XDR) i schemat XML może być przechowywane i sprawdzania poprawności. **Kolekcji XmlSchemaCollection** zwiększa wydajność, buforując schematów w pamięci zamiast dostępu do nich z pliku lub adres URL.  
  
> [!NOTE]
>  Mimo że **kolekcji XmlSchemaCollection** klasy przechowuje zarówno schematy XDR i schematów XML, wszystkie metody i właściwości, która przyjmuje lub zwraca **schematu XML** obiekt obsługuje tylko schematy XML.  
  
> [!IMPORTANT]
>  <xref:System.Xml.Schema.XmlSchemaCollection> Klasy jest teraz przestarzałe i zostało zastąpione <xref:System.Xml.Schema.XmlSchemaSet> klasy. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaSet> , zobacz klasy [XmlSchemaSet kompilowania schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).  
  
## <a name="add-schemas-to-the-collection"></a>Dodaj schematy do kolekcji  
 Schematy są załadowane do kolekcji przy użyciu **Dodaj** metody **kolekcji XmlSchemaCollection**, które jest skojarzony z identyfikatorem URI przestrzeni nazw schematu. Dla schematów XML identyfikator URI przestrzeni nazw będzie zazwyczaj docelowego obszaru nazw dla schematu. Schematy XDR, aby uzyskać identyfikator URI przestrzeni nazw jest przestrzeń nazw określona, jeśli schemat został dodany do kolekcji.  
  
## <a name="check-for-a-schema-in-the-collection"></a>Sprawdź, czy schemat w kolekcji  
 Można sprawdzić, czy schemat jest w kolekcji przy użyciu **zawiera** metody. **Zawiera** metoda przyjmuje albo **schematu XML** obiektu (na potrzeby tylko schematy XML) lub ciąg reprezentujący identyfikator URI przestrzeni nazw skojarzone ze schematem (dla schematów schematów XML i XDR).  
  
## <a name="retrieve-a-schema-from-the-collection"></a>Pobieranie schematu z kolekcji  
 Można pobrać schematu z kolekcji za pomocą **elementu** właściwości. **Elementu** właściwość przyjmuje ciąg reprezentujący przestrzeń nazw identyfikator URI skojarzony ze schematem, zwykle jego docelowy obszar nazw i zwraca **schematu XML** obiektu. **Elementu** właściwość dotyczy tylko schematy XML. Zwracana wartość jest zawsze odwołanie o wartości null dla schematy XDR, ponieważ nie mają model obiektów, które jest dostępne.  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>Sprawdzanie poprawności dokumentów XML za pomocą kolekcji XmlSchemaCollection  
 Sprawdzanie poprawności XML wystąpienia dokumentu za pomocą **kolekcji XmlSchemaCollection** tworząc **kolekcji XmlSchemaCollection** obiektu, Dodawanie użytkownika schematy do kolekcji, a ustawienie **schematów**  właściwość **elementu XmlValidatingReader** można przypisać utworzony **kolekcji XmlSchemaCollection** do **elementu XmlValidatingReader**.  
  
### <a name="improved-performance"></a>Większa wydajność  
 Jest to zalecane, jeśli jest sprawdzana poprawność więcej niż jeden dokument względem tego samego schematu, możesz użyć **kolekcji XmlSchemaCollection** ponieważ zapewnia lepszą wydajność, buforując schematów w pamięci.  
  
 Poniższy przykład kodu tworzy **kolekcji XmlSchemaCollection** obiektu, dodaje do kolekcji schematów i ustawia **schematy** właściwości.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Weryfikacja XDR przy użyciu klasy XmlSchemaCollection](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [Weryfikacja schematu XML (XSD) przy użyciu klasy XmlSchemaCollection](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
