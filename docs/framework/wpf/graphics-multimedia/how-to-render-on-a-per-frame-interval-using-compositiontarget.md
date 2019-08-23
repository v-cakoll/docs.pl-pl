---
title: 'Instrukcje: Renderowanie w interwałach klatek z użyciem elementu CompositionTarget'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
ms.openlocfilehash: 8864204ccdd1e860cc910dfe8baa2f25edfb2fcc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956983"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Instrukcje: Renderowanie w interwałach klatek z użyciem elementu CompositionTarget
Aparat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animacji zapewnia wiele funkcji tworzenia animacji opartych na ramkach. Istnieją jednak scenariusze aplikacji, w których potrzebna jest bardziej precyzyjna kontrola nad renderowaniem na poszczególnych klatkach. <xref:System.Windows.Media.CompositionTarget> Obiekt umożliwia tworzenie niestandardowych animacji na podstawie wywołania zwrotnego na klatkę.  
  
 <xref:System.Windows.Media.CompositionTarget>jest klasą statyczną reprezentującą powierzchnię wyświetlaną, na której jest rysowana aplikacja. <xref:System.Windows.Media.CompositionTarget.Rendering> Zdarzenie jest wywoływane za każdym razem, gdy zostanie narysowana scena aplikacji. Szybkość klatek renderowania to liczba prób rysowania sceny na sekundę.  
  
> [!NOTE]
> Aby uzyskać kompletny przykład kodu przy <xref:System.Windows.Media.CompositionTarget>użyciu, zobacz [Korzystanie z przykładu CompositionTarget](https://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Przykład  
 Zdarzenie wyzwalane podczas procesu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]renderowania. <xref:System.Windows.Media.CompositionTarget.Rendering> Poniższy przykład pokazuje, jak zarejestrować <xref:System.EventHandler> delegata w metodzie statycznej <xref:System.Windows.Media.CompositionTarget.Rendering> na <xref:System.Windows.Media.CompositionTarget>.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 Możesz użyć metody obsługi zdarzeń renderowania, aby utworzyć niestandardową zawartość rysunku. Ta metoda obsługi zdarzeń jest wywoływana raz na klatkę. Za każdym razem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , gdy organizowane są utrwalone dane renderowania w drzewie wizualnym na grafie sceny kompozycji, wywoływana jest metoda obsługi zdarzeń. Ponadto, jeśli zmiany w drzewie wizualnym wymuśą aktualizacje wykresu sceny tworzenia, wywoływana jest również metoda obsługi zdarzeń. Należy pamiętać, że metoda obsługi zdarzeń jest wywoływana po obliczaniu układu. Można jednak zmodyfikować układ w metodzie obsługi zdarzeń, co oznacza, że układ zostanie obliczony co więcej przed renderowaniem.  
  
 Poniższy przykład pokazuje, jak można udostępnić niestandardowe rysunki w <xref:System.Windows.Media.CompositionTarget> metodzie obsługi zdarzeń. W tym przypadku kolor <xref:System.Windows.Controls.Canvas> tła jest rysowany z wartością koloru na podstawie położenia współrzędnej myszy. Jeśli przesuniesz mysz wewnątrz, <xref:System.Windows.Controls.Canvas>jej kolor tła zmieni się. Ponadto średnia szybkość klatek jest obliczana w oparciu o bieżący czas, który upłynął, i łączną liczbę wyrenderowanych ramek.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Może się okazać, że niestandardowe rysowanie działa z różnymi szybkościami na różnych komputerach. Wynika to z faktu, że niestandardowe rysowanie nie jest zależne od szybkości klatek. W zależności od używanego systemu i obciążenia tego systemu <xref:System.Windows.Media.CompositionTarget.Rendering> zdarzenie może być nazywane inną liczbą razy na sekundę. Aby uzyskać informacje na temat określania możliwości i wydajności sprzętu grafiki dla urządzenia z uruchomioną [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacją, zobacz [warstwy renderowania grafiki](../advanced/graphics-rendering-tiers.md).  
  
 Dodanie lub usunięcie delegata <xref:System.EventHandler> renderowania, gdy zdarzenie jest wyzwalane, zostanie opóźnione do momentu zakończenia zdarzenia. Jest to zgodne z metodami <xref:System.MulticastDelegate>, które są obsługiwane w środowisku uruchomieniowym języka wspólnego (CLR). Należy również zauważyć, że zdarzenia renderowania nie są gwarantowane do wywołania w żadnej określonej kolejności. Jeśli masz wielu <xref:System.EventHandler> delegatów, które opierają się na określonej kolejności, należy zarejestrować pojedyncze <xref:System.Windows.Media.CompositionTarget.Rendering> zdarzenie i przydzielić delegatów w poprawnej kolejności.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.CompositionTarget>
- [Renderowanie grafiki WPF — przegląd](wpf-graphics-rendering-overview.md)
