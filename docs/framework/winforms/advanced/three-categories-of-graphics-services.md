---
title: Trzy kategorie usług grafiki
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: fa7391ef0f7170ddb9d9d24aa5a1a03635bf46e0
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291727"
---
# <a name="three-categories-of-graphics-services"></a>Trzy kategorie usług grafiki
Oferty graficzne w formularzach systemu Windows dzielą się na następujące trzy szerokie kategorie:  
  
- Grafika wektorowa dwuwymiarowa (2-W)  
  
- Obrazowania  
  
- Typografia  
  
## <a name="2d-vector-graphics"></a>Grafika wektorowa 2D  
 Dwuwymiarowa grafika wektorowa, taka jak linie, krzywe i liczby, to elementy pierwotne określone przez zestawy punktów w układzie współrzędnych. Na przykład linia prosta jest określona przez jego dwa punkty końcowe, a prostokąt jest określony przez punkt podający położenie jego lewego górnego rogu i parę liczb, podając jego szerokość i wysokość. Prosta ścieżka jest określona przez tablicę punktów, które są połączone liniami prostymi. Splajn Béziera to wyrafinowana krzywa określona przez cztery punkty kontrolne.  
  
 GDI+ zawiera klasy i struktury, które przechowują informacje o samych umliczerach, klasy, które przechowują informacje o tym, jak zostaną narysowane prymitywy, oraz klasy, które faktycznie wykonują rysunek. Na przykład <xref:System.Drawing.Rectangle> struktura przechowuje lokalizację i rozmiar prostokąta; <xref:System.Drawing.Pen> klasa przechowuje informacje o kolorze linii, szerokości linii i stylu linii; a <xref:System.Drawing.Graphics> klasa ma metody rysowania linii, prostokątów, ścieżek i innych cyfr. Istnieje również <xref:System.Drawing.Brush> kilka klas, które przechowują informacje o tym, jak zamknięte figury i ścieżki będą wypełnione kolorami lub wzorami.  
  
 Obraz wektorowy, który jest sekwencją poleceń graficznych, można nagrać w metapliku. GDI+ zapewnia <xref:System.Drawing.Imaging.Metafile> klasę do nagrywania, wyświetlania i zapisywania metaplików. Za <xref:System.Drawing.Imaging.MetafileHeader> pomocą <xref:System.Drawing.Imaging.MetaHeader> i klas można sprawdzić dane przechowywane w nagłówku metapliku.  
  
## <a name="imaging"></a>Obrazowania  
 Niektóre rodzaje zdjęć są trudne lub niemożliwe do wyświetlenia za pomocą technik grafiki wektorowej. Na przykład obrazy na przyciskach paska narzędzi i obrazy, które są wyświetlane jako ikony, są trudne do określenia jako kolekcje linii i krzywych. Cyfrowe zdjęcie zatłoczonego stadionu baseballowego w wysokiej rozdzielczości jest jeszcze trudniejsze do stworzenia za pomocą technik wektorowych. Obrazy tego typu są przechowywane jako mapy bitowe, które są tablicami liczb, które reprezentują kolory poszczególnych kropek na ekranie. GDI+ zapewnia <xref:System.Drawing.Bitmap> klasę do wyświetlania, manipulowania i zapisywania map bitowych.  
  
## <a name="typography"></a>Typografia  
 Typografia to wyświetlanie tekstu w różnych czcionkach, rozmiarach i stylach. GDI+ zapewnia szerokie wsparcie dla tego złożonego zadania. Jedną z nowych funkcji w GDI + jest subpikselowy antyaliasing, który nadaje tekst renderowany na ekranie LCD gładsza.  
  
 Ponadto formularze systemu Windows oferują możliwość rysowania tekstu z <xref:System.Windows.Forms.TextRenderer> możliwościami GDI w swojej klasie.  
  
## <a name="see-also"></a>Zobacz też

- [Grafika — omówienie](graphics-overview-windows-forms.md)
- [Informacje o kodzie zarządzanym GDI+](about-gdi-managed-code.md)
- [Używanie zarządzanych klas grafiki](using-managed-graphics-classes.md)
