---
title: Ładowanie informacji o schemacie elementu DataSet z pliku XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 69994c546fea842ffef1c8c43d6d6f5bc35e0629
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151055"
---
# <a name="loading-dataset-schema-information-from-xml"></a>Ładowanie informacji o schemacie elementu DataSet z pliku XML
Schemat <xref:System.Data.DataSet> (jego tabele, kolumny, relacje i ograniczenia) można zdefiniować programowo, utworzony przez **metody Wypełnij** lub **FillSchema** <xref:System.Data.Common.DataAdapter>, lub załadowany z dokumentu XML. Aby załadować informacje o schemacie **Zestawu danych** z dokumentu XML, można użyć metody **ReadXmlSchema** lub **InferXmlSchema** **zestawu danych**. **ReadXmlSchema** umożliwia ładowanie lub wnioskowanie informacji o schemacie **zestawu danych** z dokumentu zawierającego schemat języka XSD (XSD) lub dokumentu XML ze schematem XML. **InferXmlSchema** umożliwia wywnioskowanie schematu z dokumentu XML, ignorując niektóre określone przestrzenie nazw XML.  
  
> [!NOTE]
> Kolejność tabel w **zestawie danych** może nie zostać zachowana podczas przesyłania zestawu **danych** utworzonego w pamięci przy użyciu konstrukcji XSD (takich jak relacje zagnieżdżone) za pomocą usług sieci Web lub serializacji XML. W związku z tym odbiorca **DataSet** nie powinny zależeć od kolejności tabeli w tym przypadku. Jednak kolejność tabel jest zawsze zachowywana, jeśli schemat zestawu **danych, który** jest przesyłany, został odczytany z plików XSD, a nie został utworzony w pamięci.  
  
## <a name="readxmlschema"></a>Readxmlschema  
 Aby załadować schemat **zestawu danych** z dokumentu XML bez ładowania żadnych danych, można użyć metody **ReadXmlSchema** **zestawu danych**. **ReadXmlSchema** tworzy schemat **DataSet** zdefiniowany przy użyciu schematu języka XM (XSD) języka schematu XMD.  
  
 Metoda **ReadXmlSchema** przyjmuje pojedynczy argument nazwy pliku, strumienia lub **czytnika XmlReader** zawierającego dokument XML do załadowania. Dokument XML może zawierać tylko schemat lub może zawierać schemat wyklinowy z elementami XML zawierającymi dane. Aby uzyskać szczegółowe informacje na temat pisania schematu wbudowanego jako schematu XML, zobacz [Wyprowadzanie struktury relacyjnej zestawu danych ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 Jeśli dokument XML przekazany do **ReadXmlSchema** nie zawiera żadnych wbudowanych informacji o schemacie, **program ReadXmlSchema** wywnioskuje schemat z elementów dokumentu XML. Jeśli **Zestaw danych** zawiera już schemat, bieżący schemat zostanie rozszerzony przez dodanie nowych tabel, jeśli jeszcze nie istnieją. Nowe kolumny nie zostaną dodane do istniejących tabel. Jeśli dodawana kolumna już istnieje w **zestawie danych,** ale ma niezgodny typ z kolumną znalezioną w pliku XML, zostanie zgłoszony wyjątek. Aby uzyskać szczegółowe informacje o tym, jak **program ReadXmlSchema** wylicza schemat z dokumentu XML, zobacz [Wnioskowanie struktury relacyjnej zestawu danych z pliku XML](inferring-dataset-relational-structure-from-xml.md).  
  
 Chociaż **ReadXmlSchema** ładuje lub wywnioskować tylko schemat **zestawu danych,** metoda **ReadXml** **zestawu danych** ładuje lub wywnioskowała zarówno schemat, jak i dane zawarte w dokumencie XML. Aby uzyskać więcej informacji, zobacz [Ładowanie zestawu danych z pliku XML](loading-a-dataset-from-xml.md).  
  
 Poniższe przykłady kodu pokazują, jak załadować schemat **zestawu danych** z dokumentu lub strumienia XML. W pierwszym przykładzie przedstawiono nazwę pliku schematu XML przekazywany do metody **ReadXmlSchema.** Drugi przykład pokazuje **System.IO.StreamReader**.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
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
  
## <a name="inferxmlschema"></a>Inferxmlschema  
 Można również poinstruować **zestaw danych,** aby wywnioskować jego schemat z dokumentu XML przy użyciu metody **InferXmlSchema** **zestawu danych**. **InferXmlSchema** działa tak samo, jak zarówno **ReadXml** z **XmlReadMode** **inferSchema** (ładuje dane, jak również schemat wnioskujący), jak i **ReadXmlSchema,** jeśli odczytywany dokument nie zawiera schematu wbudowanego. Jednak **InferXmlSchema** zapewnia dodatkową możliwość umożliwiając określenie określonych obszarów nazw XML, które mają być ignorowane, gdy schemat jest wywnioskowany. **InferXmlSchema** przyjmuje dwa wymagane argumenty: lokalizację dokumentu XML, określoną przez nazwę pliku, strumień lub **XmlReader;** oraz tablicę ciągów obszarów nazw XML, które mają być ignorowane przez operację.  
  
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
  
 Ze względu na atrybuty określone dla elementów w poprzednim dokumencie XML zarówno **ReadXmlSchema,** jak i **Metoda ReadXml** z **XmlReadMode** **of InferSchema** utworzą tabele dla każdego elementu w dokumencie: **Kategorie**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**i **Discontinued**. (Aby uzyskać więcej informacji, zobacz [Wywnioskowanie struktury relacyjnej zestawu danych z XML).](inferring-dataset-relational-structure-from-xml.md) Jednak bardziej odpowiednią strukturą byłoby utworzenie tylko tabel **Kategorie** i **Produkty,** a następnie utworzenie kolumn **CategoryID**, **CategoryName**i **Description** w tabeli **Kategorie** oraz **ProductID**, **ReorderLevel**i **Wycofane** kolumny w tabeli **Produkty.** Aby upewnić się, że wywnioskowany schemat ignoruje atrybuty określone w elementach XML, użyj metody **InferXmlSchema** i określ obszar nazw XML dla **danych biurowych,** które mają być ignorowane, jak pokazano w poniższym przykładzie.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>Zobacz też

- [Używanie języka XML w elemencie DataSet](using-xml-in-a-dataset.md)
- [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](inferring-dataset-relational-structure-from-xml.md)
- [Ładowanie elementu DataSet z pliku XML](loading-a-dataset-from-xml.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
