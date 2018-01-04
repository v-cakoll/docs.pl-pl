---
title: "Jak renderować w interwałach klatek z użyciem CompositionTarget"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb7e917c59f11ed78f8d44fa4b674d8d572f3623
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Jak renderować w interwałach klatek z użyciem CompositionTarget
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aparat animacji zapewnia wiele funkcji do tworzenia opartych na ramki animacji. Istnieją jednak scenariuszy aplikacji, w których należy dopasowanymi bardziej precyzyjną kontrolę nad renderowania na podstawie na ramki. <xref:System.Windows.Media.CompositionTarget> Obiekt zapewnia możliwość tworzenia niestandardowych animacje oparte na wywołanie zwrotne na ramki.  
  
 <xref:System.Windows.Media.CompositionTarget>jest statycznej klasy, która reprezentuje powierzchni ekranu, na którym aplikacja jest rysowane. <xref:System.Windows.Media.CompositionTarget.Rendering> Zdarzenie jest wywoływane każdorazowo sceny aplikacji jest rysowane. Szybkość klatek renderowania jest liczba powtórzeń sceny jest rysowana na sekundę.  
  
> [!NOTE]
>  Na przykład kompletny kod przy użyciu <xref:System.Windows.Media.CompositionTarget>, zobacz [przy użyciu przykładowych CompositionTarget](http://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Media.CompositionTarget.Rendering> Zdarzenia generowane podczas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] proces renderowania. W poniższym przykładzie pokazano, jak zarejestrować <xref:System.EventHandler> przekazać statycznego <xref:System.Windows.Media.CompositionTarget.Rendering> metoda <xref:System.Windows.Media.CompositionTarget>.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 Metoda obsługi zdarzeń z renderowaniem służy do tworzenia niestandardowych rysowania zawartości. Ta metoda obsługi zdarzeń jest wywoływana raz na klatkę. Każdej aktualizacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshals danych utrwalonych renderowania w drzewie wizualnym między do wykresu sceny kompozycji, Twoje metoda obsługi zdarzeń jest wywoływana. Ponadto zmiany do drzewa wizualnego wymuszenia aktualizacji do wykresu sceny kompozycji, jest również nazywany metodę procedury obsługi zdarzeń. Należy pamiętać, że Twoje metoda obsługi zdarzeń jest wywoływana po układ został obliczony. Jednak można zmodyfikować układu w Twojej metoda obsługi zdarzeń, co oznacza, że taki układ będzie obliczana raz przed renderowaniem.  
  
 W poniższym przykładzie przedstawiono sposób można zapewnić niestandardowe Rysowanie w <xref:System.Windows.Media.CompositionTarget> metoda obsługi zdarzeń. W tym przypadku kolor tła <xref:System.Windows.Controls.Canvas> jest rysowany z wartości koloru na podstawie współrzędnych pozycji myszy. Jeśli przeniesiesz myszy wewnątrz <xref:System.Windows.Controls.Canvas>, jego zmiany kolorów w tle. Ponadto średnia szybkość jest obliczana, na podstawie bieżący czas, który upłynął i całkowitą liczbę ramek renderowany.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Użytkownik może stwierdzić, uruchamia niestandardowy rysunek przy różnych prędkościach na różnych komputerach. Wynika to z faktu niestandardowego rysunek nie jest szybkość klatek niezależne. W zależności od systemu są uruchomione i obciążenie systemu <xref:System.Windows.Media.CompositionTarget.Rendering> zdarzeń może zostać wywołana inną liczbę razy na sekundę. Aby uzyskać informacje na temat określania możliwości sprzętowe grafiki i wydajności na urządzeniu z systemem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, zobacz [warstw renderowania grafiki](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
 Dodawanie lub usuwanie renderowania <xref:System.EventHandler> delegata, gdy zdarzenie jest uruchamiane zostanie opóźnione aż do po zakończeniu zdarzenie wywołujące. Jest to zgodne z jak <xref:System.MulticastDelegate>— na podstawie zdarzenia są obsługiwane w środowiska uruchomieniowego języka wspólnego (CLR). Należy również zauważyć, że zdarzenia renderowania nie ma gwarancji można wywołać w określonej kolejności. Jeśli masz wiele <xref:System.EventHandler> delegatów, które opierają się na określonej kolejności, należy zarejestrować pojedynczy <xref:System.Windows.Media.CompositionTarget.Rendering> zdarzeń i Multipleksowanie delegatów na poziomie właściwej kolejności samodzielnie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.CompositionTarget>  
 [Renderowanie grafiki WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
