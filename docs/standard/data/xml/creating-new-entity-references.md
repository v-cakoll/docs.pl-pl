---
title: Tworzenie nowych odwołań do jednostek
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d8d4e9e1e2dfd9882504c935912bcf235608485
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965896"
---
# <a name="creating-new-entity-references"></a>Tworzenie nowych odwołań do jednostek
Metoda "XmlEntityReference" tworzy nowy węzeł XmlEntityReference. Document Object Model XML (DOM) sprawdza, czy nazwa jednostki, do której odwołuje się odwołanie, została już zadeklarowana. Jeśli ma, węzły podrzędne węzła XmlEntityReference są kopiowane z węzła deklaracji jednostki. Jeśli nie ma deklaracji jednostki zgodnej, pusty węzeł tekstowy jest dołączany jako jedyny element podrzędny węzła odwołania do jednostki. Ponieważ węzły podrzędne węzła XmlEntityReference są kopiami innych węzłów, te węzły podrzędne są tylko do odczytu i nie można ich modyfikować.  
  
 Po skopiowaniu węzłów może istnieć przestrzeń nazw w zakresie w punkcie odwołania do jednostki. Ta przestrzeń nazw ma wpływ na konfigurację wszystkich wygenerowanych węzłów elementów lub atrybutów.  
  
> [!NOTE]
> DOM dodaje węzły podrzędne do obiektu **EntityReference** tylko wtedy, gdy wstawisz węzeł **EntityReference** do dokumentu. Nowo utworzone węzły **EntityReference** nie mają węzłów podrzędnych.  
  
 Mimo że **XmlDataDocument** jest klasą pochodną XmlDocument, **XmlDataDocument** nie obsługuje tworzenia odwołań do jednostek. Dzieje się tak, ponieważ elementy podrzędne **EntityReference** są tylko do odczytu. Elementy podrzędne węzła **EntityReference** mogą obejmować więcej niż jeden region. W takim przypadku część wiersza skojarzona z regionem zawierającym część obiektu **EntityReference** będzie tylko do odczytu.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
