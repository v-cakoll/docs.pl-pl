---
title: Zbieranie pisma odręcznego w aplikacjach WPF
ms.date: 08/15/2018
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
ms.openlocfilehash: 25f9c0141a97d8e52e0883b14fd3e1f4574a05ea
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46004285"
---
# <a name="collect-ink"></a>Zbieranie pisma odręcznego

[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platformy zbiera cyfrowy atrament w ramach podstawowych jego funkcjonalność. W tym temacie omówiono metody do kolekcji pisma odręcznego w Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Wymagania wstępne

Aby użyć poniższych przykładów, należy najpierw zainstalować program Visual Studio i [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Należy również zrozumieć sposób pisania aplikacji dla WPF. Aby uzyskać więcej informacji na temat rozpoczynania pracy przy użyciu platformy WPF, zobacz [Instruktaż: Mój pierwszy aplikacji klasycznej WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="use-the-inkcanvas-element"></a>Użyj elementu InkCanvas

<xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> Element udostępnia najprostszy sposób zbieranie pisma odręcznego na platformie WPF. Użyj <xref:System.Windows.Controls.InkCanvas> element do odbierania i wyświetlania danych wejściowych pisma odręcznego. Często danych wejściowych pisma odręcznego za pomocą pióra, która współdziała z dyskretyzatora, aby wygenerować pociągnięcia odręczne. Ponadto można użyć myszy zamiast pióra. Utworzono pociągnięć są reprezentowane jako <xref:System.Windows.Ink.Stroke> obiektów i ich można modyfikować programowo i przez użytkownika dane wejściowe. <xref:System.Windows.Controls.InkCanvas> Pozwala użytkownikom wybrać, zmodyfikować lub usunąć istniejące <xref:System.Windows.Ink.Stroke>.

Przy użyciu XAML, możesz skonfigurować zbieranie pisma odręcznego równie łatwo, jak dodawanie **InkCanvas** elementu z drzewa. W poniższym przykładzie dodano <xref:System.Windows.Controls.InkCanvas> do domyślnego projektu WPF w programie Visual Studio:

[!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

**InkCanvas** elementu może również zawierać elementy podrzędne, dzięki czemu można dodać możliwości adnotacji pisma odręcznego prawie żadnego typu elementu XAML. Na przykład, umożliwiające dodanie funkcji pisma odręcznego do elementów tekstowych, po prostu Uczyń elementem podrzędnym elementu <xref:System.Windows.Controls.InkCanvas>:

[!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

Dodano obsługę Oznaczanie obrazu z pisma odręcznego jest równie proste:

[!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a>Tryby InkCollection

<xref:System.Windows.Controls.InkCanvas> Obsługuje różne dane wejściowe metody za pomocą jego <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> właściwości.

### <a name="manipulate-ink"></a>Manipulowanie pisma odręcznego

<xref:System.Windows.Controls.InkCanvas> Obsługuje wiele pisma odręcznego operacje edycji. Na przykład <xref:System.Windows.Controls.InkCanvas> wstecz pióra obsługuje wymazanie, a żaden dodatkowy kod nie jest potrzebna do dodawania funkcjonalności do elementu.

#### <a name="selection"></a>Wybór

Ustawienie trybu wyboru jest tak proste, jak ustawienie <xref:System.Windows.Controls.InkCanvasEditingMode> właściwości **wybierz**.

Poniższy kod ustawia tryb edycji, w oparciu o wartość <xref:System.Windows.Forms.CheckBox>:

[!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a>DrawingAttributes

Użyj <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> właściwości, aby zmienić wygląd pociągnięcia odręczne. Na przykład <xref:System.Windows.Ink.DrawingAttributes.Color%2A> członkiem <xref:System.Windows.Ink.DrawingAttributes> Ustawia kolor renderowanych <xref:System.Windows.Ink.Stroke>.

Poniższy przykład umożliwia zmianę koloru wybranych pociągnięć czerwony:

[!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes

<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> Właściwości zapewnia dostęp do właściwości, takie jak wysokość, szerokość i kolor pociągnięć, które zostały utworzone w <xref:System.Windows.Controls.InkCanvas>. Po zmianie <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, wszystkie przyszłe pociągnięć zawierana <xref:System.Windows.Controls.InkCanvas> są renderowane przy użyciu nowej wartości właściwości.

Oprócz modyfikowania <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> w pliku związanym z kodem, składnia XAML można użyć do określenia <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> właściwości.

Następny przykład pokazuje, jak ustawić <xref:System.Windows.Ink.DrawingAttributes.Color%2A> właściwości. Aby użyć tego kodu, Utwórz nowy projekt WPF w programie Visual Studio o nazwie "HelloInkCanvas". Zastąp kod w *MainWindow.xaml* pliku następującym kodem:

[!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

Następnie dodaj poniższe procedury obsługi zdarzeń przycisku do kodzie pliku wewnątrz klasy MainWindow:

[!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

Po skopiowaniu tego kodu, naciśnij klawisz **F5** w programie Visual Studio, aby uruchomić program w debugerze.

Zwróć uwagę sposób, w jaki <xref:System.Windows.Controls.StackPanel> umieszcza przycisków w górnej części <xref:System.Windows.Controls.InkCanvas>. Jeśli zostanie podjęta próba pisma odręcznego w górnej części przyciski, <xref:System.Windows.Controls.InkCanvas> zbiera i renderowanie pisma odręcznego za pomocą przycisków. Jest to spowodowane przyciski są elementy równorzędne <xref:System.Windows.Controls.InkCanvas> w przeciwieństwie do elementów podrzędnych. Przyciski są także wyżej w porządku, więc pisma odręcznego jest renderowany za ich.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>