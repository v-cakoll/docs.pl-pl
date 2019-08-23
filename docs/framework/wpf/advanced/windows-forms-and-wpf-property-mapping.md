---
title: Mapowanie właściwości Windows Forms i WPF
ms.date: 03/30/2017
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
ms.openlocfilehash: ae4a97bc96a4f9e93942b4995f488c427fda3134
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917502"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Mapowanie właściwości Windows Forms i WPF
Technologie i mają dwa podobne, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ale różne modele właściwości. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] *Mapowanie właściwości* obsługuje międzyoperacyjność między obiema architekturami i zapewnia następujące możliwości:  
  
- Ułatwia mapowanie istotnych zmian właściwości w środowisku hosta do hostowanej kontrolki lub elementu.  
  
- Zapewnia domyślną obsługę mapowania najczęściej używanych właściwości.  
  
- Umożliwia łatwe usuwanie, zastępowanie lub Rozszerzanie właściwości domyślnych.  
  
- Zapewnia, że zmiany wartości właściwości na hoście są automatycznie wykrywane i tłumaczone na hostowaną kontrolkę lub element.  
  
> [!NOTE]
> Zdarzenia zmiany właściwości nie są propagowane w górę kontrolki hostingu lub hierarchii elementów. Tłumaczenie właściwości nie jest wykonywane, jeśli lokalna wartość właściwości nie zmienia się z powodu ustawienia bezpośredniego, stylów, dziedziczenia, powiązania danych lub innych mechanizmów, które zmieniają wartość właściwości.  
  
 Użyj właściwości w <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemenciei<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> właściwości formantu,abyuzyskaćdostępdomapowaniawłaściwości.<xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>Mapowanie właściwości z elementem WindowsFormsHost  
 Element tłumaczy właściwości domyślne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na ich [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] odpowiedniki przy użyciu następującej tabeli translacji. <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
  
