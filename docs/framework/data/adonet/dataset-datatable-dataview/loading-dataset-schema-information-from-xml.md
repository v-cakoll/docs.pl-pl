---
title: Ładowanie informacji o schemacie zestawu danych z pliku XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 4b212a7233e6eec93cdce3e521b58e08745e35e0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="loading-dataset-schema-information-from-xml"></a>Ładowanie informacji o schemacie zestawu danych z pliku XML
Schemat <xref:System.Data.DataSet> (jego tabele, kolumny, relacji i ograniczeń) mogą być definiowane programowo, utworzone przez **wypełnienia** lub **FillSchema** metody <xref:System.Data.Common.DataAdapter>, lub załadowane z Dokument XML. Aby załadować **zestawu danych** informacji o schemacie z dokumentu XML możesz użyć dowolnej **ReadXmlSchema** lub **InferXmlSchema** metody **zestawudanych**. **ReadXmlSchema** umożliwia ładowanie lub wnioskować **DataSet** informacji schematu z dokumentu zawierającego schematu (XSD) języka definicji schematu XML lub dokument XML z wbudowanego schematu XML. **InferXmlSchema** pozwala na wnioskowanie schematu z dokumentu XML podczas ignorowanie określonych przestrzeni nazw XML, który określisz.  
  
> [!NOTE]
>  Określanie kolejności w tabeli **DataSet** nie mogą zostać zachowane, korzystając z usług sieci Web lub serializacji XML do transferu **zestawu danych** utworzony w pamięci przy użyciu konstrukcji XSD (na przykład relacjach zagnieżdżonych). W związku z tym odbiorcy **DataSet** powinien niezależnie od tabeli w takim przypadku porządkowania. Jednak tabeli porządkowania jest zawsze zachowywany, jeśli schemat **zestawu danych** przesyłania zostały odczytane z plików XSD, zamiast tworzona w pamięci.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 Można załadować schematu **DataSet** z dokumentu XML bez ładowania danych, możesz użyć **ReadXmlSchema** metody **zestawu danych**. **ReadXmlSchema** tworzy **DataSet** schematu zdefiniowane przy użyciu schematu (XSD) języka definicji schematu XML.  
  
 **ReadXmlSchema** metoda przyjmuje jeden argument nazwy pliku, typu stream, lub **XmlReader** zawierający można załadować dokumentu XML. Dokument XML może zawierać tylko schematu lub mogą zawierać wbudowanego schematu z elementów XML z danymi. Aby uzyskać informacje na temat pisania wbudowanego schematu XML Schema, zobacz [wyprowadzanie struktury relacyjne zestawu danych z schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 Jeśli dokument XML przekazany do **ReadXmlSchema** nie zawiera żadnych informacji schemat wbudowany **ReadXmlSchema** wywnioskuje schematu z elementów w dokumencie XML. Jeśli **DataSet** już zawiera schemat, bieżący schemat zostanie rozszerzony, dodając nowe tabele, jeśli jeszcze nie istnieje. Nowe kolumny nie zostanie dodany do dodane do istniejących tabel. Jeśli kolumna dodawany już istnieje w **DataSet** , ale ma niezgodny typ z kolumną znaleziony w pliku XML, jest zgłaszany wyjątek. Aby uzyskać szczegółowe informacje o tym, jak **ReadXmlSchema** wnioskuje schemat dokumentu XML, zobacz temat [wnioskowanie struktury zestawu danych relacyjnych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).  
  
 Mimo że **ReadXmlSchema** ładuje lub wnioskuje schemat z **DataSet**, **ReadXml** metody **DataSet** ładuje lub wnioskuje zarówno schemat i dane zawarte w dokumencie XML. Aby uzyskać więcej informacji, zobacz [podczas ładowania zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).  
  
 W poniższych przykładach kodu przedstawiają sposób załadować **DataSet** schematu z dokumentu XML lub strumienia. W pierwszym przykładzie pokazano, nazwa pliku schematu XML przekazywany do **ReadXmlSchema** metody. W drugim przykładzie **System.IO.StreamReader**.  
  
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
 Można także skonfigurować **DataSet** do wywnioskowany jego schemat dokumentu XML przy użyciu **InferXmlSchema** metody **zestawu danych**. **InferXmlSchema** działa tak samo, jak wykonać obie czynności **ReadXml** z **XmlReadMode** z **InferSchema** (ładuje dane jak również wnioskuje schemat), a **ReadXmlSchema** Jeśli odczytu dokumentu zawiera nie wbudowany schemat. Jednak **InferXmlSchema** zapewnia dodatkowe możliwości pozwala określić określonej przestrzeni nazw XML ma być ignorowane podczas jest wywnioskowany schemat. **InferXmlSchema** przyjmuje dwa argumenty wymagane: Lokalizacja dokumentu w formacie XML, określony przez nazwę pliku, typu stream, lub **XmlReader**; i przestrzeni nazw XML mają być ignorowane przez operację tablicy ciągów.  
  
 Rozważmy na przykład następujący kod XML:  
  
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
  
 Z powodu atrybutów określonych dla elementów w poprzednim dokument XML zarówno **ReadXmlSchema** — metoda i **ReadXml** metody z **XmlReadMode** z **InferSchema** utworzyć tabele dla każdego elementu w dokumencie: **kategorii**, **CategoryID**, **CategoryName**, **Opis**, **produktów**, **ProductID**, **ReorderLevel**, i **zaprzestać**. (Aby uzyskać więcej informacji, zobacz [wnioskowanie struktury zestawu danych relacyjnych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) Jednak bardziej odpowiednie struktury będzie można utworzyć tylko **kategorii** i **produktów** tabel, a następnie utworzyć **CategoryID**, **CategoryName** , i **opis** kolumn w **kategorii** tabeli, i **ProductID**, **ReorderLevel**, i **Wycofany** kolumn w **produktów** tabeli. Aby upewnić się, że wywnioskowany schemat ignoruje atrybuty określone w elementów XML, użyj **InferXmlSchema** metodę i określić przestrzeń nazw XML dla **officedata** mają być ignorowane, jak pokazano w Poniższy przykład.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
