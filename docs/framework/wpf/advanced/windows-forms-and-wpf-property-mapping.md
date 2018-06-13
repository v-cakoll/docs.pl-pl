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
ms.openlocfilehash: f2177c65a8b1a1d5ad2f5bad67591e6d98087539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549545"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Mapowanie właściwości Windows Forms i WPF
[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] technologii ma dwa modele inną właściwość. *Mapowanie właściwości* obsługuje współdziałanie między dwoma architektury i zapewnia następujące możliwości:  
  
-   Ułatwia Mapowanie właściwości istotne zmiany w środowisku hosta do formantu hostowanej lub elementu.  
  
-   Zapewnia możliwość domyślna Obsługa mapowania najbardziej powszechnie używane właściwości.  
  
-   Umożliwia łatwe usuwanie, zastępowanie lub rozszerzanie właściwości domyślnych.  
  
-   Zapewnia automatycznie wykryte i przetłumaczone do formantu hostowanej lub element wartość właściwości zostanie zmieniona na hoście.  
  
> [!NOTE]
>  Zdarzenia zmiany właściwości nie są propagowane w górę kontrolki hostingu lub hierarchia elementów. Tłumaczenie właściwości nie jest wykonywane, jeśli lokalne wartość właściwości nie zmienia się z powodu bezpośrednie ustawienie, style, dziedziczenia, powiązania danych lub innych mechanizmów, które spowodują zmianę wartości właściwości.  
  
 Użyj <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> właściwość <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu i <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> właściwość <xref:System.Windows.Forms.Integration.ElementHost> sterowania mapowania właściwości.  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>Mapowanie właściwości z elementem WindowsFormsHost  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Domyślne wykonuje translację elementu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości, aby ich [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] odpowiedniki przy użyciu poniższej tabeli translacji.  
  
