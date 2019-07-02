---
title: Trzy kategorie usług grafiki
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2-D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: a69fa7a1ccad353c879731de05dc47f0d6ae8795
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505230"
---
# <a name="three-categories-of-graphics-services"></a>Trzy kategorie usług grafiki
Oferty grafiki w formularzach Windows Forms dzielą się na trzech ogólnych kategorii:  
  
- Grafiki dwuwymiarowej wektorowej (2-D)  
  
- Tworzenie obrazu  
  
- Typografia  
  
## <a name="2-d-vector-graphics"></a>Grafika wektorowa 2-D  
 Grafika wektorowa dwuwymiarową są w nim elementów podstawowych; przykład linii, krzywych i liczby; które są określone przez zestawy punktów na układ współrzędnych. Na przykład prostej jest określony przez jego dwa punkty końcowe i określonej przez punkt, dzięki czemu położenie jego lewego górnego rogu oraz pary numerów, dzięki czemu jego szerokość i wysokość prostokąta. Ścieżek prostych jest określany przez tablicę punkty, które są połączone liniami proste. Krzywej Beziera jest zaawansowane krzywej określony przez punkty kontrolne cztery.  
  
 GDI + zawiera klasy i struktury, które przechowują informacje o podstawowych same klasy, które przechowują informacje o jak będą rysowane prymitywów i klas, które rzeczywiście wykonują rysunku. Na przykład <xref:System.Drawing.Rectangle> struktury są przechowywane, lokalizacja i rozmiar prostokąta; <xref:System.Drawing.Pen> klasa przechowuje informacje dotyczące koloru linii, szerokości linii i styl linii; i <xref:System.Drawing.Graphics> klasa zawiera metody służące do rysowania linii, prostokątów, ścieżek i inne rysunki. Istnieje również kilka <xref:System.Drawing.Brush> klas, które przechowują informacje o tym, jak zamknięte rysunki, a ścieżki będzie wypełniona kolorów lub wzorce.  
  
 Obraz wektora, czyli sekwencji poleceń dotyczących grafiki, można zapisać w metaplik. GDI + zapewnia <xref:System.Drawing.Imaging.Metafile> klasy dla nagrywania, wyświetlanie i zapisywanie metapliki. Za pomocą <xref:System.Drawing.Imaging.MetafileHeader> i <xref:System.Drawing.Imaging.MetaHeader> klasy, można sprawdzić dane przechowywane w nagłówku metaplik.  
  
## <a name="imaging"></a>Tworzenie obrazu  
 Niektóre rodzaje obrazy są trudne lub niemożliwe do wyświetlenia za pomocą metod grafiki wektorowej. Na przykład obrazy na przycisków paska narzędzi i obrazy, które są wyświetlane jako ikony są trudne do określenia jako kolekcje linii i krzywych. O wysokiej rozdzielczości cyfrowych fotografii stadion zatłoczonym mecz jest jeszcze trudniejsze do utworzenia przy użyciu technik wektora. Obrazy tego typu są przechowywane jako mapy bitowe, które są tablicami liczb, które reprezentują kolory poszczególnych punktów na ekranie. GDI + zapewnia <xref:System.Drawing.Bitmap> klasy do wyświetlania, modyfikowania i Zapisywanie map bitowych.  
  
## <a name="typography"></a>Typografia  
 Typografia jest wyświetlanie tekstu w różnych czcionki, rozmiary i stylów. GDI + zapewnia rozbudowaną obsługę złożone zadania. Jedną z nowych funkcji w GDI + jest antialiasingu subpixel, co daje tekstu renderowanego na ekranie LCD gładsze wygląd.  
  
 Ponadto, Windows Forms zapewnia możliwość Rysowanie tekstu za pomocą GDI możliwości w jego <xref:System.Windows.Forms.TextRenderer> klasy.  
  
## <a name="see-also"></a>Zobacz także

- [Grafika — omówienie](graphics-overview-windows-forms.md)
- [Informacje o kodzie zarządzanym GDI+](about-gdi-managed-code.md)
- [Używanie zarządzanych klas grafiki](using-managed-graphics-classes.md)
