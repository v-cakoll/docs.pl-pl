---
title: Tworzenie nowych odwołań do jednostek
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
ms.openlocfilehash: 7c94d121d00c169f0d74bc9b12c8710fb6055250
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283354"
---
# <a name="creating-new-entity-references"></a>Tworzenie nowych odwołań do jednostek
Metoda " **XmlEntityReference** " tworzy nowy węzeł **XmlEntityReference** . Document Object Model XML (DOM) sprawdza, czy nazwa jednostki, do której odwołuje się odwołanie, została już zadeklarowana. Jeśli ma, węzły podrzędne węzła **XmlEntityReference** są kopiowane z węzła deklaracji jednostki. Jeśli nie ma deklaracji jednostki zgodnej, pusty węzeł tekstowy jest dołączany jako jedyny element podrzędny węzła odwołania do jednostki. Ponieważ węzły podrzędne węzła **XmlEntityReference** są kopiami innych węzłów, te węzły podrzędne są tylko do odczytu i nie można ich modyfikować.  
  
 Po skopiowaniu węzłów może istnieć przestrzeń nazw w zakresie w punkcie odwołania do jednostki. Ta przestrzeń nazw ma wpływ na konfigurację wszystkich wygenerowanych węzłów elementów lub atrybutów.  
  
> [!NOTE]
> DOM dodaje węzły podrzędne do obiektu **EntityReference** tylko wtedy, gdy wstawisz węzeł **EntityReference** do dokumentu. Nowo utworzone węzły **EntityReference** nie mają węzłów podrzędnych.  
  
 Mimo że **XmlDataDocument** jest klasą pochodną **XmlDocument**, **XmlDataDocument** nie obsługuje tworzenia odwołań do jednostek. Dzieje się tak, ponieważ elementy podrzędne **EntityReference** są tylko do odczytu. Elementy podrzędne węzła **EntityReference** mogą obejmować więcej niż jeden region. W takim przypadku część wiersza skojarzona z regionem zawierającym część obiektu **EntityReference** będzie tylko do odczytu.  
  
## <a name="see-also"></a>Zobacz także

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
