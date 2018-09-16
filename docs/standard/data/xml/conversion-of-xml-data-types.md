---
title: Konwersja typów danych XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cec2b85c55871c8a21a74e79cfcdd041fa063bec
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664582"
---
# <a name="conversion-of-xml-data-types"></a>Konwersja typów danych XML
Większość metod znaleziony w **obiekt XmlConvert** klasy są używane do konwersji danych pomiędzy ciągami a silnie typizowane formatów. Metody są niezależnie od ustawień regionalnych. Oznacza to, że nie uwzględniają żadnych ustawień regionalnych podczas wykonywania konwersji.  
  
## <a name="reading-string-as-types"></a>Parametry odczytu jako typy  
 Poniższy przykład odczytuje parametry i konwertuje ją na **daty/godziny** typu.  
  
 Biorąc pod uwagę następujące dane wejściowe XML:  
  
 **Dane wejściowe**  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 Ten kod konwertuje ciąg na **daty/godziny** formatu:  
  
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
  
## <a name="writing-strings-as-types"></a>Zapisywanie ciągów jako typy  
 Następujące przykładowe odczyty **Int32** i konwertuje ją na ciąg.  
  
 Biorąc pod uwagę następujące dane wejściowe XML:  
  
 **Dane wejściowe**  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 Ten kod konwertuje **Int32** do **ciąg**:  
  
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