|Hosting Windows Presentation Foundation|Windows Forms|Zachowanie współdziałanie|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Integration.WindowsFormsHost> Ustawia element <xref:System.Windows.Forms.Control.BackColor%2A> właściwość hostowanej formantu i <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość hostowanej formantu. Mapowanie odbywa się za pomocą następujących reguł:<br /><br /> -Jeśli <xref:System.Windows.Controls.Control.Background%2A> jest pełny kolor jest konwertowany i służy do określania <xref:System.Windows.Forms.Control.BackColor%2A> właściwość hostowanej formantu. <xref:System.Windows.Forms.Control.BackColor%2A> Właściwość nie została ustawiona w formancie hostowanej, ponieważ obsługiwanego formantu może dziedziczyć wartość <xref:System.Windows.Forms.Control.BackColor%2A> właściwości. **Uwaga:** obsługiwanego formantu nie obsługuje przezroczystość. Dowolny kolor przypisane do <xref:System.Windows.Forms.Control.BackColor%2A> musi być całkowicie nieprzezroczyste, wartość alfa 0xFF. <br /><br /> -Jeśli <xref:System.Windows.Controls.Control.Background%2A> nie jest pełny kolor <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli tworzy mapę bitową z <xref:System.Windows.Controls.Control.Background%2A> właściwości. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Kontroli przypisuje tej mapy bitowej do <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość hostowanej formantu. Zapewnia to efekt, który jest podobny do przezroczystości. **Uwaga:** może zmienić to zachowanie lub usunąć <xref:System.Windows.Controls.Control.Background%2A> mapowania właściwości.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Jeśli nie zostało ponownie przypisane domyślne mapowanie, <xref:System.Windows.Forms.Integration.WindowsFormsHost> sterowania są przesyłane za pośrednictwem swojej hierarchii nadrzędnej aż do znalezienia elementu nadrzędnego z jego <xref:System.Windows.FrameworkElement.Cursor%2A> zestawu właściwości. Ta wartość jest translacja do najbliższego odpowiednich [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kursora.<br /><br /> Jeśli domyślne mapowanie dla <xref:System.Windows.FrameworkElement.ForceCursor%2A> nie przydzielono właściwości, podczas przechodzenia zatrzymuje się na pierwszym elemencie nadrzędnym z <xref:System.Windows.FrameworkElement.ForceCursor%2A> ustawioną `true`.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight> mapuje <xref:System.Windows.Forms.RightToLeft.No>.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft> mapuje <xref:System.Windows.Forms.RightToLeft.Yes>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit> nie jest zamapowany.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> mapuje <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A> w formancie hostowanej <xref:System.Drawing.Font?displayProperty=nameWithType>|Zbiór [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości jest przekształcana na odpowiadający jej <xref:System.Drawing.Font>. Gdy zmieni się jedna z tych właściwości, nowy <xref:System.Drawing.Font> jest tworzony. Aby uzyskać <xref:System.Windows.FontStyles.Normal%2A>: <xref:System.Drawing.FontStyle.Italic> jest wyłączona. Aby uzyskać <xref:System.Windows.FontStyles.Italic%2A> lub <xref:System.Windows.FontStyles.Oblique%2A>: <xref:System.Drawing.FontStyle.Italic> jest włączona.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A> w formancie hostowanej <xref:System.Drawing.Font?displayProperty=nameWithType>|Zbiór [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości jest przekształcana na odpowiadający jej <xref:System.Drawing.Font>. Gdy zmieni się jedna z tych właściwości, nowy <xref:System.Drawing.Font> jest tworzony. Aby uzyskać <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, <xref:System.Windows.FontWeights.DemiBold%2A>, <xref:System.Windows.FontWeights.ExtraBold%2A>, <xref:System.Windows.FontWeights.Heavy%2A>, <xref:System.Windows.FontWeights.Medium%2A>, <xref:System.Windows.FontWeights.SemiBold%2A>, lub <xref:System.Windows.FontWeights.UltraBold%2A>: <xref:System.Drawing.FontStyle.Bold> jest włączona. Aby uzyskać <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, <xref:System.Windows.FontWeights.Normal%2A>, <xref:System.Windows.FontWeights.Regular%2A>, <xref:System.Windows.FontWeights.Thin%2A>, lub <xref:System.Windows.FontWeights.UltraLight%2A>: <xref:System.Drawing.FontStyle.Bold> jest wyłączona.|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|Zbiór [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości jest przekształcana na odpowiadający jej <xref:System.Drawing.Font>. Gdy zmieni się jedna z tych właściwości, nowy <xref:System.Drawing.Font> jest tworzony. Hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolować zmienia rozmiar w oparciu o rozmiar czcionki.<br /><br /> Rozmiar czcionki w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest wyrażony jako jeden dziewięćdziesięciu szóstego cala i w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jako jednej sekundzie siedemdziesiątego cala. Konwersja odpowiedniego jest:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] rozmiar czcionki = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozmiar czcionki * 72.0 / 96.0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Foreground%2A> Mapowanie właściwości jest przeprowadzane za pomocą następujących reguł:<br /><br /> -Jeśli <xref:System.Windows.Controls.Control.Foreground%2A> jest <xref:System.Windows.Media.SolidColorBrush>, użyj <xref:System.Windows.Media.SolidColorBrush.Color%2A> dla <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Jeśli <xref:System.Windows.Controls.Control.Foreground%2A> jest <xref:System.Windows.Media.GradientBrush>, Użyj koloru <xref:System.Windows.Media.GradientStop> o najniższej wartości przesunięcia dla <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />— Dla innych <xref:System.Windows.Media.Brush> wpisz, pozostaw <xref:System.Windows.Forms.Control.ForeColor%2A> bez zmian. Oznacza to, że używana jest wartość domyślna.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Gdy <xref:System.Windows.UIElement.IsEnabled%2A> jest ustawiona, <xref:System.Windows.Forms.Integration.WindowsFormsHost> ustawia element <xref:System.Windows.Forms.Control.Enabled%2A> właściwość obsługiwanego formantu.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Wszystkie cztery wartości właściwości <xref:System.Windows.Forms.Control.Padding%2A> właściwość hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu są ustawione na <xref:System.Windows.Thickness> wartość.<br /><br /> -Wartości większe niż <xref:System.Int32.MaxValue> są ustawione na <xref:System.Int32.MaxValue>.<br />-Wartości mniejszej niż <xref:System.Int32.MinValue> są ustawione na <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible> mapuje <xref:System.Windows.Forms.Control.Visible%2A>  =  `true`. Hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant jest widoczny. Jawne ustawienie <xref:System.Windows.Forms.Control.Visible%2A> właściwość obsługiwany formant `false` nie jest zalecane.<br />-   <xref:System.Windows.Visibility.Collapsed> mapuje <xref:System.Windows.Forms.Control.Visible%2A>  =  `true` lub `false`. Hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu nie jest rysowana i jego obszar jest zwinięty.<br />-   <xref:System.Windows.Visibility.Hidden> Hostowanej [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrola zajmuje miejsce w układzie, ale nie jest widoczny. W takim przypadku <xref:System.Windows.Forms.Control.Visible%2A> właściwość jest ustawiona na `true`. Jawne ustawienie <xref:System.Windows.Forms.Control.Visible%2A> właściwość obsługiwany formant `false` nie jest zalecane.|  
  
 Dołączone właściwości na kontenery są w pełni obsługiwane przez <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.  
  
 Aby uzyskać więcej informacji, zobacz [wskazówki: Mapowanie właściwości za pomocą elementu WindowsFormsHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md).  
  
## <a name="updates-to-parent-properties"></a>Aktualizacje właściwości nadrzędnej  
 Zmiany właściwości nadrzędnej większości spowodować powiadomienia do formantu podrzędnego hostowanej. Poniżej przedstawiono listę właściwości, które nie powodują powiadomienia o zmianach ich wartości.  
  
-   <xref:System.Windows.Controls.Control.Background%2A>  
  
-   <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
-   <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
-   <xref:System.Windows.UIElement.Visibility%2A>  
  
 Na przykład w przypadku zmiany wartości <xref:System.Windows.Controls.Control.Background%2A> właściwość <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Control.BackColor%2A> właściwość hostowanej formantu nie ulega zmianie.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>Mapowanie właściwości za pomocą formantu ElementHost  
 Następujące właściwości Podaj powiadomienia o zmianie wbudowanych. Nie wywołuj <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> metody, jeśli Mapowanie właściwości:  
  
-   AutoSize  
  
-   Kolor tła  
  
-   BackgroundImage  
  
-   BackgroundImageLayout  
  
-   BindingContext  
  
-   Właściwości CausesValidation  
  
-   ContextMenu  
  
-   ContextMenuStrip  
  
-   Kursor  
  
-   Doku.  
  
-   Enabled  
  
-   Czcionki  
  
-   ForeColor  
  
-   Lokalizacja  
  
-   Margines  
  
-   Dopełnienie  
  
-   Nadrzędny  
  
-   Region  
  
-   RightToLeft  
  
-   Rozmiar  
  
-   TabIndex  
  
-   TabStop  
  
-   Tekst  
  
-   Widoczne  
  
 <xref:System.Windows.Forms.Integration.ElementHost> Kontroli tłumaczy domyślne [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] właściwości, aby ich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odpowiedniki przy użyciu poniższej tabeli translacji.  
  
 Aby uzyskać więcej informacji, zobacz [wskazówki: Mapowanie właściwości za pomocą formantu ElementHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md).  
  
|Obsługa formularzy systemu Windows|Windows Presentation Foundation|Zachowanie współdziałanie|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) w elemencie hostowanej|Ustawienie tej właściwości wymusza odświeżenia z <xref:System.Windows.Media.ImageBrush>. Jeśli <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> właściwość jest ustawiona na `false` (wartość domyślna), to <xref:System.Windows.Media.ImageBrush> opiera się na wygląd <xref:System.Windows.Forms.Integration.ElementHost> kontrolować, łącznie z jej <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> właściwości i wszystkie dołączone malowania programy obsługi.<br /><br /> Jeśli <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> właściwość jest ustawiona na `true`, <xref:System.Windows.Media.ImageBrush> opiera się na wygląd <xref:System.Windows.Forms.Integration.ElementHost> formantu nadrzędnego, łącznie z elementu nadrzędnego <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> właściwości i wszystkie dołączone malowania programy obsługi.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) w elemencie hostowanej|Ustawienie tej właściwości spowoduje, że takie samo zachowanie opisane dla <xref:System.Windows.Forms.Control.BackColor%2A> mapowania.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) w elemencie hostowanej|Ustawienie tej właściwości spowoduje, że takie samo zachowanie opisane dla <xref:System.Windows.Forms.Control.BackColor%2A> mapowania.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Standardowe kursora jest translacja do odpowiednich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standardowe kursora. Jeśli [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nie jest standard kursora, wartość domyślna jest przypisany.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Gdy <xref:System.Windows.Forms.Control.Enabled%2A> jest ustawiona, <xref:System.Windows.Forms.Integration.ElementHost> kontrolować zestawy <xref:System.Windows.UIElement.IsEnabled%2A> właściwości w elemencie hostowanej.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A> Wartość jest przekształcana na odpowiedni zestaw [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości czcionki.|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A> w elemencie hostowanej|Jeśli <xref:System.Drawing.Font.Bold%2A> jest `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> ma ustawioną wartość <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Jeśli <xref:System.Drawing.Font.Bold%2A> jest `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> ma ustawioną wartość <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A> w elemencie hostowanej|Jeśli <xref:System.Drawing.Font.Italic%2A> jest `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> ma ustawioną wartość <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Jeśli <xref:System.Drawing.Font.Italic%2A> jest `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> ma ustawioną wartość <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations> w elemencie hostowanej|Ma zastosowanie tylko wtedy, gdy hosting <xref:System.Windows.Controls.TextBlock> formantu.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations> w elemencie hostowanej|Ma zastosowanie tylko wtedy, gdy hosting <xref:System.Windows.Controls.TextBlock> formantu.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No> mapuje <xref:System.Windows.FlowDirection.LeftToRight>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes> mapuje <xref:System.Windows.FlowDirection.RightToLeft>.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost> Kontrolować zestawy <xref:System.Windows.UIElement.Visibility%2A> właściwości w elemencie hostowanej za pomocą następujących reguł:<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true` mapuje <xref:System.Windows.Visibility.Visible>.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false` mapuje <xref:System.Windows.Visibility.Hidden>.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF i Win32 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Współdziałanie WPF i Windows Forms](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)  
 [Przewodnik: mapowanie właściwości z użyciem elementu WindowsFormsHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md)  
 [Przewodnik: mapowanie właściwości z użyciem kontrolki ElementHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md)
