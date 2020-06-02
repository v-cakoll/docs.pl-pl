---
title: Kompilacja schematu a klasa XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
ms.openlocfilehash: 3d517652665d6d0693e141d623483ff8946bbbf4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290243"
---
# <a name="xmlschemacollection-schema-compilation"></a>Kompilacja schematu a klasa XmlSchemaCollection
**XmlSchemaCollection** jest pamięcią podręczną lub biblioteką, w której można przechowywać i sprawdzać dane XML (XDR) oraz schematy języka definicji schematu XML (XSD). Obiekt **XmlSchemaCollection** zwiększa wydajność przez buforowanie schematów w pamięci zamiast uzyskiwania do nich dostępu z pliku lub adresu URL.  
  
> [!NOTE]
> Chociaż Klasa **XmlSchemaCollection** przechowuje zarówno schematy XDR, jak i schematy XML, każda metoda i właściwość, która pobiera lub zwraca obiekt **XmlSchema** , obsługuje tylko schematy XML.  
  
> [!IMPORTANT]
> <xref:System.Xml.Schema.XmlSchemaCollection>Klasa jest obecnie przestarzała i została zastąpiona <xref:System.Xml.Schema.XmlSchemaSet> klasą. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaSet> klasy, zobacz zestaw [XmlSchemaSet dla kompilacji schematu](xmlschemaset-for-schema-compilation.md).  
  
## <a name="add-schemas-to-the-collection"></a>Dodaj schematy do kolekcji  
 Schematy są ładowane do kolekcji za pomocą metody **Add** klasy **XmlSchemaCollection**, w której schemat jest skojarzony z identyfikatorem URI przestrzeni nazw. W przypadku schematów XML identyfikator URI przestrzeni nazw będzie zazwyczaj docelowym obszarem nazw dla schematu. W przypadku schematów XDR identyfikator URI przestrzeni nazw jest przestrzenią nazw określoną, gdy schemat został dodany do kolekcji.  
  
## <a name="check-for-a-schema-in-the-collection"></a>Wyszukaj schemat w kolekcji  
 Możesz sprawdzić, czy schemat znajduje się w kolekcji przy użyciu metody **Contains** . Metoda **Contains** pobiera obiekt **XML** (tylko schematy XML) lub ciąg reprezentujący identyfikator URI przestrzeni nazw skojarzony ze schematem (dla schematów XML i schematów XDR).  
  
## <a name="retrieve-a-schema-from-the-collection"></a>Pobierz schemat z kolekcji  
 Schemat z kolekcji można pobrać przy użyciu właściwości **Item** . Właściwość **Item** przyjmuje ciąg reprezentujący identyfikator URI przestrzeni nazw skojarzony ze schematem, zazwyczaj jego przestrzeń nazw Target i zwraca obiekt **XmlSchema** . Właściwość **Item** ma zastosowanie tylko do schematów XML. Wartość zwracana jest zawsze odwołaniem null dla schematów XDR, ponieważ nie ma dostępnego modelu obiektów.  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>Sprawdzanie poprawności dokumentów XML przy użyciu elementu XmlSchemaCollection  
 Można sprawdzić poprawność dokumentu wystąpienia XML za **pomocą XmlSchemaCollection** , tworząc **obiekt XmlSchemaCollection** , dodając schematy do kolekcji i ustawiając właściwość **schematy** w **XmlValidatingReader** , aby przypisać utworzony element **XmlSchemaCollection** do **XmlValidatingReader**.  
  
### <a name="improved-performance"></a>Zwiększona wydajność  
 Zaleca się, aby w przypadku sprawdzania poprawności więcej niż jednego dokumentu w tym samym schemacie używać elementu **XmlSchemaCollection** , ponieważ zapewnia lepszą wydajność przez buforowanie schematów w pamięci.  
  
 Poniższy przykład kodu tworzy obiekt **XmlSchemaCollection** , dodaje schematy do kolekcji i ustawia właściwość **schematy** .  
  
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

- [Weryfikacja XDR przy użyciu klasy XmlSchemaCollection](xdr-validation-with-xmlschemacollection.md)
- [Weryfikacja schematu XML (XSD) przy użyciu klasy XmlSchemaCollection](xml-schema-xsd-validation-with-xmlschemacollection.md)
