---
title: Zapisywanie zawartości elementu DataSet jako danych XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: bf73adff89ca5cad3a71239421ac826105a387cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785220"
---
# <a name="writing-dataset-contents-as-xml-data"></a>Zapisywanie zawartości elementu DataSet jako danych XML
W ADO.NET można napisać reprezentację <xref:System.Data.DataSet>XML obiektu, z lub bez jego schematu. Jeśli informacje o schemacie są dołączone do kodu XML, są zapisywane przy użyciu języka definicji schematu XML (XSD). Schemat zawiera definicje <xref:System.Data.DataSet> tabeli, a także relacje i definicje ograniczeń.  
  
 Gdy obiekt <xref:System.Data.DataSet> jest zapisywana jako dane XML, wiersze <xref:System.Data.DataSet> w programie są zapisywane w ich bieżących wersjach. <xref:System.Data.DataSet> Jednak może być również zapisany jako DiffGram, tak aby wszystkie bieżące i oryginalne wartości wierszy były uwzględniane.  
  
 Reprezentacja <xref:System.Data.DataSet> XML można zapisać do pliku, strumienia, elementu **XmlWriter**lub ciągu. Te opcje zapewniają dużą elastyczność w zakresie transportu reprezentacji <xref:System.Data.DataSet>XML. Aby uzyskać reprezentację <xref:System.Data.DataSet> XML jako ciąg, użyj metody **GetXml —** , jak pokazano w poniższym przykładzie.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml —** zwraca reprezentację <xref:System.Data.DataSet> XML bez informacji o schemacie. Aby zapisać informacje o schemacie z <xref:System.Data.DataSet> (jako schemat XML) w ciągu, użyj elementu **GetXmlSchema**.  
  
 Aby napisać <xref:System.Data.DataSet> plik, strumień lub **XmlWriter**, użyj metody **WriteXml** . Pierwszym parametrem przekazywanym do **WriteXml** jest miejsce docelowe danych wyjściowych XML. Na przykład Przekaż ciąg zawierający nazwę pliku, obiekt **System. IO. TextWriter** i tak dalej. Aby określić sposób zapisywania danych wyjściowych XML, można przekazać opcjonalny drugi parametr **XmlWriteMode** .  
  
 W poniższej tabeli przedstawiono opcje elementu **XmlWriteMode**.  
  
|XmlWriteMode — opcja|Opis|  
|-------------------------|-----------------|  
|**IgnoreSchema**|Zapisuje bieżącą zawartość <xref:System.Data.DataSet> jako dane XML, bez schematu XML. Domyślnie włączone.|  
|**WriteSchema**|Zapisuje bieżącą zawartość <xref:System.Data.DataSet> jako dane XML przy użyciu struktury relacyjnej jako wbudowanego schematu XML.|  
|**DiffGram**|Zapisuje cały <xref:System.Data.DataSet> element w formacie DiffGram, w tym pierwotne i bieżące wartości. Aby uzyskać więcej informacji, zobacz [DiffGrams](diffgrams.md).|  
  
 Gdy piszesz reprezentację <xref:System.Data.DataSet> **XML zawierającą obiekty** , najprawdopodobniej chcesz, aby otrzymany kod XML miał wszystkie wiersze podrzędne każdej relacji zagnieżdżonej w pokrewnych elementach nadrzędnych. Aby to osiągnąć, należy ustawić **Właściwość zagnieżdżoną** elementu na **wartość true** , gdy dodasz **relację** do <xref:System.Data.DataSet>obiektu. Aby uzyskać więcej informacji, zobacz [zagnieżdżanie relacji](nesting-datarelations.md)danych.  
  
 Poniżej przedstawiono dwa przykłady sposobu pisania reprezentacji <xref:System.Data.DataSet> XML do pliku. Pierwszy przykład przekazuje nazwę pliku XML w postaci ciągu do **WriteXml**. Drugi przykład przekazuje obiekt **System. IO. StreamWriter —** .  
  
```vb  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema)  
```  
  
```csharp  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema);  
```  
  
```vb  
Dim xmlSW As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xml")  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema)  
xmlSW.Close()  
```  
  
```csharp  
System.IO.StreamWriter xmlSW = new System.IO.StreamWriter("Customers.xml");  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema);  
xmlSW.Close();  
```  
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a>Mapowanie kolumn do elementów XML, atrybutów i tekstu  
 Można określić sposób, w jaki kolumna tabeli jest reprezentowana w kodzie XML przy użyciu właściwości **ColumnMapping** obiektu **DataColumn** . W poniższej tabeli przedstawiono różne wartości **mapowaniatype** dla właściwości **ColumnMapping** kolumny tabeli oraz otrzymany kod XML.  
  
|Wartość MappingType|Opis|  
|-----------------------|-----------------|  
|**Element**|Domyślnie włączone. Kolumna jest zapisywana jako element XML, gdzie ColumnName jest nazwą elementu, a zawartość kolumny jest zapisywana jako tekst elementu. Przykład:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Atrybut**|Kolumna jest zapisywana jako atrybut XML elementu XML dla bieżącego wiersza, gdzie ColumnName jest nazwą atrybutu, a zawartość kolumny jest zapisywana jako wartość atrybutu. Na przykład:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|Zawartość kolumny jest zapisywana jako tekst w elemencie XML dla bieżącego wiersza. Przykład:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> Należy zauważyć, że nie można ustawić elementu **SimpleContent** dla kolumny tabeli, która zawiera kolumny **elementów** lub relacje zagnieżdżone.|  
|**Ukryte**|Kolumna nie jest zapisywana w danych wyjściowych XML.|  
  
## <a name="see-also"></a>Zobacz także

- [Używanie języka XML w elemencie DataSet](using-xml-in-a-dataset.md)
- [Elementy DiffGram](diffgrams.md)
- [Zagnieżdżanie elementów DataRelation](nesting-datarelations.md)
- [Zapisywanie informacji o schemacie elementu DataSet jako pliku XSD](writing-dataset-schema-information-as-xsd.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
