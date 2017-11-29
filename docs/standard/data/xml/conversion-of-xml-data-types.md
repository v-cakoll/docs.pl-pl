---
title: "Konwersja typów danych XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2f5f5d27b3d21ff12f5eea7613e80e73c5b6597
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="conversion-of-xml-data-types"></a>Konwersja typów danych XML
Znaleziono większości metod w **obiekt XmlConvert** klasy służą do konwertowania danych pomiędzy ciągami a jednoznacznie formatów. Metody są niezależnie od ustawień regionalnych. Oznacza to, że nie uwzględniają wszystkie ustawienia regionalne podczas konwersji.  
  
## <a name="reading-string-as-types"></a>Parametry odczytu jako typy  
 Poniższy przykład odczytuje ciąg i konwertuje ją na **DateTime** typu.  
  
 Należy podać następujące dane wejściowe XML:  
  
 **Dane wejściowe**  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 Ten kod konwertuje ciąg na **DateTime** format:  
  
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
  
 Należy podać następujące dane wejściowe XML:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Konwertowanie ciągów na typy danych programu .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [Konwertowanie typów programu .NET Framework na ciągi](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
