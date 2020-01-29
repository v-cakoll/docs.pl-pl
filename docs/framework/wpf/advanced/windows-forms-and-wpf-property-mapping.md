---
title: Mapowanie właściwości Windows Forms i WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
ms.openlocfilehash: 07e58f87d886212426e25be83f988037549ab642
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735239"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Mapowanie właściwości Windows Forms i WPF
Technologie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mają dwa podobne, ale różne modele właściwości. *Mapowanie właściwości* obsługuje międzyoperacyjność między obiema architekturami i zapewnia następujące możliwości:  
  
- Ułatwia mapowanie istotnych zmian właściwości w środowisku hosta do hostowanej kontrolki lub elementu.  
  
- Zapewnia domyślną obsługę mapowania najczęściej używanych właściwości.  
  
- Umożliwia łatwe usuwanie, zastępowanie lub Rozszerzanie właściwości domyślnych.  
  
- Zapewnia, że zmiany wartości właściwości na hoście są automatycznie wykrywane i tłumaczone na hostowaną kontrolkę lub element.  
  
> [!NOTE]
> Zdarzenia zmiany właściwości nie są propagowane w górę kontrolki hostingu lub hierarchii elementów. Tłumaczenie właściwości nie jest wykonywane, jeśli lokalna wartość właściwości nie zmienia się z powodu ustawienia bezpośredniego, stylów, dziedziczenia, powiązania danych lub innych mechanizmów, które zmieniają wartość właściwości.  
  
 Użyj właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> w elemencie <xref:System.Windows.Forms.Integration.WindowsFormsHost> i właściwości <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> w formancie <xref:System.Windows.Forms.Integration.ElementHost>, aby uzyskać dostęp do mapowania właściwości.  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>Mapowanie właściwości z elementem WindowsFormsHost  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> element tłumaczy domyślne właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na ich [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] równoważne przy użyciu poniższej tabeli translacji.  
  
