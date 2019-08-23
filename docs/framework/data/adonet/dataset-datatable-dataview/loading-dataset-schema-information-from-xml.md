---
title: Ładowanie informacji o schemacie elementu DataSet z pliku XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: b895ad59ed0ab2542ecdfb04b6db559e12edc55c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928383"
---
# <a name="loading-dataset-schema-information-from-xml"></a>Ładowanie informacji o schemacie elementu DataSet z pliku XML
Schemat <xref:System.Data.DataSet> (tabele, kolumny, relacje i ograniczenia) można definiować programowo, tworząc przy użyciu metod <xref:System.Data.Common.DataAdapter> **Fill** lub **FillSchema** lub załadowanych z dokumentu XML. Aby załadować informacje o schemacie **zestawu danych** z dokumentu XML, można użyć metody **ReadXmlSchema** lub **InferXmlSchema** **zestawu danych**. **ReadXmlSchema** umożliwia ładowanie lub wnioskowanie informacji o schemacie **zestawu danych** z dokumentu zawierającego schemat języka definicji schematu XML (XSD) lub dokument XML z wbudowanym schematem XML. **InferXmlSchema** umożliwia wywnioskowanie schematu z dokumentu XML podczas ignorowania określonych przestrzeni nazw XML.  
  
> [!NOTE]
> Porządkowanie tabeli w **zestawie danych** może nie być zachowywane podczas korzystania z usług sieci Web lub serializacji XML do transferu **zestawu danych** , który został utworzony w pamięci przy użyciu konstrukcji XSD (takich jak relacje zagnieżdżone). W związku z tym odbiorca **zestawu danych** nie powinien zależeć od uporządkowania tabeli w tym przypadku. Jednak porządkowanie tabeli jest zawsze zachowywane, jeśli schemat transferu **danych** został odczytany z plików XSD, zamiast tworzyć w pamięci.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 Aby załadować schemat **zestawu danych** z dokumentu XML bez ładowania jakichkolwiek danych, można użyć metody **ReadXmlSchema** **zestawu danych**. **ReadXmlSchema** tworzy schemat **zestawu danych** zdefiniowany przy użyciu schematu języka definicji schematu XML (XSD).  
  
 Metoda **ReadXmlSchema** przyjmuje pojedynczy argument nazwy pliku, strumienia lub elementu **XMLREADER** zawierającego dokument XML do załadowania. Dokument XML może zawierać tylko schemat lub może zawierać schemat w tekście z elementami XML zawierającymi dane. Aby uzyskać szczegółowe informacje na temat pisania schematu wbudowanego jako schematu XML, zobacz [wyprowadzanie relacyjnej struktury zestawu danych ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 Jeśli dokument XML przesłany do **ReadXmlSchema** nie zawiera wbudowanych informacji o schemacie, **ReadXmlSchema** będzie wnioskować o schemat z elementów w dokumencie XML. Jeśli **zestaw danych** zawiera już schemat, bieżący schemat zostanie rozszerzony przez dodanie nowych tabel, jeśli jeszcze nie istnieją. Nowe kolumny nie zostaną dodane do istniejących tabel. Jeśli dodawana kolumna już istnieje w **zestawie danych** , ale ma niezgodny typ z kolumną znalezioną w kodzie XML, zgłaszany jest wyjątek. Aby uzyskać szczegółowe informacje na temat sposobu, w jaki program **ReadXmlSchema** wnioskuje schemat z dokumentu XML, zobacz wnioskowanie o [relacyjnej strukturze zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).  
  
 Mimo że **ReadXmlSchema** ładuje lub wnioskuje tylko schemat **zestawu danych**, Metoda **ReadXml** **zestawu danych** ładuje lub wnioskuje schemat oraz dane zawarte w dokumencie XML. Aby uzyskać więcej informacji, zobacz [Ładowanie zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).  
  
 Poniższy przykład kodu pokazuje, jak załadować schemat **zestawu danych** z dokumentu lub strumienia XML. Pierwszy przykład przedstawia nazwę pliku schematu XML, który jest przesyłany do metody **ReadXmlSchema** . W drugim przykładzie pokazano element **System. IO. StreamReader**.  
  
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
 Można również nakazać **zestawowi danych** wywnioskowanie schematu z dokumentu XML przy użyciu metody **InferXmlSchema** **zestawu danych**. Funkcja **InferXmlSchema** działa tak samo jak w przypadku obu **ReadXml** z atrybutem XmlReadMode of **InferSchema** (ładuje dane, a także schemat wniosku) i **ReadXmlSchema** , jeśli dokument jest odczytywany nie zawiera wbudowanego schematu. **InferXmlSchema** oferuje jednak dodatkową możliwość, która umożliwia określenie określonych przestrzeni nazw XML, które mają być ignorowane, gdy schemat zostanie wywnioskowany. **InferXmlSchema** przyjmuje dwa wymagane argumenty: lokalizację dokumentu XML, określoną przez nazwę pliku, strumień lub element **XmlReader**; i tablica ciągów przestrzeni nazw XML, która ma być ignorowana przez operację.  
  
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
  
 Ze względu na atrybuty określone dla elementów w poprzednim dokumencie XML, Metoda **ReadXmlSchema** i Metoda **ReadXml** z atrybutem XmlReadMode klasy **InferSchema** utworzy tabele dla każdego elementu w dokumentu **Kategorie**, **IDkategorii**, **CategoryName**, **Opis**, **produkty**, **ProductID**, **ReorderLevel**i **wycofane**. (Aby uzyskać więcej informacji, zobacz [wnioskowanie relacyjnej struktury zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)). Jednak bardziej odpowiednią strukturą jest utworzenie tylko tabel **Kategorie** i **produkty** , a następnie utworzenie kolumn **IDkategorii**, **CategoryName**i **Description** w tabeli **Kategorie** i  **Kolumny ProductID**, **ReorderLevel**i uncontinued w tabeli **Products** . Aby upewnić się, że wywnioskowany schemat ignoruje atrybuty określone w elementach XML, należy użyć metody **InferXmlSchema** i określić przestrzeń nazw XML do ignorowania, jak pokazano w poniższym przykładzie.  
  
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
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
