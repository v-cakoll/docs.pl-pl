---
title: Zmienianie deklaracji przestrzeni nazw w dokumencie XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
ms.openlocfilehash: b8aa670764deb8e77cfb67fd16dbcf8b1cc9b4c0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711132"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Zmienianie deklaracji przestrzeni nazw w dokumencie XML
Element **XmlDocument** ujawnia deklaracje przestrzeni nazw i atrybuty **xmlns** w ramach modelu obiektów dokumentu. Są one przechowywane w **XmlDocument**, dlatego po zapisaniu dokumentu można zachować jego lokalizację. Zmiana tych atrybutów nie ma wpływu na właściwości **name**, **NamespaceURI**i **prefix** innych węzłów znajdujących się już w drzewie. Na przykład, Jeśli załadujesz następujący dokument, `test` element ma **NamespaceURI**`123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 Usunięcie `xmlns` atrybutu w następujący sposób oznacza, że `test` element nadal ma **NamespaceURI** . `123`  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 Podobnie, jeśli `xmlns` dodasz inny atrybut do `doc` elementu w następujący sposób, `test` element nadal ma **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456")
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 W związku z `xmlns` tym zmiana atrybutów nie będzie miała wpływu do momentu zapisania i ponownego załadowania obiektu **XmlDocument** .  
  
## <a name="see-also"></a>Zobacz też

- [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
