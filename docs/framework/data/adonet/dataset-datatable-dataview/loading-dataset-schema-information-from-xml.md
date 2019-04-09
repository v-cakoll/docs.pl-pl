---
title: Ładowanie informacji o schemacie elementu DataSet z pliku XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 06dcbbedf8c1533b3da52b447c121746ce705083
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083351"
---
# <a name="loading-dataset-schema-information-from-xml"></a>Ładowanie informacji o schemacie elementu DataSet z pliku XML
Schemat <xref:System.Data.DataSet> (jego tabele, kolumny, relacje i ograniczenia) mogą być definiowane programowo, utworzone przez **wypełnienia** lub **FillSchema** metody <xref:System.Data.Common.DataAdapter>, lub załadowany z Dokument XML. Ładowanie **zestawu danych** informacji o schemacie z dokumentu XML, można użyć dowolnego **ReadXmlSchema** lub **InferXmlSchema** metody **zestawudanych**. **ReadXmlSchema** umożliwia ładowanie lub wywnioskować **DataSet** informacji o schemacie z dokumentu zawierającego schematu języka (XSD) definicji schematu XML lub dokumentu XML z wbudowanego schematu XML. **InferXmlSchema** pozwala na wnioskowanie schematu z dokumentów XML podczas ignoruje niektóre obszary nazw XML, który określisz.  
  
> [!NOTE]
>  Określanie kolejności w tabeli **zestawu danych** nie mogą zostać zachowane, korzystając z usług sieci Web lub serializacji XML do transferu **zestawu danych** utworzony w pamięci za pomocą konstrukcji XSD (na przykład relacjach zagnieżdżonych). W związku z tym, odbiorca **DataSet** nie powinna zależeć od tabeli kolejność, w tym przypadku. Jednak porządkowanie tabeli jest zawsze zachowywany, jeśli schemat **zestawu danych** przesyłane została odczytana z pliki XSD, zamiast tworzonych w pamięci.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 Można załadować schematu **DataSet** z dokumentu XML bez ładowania wszystkie dane, możesz użyć **ReadXmlSchema** metody **zestawu danych**. **ReadXmlSchema** tworzy **DataSet** schematu zdefiniowane przy użyciu schematu języka (XSD) definicji schematu XML.  
  
 **ReadXmlSchema** metoda przyjmuje jeden argument nazwy pliku strumienia, lub **XmlReader** zawierającego dokumentu XML do załadowania. Dokument XML może zawierać tylko schematu lub może zawierać wbudowanego schematu za pomocą elementów XML zawierający dane. Aby uzyskać informacje na temat pisania wbudowanego schematu XML Schema zobacz [elementu pochodnego dla zestawu danych relacyjnej struktury z schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 Jeśli dokument XML jest przekazywany do **ReadXmlSchema** nie zawiera żadnych informacji schematu wbudowane **ReadXmlSchema** wywnioskuje schematu z elementów w dokumencie XML. Jeśli **DataSet** już zawiera schemat z z bieżącym schemacie będzie można rozszerzyć, dodając nowe tabele, jeśli jeszcze nie istnieje. Nowe kolumny nie zostanie dodany do dodawane do istniejących tabel. Jeśli kolumna dodawany już istnieje w **DataSet** , ale typem niezgodny z kolumną wykryła w pliku XML, zgłaszany jest wyjątek. Aby uzyskać szczegółowe informacje o tym, jak **ReadXmlSchema** wnioskuje schemat z dokumentu XML, zobacz [wnioskowanie zestawu danych relacyjnej struktury z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).  
  
 Mimo że **ReadXmlSchema** ładuje lub wnioskuje schemat z **DataSet**, **ReadXml** metody **zestawu danych** ładuje lub wnioskuje zarówno schemat i dane zawarte w dokumencie XML. Aby uzyskać więcej informacji, zobacz [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).  
  
 W poniższych przykładach kodu pokazano sposób ładowania **DataSet** schematu z dokumentów XML lub strumienia. Pierwszy przykład przedstawia nazwę pliku schematu XML został przekazany do **ReadXmlSchema** metody. W drugim przykładzie pokazano **System.IO.StreamReader**.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As System.IO.StreamReader = New System.IO.StreamReader ("schema.xsd");  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a>InferXmlSchema  
 Można również poinstruować **DataSet** wywnioskowania jego schematu z dokumentów XML za pomocą **InferXmlSchema** metody **zestawu danych**. **InferXmlSchema** działa tak samo jak wykonać obie czynności **ReadXml** z **XmlReadMode** z **InferSchema** (powoduje załadowanie danych także wnioskuje schemat), a **ReadXmlSchema** Jeśli dokument odczytywanych zawiera nie wbudowany schemat. Jednak **InferXmlSchema** zapewnia dodatkowe możliwości dzięki czemu możesz określić określonej przestrzeni nazw XML mają być ignorowane, gdy schemat jest wnioskowany. **InferXmlSchema** przyjmuje dwa argumenty wymagane: lokalizację dokumentu XML, określonego przez nazwę pliku strumienia, lub **XmlReader**; i tablicą ciągów w przestrzeni nazw XML mają być ignorowane przez operację.  
  
 Na przykład rozważmy następujący kod XML:  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>   
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>   
  <Description od:adotype="203">Soft drinks and teas</Description>   
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>   
  <ReorderLevel od:adotype="3">10</ReorderLevel>   
  <Discontinued od:adotype="11">0</Discontinued>   
</Products>  
</NewDataSet>  
```  
  
 Ze względu na atrybuty określone dla elementów w poprzednim dokumentu XML zarówno **ReadXmlSchema** metody i **ReadXml** metody z **XmlReadMode** programu **InferSchema** utworzyłoby tabel dla każdego elementu w dokumencie: **Kategorie**, **CategoryID**, **CategoryName**, **opis**, **produktów**, **ProductID**, **ReorderLevel**, i **wycofane**. (Aby uzyskać więcej informacji, zobacz [wnioskowanie zestawu danych relacyjnej struktury z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) Jednakże bardziej odpowiednie struktury może być tylko utworzyć **kategorie** i **produktów** tabel, a następnie utworzyć **CategoryID**, **CategoryName** , i **opis** kolumn w **kategorie** tabeli i **ProductID**, **ReorderLevel**, i **Wycofany** kolumn w **produktów** tabeli. Aby upewnić się, że schemat wykrywany ignoruje atrybuty określone w elementach XML, należy użyć **InferXmlSchema** metody i określ obszar nazw XML dla **officedata** mają być ignorowane, jak pokazano w Poniższy przykład.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>Zobacz także

- [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
