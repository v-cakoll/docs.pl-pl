---
title: 'Instrukcje: Kontrolowanie wypełnienia kształtu złożonego'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 9b3ab1f7b81c296aa1ee766136b6c95b82cab105
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084053"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>Instrukcje: Kontrolowanie wypełnienia kształtu złożonego
<xref:System.Windows.Media.GeometryGroup.FillRule%2A> Właściwość <xref:System.Windows.Media.GeometryGroup> lub <xref:System.Windows.Media.PathGeometry>, określa "reguła", który używa kształtu złożonego, aby określić, czy dany punkt znajduje się część geometrii. Istnieją dwa możliwe wartości <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> i <xref:System.Windows.Media.FillRule.Nonzero>. Poniższych sekcjach opisano sposób używania tych dwóch reguł.  
  
 **Wartości EvenOdd:** Ta zasada ustala, czy punkt znajduje się w regionie wypełnienia rysunek promień od tego momentu do nieskończoności w dowolnym kierunku i zliczenie liczby segmentów ścieżki w ramach danego kształtu przecina ten promień. Jeśli ta liczba jest nieparzysta, punkt znajduje się wewnątrz; Jeśli nawet punkt znajduje się poza.  
  
 Na przykład, poniższe XAML tworzy kształtu złożonego składa się z szeregu koncentrycznych pierścieniami (docelowy) z <xref:System.Windows.Media.GeometryGroup.FillRule%2A> równa <xref:System.Windows.Media.FillRule.EvenOdd>.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]  
  
 Poniższa ilustracja przedstawia kształtem utworzona w poprzednim przykładzie.  
  
 ![Zrzut ekranu: Właściwość FillRule o wartości EvenOdd](./media/fillruleevenoddfirstone.png "FillRuleEvenOddFirstOne")  
  
 Na powyższej ilustracji Zwróć uwagę, nie wypełniono Centrum a pierścień 3. Jest to spowodowane ray, z dowolnego punktu w jednej z tych dwóch sygnałów przechodzi przez parzystą liczbę segmentów. Zobacz na poniższej ilustracji:  
  
 ![Diagram: Właściwość FillRule EvenOdd](./media/fillruleevenodd2.png "FillRuleEvenOdd2")  
  
 **Wartość różną od zera:** Ta zasada ustala, czy punkt znajduje się w regionie wypełnienia ścieżki rysunek promień od tego momentu do nieskończoności w dowolnym kierunku i sprawdzając miejsca, w których segment kształtu przecina ten promień. Począwszy od liczby o wartości zero, dodać każdy Segment przecina ten promień od lewej do prawej i odejmowanie jednej czasu ścieżką segmentu przecina ten promień od prawej do lewej. Po zliczanie przejazdów, jeśli wynik wynosi zero, a następnie punkt znajduje się poza ścieżki. W przeciwnym razie znajduje się wewnątrz.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]  
  
 W przykładzie powyżej wartości <xref:System.Windows.Media.FillRule.Nonzero> dla <xref:System.Windows.Media.GeometryGroup.FillRule%2A> daje w wyniku poniższej ilustracji:  
  
 ![Zrzut ekranu: Wartość FillRule NonZero](./media/fillrulenonzero1.png "FillRuleNonZero1")  
  
 Jak widać, wszystkich pierścieni są wypełnione. Jest to, ponieważ wszystkie segmenty są uruchomione w tym samym kierunku, a więc promień rysowane w dowolnym momencie zostanie między jedną lub więcej segmentów i sumę przejazdów nie będzie równa zero. Na przykład na poniższej ilustracji Czerwone strzałki oznaczają kierunek, w których segmentów są rysowane i biały strzałek reprezentuje dowolne ray uruchamianie z punktu w najbardziej pierścień. Począwszy od wartości zero dla każdego segmentu, który przecina ten promień, wartość jednej zostanie dodany, ponieważ segmentu przecina ten promień od lewej do prawej.  
  
 ![Diagram: Właściwość FillRule równej NonZero](./media/fillrulenonzero2.png "FillRuleNonZero2")  
  
 Aby zademonstrować lepsze zachowanie <xref:System.Windows.Media.FillRule.Nonzero> reguła bardziej złożonych kształtów segmentów działające w różnych kierunkach jest wymagana. Poniższy kod XAML tworzy kształt podobne jak w poprzednim przykładzie, z tą różnicą, że jest tworzony z <xref:System.Windows.Media.PathGeometry> zamiast następnie <xref:System.Windows.Media.EllipseGeometry> koncentrycznych zamiast tworzy cztery Łuki koncentrycznych całkowicie zamknięty.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]  
  
 Poniższa ilustracja przedstawia kształtem utworzona w poprzednim przykładzie.  
  
 ![Zrzut ekranu: Właściwość FillRule NonZero](./media/fillrulenonzero3.png "FillRuleNonZero3")  
  
 Zwróć uwagę, trzeci łuk z Centrum nie jest wypełnione. Na poniższej ilustracji przedstawiono, to dlaczego. Na ilustracji strzałki czerwony reprezentują kierunku, w którym są rysowane segmenty. Dwa biały strzałek reprezentują dwie dowolnego promieni, łączące z punktem w regionie "niewypełniony". Jak wynika z na ilustracji, sumę wartości z danej promień wykraczania poza granice segmentów w ścieżce wynosi zero. Zdefiniowane powyżej sumę zero oznacza, że punkt jest częścią geometrii (nie jest częścią wypełnienie) podczas sumy, która jest *nie* zero, w tym wartość ujemną, jest częścią geometrii.  
  
 ![Diagram: Właściwość FillRule NonZero](./media/fillrulenonzero4.png "FillRuleNonZero4")  
  
 **Uwaga:** Na potrzeby <xref:System.Windows.Media.FillRule>, wszystkie kształty są traktowane jako zamknięte. W przypadku przerwy w segmencie, narysuj urojone wiersza, aby je zamknąć. W powyższym przykładzie są małe przerwy pierścienie. Biorąc pod uwagę to, można oczekiwać, że ray, wykonywana za pośrednictwem przerwa, aby nadać różne wyniki, a następnie promień uruchomiona w innym kierunku. Poniżej znajduje się ilustrację rozszerzonej jednej z tych luk i "odcinka urojone" (segment, który jest rysowana w celu stosowania <xref:System.Windows.Media.FillRule>), zostanie zamknięty.  
  
 ![Diagram: Dla właściwości FillRule segmenty są zawsze zamknięte](./media/fillruleclosedshapes.png "FillRuleClosedShapes")  
  
## <a name="example"></a>Przykład  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie kształtu złożonego](how-to-create-a-composite-shape.md)
- [Przegląd Geometria](geometry-overview.md)
