---
title: Zbieranie cyfrowego atramentu
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
ms.openlocfilehash: 813a5313a6fbf83c36cdbed1f64ce69a217ad788
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747030"
---
# <a name="collect-ink"></a>Zbierz atrament

Platforma [Windows Presentation Foundation](../index.md) zbiera cyfrowy atrament jako rdzeń części swojej funkcjonalności. W tym temacie omówiono metody zbierania pisma odręcznego w Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Wymagania wstępne

Aby skorzystać z poniższych przykładów, należy najpierw zainstalować program Visual Studio i Windows SDK. Należy również zrozumieć, jak pisać aplikacje dla WPF. Aby uzyskać więcej informacji na temat rozpoczynania pracy z programem WPF, zobacz [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="use-the-inkcanvas-element"></a>Użyj elementu InkCanvas

Element <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> zapewnia najprostszy sposób zbierania pisma odręcznego w WPF. Użyj elementu <xref:System.Windows.Controls.InkCanvas>, aby odbierać i wyświetlać dane wejściowe odręczne. Często wprowadzasz atrament za pomocą pióra, który współdziała z dyskretyzatoram do tworzenia pociągnięć odręcznych. Ponadto mysz może być używana zamiast pióra. Utworzone pociągnięcia są reprezentowane jako obiekty <xref:System.Windows.Ink.Stroke> i mogą być przetwarzane programowo i przez użytkownika. <xref:System.Windows.Controls.InkCanvas> umożliwia użytkownikom wybranie, zmodyfikowanie lub usunięcie istniejących <xref:System.Windows.Ink.Stroke>.

Używając języka XAML, można tak szybko skonfigurować kolekcje farb, jak dodanie elementu **InkCanvas** do drzewa. Poniższy przykład dodaje <xref:System.Windows.Controls.InkCanvas> do domyślnego projektu WPF utworzonego w programie Visual Studio:

[!code-xaml[DigitalInkTopics#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

Element **InkCanvas** może także zawierać elementy podrzędne, dzięki czemu można dodać możliwości adnotacji odręcznej do niemal dowolnego typu elementu XAML. Na przykład, aby dodać możliwości pisma odręcznego do elementu tekstowego, wystarczy, że jest on elementem podrzędnym <xref:System.Windows.Controls.InkCanvas>:

[!code-xaml[DigitalInkTopics#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

Dodawanie obsługi oznaczania obrazu za pomocą pisma odręcznego jest równie proste:

[!code-xaml[DigitalInkTopics#7](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a>Tryby InkCollection

<xref:System.Windows.Controls.InkCanvas> zapewnia obsługę różnych trybów wprowadzania za pomocą właściwości <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>.

### <a name="manipulate-ink"></a>Manipulowanie atramentem

<xref:System.Windows.Controls.InkCanvas> zapewnia obsługę wielu operacji edycji farb. Na przykład <xref:System.Windows.Controls.InkCanvas> obsługuje wymazywanie z tyłu pióra i nie jest wymagany żaden dodatkowy kod, aby dodać funkcje do elementu.

#### <a name="selection"></a>Wybór

Ustawienie tryb wyboru jest proste, ponieważ ustawia właściwość <xref:System.Windows.Controls.InkCanvasEditingMode> do **wybrania**.

Poniższy kod ustawia tryb edycji na podstawie wartości <xref:System.Windows.Forms.CheckBox>:

[!code-csharp[DigitalInkTopics#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a>DrawingAttributes

Użyj właściwości <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>, aby zmienić wygląd pociągnięć odręcznych. Na przykład <xref:System.Windows.Ink.DrawingAttributes.Color%2A> element członkowski <xref:System.Windows.Ink.DrawingAttributes> ustawia kolor renderowanego <xref:System.Windows.Ink.Stroke>.

Poniższy przykład zmienia kolor wybranych pociągnięć na czerwony:

[!code-csharp[DigitalInkTopics#9](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes

Właściwość <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> zapewnia dostęp do właściwości, takich jak wysokość, Szerokość i kolor pociągnięć, które mają zostać utworzone w <xref:System.Windows.Controls.InkCanvas>. Po zmianie <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>wszystkie przyszłe pociągnięcia wprowadzane do <xref:System.Windows.Controls.InkCanvas> są renderowane z nowymi wartościami właściwości.

Oprócz modyfikacji <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> w pliku związanym z kodem, można użyć składni języka XAML do określania właściwości <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>.

W następnym przykładzie pokazano, jak ustawić właściwość <xref:System.Windows.Ink.DrawingAttributes.Color%2A>. Aby użyć tego kodu, Utwórz nowy projekt WPF o nazwie "HelloInkCanvas" w programie Visual Studio. Zastąp kod w pliku *MainWindow. XAML* następującym kodem:

[!code-xaml[HelloInkCanvas#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

Następnie Dodaj następujące programy obsługi zdarzeń przycisku do kodu związanego z kodem, wewnątrz klasy MainWindow:

[!code-csharp[HelloInkCanvas#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

Po skopiowaniu tego kodu naciśnij klawisz **F5** w programie Visual Studio, aby uruchomić program w debugerze.

Zauważ, jak <xref:System.Windows.Controls.StackPanel> umieszcza przyciski na górze <xref:System.Windows.Controls.InkCanvas>. Jeśli spróbujesz użyć atramentu w górnej części przycisków, <xref:System.Windows.Controls.InkCanvas> zbiera i renderuje pismo odręczne za przyciskami. Dzieje się tak, ponieważ przyciski są elementami równorzędnymi <xref:System.Windows.Controls.InkCanvas>, a nie elementami podrzędnymi. Ponadto przyciski są wyższe w kolejności z, dlatego atrament jest renderowany w tle.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>
