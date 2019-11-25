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
ms.openlocfilehash: 5457eab1f34eb3e7424d508509f5dd6a42ffb51f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976935"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Zmienianie deklaracji przestrzeni nazw w dokumencie XML
Element **XmlDocument** ujawnia deklaracje przestrzeni nazw i atrybuty **xmlns** w ramach modelu obiektów dokumentu. Są one przechowywane w **XmlDocument**, dlatego po zapisaniu dokumentu można zachować jego lokalizację. Zmiana tych atrybutów nie ma wpływu na właściwości **name**, **NamespaceURI**i **prefix** innych węzłów znajdujących się już w drzewie. Na przykład, Jeśli załadujesz następujący dokument, element `test` ma **NamespaceURI** `123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 W przypadku usunięcia `xmlns` atrybutu w następujący sposób element `test` nadal ma **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 Podobnie, jeśli dodasz inny atrybut `xmlns` do elementu `doc` w następujący sposób, element `test` nadal ma `123`**NamespaceURI** .  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456")
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 W związku z tym zmiana atrybutów `xmlns` nie będzie miała wpływu do momentu zapisania i ponownego załadowania obiektu **XmlDocument** .  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
