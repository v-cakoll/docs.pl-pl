---
title: Jak renderować w interwałach klatek z użyciem CompositionTarget
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
ms.openlocfilehash: cc043e6d225ad3dbe57a0924593fac0f68af7eb1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43473921"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Jak renderować w interwałach klatek z użyciem CompositionTarget
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aparat animacji udostępnia wiele funkcji do tworzenia opartych na klatkach animacji. Istnieją jednak scenariuszy aplikacji, w których potrzebujesz bardziej szczegółowej kontroli nad renderowania na zasadzie na ramki. <xref:System.Windows.Media.CompositionTarget> Obiekt zapewnia możliwość tworzenia niestandardowe animacje oparte na wywołanie zwrotne poszczególnych klatkach.  
  
 <xref:System.Windows.Media.CompositionTarget> jest klasą statyczną, który reprezentuje powierzchni ekranu, na którym jest rysowana aplikacji. <xref:System.Windows.Media.CompositionTarget.Rendering> Zdarzenie jest zgłaszane w każdym sceny aplikacji rysowania. Szybkość klatek renderowania jest to liczba razy na sekundę rysowania sceny.  
  
> [!NOTE]
>  Na przykład kompletny kod przy użyciu <xref:System.Windows.Media.CompositionTarget>, zobacz [przy użyciu przykładu CompositionTarget](https://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Media.CompositionTarget.Rendering> Zdarzenia generowane podczas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] proces renderowania. W poniższym przykładzie pokazano, jak zarejestrować <xref:System.EventHandler> delegować statycznej <xref:System.Windows.Media.CompositionTarget.Rendering> metody <xref:System.Windows.Media.CompositionTarget>.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 Twoja metoda programu obsługi zdarzeń renderowania służy do tworzenia niestandardowego rysowania zawartości. Ta metoda obsługi zdarzeń jest wywoływana raz na klatkę. Każdym razem, gdy program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshals danych utrwalonych renderowania, w drzewie wizualnym między do składu wykres scen, Twoja metoda programu obsługi zdarzeń jest wywoływana. Ponadto zmiany do drzewa wizualnego wymuszenia aktualizacji do wykresu sceny kompozycji, jest również nazywany metodę programu obsługi zdarzeń. Należy pamiętać, że Twoja metoda programu obsługi zdarzeń jest wywoływana po obliczeniu układu. Jednak można modyfikować układ w metodzie obsługi zdarzeń, co oznacza, że taki układ zostanie obliczona ponownie przed renderowaniem.  
  
 Poniższy przykład pokazuje, jak możesz podać niestandardowy Rysowanie w <xref:System.Windows.Media.CompositionTarget> metody obsługi zdarzeń. W tym przypadku kolor tła <xref:System.Windows.Controls.Canvas> jest rysowany przy użyciu wartości koloru w oparciu o współrzędnych położenie kursora myszy. Po przesunięciu myszy wewnątrz <xref:System.Windows.Controls.Canvas>, jego zmiany kolorów w tle. Ponadto średnia szybkość klatek jest obliczana, na podstawie bieżący czas i całkowitą liczbę ramek renderowany.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Użytkownik może stwierdzić, uruchamia niestandardowy rysunek przy różnych prędkościach na różnych komputerach. Jest to spowodowane niestandardowy rysunek nie jest szybkość klatek niezależne. W zależności od systemu, są uruchomione i obciążenie systemu <xref:System.Windows.Media.CompositionTarget.Rendering> zdarzeń może zostać wywołana różną liczbę razy na sekundę. Aby uzyskać informacje na temat określania możliwości sprzętu grafiki i wydajności na urządzeniu z systemem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, zobacz [poziomy renderowania grafiki](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
 Dodawanie lub usuwanie renderowania <xref:System.EventHandler> po zakończeniu zdarzenia delegata, gdy zdarzenie jest uruchamiana zostanie opóźnione aż do wyzwalania. Jest to zgodne z jak <xref:System.MulticastDelegate>— na podstawie zdarzenia są obsługiwane w środowiska uruchomieniowego języka wspólnego (CLR). Należy również zauważyć, że renderowanie zdarzeń nie ma gwarancji, można wywołać w określonej kolejności. Jeśli masz wiele <xref:System.EventHandler> delegatów, które zależą od określonej kolejności, należy zarejestrować pojedynczy <xref:System.Windows.Media.CompositionTarget.Rendering> zdarzeń i multipleksować delegatów prawidłowo kolejność samodzielnie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.CompositionTarget>  
 [Renderowanie grafiki WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