|Hosting Windows Presentation Foundation|Windows Forms|Zachowanie międzyoperacyjności|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|Element ustawia właściwość kontrolki hostowanej i <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości kontrolki hostowanej. <xref:System.Windows.Forms.Control.BackColor%2A> <xref:System.Windows.Forms.Integration.WindowsFormsHost> Mapowanie jest wykonywane przy użyciu następujących reguł:<br /><br /> -Jeśli <xref:System.Windows.Controls.Control.Background%2A> jest pełny kolor, jest konwertowany i używany do <xref:System.Windows.Forms.Control.BackColor%2A> ustawiania właściwości kontrolki hostowanej. Właściwość nie jest ustawiona w formancie hostowanym, ponieważ hostowana kontrolka może dziedziczyć wartość <xref:System.Windows.Forms.Control.BackColor%2A> właściwości. <xref:System.Windows.Forms.Control.BackColor%2A> **Uwaga:**  Formant hostowany nie obsługuje przezroczystości. Wszystkie kolory przypisane do <xref:System.Windows.Forms.Control.BackColor%2A> muszą być całkowicie nieprzezroczyste, z wartością alfa równą 0xFF. <br /><br /> -Jeśli <xref:System.Windows.Controls.Control.Background%2A> nie jest pełny kolor <xref:System.Windows.Forms.Integration.WindowsFormsHost> , formant <xref:System.Windows.Controls.Control.Background%2A> tworzy mapę bitową na podstawie właściwości. Formant przypisuje tę mapę bitową <xref:System.Windows.Forms.Control.BackgroundImage%2A> do właściwości kontrolki hostowanej. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Zapewnia to efekt podobny do przejrzystości. **Uwaga:**  Można zastąpić to zachowanie lub usunąć <xref:System.Windows.Controls.Control.Background%2A> mapowanie właściwości.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Jeśli domyślne mapowanie nie zostało ponownie przypisane, <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrola przechodzi przez jego hierarchię nadrzędną do momentu znalezienia elementu nadrzędnego <xref:System.Windows.FrameworkElement.Cursor%2A> z zestawem właściwości. Ta wartość jest tłumaczona na najbliższy odpowiedni [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kursor.<br /><br /> Jeśli mapowanie domyślne dla <xref:System.Windows.FrameworkElement.ForceCursor%2A> właściwości nie zostało ponownie przypisane, przechodzenie zostanie zatrzymane na pierwszym elemencie nadrzędnym z <xref:System.Windows.FrameworkElement.ForceCursor%2A> ustawioną na. `true`|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight>mapuje <xref:System.Windows.Forms.RightToLeft.No>do.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft>mapuje <xref:System.Windows.Forms.RightToLeft.Yes>do.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit>nie jest zamapowany.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType>mapuje <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>do.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A>na hostowanej kontrolce<xref:System.Drawing.Font?displayProperty=nameWithType>|Zestaw [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości jest tłumaczony na odpowiadający <xref:System.Drawing.Font>. Po zmianie jednej z tych właściwości zostanie utworzony nowy <xref:System.Drawing.Font> . Dla <xref:System.Windows.FontStyles.Normal%2A> :<xref:System.Drawing.FontStyle.Italic> jest wyłączone. Dla <xref:System.Windows.FontStyles.Italic%2A> lub <xref:System.Windows.FontStyles.Oblique%2A> :<xref:System.Drawing.FontStyle.Italic> jest włączony.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A>na hostowanej kontrolce<xref:System.Drawing.Font?displayProperty=nameWithType>|Zestaw [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości jest tłumaczony na odpowiadający <xref:System.Drawing.Font>. Po zmianie jednej z tych właściwości zostanie utworzony nowy <xref:System.Drawing.Font> . Dla <xref:System.Windows.FontWeights.Black%2A> ,<xref:System.Windows.FontWeights.Bold%2A>, ,<xref:System.Windows.FontWeights.Heavy%2A> ,,<xref:System.Drawing.FontStyle.Bold> , lub :jestwłączony.<xref:System.Windows.FontWeights.UltraBold%2A> <xref:System.Windows.FontWeights.ExtraBold%2A> <xref:System.Windows.FontWeights.DemiBold%2A> <xref:System.Windows.FontWeights.Medium%2A> <xref:System.Windows.FontWeights.SemiBold%2A> Dla <xref:System.Windows.FontWeights.ExtraLight%2A> ,<xref:System.Windows.FontWeights.Regular%2A> ,,<xref:System.Drawing.FontStyle.Bold> , lub :jestwyłączone.<xref:System.Windows.FontWeights.UltraLight%2A> <xref:System.Windows.FontWeights.Light%2A> <xref:System.Windows.FontWeights.Normal%2A> <xref:System.Windows.FontWeights.Thin%2A>|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|Zestaw [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości jest tłumaczony na odpowiadający <xref:System.Drawing.Font>. Po zmianie jednej z tych właściwości zostanie utworzony nowy <xref:System.Drawing.Font> . Formant hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zmienia rozmiar na podstawie rozmiaru czcionki.<br /><br /> Rozmiar czcionki w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programie jest wyrażony jako jedna część 90 szósta cala i w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jednym siedemdziesiątego sekundy. Odpowiednia konwersja to:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]rozmiar czcionki = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozmiar czcionki * 72,0/96,0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|Mapowanie <xref:System.Windows.Controls.Control.Foreground%2A> właściwości jest wykonywane przy użyciu następujących reguł:<br /><br /> -Jeśli <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Media.SolidColorBrush.Color%2A> jest, użyj dla<xref:System.Windows.Forms.Control.ForeColor%2A>. <xref:System.Windows.Media.SolidColorBrush><br />-Jeśli <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Forms.Control.ForeColor%2A>jest, Użyj koloru zwartościąonajniższejwartościprzesunięciadla.<xref:System.Windows.Media.GradientStop> <xref:System.Windows.Media.GradientBrush><br />— Dla dowolnego innego <xref:System.Windows.Media.Brush> typu pozostaw <xref:System.Windows.Forms.Control.ForeColor%2A> bez zmian. Oznacza to, że wartość domyślna jest używana.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Gdy <xref:System.Windows.UIElement.IsEnabled%2A> jest ustawiona, <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ustawia <xref:System.Windows.Forms.Control.Enabled%2A> właściwość w formancie hostowanym.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Wszystkie cztery wartości <xref:System.Windows.Forms.Control.Padding%2A> właściwości w formancie hostowanym [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mają ustawioną taką samą <xref:System.Windows.Thickness> wartość.<br /><br /> -Wartości większe niż <xref:System.Int32.MaxValue> są ustawione na <xref:System.Int32.MaxValue>.<br />-Wartości mniejsze niż <xref:System.Int32.MinValue> są ustawione na <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible>mapuje <xref:System.Windows.Forms.Control.Visible%2A>do  =  .`true` Formant hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest widoczny. Jawne ustawienie <xref:System.Windows.Forms.Control.Visible%2A> właściwości kontrolki hostowanej na `false` nie jest zalecane.<br />-   <xref:System.Windows.Visibility.Collapsed>mapuje <xref:System.Windows.Forms.Control.Visible%2A>  =  do lub`true` . `false` Formant hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nie jest rysowany i jego obszar jest zwinięty.<br />-   <xref:System.Windows.Visibility.Hidden>: Hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant zajmuje miejsce w układzie, ale nie jest widoczny. W tym przypadku <xref:System.Windows.Forms.Control.Visible%2A> właściwość jest ustawiona na `true`. Jawne ustawienie <xref:System.Windows.Forms.Control.Visible%2A> właściwości kontrolki hostowanej na `false` nie jest zalecane.|  
  
 Dołączone właściwości elementów kontenera są w pełni obsługiwane przez <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.  
  
 Aby uzyskać więcej informacji, [zobacz Przewodnik: Mapowanie właściwości przy użyciu elementu](walkthrough-mapping-properties-using-the-windowsformshost-element.md)WindowsFormsHost.  
  
## <a name="updates-to-parent-properties"></a>Aktualizacje właściwości nadrzędnych  
 Zmiany w większości właściwości nadrzędnych powodują powiadomienia do hostowanego formantu podrzędnego. Poniższa lista zawiera opis właściwości, które nie powodują powiadomienia w przypadku zmiany ich wartości.  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 Na przykład jeśli zmienisz wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, właściwość kontrolki hostowanej nie zostanie <xref:System.Windows.Forms.Control.BackColor%2A> zmieniona.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>Mapowanie właściwości z kontrolką ElementHost  
 Następujące właściwości zapewniają wbudowane powiadomienie o zmianie. Nie wywołuj <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> metody podczas mapowania tych właściwości:  
  
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
  
- Enabled  
  
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
  
- Widoczne  
  
 Kontrolka tłumaczy właściwości [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] domyślne na ich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odpowiedniki przy użyciu poniższej tabeli translacji. <xref:System.Windows.Forms.Integration.ElementHost>  
  
 Aby uzyskać więcej informacji, [zobacz Przewodnik: Mapowanie właściwości przy użyciu formantu](walkthrough-mapping-properties-using-the-elementhost-control.md)ElementHost.  
  
|Hosting Windows Forms|Windows Presentation Foundation|Zachowanie międzyoperacyjności|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) dla elementu hostowanego|Ustawienie tej właściwości wymusza odświeżenie przy użyciu <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Forms.Control.BackColor%2A> <xref:System.Windows.Media.ImageBrush> `false` <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> <xref:System.Windows.Forms.Control.BackgroundImage%2A>Jeśli właściwość jest ustawiona na (wartość domyślna), jest to zależne od wyglądu <xref:System.Windows.Forms.Integration.ElementHost> kontrolki, w tym jej właściwości i dowolnych dołączonych farb <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> programy obsługi.<br /><br /> <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Forms.Control.BackgroundImage%2A> <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> Jeśli właściwość jest ustawiona na `true`, jest oparta na wyglądzie elementu nadrzędnego kontrolki, w tym elementu nadrzędnego <xref:System.Windows.Forms.Control.BackColor%2A>, właściwości i dowolnych dołączonych farb <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> programy obsługi.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) dla elementu hostowanego|Ustawienie tej właściwości powoduje zachowanie tego samego zachowania opisanego dla <xref:System.Windows.Forms.Control.BackColor%2A> mapowania.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) dla elementu hostowanego|Ustawienie tej właściwości powoduje zachowanie tego samego zachowania opisanego dla <xref:System.Windows.Forms.Control.BackColor%2A> mapowania.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|Kursor standardowy jest tłumaczony na odpowiedni [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kursor standardowy. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Jeśli nie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jest kursorem standardowym, przypisywana jest wartość domyślna.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Gdy <xref:System.Windows.Forms.Control.Enabled%2A> jest ustawiona <xref:System.Windows.Forms.Integration.ElementHost> , formant ustawia <xref:System.Windows.UIElement.IsEnabled%2A> właściwość dla hostowanego elementu.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|Wartość jest tłumaczona na odpowiedni [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestaw właściwości czcionki. <xref:System.Windows.Forms.Control.Font%2A>|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A>w elemencie hostowanym|Jeśli <xref:System.Drawing.Font.Bold%2A> jest `true`, jest<xref:System.Windows.Controls.Control.FontWeight%2A> ustawiona na <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Jeśli <xref:System.Drawing.Font.Bold%2A> jest `false`, jest<xref:System.Windows.Controls.Control.FontWeight%2A> ustawiona na <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A>w elemencie hostowanym|Jeśli <xref:System.Drawing.Font.Italic%2A> jest `true`, jest<xref:System.Windows.Controls.Control.FontStyle%2A> ustawiona na <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Jeśli <xref:System.Drawing.Font.Italic%2A> jest `false`, jest<xref:System.Windows.Controls.Control.FontStyle%2A> ustawiona na <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations>w elemencie hostowanym|Ma zastosowanie tylko w przypadku <xref:System.Windows.Controls.TextBlock> hostowania formantu.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations>w elemencie hostowanym|Ma zastosowanie tylko w przypadku <xref:System.Windows.Controls.TextBlock> hostowania formantu.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No>mapuje <xref:System.Windows.FlowDirection.LeftToRight>do.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes>mapuje <xref:System.Windows.FlowDirection.RightToLeft>do.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost> Formant<xref:System.Windows.UIElement.Visibility%2A> ustawia właściwość dla hostowanego elementu przy użyciu następujących reguł:<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true`mapuje <xref:System.Windows.Visibility.Visible>do.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false`mapuje <xref:System.Windows.Visibility.Hidden>do.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
- [Współdziałanie WPF i Windows Forms](wpf-and-windows-forms-interoperation.md)
- [Przewodnik: Mapowanie właściwości przy użyciu elementu WindowsFormsHost](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [Przewodnik: Mapowanie właściwości przy użyciu kontrolki ElementHost](walkthrough-mapping-properties-using-the-elementhost-control.md)
