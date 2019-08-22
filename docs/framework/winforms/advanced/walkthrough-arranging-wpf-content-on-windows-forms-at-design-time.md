---
title: 'Przewodnik: Rozmieszczanie zawartości WPF na formularzach systemu Windows w czasie projektowania'
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
ms.openlocfilehash: 7858ffd708c78d6397d533f613ccc2ea78d6cbed
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658521"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a>Przewodnik: Rozmieszczanie zawartości WPF na Windows Forms w czasie projektowania

W tym artykule pokazano, jak używać funkcji układu Windows Forms, takich jak kotwice i linii wyrównania, aby rozmieścić kontrolki Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.

## <a name="create-the-project"></a>Utwórz projekt

Otwórz program Visual Studio i Utwórz nowy projekt aplikacji Windows Forms w Visual Basic lub C# wizualizacji `ArrangeElementHost`o nazwie.

> [!NOTE]
> W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.

## <a name="create-the-wpf-control"></a>Tworzenie kontrolki WPF

Po dodaniu kontrolki WPF do projektu można ją rozmieścić w formularzu.

1. Dodaj nową WPF <xref:System.Windows.Controls.UserControl> do projektu. Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`. Aby uzyskać więcej informacji, [zobacz Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)projektowania.

2. W widok Projekt upewnij się, że `UserControl1` jest zaznaczone.

3. W oknie **Właściwości** ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> właściwości i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

4. Ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości na niebieską.

5. Skompiluj projekt.

## <a name="host-wpf-controls-in-a-layout-panel"></a>Hostowanie formantów WPF w panelu układu

W panelach układów można używać formantów WPF w taki sam sposób, jak w przypadku innych kontrolek Windows Forms.

1. Otwórz `Form1` w Projektant formularzy systemu Windows.

2. W **przyborniku**przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę na formularz.

3. Na panelu tagu inteligentnego kontrolkiwybierzpozycjęUsuńostatni<xref:System.Windows.Forms.TableLayoutPanel> wiersz.

4. Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolki na większą szerokość i wysokość.

5. W **przyborniku**kliknij `UserControl1` dwukrotnie, aby utworzyć wystąpienie elementu `UserControl1` w pierwszej komórce <xref:System.Windows.Forms.TableLayoutPanel> formantu.

   Wystąpienie `UserControl1` jest hostowane w nowym <xref:System.Windows.Forms.Integration.ElementHost> formancie o nazwie `elementHost1`.

6. W **przyborniku**kliknij `UserControl1` dwukrotnie, aby utworzyć inne wystąpienie w <xref:System.Windows.Forms.TableLayoutPanel> drugiej komórce formantu.

7. W oknie **Konspekt dokumentu** wybierz opcję `tableLayoutPanel1`.

8. W oknie **Właściwości** ustaw wartość <xref:System.Windows.Forms.Control.Padding%2A> właściwości na **10, 10, 10, 10**.

   Oba <xref:System.Windows.Forms.Integration.ElementHost> kontrolki są zmieniane w celu dopasowania do nowego układu.

## <a name="use-snaplines-to-align-wpf-controls"></a>Użyj linii wyrównania do wyrównania formantów WPF

Linii wyrównania umożliwia łatwe wyrównywanie kontrolek w formularzu. Możesz użyć linii wyrównania, aby również wyrównać formanty WPF. Aby uzyskać więcej informacji, [zobacz Przewodnik: Rozmieszczanie kontrolek na Windows Forms](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)przy użyciu linii wyrównania.

1. Z **przybornika**przeciągnij wystąpienie do `UserControl1` formularza i umieść je w miejscu pod <xref:System.Windows.Forms.TableLayoutPanel> kontrolką.

   Wystąpienie `UserControl1` jest hostowane w nowym <xref:System.Windows.Forms.Integration.ElementHost> formancie o nazwie `elementHost3`.

2. Przy użyciu linii wyrównania, Wyrównaj lewą krawędź `elementHost3` z lewej <xref:System.Windows.Forms.TableLayoutPanel> krawędzią kontrolki.

3. Przy użyciu linii wyrównania, `elementHost3` rozmiar do tej samej szerokości <xref:System.Windows.Forms.TableLayoutPanel> jak kontrolka.

4. Poruszanie `elementHost3` się <xref:System.Windows.Forms.TableLayoutPanel> w kierunku kontroli do momentu pojawienia się środkowego snapline między kontrolkami.

5. W oknie **Właściwości** ustaw wartość właściwości Margin na **20, 20, 20, 20**.

6. Przesuń z powrotem z kontrolki do momentu, gdy zostanie wyświetlone okno Center snapline. <xref:System.Windows.Forms.TableLayoutPanel> `elementHost3` Centrum snapline teraz wskazuje margines 20.

7. Przejście `elementHost3` w prawo do momentu, aż jego lewa krawędź zostanie wyrównana do lewej `elementHost1`krawędzi.

8. Zmień szerokość `elementHost3` do wyrównania `elementHost2`do prawej krawędzi.

## <a name="anchor-and-dock-wpf-controls"></a>Zakotwiczenie i dokowanie formantów WPF

Kontrolka WPF hostowana w formularzu ma takie samo zachowanie dotyczące zakotwiczania i dokowania jak inne kontrolki Windows Forms.

1. Wybierz `elementHost1`opcję.

2. W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.Control.Anchor%2A> właściwość na **Top, Bottom, Left, Right**.

3. Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolki na większy.

   Zmienia `elementHost1` rozmiar kontrolki w celu wypełnienia komórki.

4. Wybierz `elementHost2`opcję.

5. W oknie **Właściwości** ustaw wartość <xref:System.Windows.Forms.Control.Dock%2A> właściwości na <xref:System.Windows.Forms.DockStyle.Fill>.

   Zmienia `elementHost2` rozmiar kontrolki w celu wypełnienia komórki.

6. <xref:System.Windows.Forms.TableLayoutPanel> Zaznacz kontrolkę.

7. Ustaw wartość <xref:System.Windows.Forms.Control.Dock%2A> właściwości na <xref:System.Windows.Forms.DockStyle.Top>.

8. Wybierz `elementHost3`opcję.

9. Ustaw wartość <xref:System.Windows.Forms.Control.Dock%2A> właściwości na <xref:System.Windows.Forms.DockStyle.Fill>.

   Zmienia `elementHost3` rozmiar kontrolki w celu wypełnienia pozostałego miejsca w formularzu.

10. Zmień rozmiar formularza.

    Wszystkie trzy <xref:System.Windows.Forms.Integration.ElementHost> kontrolki odpowiednio zmieniają rozmiar.

    Aby uzyskać więcej informacji, zobacz [jak: Zakotwiczenie i dokowanie formantów podrzędnych w formancie](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)TableLayoutPanel.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Instrukcje: Wyrównywanie kontrolki do krawędzi formularzy w czasie projektowania](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu linii wyrównania](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Migracja i współdziałanie](../../wpf/advanced/migration-and-interoperability.md)
- [Korzystanie z kontrolek WPF](using-wpf-controls.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
