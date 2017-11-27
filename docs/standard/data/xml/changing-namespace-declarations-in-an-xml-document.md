---
title: Zmiana deklaracji Namespace w dokumencie XML
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
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 627882efcbc41310ee177cba984e4add5b07bd15
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Zmiana deklaracji Namespace w dokumencie XML
**XmlDocument** przedstawia deklaracje przestrzeni nazw i **xmlns** atrybuty jako część modelu obiektu dokumentu. Są one przechowywane w **XmlDocument**, dlatego podczas zapisywania dokumentu, można zachować lokalizację te atrybuty. Zmiana tych atrybutów nie ma wpływu na **nazwa**, **NamespaceURI**, i **prefiksu** właściwości innych węzłów w drzewie. Na przykład, jeśli załadować następującego dokumentu a następnie `test` element ma **NamespaceURI**`123.`  
  
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
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
