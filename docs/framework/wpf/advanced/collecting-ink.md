---
title: Zbieranie atramentu
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
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cbf55b5d84420a6aa7af06e94497a85a2b54a0c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="collecting-ink"></a>Zbieranie atramentu
[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platformy zbiera elektroniczne pismo odręczne jako podstawowy element jej funkcji. W tym temacie omówiono metody pobierania pismo odręczne w [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby użyć w poniższych przykładach, należy najpierw zainstalować [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] i [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Należy także zrozumienie sposobu pisania aplikacji dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Aby uzyskać więcej informacji na temat rozpoczynania pracy z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [wskazówki: Moje pierwszą aplikację pulpitu WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="using-the-inkcanvas-element"></a>Za pomocą elementu InkCanvas  
 <xref:System.Windows.Controls.InkCanvas> Element udostępnia Najprostszym sposobem zbieranie pismo odręczne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.InkCanvas> Element jest podobny do [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx) obiekt z [!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)] i starszych wersji.  
  
 Użyj <xref:System.Windows.Controls.InkCanvas> element do pobierania i wyświetlania odręczne. Często wejściowe odręczne przy użyciu pióra, współpracującej z dyskretyzatora, aby utworzyć pociągnięcia odręczne. Ponadto można użyć myszy zamiast pióra. Utworzona kolekcja strokes są reprezentowane jako <xref:System.Windows.Ink.Stroke> obiektów i ich może manipulować programowo i przez użytkownika. <xref:System.Windows.Controls.InkCanvas> , Użytkownicy mogą wybrać, zmodyfikować lub usunąć istniejące <xref:System.Windows.Ink.Stroke>.  
  
 Przy użyciu języka XAML, możesz skonfigurować zbieranie pisma odręcznego równie łatwo, jak dodawanie `InkCanvas` elementu z drzewa. W poniższym przykładzie dodano <xref:System.Windows.Controls.InkCanvas> do domyślnego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projekt utworzony w [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)].  
  
 [!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]  
  
 `InkCanvas` Może również zawierać elementy podrzędne, umożliwiające dodanie funkcji adnotacji odręczne prawie każdego typu elementu XAML. Na przykład, umożliwiające dodanie funkcji pisma odręcznego do elementu tekstu, po prostu była elementem podrzędnym <xref:System.Windows.Controls.InkCanvas>.  
  
 [!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]  
  
 Dodawanie obsługi do oznaczania obrazu odręczne jest równie proste.  
  
 [!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]  
  
### <a name="inkcollection-modes"></a>Tryby InkCollection  
 <xref:System.Windows.Controls.InkCanvas> Zapewnia obsługę wejściowych różne metody za pomocą jego <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> właściwości.  
  
### <a name="manipulating-ink"></a>Manipulowanie odręcznego  
 <xref:System.Windows.Controls.InkCanvas> Zapewnia obsługę wielu odręczne operacje edycji. Na przykład <xref:System.Windows.Controls.InkCanvas> wstecz pióra obsługuje wymazać z żaden dodatkowy kod, aby dodać funkcje do elementu.  
  
#### <a name="selection"></a>Wybór  
 Ustawienie trybu wyboru jest tak proste, jak ustawienie <xref:System.Windows.Controls.InkCanvasEditingMode> właściwości **wybierz**. Poniższy kod ustawia tryb edycji, na podstawie wartości z <xref:System.Windows.Forms.CheckBox>:  
  
 [!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
 [!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]  
  
#### <a name="drawingattributes"></a>DrawingAttributes  
 Użyj <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> właściwości, aby zmienić wygląd pociągnięcia odręczne. Na przykład <xref:System.Windows.Ink.DrawingAttributes.Color%2A> członkiem <xref:System.Windows.Ink.DrawingAttributes> Ustawia kolor renderowanych <xref:System.Windows.Ink.Stroke>. Poniższy przykład umożliwia zmianę wybranych pociągnięć kolor na czerwony.  
  
 [!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
 [!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]  
  
### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> Właściwości zapewnia dostęp do właściwości, takie jak wysokość, szerokość i kolor pociągnięć mogą być tworzone w <xref:System.Windows.Controls.InkCanvas>. Po zmianie <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, wszystkie przyszłe pociągnięć wprowadzany do <xref:System.Windows.Controls.InkCanvas> są renderowane przy użyciu nowych wartości właściwości.  
  
 Oprócz modyfikowania <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> w pliku związanym z kodem za pomocą składni języka XAML służący do określania <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> właściwości. Poniższy kod XAML przedstawia sposób ustawiania <xref:System.Windows.Ink.DrawingAttributes.Color%2A> właściwości. Aby użyć tego kodu, Utwórz nową [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projektu o nazwie "HelloInkCanvas" w programie Visual Studio 2005. Zastąp kod w pliku Window1.xaml następującym kodem.  
  
 [!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]  
  
 Następnie dodaj poniższe obsługi zdarzeń przycisku do kodzie pliku wewnątrz klasy Window1.  
  
 [!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]  
  
 Po skopiowaniu tego kodu, naciśnij klawisz **F5** programu Microsoft Visual Studio 2005 do uruchomienia programu w debugerze.  
  
 Powiadomienie jak <xref:System.Windows.Controls.StackPanel> umieszcza przycisków nad <xref:System.Windows.Controls.InkCanvas>. Jeśli spróbujesz pismo odręczne na początku przyciski, <xref:System.Windows.Controls.InkCanvas> zbiera i renderuje pismo odręczne za pomocą przycisków. Wynika to z faktu przyciski są elementy równorzędne <xref:System.Windows.Controls.InkCanvas> w przeciwieństwie do elementów podrzędnych. Przyciski są także wyżej w kolejności, więc pismo odręczne jest renderowany za ich.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Ink.DrawingAttributes>  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>  
 <xref:System.Windows.Ink>
