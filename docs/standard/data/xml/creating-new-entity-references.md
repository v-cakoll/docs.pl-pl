---
title: "Tworzenie nowego odwołania do jednostek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 76093fbe7095c2aae7caa69147f6181c292ca734
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="creating-new-entity-references"></a>Tworzenie nowego odwołania do jednostek
**CreateEntityReference** metoda tworzy nowy **XmlEntityReference** węzła. XML modelu DOM (Document Object) sprawdza, czy nazwa jednostki, do którego nastąpiło odwołanie została już zadeklarowana. Jeśli tak, węzły podrzędne **XmlEntityReference** węzła są kopiowane z węzła deklaracji entity. Jeśli nie ma żadnych deklaracji jednostki, która jest zgodna, węzeł pusty tekst jest dołączony jako element podrzędny tylko jednostki węzła odniesienia. Ponieważ węzły podrzędne **XmlEntityReference** węzła to kopie inne węzły, te węzły podrzędne są tylko do odczytu i nie może być modyfikowany.  
  
 W przypadku kopiowania węzły, w zakresie w punkcie odwołanie do jednostki mogą istnieć przestrzeni nazw. Ta przestrzeń nazw wpływa na konfigurację węzły elementu lub atrybutu wygenerowany.  
  
> [!NOTE]
>  Węzły podrzędne dodaje modelu DOM **EntityReference** tylko po wstawieniu **EntityReference** węzła do dokumentu. Nowo utworzona **EntityReference** węzły mają bez węzłów podrzędnych.  
  
 Mimo że **dokumentu XmlDataDocument** jest klasy pochodnej z **XmlDocument**, **dokumentu XmlDataDocument** nie obsługuje tworzenia odwołań do jednostek. Jest to spowodowane **EntityReference** elementy podrzędne są tylko do odczytu. Elementy podrzędne **EntityReference** węzeł może obejmować więcej niż jeden region. W takim przypadku część wiersz skojarzony z regionu, który zawiera część **EntityReference** będą tylko do odczytu.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
