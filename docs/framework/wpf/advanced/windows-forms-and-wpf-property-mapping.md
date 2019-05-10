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
ms.openlocfilehash: 67d1d1f2cb712c0c8ffec3972fd83bc46a66d65c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650799"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Mapowanie właściwości Windows Forms i WPF
[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] technologie mają dwa modele inną właściwość. *Mapowanie właściwości* obsługuje współdziałanie między dwoma architekturami i zapewnia następujące możliwości:  
  
- Ułatwia Mapowanie właściwości istotne zmiany w środowisku hosta do obsługiwanego formantu lub elementu.  
  
- Udostępnia domyślne Obsługa powszechnie mapowania najczęściej używanych właściwości.  
  
- Umożliwia łatwe usuwanie, zastępowanie i rozszerzanie właściwości domyślnych.  
  
- Zapewnia automatycznego wykrywania i przekonwertowana na hostowanej formantu lub elementu zmiany wartości właściwości na hoście.  
  
> [!NOTE]
>  Zdarzenia zmiany właściwości nie są propagowane w górę kontrolka hostująca lub hierarchia elementów. Nie jest wykonywana Translacja właściwość, jeśli lokalna wartość właściwości nie zmienia się ze względu na ustawienie bezpośredniego, style, dziedziczenie, powiązania danych lub innych mechanizmów, które zmieniają wartości właściwości.  
  
 Użyj <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> właściwość <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu i <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> właściwość <xref:System.Windows.Forms.Integration.ElementHost> sterowania mapowania właściwości.  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>Mapowanie właściwości z elementu WindowsFormsHost  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element tłumaczy domyślne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości w celu ich [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] odpowiedniki przy użyciu poniższej tabeli translacji.  
  
