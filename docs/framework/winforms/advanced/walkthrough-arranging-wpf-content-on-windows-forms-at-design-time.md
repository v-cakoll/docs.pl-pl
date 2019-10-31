---
title: 'Wskazówki: rozmieszczanie zawartości WPF na formularzach systemu Windows w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9062a3da9a6020762114702b6cce6b42414ab92d
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197458"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a>Przewodnik: rozmieszczanie zawartości WPF na Windows Forms w czasie projektowania

W tym artykule pokazano, jak używać funkcji układu Windows Forms, takich jak kotwice i linii wyrównania, aby rozmieścić kontrolki Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.

## <a name="create-the-project"></a>Utwórz projekt

Otwórz program Visual Studio i Utwórz nowy projekt aplikacji Windows Forms w Visual Basic lub wizualizacji C# o nazwie `ArrangeElementHost`.

> [!NOTE]
> W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.

## <a name="create-the-wpf-control"></a>Tworzenie kontrolki WPF

Po dodaniu kontrolki WPF do projektu można ją rozmieścić w formularzu.

1. Dodaj nowy <xref:System.Windows.Controls.UserControl> WPF do projektu. Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. W widok Projekt upewnij się, że wybrano pozycję `UserControl1`.

3. W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

4. Ustaw wartość właściwości <xref:System.Windows.Controls.Control.Background%2A> na **niebieską**.

5. Skompiluj projekt.

## <a name="host-wpf-controls-in-a-layout-panel"></a>Hostowanie formantów WPF w panelu układu

W panelach układów można używać formantów WPF w taki sam sposób, jak w przypadku innych kontrolek Windows Forms.

1. Otwórz `Form1` w Projektant formularzy systemu Windows.

2. W **przyborniku**przeciągnij kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> na formularz.

3. Na panelu tagów inteligentnych kontrolki <xref:System.Windows.Forms.TableLayoutPanel> wybierz pozycję **Usuń ostatni wiersz**.

4. Zmień rozmiar kontrolki <xref:System.Windows.Forms.TableLayoutPanel> na większą szerokość i wysokość.

5. W **przyborniku**kliknij dwukrotnie `UserControl1`, aby utworzyć wystąpienie `UserControl1` w pierwszej komórce kontrolki <xref:System.Windows.Forms.TableLayoutPanel>.

   Wystąpienie `UserControl1` jest hostowane w nowej kontrolce <xref:System.Windows.Forms.Integration.ElementHost> o nazwie `elementHost1`.

6. W **przyborniku**kliknij dwukrotnie `UserControl1`, aby utworzyć inne wystąpienie w drugiej komórce kontrolki <xref:System.Windows.Forms.TableLayoutPanel>.

7. W oknie **Konspekt dokumentu** wybierz pozycję `tableLayoutPanel1`.

8. W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.Forms.Control.Padding%2A> na **10, 10, 10, 10**.

   Zmiany rozmiaru obu formantów <xref:System.Windows.Forms.Integration.ElementHost> są dopasowane do nowego układu.

## <a name="use-snaplines-to-align-wpf-controls"></a>Użyj linii wyrównania do wyrównania formantów WPF

Linii wyrównania umożliwia łatwe wyrównywanie kontrolek w formularzu. Możesz użyć linii wyrównania, aby również wyrównać formanty WPF. Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu linii wyrównania](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

1. Z **przybornika**przeciągnij wystąpienie `UserControl1` na formularz i umieść je w miejscu poniżej kontrolki <xref:System.Windows.Forms.TableLayoutPanel>.

   Wystąpienie `UserControl1` jest hostowane w nowej kontrolce <xref:System.Windows.Forms.Integration.ElementHost> o nazwie `elementHost3`.

2. Korzystając z linii wyrównania, Wyrównaj lewą krawędź `elementHost3` z lewą krawędzią <xref:System.Windows.Forms.TableLayoutPanel> formantu.

3. Przy użyciu linii wyrównania rozmiar `elementHost3` ma taką samą szerokość jak kontrolka <xref:System.Windows.Forms.TableLayoutPanel>.

4. Przenieś `elementHost3` do kontrolki <xref:System.Windows.Forms.TableLayoutPanel> do momentu pojawienia się środkowej snapline między kontrolkami.

5. W oknie **Właściwości** ustaw wartość właściwości Margin na **20, 20, 20, 20**.

6. Przenieś `elementHost3` z powrotem do kontrolki <xref:System.Windows.Forms.TableLayoutPanel> do momentu, aż zostanie wyświetlone centrum snapline. Centrum snapline teraz wskazuje margines 20.

7. Przenieś `elementHost3` w prawo do momentu, aż lewa krawędź wyrównuje z lewą krawędzią `elementHost1`.

8. Zmień szerokość `elementHost3` do momentu, aż jego prawa krawędź wyrównuje z prawą krawędzią `elementHost2`.

## <a name="anchor-and-dock-wpf-controls"></a>Zakotwiczenie i dokowanie formantów WPF

Kontrolka WPF hostowana w formularzu ma takie samo zachowanie dotyczące zakotwiczania i dokowania jak inne kontrolki Windows Forms.

1. Wybierz `elementHost1`.

2. W oknie **Właściwości** ustaw właściwość <xref:System.Windows.Forms.Control.Anchor%2A> na **Top, Bottom, Left, Right**.

3. Zmień rozmiar kontrolki <xref:System.Windows.Forms.TableLayoutPanel> na większy.

   Formant `elementHost1` zmienia rozmiar, aby wypełnić komórkę.

4. Wybierz `elementHost2`.

5. W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>.

   Formant `elementHost2` zmienia rozmiar, aby wypełnić komórkę.

6. Wybierz kontrolkę <xref:System.Windows.Forms.TableLayoutPanel>.

7. Ustaw wartość właściwości <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Top>.

8. Wybierz `elementHost3`.

9. Ustaw wartość właściwości <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>.

   Kontrolka `elementHost3` zmienia rozmiar w celu wypełnienia pozostałego miejsca w formularzu.

10. Zmień rozmiar formularza.

    Wszystkie trzy <xref:System.Windows.Forms.Integration.ElementHost> kontrolki odpowiednio zmieniają rozmiar.

    Aby uzyskać więcej informacji, zobacz [How to: Zakotwiczanie i dokowanie formantów podrzędnych w formancie TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Instrukcje: wyrównywanie kontrolki z krawędziami formularzy w czasie projektowania](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Migracja i współdziałanie](../../wpf/advanced/migration-and-interoperability.md)
- [Korzystanie z kontrolek WPF](using-wpf-controls.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
