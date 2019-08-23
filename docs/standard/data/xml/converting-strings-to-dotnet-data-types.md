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
ms.openlocfilehash: 31f277d11cba8191c326d56f017b8acc6503c6b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968712"
---
# <a name="converting-strings-to-net-framework-data-types"></a>Konwertowanie ciągów na typy danych programu .NET Framework
Jeśli chcesz przekonwertować ciąg na typ danych .NET Framework, użyj metody XmlConvert, która pasuje do wymagań aplikacji. Aby uzyskać listę wszystkich metod konwersji dostępnych w klasie XmlConvert, zobacz. <xref:System.Xml.XmlConvert>  
  
 Ciąg zwracany przez metodę **ToString** jest ciągiem wersji, która została przekazana. Ponadto istnieje kilka typów .NET Framework, które konwertują się przy użyciu klasy XmlConvert, ale nie używają metod w klasie **System. Convert** . Klasa **XmlConvert** jest zgodna ze specyfikacją typu danych schematu XML (XSD) i ma typ danych, na który mapowanie XmlConvert może być mapowane.  
  
 Poniższa tabela zawiera listę typów danych .NET Framework i typy ciągów, które są zwracane przy użyciu mapowania typu danych schematu XML (XSD). Te typy .NET Framework nie mogą być przetwarzane przy użyciu funkcji **System. Convert**.  
  
|Typ programu .NET Framework|Zwrócony ciąg|  
|-------------------------|---------------------|  
|Boolean|"true", "false"|  
|Single. PositiveInfinity|INF|  
|Single. NegativeInfinity|"-INF"|  
|Double. PositiveInfinity|INF|  
|Double. NegativeInfinity|"-INF"|  
|DataGodzina|Format to "RRRR-MM-DDTgg: mm: sszzzzzz" i jego podzestawy.|  
|Timespan|Format to PnYnMnTnHnMnS, `P2Y10M15DT10H30M20S` czyli okres 2 lat, 10 miesięcy, 15 dni, 10 godzin, 30 minut i 20 sekund.|  
  
> [!NOTE]
> W przypadku konwertowania dowolnego typu .NET Framework wymienionego w tabeli na ciąg przy użyciu metody **ToString** zwracany ciąg nie jest typem podstawowym, ale typ ciągu schematu XML (XSD).  
  
 Typ wartości **DateTime** i **TimeSpan** różni się w tym, że element **DateTime** reprezentuje chwilę w czasie, podczas gdy obiekt **TimeSpan** reprezentuje przedział czasu. Formaty **DateTime** i **TimeSpan** są określone w specyfikacji typów danych schematu XML (XSD). Przykład:  
  
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
  
 Jeśli jednak konwertujesz ciąg na **wartość Boolean**, **Single**lub **Double**, zwracany typ .NET Framework nie jest taki sam jak typ zwracany podczas używania klasy **System. Convert** .  
  
## <a name="string-to-boolean"></a>Ciąg do wartości logicznej  
 W poniższej tabeli przedstawiono typ, który jest generowany dla danego ciągu wejściowego podczas konwertowania ciągu na **wartość logiczną** przy użyciu metody **ToBoolean** .  
  
|Prawidłowy parametr wejściowy ciągu|Typ danych wyjściowych .NET Framework|  
|----------------------------------|--------------------------------|  
|"true"|Wartość logiczna. true|  
|"1"|Wartość logiczna. true|  
|false|Boolean.False|  
|„0”|Boolean.False|  
  
 Na przykład, uwzględniając następujący kod XML:  
  
 **Dane wejściowe**  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 Obie te wartości można zrozumieć przy użyciu poniższego kodu, a **bValue** to **System. Boolean. true**:  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a>Ciąg do jednego  
 W poniższej tabeli przedstawiono typ, który jest generowany dla danych wejściowych ciągów, podczas konwertowania ciągu na **pojedynczy** przy użyciu metody **ToSingle —** .  
  
|Prawidłowy parametr wejściowy ciągu|Typ danych wyjściowych .NET Framework|  
|----------------------------------|--------------------------------|  
|INF|Single. PositiveInfinity|  
|"-INF"|Single. NegativeInfinity|  
  
## <a name="string-to-double"></a>Ciąg na Double  
 W poniższej tabeli przedstawiono typ, który jest generowany dla danych wejściowych ciągów, podczas konwertowania ciągu na **pojedynczy** przy użyciu metody **ToDouble —** .  
  
|Prawidłowy parametr wejściowy ciągu|Typ danych wyjściowych .NET Framework|  
|----------------------------------|--------------------------------|  
|INF|Double. PositiveInfinity|  
|"-INF"|Double. NegativeInfinity|  
  
 Poniższy kod zapisuje `<Infinity>INF</Infinity>`:  
  
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
