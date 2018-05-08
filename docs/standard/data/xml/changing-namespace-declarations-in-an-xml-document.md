---
title: Zmiana deklaracji Namespace w dokumencie XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fa41e8a4e8f5a15d789ddc81c2b94072c6f16b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Zmiana deklaracji Namespace w dokumencie XML
**XmlDocument** przedstawia deklaracje przestrzeni nazw i **xmlns** atrybuty jako część modelu obiektu dokumentu. Są one przechowywane w **XmlDocument**, dlatego podczas zapisywania dokumentu, można zachować lokalizację te atrybuty. Zmiana tych atrybutów nie ma wpływu na **nazwa**, **NamespaceURI**, i **prefiksu** właściwości innych węzłów w drzewie. Na przykład, jeśli załadować następującego dokumentu a następnie `test` element ma **NamespaceURI** `123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 Po usunięciu `xmlns` atrybutu w następujący sposób, a następnie `test` element nadal ma **NamespaceURI** z `123`.  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 Podobnie jeśli dodasz do innej `xmlns` atrybutu `doc` elementu w następujący sposób, a następnie `test` element nadal ma **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 W związku z tym zmiana `xmlns` atrybutów nie będzie miał znaczenia dopóki Zapisz i ponownie załaduj **XmlDocument** obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
