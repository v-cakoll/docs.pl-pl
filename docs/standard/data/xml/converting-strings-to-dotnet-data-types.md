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
ms.openlocfilehash: 5954a580ca9b7f00f6339f70d0df9d20ba96715e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576582"
---
# <a name="converting-strings-to-net-framework-data-types"></a>Konwertowanie ciągów na typy danych programu .NET Framework
Do przekonwertowania ciągu na typ danych .NET Framework, należy użyć **obiekt XmlConvert** — metoda, która pasuje do wymagań aplikacji. Aby uzyskać listę wszystkich metod konwersji danych dostępne w **obiekt XmlConvert** , zobacz <xref:System.Xml.XmlConvert>.  
  
 Ciąg zwrócony przez **ToString** metoda jest wersję danych, który jest przekazywany w ciągu. Ponadto istnieje kilka typów .NET Framework, które konwersji, używając **obiekt XmlConvert** klasy jeszcze nie używaj metod w **System.Convert** klasy. **Obiekt XmlConvert** klasy zgodna ze specyfikacją typu danych schematu XML (XSD) i ma typ, który danych **obiekt XmlConvert** można mapować.  
  
 W poniższej tabeli wymieniono typy danych .NET Framework i typów ciągów, które są zwracane przy użyciu mapowanie typu danych schematu XML (XSD). Nie można przetworzyć tych typów .NET Framework za pomocą **System.Convert**.  
  
|Typ programu .NET Framework|Zwrócony ciąg|  
|-------------------------|---------------------|  
|Boolean|"true", "fałsz"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DataGodzina|Format to "RRRR-MM-ddTHH:mm:sszzzzzz" i jego podzestawy.|  
|Zakres czasu|Format jest PnYnMnTnHnMnS czyli `P2Y10M15DT10H30M20S` jest równa 2 lata, 10 miesięcy, 15 dni, 10 godzin, 30 minut, i 20 sekund.|  
  
> [!NOTE]
>  Jeśli konwertowanie dowolnego typu .NET Framework wymieniony w tabeli, aby parametry za pomocą **ToString** metody, zwracany ciąg nie jest typu podstawowego, ale typ ciągu schematu XML (XSD).  
  
 **DateTime** i **Timespan** typ wartości różni się w tym **DateTime** reprezentuje moment w czasie, podczas gdy **TimeSpan** reprezentuje przedział czasu. **DateTime** i **Timespan** formaty są określone w specyfikacji typów danych schematu XML (XSD). Na przykład:  
  
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
  
 Poniższy kod konwertuje całkowitą na ciąg:  
  
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
  
 Jednak jeśli konwertowania ciągu na **logiczna**, **pojedynczego**, lub **podwójne**, zwraca typ .NET Framework nie jest taki sam jak typ zwracany po użyciu **System.Convert** klasy.  
  
## <a name="string-to-boolean"></a>Ciąg na wartość logiczną  
 W poniższej tabeli przedstawiono, jakiego typu jest generowane dla danego ciągów wejściowych podczas konwertowania ciągu na **logiczna** przy użyciu **ToBoolean** metody.  
  
|Parametr wejściowy prawidłowy ciąg|Typ danych wyjściowych .NET framework|  
|----------------------------------|--------------------------------|  
|wartość "prawda"|Boolean.True|  
|"1"|Boolean.True|  
|"false"|Boolean.False|  
|„0”|Boolean.False|  
  
 Na przykład podać następujący kod XML:  
  
 **Dane wejściowe**  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 Zarówno zostały zrozumiane przez następujący kod i **bDane wartości** jest **System.Boolean.True**:  
  
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
 W poniższej tabeli przedstawiono, jakiego typu jest generowane dla danego ciągów wejściowych podczas konwertowania ciągu na **pojedynczego** przy użyciu **tosingle —** metody.  
  
|Parametr wejściowy prawidłowy ciąg|Typ danych wyjściowych .NET framework|  
|----------------------------------|--------------------------------|  
|"INF"|Single.PositiveInfinity|  
|"-INF"|Single.NegativeInfinity|  
  
## <a name="string-to-double"></a>Ciąg o podwójnej precyzji  
 W poniższej tabeli przedstawiono, jakiego typu jest generowane dla danego ciągów wejściowych podczas konwertowania ciągu na **pojedynczego** przy użyciu **todouble —** metody.  
  
|Parametr wejściowy prawidłowy ciąg|Typ danych wyjściowych .NET framework|  
|----------------------------------|--------------------------------|  
|"INF"|Double.PositiveInfinity|  
|"-INF"|Double.NegativeInfinity|  
  
 Poniższy kod zapisy `<Infinity>INF</Infinity>`:  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja typów danych XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [Konwertowanie typów programu .NET Framework na ciągi](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
