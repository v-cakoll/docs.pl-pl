---
title: "Zmiana właściwości Namespace prefiksu"
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
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7ce6e4b705188b9c1d0949703991633e3f450689
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="changing-namespace-prefix-properties"></a>Zmiana właściwości Namespace prefiksu
**XmlNode** klasa pozwala na zmianę skojarzonych z danym węźle prefiks przestrzeni nazw. Na przykład poniższy kod przedstawia prefiks elementu zostanie zmieniona.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 **Dane wyjściowe**  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 Zmiana prefiksu węzła nie zmienia jego przestrzeni nazw. Przestrzeń nazw można ustawić tylko w przypadku, gdy węzeł zostanie utworzony. Podczas utrwalania drzewa, nowe atrybuty przestrzeni nazw może się trwale do zaspokojenia prefiksu, które można ustawić. Jeśli nie można utworzyć nowej przestrzeni nazw, prefiks zostanie zmieniona, więc węzeł zachowuje lokalnej nazwy i przestrzeni nazw. W poniższym przykładzie przedstawiono dodawany atrybut przestrzeni nazw.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 **Dane wyjściowe**  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 Po drzewie został utrwalony na ciąg w wyniku wywołania **dokumentu. InnerXml**, `xmlns:a='123'` atrybut został dodany do zachowania przestrzeń nazw `test` elementu. Było `'123'`, i pozostaje `'123'`.  
  
## <a name="see-also"></a>Zobacz też  
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