|Hosting Windows Presentation Foundation|Windows Forms|Zachowanie współdziałanie|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Integration.WindowsFormsHost> Ustawia element <xref:System.Windows.Forms.Control.BackColor%2A> właściwość hostowanej formantu i <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości hostowanego formantu. Mapowanie odbywa się za pomocą następujących reguł:<br /><br /> -Jeśli <xref:System.Windows.Controls.Control.Background%2A> jest pełny kolor jest konwertowany i używane do ustawiania <xref:System.Windows.Forms.Control.BackColor%2A> właściwość hostowanej formantu. <xref:System.Windows.Forms.Control.BackColor%2A> Właściwość nie jest ustawiona na formancie hostowanej, ponieważ obsługiwanego formantu może dziedziczyć wartość <xref:System.Windows.Forms.Control.BackColor%2A> właściwości. **Uwaga:**  Obsługiwanego formantu nie obsługuje przezroczystość. Żadnych przypisanych im kolorów <xref:System.Windows.Forms.Control.BackColor%2A> musi być całkowicie nieprzezroczyste, wartość alfa 0xFF. <br /><br /> -Jeśli <xref:System.Windows.Controls.Control.Background%2A> nie jest pełny kolor <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli tworzy mapę bitową z <xref:System.Windows.Controls.Control.Background%2A> właściwości. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Kontroli przypisuje tę mapę bitową do <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości hostowanego formantu. Dzięki temu efekt, co jest podobne do przezroczystości. **Uwaga:**  Zachowanie to można zastąpić, lub usunąć <xref:System.Windows.Controls.Control.Background%2A> mapowania właściwości.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Jeśli nie zostało ponownie przypisane do domyślnego mapowania, <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli przesyłane za pośrednictwem swojej hierarchii nadrzędny do momentu znalezienia elementu nadrzędnego z jego <xref:System.Windows.FrameworkElement.Cursor%2A> zestawu właściwości. Ta wartość jest tłumaczony w najbliższej odpowiadających im [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kursora.<br /><br /> Jeśli do domyślnego mapowania dla <xref:System.Windows.FrameworkElement.ForceCursor%2A> właściwości nie zostało ponownie przypisane, zatrzymuje się podczas przechodzenia na pierwszym elemencie nadrzędnym z <xref:System.Windows.FrameworkElement.ForceCursor%2A> równa `true`.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight> mapuje <xref:System.Windows.Forms.RightToLeft.No>.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft> mapuje <xref:System.Windows.Forms.RightToLeft.Yes>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit> nie jest zamapowany.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> mapuje <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A> na kontrolce hostowanej <xref:System.Drawing.Font?displayProperty=nameWithType>|Zbiór [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości są tłumaczone na odpowiednie <xref:System.Drawing.Font>. Jedną z tych właściwości zmianie nową <xref:System.Drawing.Font> zostanie utworzony. Aby uzyskać <xref:System.Windows.FontStyles.Normal%2A>: <xref:System.Drawing.FontStyle.Italic> jest wyłączona. Aby uzyskać <xref:System.Windows.FontStyles.Italic%2A> lub <xref:System.Windows.FontStyles.Oblique%2A>: <xref:System.Drawing.FontStyle.Italic> jest włączona.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A> na kontrolce hostowanej <xref:System.Drawing.Font?displayProperty=nameWithType>|Zbiór [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości są tłumaczone na odpowiednie <xref:System.Drawing.Font>. Jedną z tych właściwości zmianie nową <xref:System.Drawing.Font> zostanie utworzony. Aby uzyskać <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, <xref:System.Windows.FontWeights.DemiBold%2A>, <xref:System.Windows.FontWeights.ExtraBold%2A>, <xref:System.Windows.FontWeights.Heavy%2A>, <xref:System.Windows.FontWeights.Medium%2A>, <xref:System.Windows.FontWeights.SemiBold%2A>, lub <xref:System.Windows.FontWeights.UltraBold%2A>: <xref:System.Drawing.FontStyle.Bold> jest włączona. Aby uzyskać <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, <xref:System.Windows.FontWeights.Normal%2A>, <xref:System.Windows.FontWeights.Regular%2A>, <xref:System.Windows.FontWeights.Thin%2A>, lub <xref:System.Windows.FontWeights.UltraLight%2A>: <xref:System.Drawing.FontStyle.Bold> jest wyłączona.|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|Zbiór [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości są tłumaczone na odpowiednie <xref:System.Drawing.Font>. Jedną z tych właściwości zmianie nową <xref:System.Drawing.Font> zostanie utworzony. Hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolować zmiany rozmiaru w oparciu o rozmiar czcionki.<br /><br /> Rozmiar czcionki w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest wyrażona jako jeden 90 szósta cala i w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jako jedna sekunda siedemdziesiątego cala. Odpowiedniej konwersji jest:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] rozmiar czcionki = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozmiar czcionki * 72.0 / 96.0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Foreground%2A> Mapowanie właściwości odbywa się za pomocą następujących reguł:<br /><br /> -Jeśli <xref:System.Windows.Controls.Control.Foreground%2A> jest <xref:System.Windows.Media.SolidColorBrush>, użyj <xref:System.Windows.Media.SolidColorBrush.Color%2A> dla <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Jeśli <xref:System.Windows.Controls.Control.Foreground%2A> jest <xref:System.Windows.Media.GradientBrush>, użyj kolor <xref:System.Windows.Media.GradientStop> o najniższej wartości przesunięcia <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />– W przypadku wszelkich innych <xref:System.Windows.Media.Brush> wpisz, pozostaw <xref:System.Windows.Forms.Control.ForeColor%2A> bez zmian. Oznacza to, że używana jest wartość domyślna.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Gdy <xref:System.Windows.UIElement.IsEnabled%2A> jest ustawiona, <xref:System.Windows.Forms.Integration.WindowsFormsHost> ustawia element <xref:System.Windows.Forms.Control.Enabled%2A> właściwość obsługiwanego formantu.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Wszystkie cztery wartości właściwości <xref:System.Windows.Forms.Control.Padding%2A> właściwość hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki są ustawione na <xref:System.Windows.Thickness> wartość.<br /><br /> — Większa od wartości <xref:System.Int32.MaxValue> są ustawione na <xref:System.Int32.MaxValue>.<br />-Wartości mniejszej niż <xref:System.Int32.MinValue> są ustawione na <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible> mapuje <xref:System.Windows.Forms.Control.Visible%2A>  =  `true`. Hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolka jest widoczna. Jawne ustawianie <xref:System.Windows.Forms.Control.Visible%2A> właściwość obsługiwany formant `false` nie jest zalecane.<br />-   <xref:System.Windows.Visibility.Collapsed> mapuje <xref:System.Windows.Forms.Control.Visible%2A>  =  `true` lub `false`. Hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki nie jest narysowany i jego obszar jest zwinięta.<br />-   <xref:System.Windows.Visibility.Hidden> : Hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrola zajmuje miejsce w układzie, ale nie jest widoczny. W tym przypadku <xref:System.Windows.Forms.Control.Visible%2A> właściwość jest ustawiona na `true`. Jawne ustawianie <xref:System.Windows.Forms.Control.Visible%2A> właściwość obsługiwany formant `false` nie jest zalecane.|  
  
 Dołączone właściwości elementów kontenera są w pełni obsługiwane przez <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.  
  
 Aby uzyskać więcej informacji, zobacz [instruktażu: Mapowanie właściwości z użyciem elementu WindowsFormsHost](walkthrough-mapping-properties-using-the-windowsformshost-element.md).  
  
## <a name="updates-to-parent-properties"></a>Aktualizacje właściwości nadrzędnej  
 Zmiany właściwości nadrzędnej większość spowodować powiadomień do kontroli podrzędny obiekt obsługiwany. Poniższa lista zawiera opis właściwości, które nie powodują powiadomienia, gdy zmienią się ich wartości.  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 Na przykład, jeśli zmienisz wartość <xref:System.Windows.Controls.Control.Background%2A> właściwość <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Control.BackColor%2A> nie zmienia własności obsługiwanego formantu.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>Mapowanie właściwości z formantu ElementHost  
 Następujące właściwości zapewniają powiadomienia o zmianie wbudowanych. Nie wywołuj <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> metody, gdy mapowanie tych właściwości:  
  
- AutoSize  
  
- BackColor  
  
- BackgroundImage  
  
- BackgroundImageLayout  
  
- BindingContext  
  
- Właściwości CausesValidation  
  
- ContextMenu  
  
- ContextMenuStrip  
  
- Kursor  
  
- Dock  
  
- Enabled  
  
- Czcionka  
  
- ForeColor  
  
- Lokalizacja  
  
- Margines  
  
- Dopełnienie  
  
- Nadrzędny  
  
- Region  
  
- RightToLeft  
  
- Rozmiar  
  
- TabIndex  
  
- TabStop  
  
- Tekst  
  
- Widoczne  
  
 <xref:System.Windows.Forms.Integration.ElementHost> Kontroli tłumaczy domyślne [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] właściwości w celu ich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odpowiedniki przy użyciu poniższej tabeli translacji.  
  
 Aby uzyskać więcej informacji, zobacz [instruktażu: Mapowanie właściwości z użyciem formantu ElementHost](walkthrough-mapping-properties-using-the-elementhost-control.md).  
  
|Formularze Windows hostingu|Windows Presentation Foundation|Zachowanie współdziałanie|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) w elemencie hostowanej|Ustawienie tej właściwości wymusza repaint z <xref:System.Windows.Media.ImageBrush>. Jeśli <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> właściwość jest ustawiona na `false` (wartość domyślna), to <xref:System.Windows.Media.ImageBrush> opiera się na wygląd <xref:System.Windows.Forms.Integration.ElementHost> kontrolować, łącznie z jej <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> właściwości i wszelkich dołączonych malowania procedury obsługi.<br /><br /> Jeśli <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> właściwość jest ustawiona na `true`, <xref:System.Windows.Media.ImageBrush> opiera się na wygląd <xref:System.Windows.Forms.Integration.ElementHost> kontrolki nadrzędnej, łącznie z elementu nadrzędnego <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> właściwości i wszelkich dołączonych malowania procedury obsługi.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) w elemencie hostowanej|Ustawienie tej właściwości powoduje, że takie samo zachowanie, które są opisane dla <xref:System.Windows.Forms.Control.BackColor%2A> mapowania.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) w elemencie hostowanej|Ustawienie tej właściwości powoduje, że takie samo zachowanie, które są opisane dla <xref:System.Windows.Forms.Control.BackColor%2A> mapowania.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Standardowa kursora jest tłumaczone na odpowiednie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standardowa kursora. Jeśli [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nie jest standardowy kursora, jest przypisywana wartość domyślna.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Gdy <xref:System.Windows.Forms.Control.Enabled%2A> jest ustawiona, <xref:System.Windows.Forms.Integration.ElementHost> kontrolować zestawy <xref:System.Windows.UIElement.IsEnabled%2A> właściwości hostowanego elementu.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A> Wartość jest przekształcana na odpowiedni zestaw [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości czcionki.|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A> w elemencie hostowanej|Jeśli <xref:System.Drawing.Font.Bold%2A> jest `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> ustawiono <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Jeśli <xref:System.Drawing.Font.Bold%2A> jest `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> ustawiono <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A> w elemencie hostowanej|Jeśli <xref:System.Drawing.Font.Italic%2A> jest `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> ustawiono <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Jeśli <xref:System.Drawing.Font.Italic%2A> jest `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> ustawiono <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations> w elemencie hostowanej|Ma zastosowanie tylko wtedy, gdy hostingu <xref:System.Windows.Controls.TextBlock> kontroli.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations> w elemencie hostowanej|Ma zastosowanie tylko wtedy, gdy hostingu <xref:System.Windows.Controls.TextBlock> kontroli.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No> mapuje <xref:System.Windows.FlowDirection.LeftToRight>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes> mapuje <xref:System.Windows.FlowDirection.RightToLeft>.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost> Kontrolować zestawy <xref:System.Windows.UIElement.Visibility%2A> właściwości hostowanego elementu za pomocą następujących reguł:<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true` mapuje <xref:System.Windows.Visibility.Visible>.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false` mapuje <xref:System.Windows.Visibility.Hidden>.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
- [Współdziałanie WPF i Windows Forms](wpf-and-windows-forms-interoperation.md)
- [Przewodnik: Mapowanie właściwości z użyciem elementu WindowsFormsHost](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [Przewodnik: Mapowanie właściwości z użyciem formantu ElementHost](walkthrough-mapping-properties-using-the-elementhost-control.md)
