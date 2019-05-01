---
title: Konwertowanie ciągów na typy danych programu .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 376dd9df4666193f8e5a6be83f3fcaf5dc32f1a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62027267"
---
# <a name="converting-strings-to-net-framework-data-types"></a>Konwertowanie ciągów na typy danych programu .NET Framework
Do przekonwertowania ciągu na typ danych .NET Framework, należy użyć **obiekt XmlConvert** metodę, która spełnia wymagania aplikacji. Aby uzyskać listę wszystkich metod konwersji dostępnych w **obiekt XmlConvert** klasy, zobacz <xref:System.Xml.XmlConvert>.  
  
 Ciąg zwracany z **ToString** metodą jest wersję danych, które są przekazywane w ciągu. Ponadto, istnieje kilka typów programu .NET Framework, które konwertują przy użyciu **obiekt XmlConvert** klasy, ale nie należy używać metod w **System.Convert** klasy. **Obiekt XmlConvert** klasy następuje określenie typów danych schematu XML (XSD) i zawiera dane typu **obiekt XmlConvert** można mapować.  
  
 Poniższa tabela zawiera listę typów danych programu .NET Framework i typy parametrów, które są zwracane wartości przy użyciu mapowania typów danych schematu XML (XSD). Nie można przetworzyć tych typów programu .NET Framework za pomocą **System.Convert**.  
  
|Typ programu .NET Framework|Ciąg zwracany|  
|-------------------------|---------------------|  
|Boolean|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DataGodzina|Format to "RRRR-MM-ddTHH:mm:sszzzzzz" i jego podzbiory.|  
|Przedział czasu|Format jest PnYnMnTnHnMnS czyli `P2Y10M15DT10H30M20S` to wartość typu duration 2 lat, 10 miesięcy, 15 dni, 10 godzin, 30 minut, a 20 sekund.|  
  
> [!NOTE]
>  Jeśli konwersja żadnego z typów programu .NET Framework wymienione w tabeli na ciąg za pośrednictwem **ToString** metody, w zwracanym ciągu nie jest typu podstawowego, ale typ ciągu schematu XML (XSD).  
  
 **Daty/godziny** i **Timespan** typ wartości różni się w tym **daty/godziny** reprezentuje moment w czasie, natomiast **TimeSpan** reprezentuje przedział czasu. **Daty/godziny** i **Timespan** formaty są określone w specyfikacji typy danych schematu XML (XSD). Na przykład:  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 **Output**  
  
 `<Date>2001-08-04T00:00:00</Date>`.  
  
 Poniższy kod konwertuje liczbę całkowitą na ciąg:  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 **Output**  
  
 `<Number>200</Number>`  
  
 Jednak Jeśli konwertujesz ciąg **logiczna**, **pojedynczego**, lub **Double**, typ .NET Framework, która jest zwracana nie jest taki sam jak typ zwracany, gdy za pomocą **System.Convert** klasy.  
  
## <a name="string-to-boolean"></a>Ciąg, aby atrybut typu wartość logiczna  
 W poniższej tabeli przedstawiono, jaki typ jest generowany dla danego ciągi wejściowe podczas konwertowania ciągu do **logiczna** przy użyciu **ToBoolean** metody.  
  
|Parametr wejściowy prawidłowy ciąg|Typ danych wyjściowych .NET framework|  
|----------------------------------|--------------------------------|  
|"true"|Boolean.True|  
|"1"|Boolean.True|  
|"false"|Boolean.False|  
|„0”|Boolean.False|  
  
 Na przykład biorąc pod uwagę następujący kod XML:  
  
 **Dane wejściowe**  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 Jednocześnie może być rozumiany przez następujący kod i **bDane wartości** jest **System.Boolean.True**:  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a>Ciąg na wartość typu Single  
 W poniższej tabeli przedstawiono, jaki typ jest generowany dla danego ciągi wejściowe podczas konwertowania ciągu do **pojedynczego** przy użyciu **tosingle —** metody.  
  
|Parametr wejściowy prawidłowy ciąg|Typ danych wyjściowych .NET framework|  
|----------------------------------|--------------------------------|  
|"INF"|Single.PositiveInfinity|  
|"-INF"|Single.NegativeInfinity|  
  
## <a name="string-to-double"></a>Ciąg na wartość typu Double  
 W poniższej tabeli przedstawiono, jaki typ jest generowany dla danego ciągi wejściowe podczas konwertowania ciągu do **pojedynczego** przy użyciu **todouble —** metody.  
  
|Parametr wejściowy prawidłowy ciąg|Typ danych wyjściowych .NET framework|  
|----------------------------------|--------------------------------|  
|"INF"|Double.PositiveInfinity|  
|"-INF"|Double.NegativeInfinity|  
  
 Poniższy kod zapisów `<Infinity>INF</Infinity>`:  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a>Zobacz także

- [Konwersja typów danych XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [Konwertowanie typów programu .NET Framework na ciągi](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
