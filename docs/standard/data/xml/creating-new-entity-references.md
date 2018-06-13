---
title: Tworzenie nowego odwołania do jednostek
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0fefea6f8dfd74dfd31c7c07a158e4935ab0e02c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568449"
---
# <a name="creating-new-entity-references"></a>Tworzenie nowego odwołania do jednostek
**CreateEntityReference** metoda tworzy nowy **XmlEntityReference** węzła. XML modelu DOM (Document Object) sprawdza, czy nazwa jednostki, do którego nastąpiło odwołanie została już zadeklarowana. Jeśli tak, węzły podrzędne **XmlEntityReference** węzła są kopiowane z węzła deklaracji entity. Jeśli nie ma żadnych deklaracji jednostki, która jest zgodna, węzeł pusty tekst jest dołączony jako element podrzędny tylko jednostki węzła odniesienia. Ponieważ węzły podrzędne **XmlEntityReference** węzła to kopie inne węzły, te węzły podrzędne są tylko do odczytu i nie może być modyfikowany.  
  
 W przypadku kopiowania węzły, w zakresie w punkcie odwołanie do jednostki mogą istnieć przestrzeni nazw. Ta przestrzeń nazw wpływa na konfigurację węzły elementu lub atrybutu wygenerowany.  
  
> [!NOTE]
>  Węzły podrzędne dodaje modelu DOM **EntityReference** tylko po wstawieniu **EntityReference** węzła do dokumentu. Nowo utworzona **EntityReference** węzły mają bez węzłów podrzędnych.  
  
 Mimo że **dokumentu XmlDataDocument** jest klasy pochodnej z **XmlDocument**, **dokumentu XmlDataDocument** nie obsługuje tworzenia odwołań do jednostek. Jest to spowodowane **EntityReference** elementy podrzędne są tylko do odczytu. Elementy podrzędne **EntityReference** węzeł może obejmować więcej niż jeden region. W takim przypadku część wiersz skojarzony z regionu, który zawiera część **EntityReference** będą tylko do odczytu.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
