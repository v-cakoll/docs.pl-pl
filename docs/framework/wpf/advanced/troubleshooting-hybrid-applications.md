---
title: Rozwiązywanie problemów aplikacji hybrydowych
ms.date: 03/30/2017
helpviewer_keywords:
- overlapping controls [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid applications [WPF interoperability]
- message loops [WPF]
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
ms.openlocfilehash: 707e77ac69878c1c7fb8e975c1f90ad657228d1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079678"
---
# <a name="troubleshooting-hybrid-applications"></a>Rozwiązywanie problemów aplikacji hybrydowych
<a name="introduction"></a> W tym temacie wymieniono niektóre typowe problemy, które mogą wystąpić podczas tworzenia aplikacji hybrydowych, które używają zarówno [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] technologii.  

<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>Nakładanie się formantów  
 Kontrolki nie nakładają się, jak można oczekiwać. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] używa oddzielnych HWND dla każdego formantu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa jednego HWND dla całej zawartości na stronie. Różnica ta implementacja powoduje, że nieoczekiwane zachowania nakładających się.  
  
 A [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sterowania hostowaną w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest zawsze wyświetlany w górnej części [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości hostowanej w <xref:System.Windows.Forms.Integration.ElementHost> formant jest widoczny w porządku osi z <xref:System.Windows.Forms.Integration.ElementHost> kontroli. Istnieje możliwość nakładają się na siebie <xref:System.Windows.Forms.Integration.ElementHost> kontrolek, ale hostowanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość nie jest w stanie połączyć lub wchodzić w interakcje.  
  
<a name="child_property"></a>   
## <a name="child-property"></a>Właściwości elementu podrzędnego  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> klasy może obsługiwać tylko pojedynczy element podrzędny formantu lub elementu. Aby obsługiwać więcej niż jeden formant lub element, należy użyć kontenera jako zawartość elementu podrzędnego. Na przykład można dodać [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki przycisk i pole wyboru do <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> sterowania, a następnie przypisz panelu, aby <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolki <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> właściwości. Jednak nie można dodać przycisk i pole wyboru kontrolek oddzielnie do tej samej <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontroli.  
  
<a name="scaling"></a>   
## <a name="scaling"></a>Skalowanie  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mają różne modele skalowania. Niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] skalowania przekształcenia są zrozumiałe dla [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolek, ale inne osoby nie są. Na przykład skalowanie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant 0 będzie działać, ale jeśli zostanie podjęta próba skalowania tej samej kontrolki wartość niezerową, rozmiar formantu pozostaje 0. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące układu dla elementu WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>   
## <a name="adapter"></a>Adapter  
 Może być pomyłek, pracując <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> klasy, ponieważ zawierają one ukryte kontenera. Zarówno <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> klasy mają ukryte kontener o nazwie *karty*, używane do hostowania zawartości. Aby uzyskać <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, adaptera pochodzi od klasy <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> klasy. Aby uzyskać <xref:System.Windows.Forms.Integration.ElementHost> kontrolki karty pochodzi od klasy <xref:System.Windows.Controls.DockPanel> elementu. Po pojawieniu się odwołań do karty sieciowej w innych tematach współdziałanie, ten kontener jest, co omówiono.  
  
<a name="nesting"></a>   
## <a name="nesting"></a>Zagnieżdżanie  
 Zagnieżdżanie <xref:System.Windows.Forms.Integration.WindowsFormsHost> element wewnątrz <xref:System.Windows.Forms.Integration.ElementHost> nie jest obsługiwany. Zagnieżdżanie <xref:System.Windows.Forms.Integration.ElementHost> kontrolować wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> element również nie jest obsługiwane.  
  
<a name="focus"></a>   
## <a name="focus"></a>fokus  
 Fokus działa inaczej w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], co oznacza, że skupić się problemy mogą wystąpić w aplikacji hybrydowej. Na przykład, jeśli masz fokus wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, a albo minimalizowanie i przywracanie strony lub Pokaż modalne okno dialogowe, skupić się wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> element mogą zostać utracone. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element nadal ma fokus, ale kontrolki wewnątrz jej nie może.  
  
 Sprawdzanie poprawności danych jest także wpływ fokus. Sprawdzanie poprawności działa w <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, ale nie działa zgodnie z karty z <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, lub z dwóch różnych <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementów.  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>Mapowanie właściwości  
 Niektóre właściwości mapowania wymagać rozbudowane interpretacji do zestawiania różnych implementacji między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] technologii. Mapowania właściwości Włącz swój kod, aby reagować na zmiany w czcionki, kolory i inne właściwości. Ogólnie rzecz biorąc, mapowania właściwości działają przez nasłuchiwanie w obu *właściwość*zmienione zdarzenia lub na*właściwość*zmienione wywołania i ustawienie odpowiednie właściwości kontrolki podrzędnej lub jego karty. Aby uzyskać więcej informacji, zobacz [Windows Forms i WPF właściwość mapowanie](windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>Właściwości związane z układem hostowaną zawartość  
 Gdy <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> właściwość jest przypisana, kilka właściwości związane z układem hostowaną zawartość są ustawiane automatycznie. Zmiana tych właściwości zawartości może spowodować nieoczekiwane układ zachowania.  
  
 Hostowanej zawartości jest zadokowany do wypełnienia <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> nadrzędnej. Aby włączyć to zachowanie wypełnienia, kilka właściwości są ustawiane podczas ustawiania właściwości elementu podrzędnego. W poniższej tabeli wymieniono, których właściwości zawartości są ustawiane przez <xref:System.Windows.Forms.Integration.ElementHost> i <xref:System.Windows.Forms.Integration.WindowsFormsHost> klasy.  
  
|Host Class|Właściwości zawartości|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Nie należy ustawiać właściwości tych bezpośrednio na hostowaną zawartość. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące układu dla elementu WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>Aplikacje nawigacji  
 Aplikacje nawigacji nie może utrzymywać stan użytkownika. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element odtwarza jego środków kontroli, gdy jest używany w aplikacji nawigacji. Ponowne tworzenie formantów podrzędnych występuje, gdy użytkownik przechodzi od hostowania stron <xref:System.Windows.Forms.Integration.WindowsFormsHost> element i zwraca do niego. Zawartość, która została wpisana przez użytkownika w zostaną utracone.  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>Współdziałanie pętli komunikatów  
 Podczas pracy z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pętli komunikatów, wiadomości nie mogą być przetwarzane, zgodnie z oczekiwaniami. <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> Metoda jest wywoływana przez <xref:System.Windows.Forms.Integration.WindowsFormsHost> konstruktora. Metoda ta umożliwia dodanie filtru komunikatów w celu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pętli komunikatów. Wywołuje ten filtr <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> metoda Jeśli <xref:System.Windows.Forms.Control?displayProperty=nameWithType> docelowym komunikat i wykonuje translację/wysyłki wiadomości.  
  
 Jeśli wyświetlisz <xref:System.Windows.Window> w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pętli komunikatów za pomocą <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>, nie można niczego wpisywać, chyba że wywołanie <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> metody. <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> Metoda przyjmuje <xref:System.Windows.Window> i dodaje <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>, który zmienia trasę komunikatów dotyczących klucza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pętli komunikatów. Aby uzyskać więcej informacji, zobacz [Windows Forms i architektura danych wejściowych współdziałania WPF](windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>Nieprzezroczystość i warstw  
 <xref:System.Windows.Interop.HwndHost> Klasa nie obsługuje warstwowe. Oznacza to, że ustawienie <xref:System.Windows.UIElement.Opacity%2A> właściwość <xref:System.Windows.Forms.Integration.WindowsFormsHost> element nie ma wpływu, a nie mieszania będą naliczane z innymi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemu windows, które mają <xref:System.Windows.Window.AllowsTransparency%2A> równa `true`.  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Metody Dispose  
 Nie prawidłowo usuwania klasy można przecieku zasobów. Upewnij się, że w aplikacjach hybrydowych <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> klasy będą usuwane, w przeciwnym razie mogą spowodować wyciek zasobów. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Usuwa <xref:System.Windows.Forms.Integration.ElementHost> sterować jego niemodalnym <xref:System.Windows.Forms.Form> nadrzędny zostanie zamknięty. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Usuwa <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementów podczas zamykania aplikacji. Istnieje możliwość pokazać <xref:System.Windows.Forms.Integration.WindowsFormsHost> element <xref:System.Windows.Window> w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pętli komunikatów. W takim przypadku Twój kod nie może otrzymywać powiadomienie, że Twoja aplikacja jest zamykana.  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>Włączanie stylów wizualnych  
 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] style wizualizacji, na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu może nie być włączona. <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> Metoda jest wywoływana w szablonie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacji. Chociaż ta metoda nie jest wywoływany przez ustawienie domyślne, jeśli używasz [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] do tworzenia projektu uzyskasz [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual style na kontrolki, jeśli jest dostępna wersja 6.0 Comctl32.dll. Należy wywołać <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda przed utworzeniem dojść w wątku. Aby uzyskać więcej informacji, zobacz [jak: Włączyć style Visual w aplikacji hybrydowej](how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>Licencjonowane formanty  
 Licencjonowane [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów, które wyświetlają informacje licencyjne w oknie komunikatu dla użytkownika może spowodować nieoczekiwane zachowanie w przypadku aplikacji hybrydowych. Niektóre licencjonowane formanty w odpowiedzi i obsługę tworzenia Wyświetla okno dialogowe. Na przykład licencjonowany formant może informować użytkownika, że wymagana jest licencja, lub czy użytkownik ma trzy pozostałe wersji próbnej używa kontrolki.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Dziedziczy po elemencie <xref:System.Windows.Interop.HwndHost> klasy i obsługują kontrolę rodzicielską jest tworzony w <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> metody. <xref:System.Windows.Interop.HwndHost> Klasy nie zezwala na komunikaty, które mają być przetwarzane w <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> metody, ale wyświetlanie okna dialogowego powoduje, że wiadomości do wysłania. Aby umożliwić wykonanie tego scenariusza licencjonowania, należy wywołać <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> metody kontroli przed przypisaniem go jako <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu podrzędnego.  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>Projektant WPF  
 Można zaprojektować zawartości WPF za pomocą [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]. W poniższych sekcjach wymieniono niektóre typowe problemy, które mogą wystąpić podczas tworzenia aplikacji hybrydowych przy użyciu [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent jest ignorowany w czasie projektowania  
 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> Właściwości mogą nie działać zgodnie z oczekiwaniami w czasie projektowania.  
  
 Jeśli kontrolki WPF nie jest widoczne nadrzędnego, środowisko uruchomieniowe WPF ignoruje <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> wartość. Przyczyna, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> może być ignorowane ponieważ <xref:System.Windows.Forms.Integration.ElementHost> tworzony jest obiekt w osobnym <xref:System.AppDomain>. Jednak po uruchomieniu aplikacji, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> działać zgodnie z oczekiwaniami.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Lista błędów w czasie projektowania jest wyświetlany, gdy obj folder zostanie usunięty  
 Jeśli obj folder zostanie usunięty, pojawi się lista błędów w czasie projektowania.  
  
 Podczas projektowania przy użyciu <xref:System.Windows.Forms.Integration.ElementHost>, Windows Forms Designer używa wygenerowane pliki w folderze debugowania lub wydania w folderze obj. projektu. Jeśli usuniesz te pliki, pojawi się lista błędów w czasie projektowania. Aby rozwiązać ten problem, ponownie skompiluj projekt. Aby uzyskać więcej informacji, zobacz [błędy czasu projektowania w programie Windows Forms Designer](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>Elementhost — i edytora IME  
 Formanty WPF hostowane w <xref:System.Windows.Forms.Integration.ElementHost> aktualnie nie obsługują <xref:System.Windows.Forms.Control.ImeMode%2A> właściwości. Zmienia się na <xref:System.Windows.Forms.Control.ImeMode%2A> zostaną zignorowane przez formanty hostowanej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Współdziałanie w Projektancie WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Architektura danych wejściowych współdziałania dla Windows Forms i WPF](windows-forms-and-wpf-interoperability-input-architecture.md)
- [Instrukcje: Włączyć style Visual w aplikacji hybrydowej](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [Zagadnienia dotyczące układu dla elementu WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Mapowanie właściwości Windows Forms i WPF](windows-forms-and-wpf-property-mapping.md)
- [Błędy czasu projektowania w narzędziu Projektant dla formularzy Windows Forms](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [Migracja i współdziałanie](migration-and-interoperability.md)
