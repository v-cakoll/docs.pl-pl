---
title: Konwersja typów danych XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: b0cdab8861ca50b40ce2b422fcc1acf16e2f2273
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711093"
---
# <a name="conversion-of-xml-data-types"></a>Konwersja typów danych XML
Większość metod znalezionych w klasie **XmlConvert** służy do konwertowania danych między ciągami i formatami o jednoznacznie określonym typie. Metody są niezależne od ustawień regionalnych. Oznacza to, że nie uwzględniają żadnych ustawień regionalnych podczas konwersji.  
  
## <a name="reading-string-as-types"></a>Odczytywanie ciągu jako typów  
 Poniższy przykład odczytuje ciąg i konwertuje go na typ **DateTime** .  
  
 Uwzględniając następujące dane wejściowe XML:  
  
 **Dane wejściowe**  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 Ten kod konwertuje ciąg na format **DateTime** :  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a>Pisanie ciągów jako typów  
 Poniższy przykład odczytuje wartość **Int32** i konwertuje ją na ciąg.  
  
 Uwzględniając następujące dane wejściowe XML:  
  
 **Dane wejściowe**  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 Ten kod konwertuje wartość **Int32** na **ciąg**:  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a>Zobacz także

- [Konwertowanie ciągów na typy danych programu .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
- [Konwertowanie typów programu .NET Framework na ciągi](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
