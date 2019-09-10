---
title: 'Instrukcje: Kontrolowanie wypełnienia kształtu złożonego'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 89f69d392e8838af99538c759a2f06453e1bcd60
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855898"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>Instrukcje: Kontrolowanie wypełnienia kształtu złożonego

<xref:System.Windows.Media.GeometryGroup.FillRule%2A> Właściwość lub<xref:System.Windows.Media.GeometryGroup> a ,określa"regułę",którejużywakształtzłożony,abyokreślić,<xref:System.Windows.Media.PathGeometry>czy dany punkt jest częścią geometrii. Dostępne są dwie możliwe wartości <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> i <xref:System.Windows.Media.FillRule.Nonzero>. W poniższych sekcjach opisano sposób korzystania z tych dwóch reguł.

**EvenOdd** Ta reguła określa, czy punkt znajduje się w regionie wypełnienia, rysując promień od tego punktu do nieskończoności w dowolnym kierunku i obliczając liczbę segmentów ścieżki w ramach danego kształtu, który przekroczy promień. Jeśli ta liczba jest nieparzysta, punkt jest wewnątrz; Jeśli nawet, punkt znajduje się poza.

Na przykład poniższy kod XAML tworzy kształt złożony składający się z serii koncentrycznych pierścieni (target) z <xref:System.Windows.Media.GeometryGroup.FillRule%2A> zestawem do. <xref:System.Windows.Media.FillRule.EvenOdd>

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]

Na poniższej ilustracji przedstawiono kształt utworzony w poprzednim przykładzie.

![Okrąg składający się z serii koncentrycznego pierścieni z przemiennymi kolorami.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-property.png)

Na poprzedniej ilustracji Zauważ, że środkowe i trzeci pierścień nie są wypełnione. Wynika to z faktu, że promień narysowany z dowolnego punktu w jednym z dwóch pierścieni przechodzi przez parzystą liczbę segmentów. Zapoznaj się z następującą ilustracją:

![Diagram przedstawiający promienie EvenOdd rysowane w okręgu.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-rays.png)

**Różną od zera** Ta reguła określa, czy punkt znajduje się w regionie wypełnienia ścieżki, rysując promień od tego punktu do nieskończoności w dowolnym kierunku, a następnie sprawdzając miejsca, w których segment kształtu przecina promień. Rozpoczynając od liczby zero, Dodaj jeden za każdym razem, gdy segment przecina promień od lewej do prawej, i Odejmij jeden za każdym razem, gdy segment ścieżki przecina promień od prawej do lewej. Po zliczaniu skrzyżowań, jeśli wynik wynosi zero, punkt znajduje się poza ścieżką. W przeciwnym razie jest wewnątrz.

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]

Korzystając z poprzedniego przykładu, wartość <xref:System.Windows.Media.FillRule.Nonzero> dla elementu <xref:System.Windows.Media.GeometryGroup.FillRule%2A> daje następującą ilustrację:

![Okrąg składający się z serii koncentrycznej pierścieni wszystko wypełnienie z tym samym kolorem.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-nonzero.png)

Jak widać, wszystkie pierścienie są wypełniane. Wynika to z faktu, że wszystkie segmenty są uruchomione w tym samym kierunku i dlatego promień narysowany z dowolnego punktu będzie przecinał jeden lub więcej segmentów, a suma przecięć nie będzie równa zero. Na przykład na poniższej ilustracji czerwona strzałka reprezentuje kierunek rysowania segmentów, a biała strzałka reprezentuje dowolny promień działający z punktu w wewnętrznym pierścieniu. Rozpoczynając od wartości zero, dla każdego segmentu, który przekroczy promień, jest dodawana wartość jednej, ponieważ segment przecina promień od lewej do prawej.

![Diagram przedstawiający wartość właściwości FillRule równą zero.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-equal-nonzero.png)

Aby lepiej zademonstrować zachowanie <xref:System.Windows.Media.FillRule.Nonzero> reguły, wymagany jest bardziej złożony kształt z segmentami uruchomionymi w różnych kierunkach. Poniższy kod XAML tworzy podobny kształt jak w poprzednim przykładzie, z wyjątkiem tego, że jest tworzony przy <xref:System.Windows.Media.PathGeometry> użyciu zamiast <xref:System.Windows.Media.EllipseGeometry> tego, który tworzy cztery okręgi koncentryczne zamiast całkowicie zamknięte koła koncentryczne.

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]

Na poniższej ilustracji przedstawiono kształt utworzony w poprzednim przykładzie.

![Okrąg składający się z serii koncentrycznego pierścieni z przemiennymi kolorami z niewypełnionym trzecim łukiem.](./media/how-to-control-the-fill-of-a-composite-shape/pathgeometry-concentric-arcs.png)

Zwróć uwagę, że trzeci łuk z centrum nie jest wypełniony. Na poniższej ilustracji przedstawiono przyczyny tego. Na ilustracji czerwona strzałka reprezentuje kierunek rysowania segmentów. Dwie białe strzałki przedstawiają dwie dowolne promienie, które przechodzą z punktu w regionie "niewypełniony". Jak widać na ilustracji, suma wartości z danego promienia przekraczających segmenty w jego ścieżce wynosi zero. Jak określono powyżej, suma zero oznacza, że punkt nie jest częścią geometrii (nie jest częścią wypełnienia), podczas gdy suma *nierówna zero,* w tym wartość ujemna, jest częścią geometrii.

![Diagram przedstawiający dowolne promienie przecinające segmenty.](./media/how-to-control-the-fill-of-a-composite-shape/arbitrary-ray-cross-segment.png)

> [!NOTE]
> Na potrzeby programu <xref:System.Windows.Media.FillRule>wszystkie kształty są uważane za zamknięte. Jeśli w segmencie występuje przerwy, narysuj linię urojoną, aby ją zamknąć. W powyższym przykładzie występują małe przerwy w pierścieniach. W związku z tym, jeden może oczekiwać, że promień działający w ramach przerwy, aby dać inny wynik, a następnie promień działający w innym kierunku. Poniżej znajduje się powiększona ilustracja jednego z tych luk i "segmentu urojonego" (segment, który jest rysowany do celów zastosowania <xref:System.Windows.Media.FillRule>), który go zamyka.

![Diagram przedstawiający segmenty FillRule, które są zawsze zamknięte.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-closed-segments.png)

## <a name="example"></a>Przykład

## <a name="see-also"></a>Zobacz także

- [Tworzenie kształtu złożonego](how-to-create-a-composite-shape.md)
- [Geometria — przegląd](geometry-overview.md)
