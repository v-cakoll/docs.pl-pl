---
title: Zmienianie deklaracji przestrzeni nazw w dokumencie XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a6b80a885f43facf4b3d4dd1dcb56d937d4f8de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669163"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Zmienianie deklaracji przestrzeni nazw w dokumencie XML
**XmlDocument** udostępnia deklaracje przestrzeni nazw i **xmlns** atrybutów jako część document object model. Są one przechowywane w **XmlDocument**, dzięki czemu podczas zapisywania dokumentu, można zachować w niej lokalizacja tych atrybutów. Zmiana tych atrybutów nie ma wpływu na **nazwa**, **NamespaceURI**, i **prefiksu** właściwości innych węzłów w drzewie. Na przykład, jeśli załadować dokument a następnie `test` element ma **NamespaceURI** `123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 Jeśli usuniesz `xmlns` atrybutu w następujący sposób, a następnie `test` element środki, nieopłacone **NamespaceURI** z `123`.  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 Podobnie jeśli dodasz innego `xmlns` atrybutu `doc` elementu w następujący sposób, a następnie `test` element środki, nieopłacone **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 W związku z tym, zmieniając `xmlns` atrybuty będzie miał znaczenia, dopóki nie można zapisać i ponownie załaduj **XmlDocument** obiektu.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
