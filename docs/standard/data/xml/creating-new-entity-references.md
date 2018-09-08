---
title: Tworzenie nowych odwołań do jednostek
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67fdbcdbff64bcd91c80fbeaec0c41982b68d98f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192382"
---
# <a name="creating-new-entity-references"></a>Tworzenie nowych odwołań do jednostek
**CreateEntityReference** metoda tworzy nowy **XmlEntityReference** węzła. XML Document Object Model (DOM) sprawdza, jeśli został już zadeklarowany nazwa jednostki, do którego nastąpiło odwołanie. Jeśli tak, węzły podrzędne **XmlEntityReference** węzłów są kopiowane z węzła deklaracji entity. W przypadku deklaracja nie jednostki, który odpowiada pusty węzeł tekstowy jest dołączony jako tylko element podrzędny węzła odwołanie do jednostki. Ponieważ węzły podrzędne **XmlEntityReference** węzła to kopie innych węzłów, tych węzłów podrzędnych są przeznaczone tylko do odczytu i nie może być modyfikowany.  
  
 Jeśli węzły są kopiowane, w zakresie punkcie odwołania do jednostki może powstać przestrzeni nazw. Ta przestrzeń nazw ma wpływ na konfigurację węzłów elementów lub atrybutów generowane.  
  
> [!NOTE]
>  Model DOM dodaje węzły podrzędne **EntityReference** tylko po wstawieniu **EntityReference** węzeł w dokumencie. Nowo utworzony **EntityReference** węzły mają bez węzłów podrzędnych.  
  
 Mimo że **XmlDataDocument** klasy pochodnej jest **XmlDocument**, **XmlDataDocument** nie obsługuje tworzenia odwołań do jednostek. Jest to spowodowane **EntityReference** elementy podrzędne są przeznaczone tylko do odczytu. Elementy podrzędne **EntityReference** węzła może obejmować więcej niż jednym regionie. W tym przypadku część wiersz skojarzony region, który zawiera część **EntityReference** będą tylko do odczytu.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