|Hosting Windows Presentation Foundation|Windows Forms|Zachowanie międzyoperacyjności|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> ustawia właściwość <xref:System.Windows.Forms.Control.BackColor%2A> formantu hostowanego i Właściwość <xref:System.Windows.Forms.Control.BackgroundImage%2A> hostowanej kontrolki. Mapowanie jest wykonywane przy użyciu następujących reguł:<br /><br /> -Jeśli <xref:System.Windows.Controls.Control.Background%2A> jest pełny kolor, jest konwertowany i używany do ustawiania właściwości <xref:System.Windows.Forms.Control.BackColor%2A> hostowanej kontrolki. Właściwość <xref:System.Windows.Forms.Control.BackColor%2A> nie jest ustawiona w formancie hostowanym, ponieważ hostowana kontrolka może dziedziczyć wartość właściwości <xref:System.Windows.Forms.Control.BackColor%2A>. **Uwaga:**  Formant hostowany nie obsługuje przezroczystości. Wszystkie kolory przypisane do <xref:System.Windows.Forms.Control.BackColor%2A> muszą być całkowicie nieprzezroczyste, z wartością alfa równą 0xFF. <br /><br /> -Jeśli <xref:System.Windows.Controls.Control.Background%2A> nie jest pełny kolor, formant <xref:System.Windows.Forms.Integration.WindowsFormsHost> tworzy mapę bitową na podstawie właściwości <xref:System.Windows.Controls.Control.Background%2A>. Formant <xref:System.Windows.Forms.Integration.WindowsFormsHost> przypisuje tę mapę bitową do właściwości <xref:System.Windows.Forms.Control.BackgroundImage%2A> hostowanej kontrolki. Zapewnia to efekt podobny do przejrzystości. **Uwaga:**  Można zastąpić to zachowanie lub usunąć <xref:System.Windows.Controls.Control.Background%2A> mapowanie właściwości.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Jeśli domyślne mapowanie nie zostało ponownie przypisane, kontrola <xref:System.Windows.Forms.Integration.WindowsFormsHost> przechodzi przez jego hierarchię nadrzędną, dopóki nie znajdzie elementu nadrzędnego z ustawionym właściwością <xref:System.Windows.FrameworkElement.Cursor%2A>. Ta wartość jest tłumaczona na najbliższy odpowiedni kursor [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].<br /><br /> Jeśli mapowanie domyślne dla właściwości <xref:System.Windows.FrameworkElement.ForceCursor%2A> nie zostało ponownie przypisane, przechodzenie zostanie zatrzymane na pierwszym elemencie nadrzędnym z <xref:System.Windows.FrameworkElement.ForceCursor%2A> ustawionym na `true`.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight> mapowanie do <xref:System.Windows.Forms.RightToLeft.No>.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft> mapowanie do <xref:System.Windows.Forms.RightToLeft.Yes>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit> nie jest zamapowana.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> mapowanie do <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A> na <xref:System.Drawing.Font?displayProperty=nameWithType> hostowanej kontroli|Zestaw właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest tłumaczony na odpowiadającą <xref:System.Drawing.Font>. Po zmianie jednej z tych właściwości zostanie utworzony nowy <xref:System.Drawing.Font>. Dla <xref:System.Windows.FontStyles.Normal%2A>: <xref:System.Drawing.FontStyle.Italic> jest wyłączone. W przypadku <xref:System.Windows.FontStyles.Italic%2A> lub <xref:System.Windows.FontStyles.Oblique%2A>: <xref:System.Drawing.FontStyle.Italic> jest włączona.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A> na <xref:System.Drawing.Font?displayProperty=nameWithType> hostowanej kontroli|Zestaw właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest tłumaczony na odpowiadającą <xref:System.Drawing.Font>. Po zmianie jednej z tych właściwości zostanie utworzony nowy <xref:System.Drawing.Font>. W przypadku <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, <xref:System.Windows.FontWeights.DemiBold%2A>, <xref:System.Windows.FontWeights.ExtraBold%2A>, <xref:System.Windows.FontWeights.Heavy%2A>, <xref:System.Windows.FontWeights.Medium%2A>, <xref:System.Windows.FontWeights.SemiBold%2A>lub <xref:System.Windows.FontWeights.UltraBold%2A>: <xref:System.Drawing.FontStyle.Bold> jest włączona. W przypadku <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, <xref:System.Windows.FontWeights.Normal%2A>, <xref:System.Windows.FontWeights.Regular%2A>, <xref:System.Windows.FontWeights.Thin%2A>lub <xref:System.Windows.FontWeights.UltraLight%2A>: <xref:System.Drawing.FontStyle.Bold> jest wyłączone.|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|Zestaw właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest tłumaczony na odpowiadającą <xref:System.Drawing.Font>. Po zmianie jednej z tych właściwości zostanie utworzony nowy <xref:System.Drawing.Font>. Kontrolka hostowana [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zmienia rozmiar na podstawie rozmiaru czcionki.<br /><br /> Rozmiar czcionki w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest wyrażony jako jedna część 90 szósta cala, a w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jako jeden siedemdziesiątego sekund. Odpowiednia konwersja to:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] rozmiar czcionki = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozmiar czcionki * 72,0/96,0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|Mapowanie właściwości <xref:System.Windows.Controls.Control.Foreground%2A> jest wykonywane przy użyciu następujących reguł:<br /><br /> -Jeśli <xref:System.Windows.Controls.Control.Foreground%2A> jest <xref:System.Windows.Media.SolidColorBrush>, użyj <xref:System.Windows.Media.SolidColorBrush.Color%2A> do <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Jeśli <xref:System.Windows.Controls.Control.Foreground%2A> jest <xref:System.Windows.Media.GradientBrush>, Użyj koloru <xref:System.Windows.Media.GradientStop> z najniższą wartością przesunięcia dla <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Dla dowolnego innego typu <xref:System.Windows.Media.Brush> pozostaw <xref:System.Windows.Forms.Control.ForeColor%2A> bez zmian. Oznacza to, że wartość domyślna jest używana.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Gdy <xref:System.Windows.UIElement.IsEnabled%2A> jest ustawiona, element <xref:System.Windows.Forms.Integration.WindowsFormsHost> ustawia właściwość <xref:System.Windows.Forms.Control.Enabled%2A> dla hostowanej kontrolki.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Wszystkie cztery wartości właściwości <xref:System.Windows.Forms.Control.Padding%2A> w formancie hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mają tę samą wartość <xref:System.Windows.Thickness>.<br /><br /> -Wartości większe niż <xref:System.Int32.MaxValue> są ustawione na <xref:System.Int32.MaxValue>.<br />-Wartości mniejsze niż <xref:System.Int32.MinValue> są ustawione na <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible> mapy <xref:System.Windows.Forms.Control.Visible%2A> = `true`. Formant hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest widoczny. Jawne ustawienie właściwości <xref:System.Windows.Forms.Control.Visible%2A> w hostowanej kontroli na `false` nie jest zalecane.<br />-   <xref:System.Windows.Visibility.Collapsed> mapy do <xref:System.Windows.Forms.Control.Visible%2A> = `true` lub `false`. Kontrolka hostowana [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nie jest rysowana, a jej obszar jest zwinięty.<br />-   <xref:System.Windows.Visibility.Hidden>: formant hostowane [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zajmuje miejsce w układzie, ale nie jest widoczny. W tym przypadku Właściwość <xref:System.Windows.Forms.Control.Visible%2A> jest ustawiona na `true`. Jawne ustawienie właściwości <xref:System.Windows.Forms.Control.Visible%2A> w hostowanej kontroli na `false` nie jest zalecane.|  
  
 Dołączone właściwości elementów kontenera są w pełni obsługiwane przez element <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
 Aby uzyskać więcej informacji, zobacz [Przewodnik: Mapowanie właściwości przy użyciu elementu WindowsFormsHost](walkthrough-mapping-properties-using-the-windowsformshost-element.md).  
  
## <a name="updates-to-parent-properties"></a>Aktualizacje właściwości nadrzędnych  
 Zmiany w większości właściwości nadrzędnych powodują powiadomienia do hostowanego formantu podrzędnego. Poniższa lista zawiera opis właściwości, które nie powodują powiadomienia w przypadku zmiany ich wartości.  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 Na przykład jeśli zmienisz wartość właściwości <xref:System.Windows.Controls.Control.Background%2A> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>, właściwość <xref:System.Windows.Forms.Control.BackColor%2A> hostowanej kontroli nie zostanie zmieniona.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>Mapowanie właściwości z kontrolką ElementHost  
 Następujące właściwości zapewniają wbudowane powiadomienie o zmianie. Nie wywołuj metody <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> podczas mapowania tych właściwości:  
  
- AutoSize  
  
- BackColor  
  
- BackgroundImage  
  
- BackgroundImageLayout  
  
- BindingContext  
  
- Właściwości CausesValidation  
  
- ContextMenu  
  
- ContextMenuStrip  
  
- Biera  
  
- Zadokuj  
  
- Aktywny  
  
- Font  
  
- ForeColor  
  
- Lokalizacja  
  
- Praw  
  
- Uzupełni  
  
- Nadrzędny  
  
- Region  
  
- RightToLeft  
  
- Rozmiar  
  
- TabIndex  
  
- TabStop  
  
- Tekst  
  
- Widoczny  
  
 Formant <xref:System.Windows.Forms.Integration.ElementHost> przetłumaczy domyślne właściwości [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] na ich odpowiedniki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] za pomocą poniższej tabeli translacji.  
  
 Aby uzyskać więcej informacji, zobacz [Przewodnik: Mapowanie właściwości przy użyciu formantu ElementHost](walkthrough-mapping-properties-using-the-elementhost-control.md).  
  
|Hosting Windows Forms|Windows Presentation Foundation|Zachowanie międzyoperacyjności|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) dla elementu hostowanego|Ustawienie tej właściwości wymusza odświeżenie przy użyciu <xref:System.Windows.Media.ImageBrush>. Jeśli właściwość <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> jest ustawiona na `false` (wartość domyślna), ta <xref:System.Windows.Media.ImageBrush> jest oparta na wyglądzie kontrolki <xref:System.Windows.Forms.Integration.ElementHost>, w tym jej <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> właściwości i dowolnych dołączanych programów do malowania.<br /><br /> Jeśli właściwość <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> jest ustawiona na `true`, <xref:System.Windows.Media.ImageBrush> jest oparta na wyglądzie elementu nadrzędnego kontrolki <xref:System.Windows.Forms.Integration.ElementHost>, w tym <xref:System.Windows.Forms.Control.BackColor%2A>elementu nadrzędnego, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> właściwości i dowolnych dołączonych programów do obsługi farb.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) dla elementu hostowanego|Ustawienie tej właściwości powoduje zachowanie tego samego zachowania opisanego dla mapowania <xref:System.Windows.Forms.Control.BackColor%2A>.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) dla elementu hostowanego|Ustawienie tej właściwości powoduje zachowanie tego samego zachowania opisanego dla mapowania <xref:System.Windows.Forms.Control.BackColor%2A>.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|Kursor standardowy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest tłumaczony na odpowiadającą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standardowego kursora. Jeśli [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nie jest kursorem standardowym, przypisywana jest wartość domyślna.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Po ustawieniu <xref:System.Windows.Forms.Control.Enabled%2A>, formant <xref:System.Windows.Forms.Integration.ElementHost> ustawia właściwość <xref:System.Windows.UIElement.IsEnabled%2A> dla elementu hostowanego.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|Wartość <xref:System.Windows.Forms.Control.Font%2A> jest tłumaczona na odpowiedni zestaw właściwości czcionki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A> w hostowanym elemencie|Jeśli <xref:System.Drawing.Font.Bold%2A> jest `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> jest ustawiony na <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Jeśli <xref:System.Drawing.Font.Bold%2A> jest `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> jest ustawiony na <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A> w hostowanym elemencie|Jeśli <xref:System.Drawing.Font.Italic%2A> jest `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> jest ustawiony na <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Jeśli <xref:System.Drawing.Font.Italic%2A> jest `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> jest ustawiony na <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations> w hostowanym elemencie|Ma zastosowanie tylko w przypadku hostowania formantu <xref:System.Windows.Controls.TextBlock>.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations> w hostowanym elemencie|Ma zastosowanie tylko w przypadku hostowania formantu <xref:System.Windows.Controls.TextBlock>.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No> mapowanie do <xref:System.Windows.FlowDirection.LeftToRight>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes> mapowanie do <xref:System.Windows.FlowDirection.RightToLeft>.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|Formant <xref:System.Windows.Forms.Integration.ElementHost> ustawia właściwość <xref:System.Windows.UIElement.Visibility%2A> dla elementu hostowanego za pomocą następujących reguł:<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true` mapy <xref:System.Windows.Visibility.Visible>.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false` mapy <xref:System.Windows.Visibility.Hidden>.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
- [Współdziałanie WPF i Windows Forms](wpf-and-windows-forms-interoperation.md)
- [Przewodnik: mapowanie właściwości z użyciem elementu WindowsFormsHost](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [Przewodnik: mapowanie właściwości z użyciem kontrolki ElementHost](walkthrough-mapping-properties-using-the-elementhost-control.md)
