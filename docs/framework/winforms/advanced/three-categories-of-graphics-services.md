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
ms.openlocfilehash: 5621a2c0bba2e922e62006feba9ca0381181c780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="three-categories-of-graphics-services"></a>Trzy kategorie usług grafiki
Oferty grafiki w formularzach systemu Windows można podzielić na następujące trzy kategorie:  
  
-   Grafika wektorowa dwuwymiarowa (2-D)  
  
-   Tworzenie obrazów  
  
-   Typografia  
  
## <a name="2-d-vector-graphics"></a>Grafika wektorowa 2-D  
 Grafika wektorowa dwuwymiarowa są w nim elementów podstawowych; przykład linii, krzywych i rysunki; które zostały określone przez zestawy punktów na układ współrzędnych. Na przykład prostej jest określony przez jego dwa punkty końcowe i prostokąt jest określona przez punkt, podając lokalizację jego lewego górnego rogu oraz pary numerów nadanie szerokości i wysokości. Proste ścieżki jest określany przez tablicę punktów, które są połączone liniami proste. Krzywej Beziera jest krzywą zaawansowane określony przez formant cztery punkty.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zawiera klasy i struktury, w których są przechowywane informacje o podstawowych, samodzielnie, klasy, które przechowywania informacji na temat sposobu będzie rysowany podstawowych i klasy, które faktycznie nie. Na przykład <xref:System.Drawing.Rectangle> struktury przechowuje lokalizacja i rozmiar prostokąta; <xref:System.Drawing.Pen> klasy przechowuje informacje dotyczące wiersza kolor, szerokość linii i styl linii; i <xref:System.Drawing.Graphics> klasa zawiera metody służące do rysowania linii, prostokąty, ścieżki, a inne rysunki. Istnieją również kilka <xref:System.Drawing.Brush> klasy, które przechowują informacje na temat zamknięte rysunki i ścieżki będzie wypełniona kolorów lub wzorce.  
  
 Obraz wektora, czyli sekwencji poleceń grafiki, można rejestrować w metaplik. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] udostępnia <xref:System.Drawing.Imaging.Metafile> klasy rejestrowania, wyświetlanie i zapisywania metapliki. Z <xref:System.Drawing.Imaging.MetafileHeader> i <xref:System.Drawing.Imaging.MetaHeader> klasy, możesz sprawdzić danych przechowywanych w nagłówku metaplik.  
  
## <a name="imaging"></a>Tworzenie obrazów  
 Niektóre rodzaje obrazy są trudne lub niemożliwe do wyświetlenia techniki grafiki wektorowej. Na przykład obrazów na przycisków paska narzędzi i obrazy, które są wyświetlane jako ikony są trudne do określenia jako kolekcje linii i krzywych. O wysokiej rozdzielczości cyfrowych fotografii stadium wiele baseball nawet trudniej jest tworzenie techniki wektora. Obrazy tego typu są przechowywane jako mapy bitowe, które są tablice liczb, które reprezentują kolory poszczególnych punktów na ekranie. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] udostępnia <xref:System.Drawing.Bitmap> klasy wyświetlanie, manipulowanie i Zapisywanie map bitowych.  
  
## <a name="typography"></a>Typografia  
 Typografia jest wyświetlanie tekstu w różnych czcionek, rozmiarów i style. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zapewnia zaawansowaną obsługę tego złożone zadania. Jedną z nowych funkcji w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] antialiasingu subpixel, który zawiera tekst renderowany na ekranie LCD płynniejszy wyglądu.  
  
 Ponadto program Windows Forms oferuje możliwość Rysowanie tekstu za pomocą [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] możliwości w jego <xref:System.Windows.Forms.TextRenderer> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Grafika — omówienie](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [Informacje o kodzie zarządzanym GDI+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [Używanie zarządzanych klas grafiki](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
