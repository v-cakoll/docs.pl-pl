---
title: Jak kontrolować wypełnienie kształtu złożonego
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: a9a17434f11f432f6446e09bd853ed0d2f23fbe8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563046"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>Jak kontrolować wypełnienie kształtu złożonego
<xref:System.Windows.Media.GeometryGroup.FillRule%2A> Właściwość <xref:System.Windows.Media.GeometryGroup> lub <xref:System.Windows.Media.PathGeometry>, określa "reguły" używanym do ustalenia, czy dany punkt jest częścią geometrii złożonego kształtu. Istnieją dwa możliwe wartości <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> i <xref:System.Windows.Media.FillRule.Nonzero>. W poniższych sekcjach zostaną opisano sposób używania tych dwóch reguł.  
  
 **Wartości EvenOdd:** ta reguła ustala, czy punkt znajduje się w regionie fill, rysując promień od tego punktu do nieskończoności w dowolnym kierunku i obliczając, ile segmentów ścieżki w ramach danego kształtu przecina ten promień. Jeśli ta liczba jest nieparzysta, punkt znajduje się wewnątrz; Jeśli nawet, punkt znajduje się poza.  
  
 Na przykład poniżej XAML tworzy kształt złożone składają się z szeregu koncentrycznych sygnałów (docelowy) z <xref:System.Windows.Media.GeometryGroup.FillRule%2A> ustawioną <xref:System.Windows.Media.FillRule.EvenOdd>.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]  
  
 Na poniższej ilustracji przedstawiono utworzone w poprzednim przykładzie kształtu.  
  
 ![Zrzut ekranu: Właściwość FillRule o wartości EvenOdd](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenoddfirstone.png "FillRuleEvenOddFirstOne")  
  
 Na ilustracji powyżej zauważyć nie wypełniono Centrum i 3 pierścień. Jest to spowodowane promień z dowolnego punktu w jednej z tych dwóch sygnałów przechodzi przez parzystą liczbę segmentów. Znajduje się na poniższej ilustracji:  
  
 ![Diagram: Właściwość FillRule o wartości EvenOdd](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenodd2.png "FillRuleEvenOdd2")  
  
 **NonZero:** ta reguła ustala, czy punkt znajduje się w regionie wypełnienia ścieżki, rysując promień od tego punktu do nieskończoności w dowolnym kierunku i sprawdzając miejsca, w których segment kształtu przecina ten promień. Począwszy od liczby zero, dodaj je każdy Segment przecina ten promień od lewej do prawej i odjąć jednej czasu ścieżki segment przecina ten promień od prawej do lewej. Po inwentaryzacji przejścia, jeśli wynik wynosi zero, a następnie punkt znajduje się poza ścieżki. W przeciwnym razie znajduje się wewnątrz.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]  
  
 W przykładzie powyżej wartości <xref:System.Windows.Media.FillRule.Nonzero> dla <xref:System.Windows.Media.GeometryGroup.FillRule%2A> daje w wyniku poniższej ilustracji:  
  
 ![Zrzut ekranu: FillRule o wartości NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero1.png "FillRuleNonZero1")  
  
 Jak widać, wszystkie sygnałów są wypełnione. Jest tak, ponieważ wszystkie segmenty są uruchomione w tym samym kierunku w związku z czym promień z dowolnego punktu będzie przekraczają jedną lub więcej segmentów i sumę przejścia nie równa zero. Na przykład na poniższej ilustracji Czerwone strzałki reprezentowania kierunku, w którym są rysowane segmenty i białe Strzałka reprezentuje promień dowolne uruchomione z punktem w najbardziej pierścień. Począwszy od wartości zero dla każdego segmentu przecina ten promień, wartości jeden dodaniu ponieważ segment przecina ten promień od lewej do prawej.  
  
 ![Diagram: Właściwość FillRule o wartości równej NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero2.png "FillRuleNonZero2")  
  
 Aby lepiej zaprezentować zachowanie <xref:System.Windows.Media.FillRule.Nonzero> reguła bardziej złożonych kształt z segmentów uruchomione w różnych kierunkach jest wymagana. Poniższy kod XAML tworzy podobnym kształcie co w poprzednim przykładzie z tą różnicą, że jest tworzony z <xref:System.Windows.Media.PathGeometry> a nie <xref:System.Windows.Media.EllipseGeometry> koncentrycznych zamiast co powoduje cztery Łuki koncentrycznych całkowicie zamknięte.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]  
  
 Na poniższej ilustracji przedstawiono utworzone w poprzednim przykładzie kształtu.  
  
 ![Zrzut ekranu: Właściwość FillRule NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero3.png "FillRuleNonZero3")  
  
 Zwróć uwagę, trzeci łuku z Centrum nie jest wypełnione. Na poniższej ilustracji przedstawiono, dlaczego jest. Na ilustracji Czerwone strzałki reprezentowania kierunku, w którym są rysowane segmentów. Dwie strzałki białe reprezentują dwa dowolnego promienie, łączące z punktem w regionie "niewypełniony". Jak wynika z na ilustracji, sumę wartości z danej promień przekraczania segmentów ścieżki wynosi zero. Zgodnie z definicją powyżej, sumę zero oznacza, że punkt nie jest częścią geometrii (nie jest częścią wypełnienia) podczas sum, który jest *nie* zero, łącznie z wartością ujemną, jest częścią geometrii.  
  
 ![Diagram: Właściwość FillRule NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero4.png "FillRuleNonZero4")  
  
 **Uwaga:** na potrzeby <xref:System.Windows.Media.FillRule>, wszystkie kształty są traktowane jako zamknięte. Jeśli istnieje luka w segmencie, Rysuj urojony wiersza, aby je zamknąć. W powyższym przykładzie są małe przerwy w pierścieni. Biorąc pod uwagę to, co może oczekiwać promień wykonywana za pośrednictwem odstępu, aby zapewnić różne wyniki, a następnie promień uruchomiona w innym kierunku. Poniżej znajduje się rozszerzonej ilustracji jednej z tych luk i "urojony segmentu" (segment, który jest rysowana w celu stosowania <xref:System.Windows.Media.FillRule>) która zostanie zamknięte.  
  
 ![Diagram: Dla właściwości FillRule segmenty są zawsze zamknięte](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleclosedshapes.png "FillRuleClosedShapes")  
  
## <a name="example"></a>Przykład  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie kształtu złożonego](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Geometria — przegląd](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
