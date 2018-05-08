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
ms.openlocfilehash: 878761c030d4950e53ee24b76f7e29101584143a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-hybrid-applications"></a>Rozwiązywanie problemów aplikacji hybrydowych
<a name="introduction"></a> W tym temacie wymieniono niektóre typowe problemy, które mogą wystąpić, gdy tworzenie hybrydowych aplikacji korzystających z obu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] technologii.  
  

  
<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>Nakładanie się kontrolek  
 Formanty nie może nakładać się zgodnie z regułami. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] używa oddzielnych HWND dla każdego formantu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa jednego HWND dla całej zawartości na stronie. Ta różnica implementacji powoduje nieoczekiwane zachowania nakładające się.  
  
 A [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli hostowanych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawsze jest wyświetlany nad [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość udostępniana w <xref:System.Windows.Forms.Integration.ElementHost> formant jest widoczny w porządek osi z <xref:System.Windows.Forms.Integration.ElementHost> formantu. Można zastąpić <xref:System.Windows.Forms.Integration.ElementHost> formantów, ale hostowanej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości nie łączyć lub interakcji.  
  
<a name="child_property"></a>   
## <a name="child-property"></a>Właściwość elementu podrzędnego  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> klasy może obsługiwać tylko pojedynczy element potomny formantu lub elementu. Aby obsługuje więcej niż jeden formant lub elementu, musisz użyć kontener jako zawartość elementu podrzędnego. Na przykład można dodać [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli przycisk i pole wyboru w celu <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> kontroli, a następnie przypisz panelu <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> właściwości. Jednak nie można dodać kontrolki przycisku i pole wyboru osobno do tej samej <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu.  
  
<a name="scaling"></a>   
## <a name="scaling"></a>Skalowanie  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mają różne modele skalowania. Niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] skalowania przekształceń są przydatne do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów, ale inne osoby nie są. Na przykład skalowanie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli 0 będą działać, ale próba skalowania formantu tego samego wartość niezerową rozmiar formantu pozostaje 0. Aby uzyskać więcej informacji, zobacz [zagadnienia układu elementu WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>   
## <a name="adapter"></a>Adapter  
 Mogą wystąpić problemy interpretacyjne podczas pracy <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> klas, ponieważ zawierają one ukryte kontenera. Zarówno <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> klasy mają ukryte kontener o nazwie *karty*, które używają do hosta zawartości. Dla <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, karta pochodną <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> klasy. Dla <xref:System.Windows.Forms.Integration.ElementHost> kontroli, karta pochodną <xref:System.Windows.Controls.DockPanel> elementu. Gdy pojawi się odwołania do karty w innych tematach współdziałanie, ten kontener jest co omówiono.  
  
<a name="nesting"></a>   
## <a name="nesting"></a>Zagnieżdżania  
 Zagnieżdżania <xref:System.Windows.Forms.Integration.WindowsFormsHost> element wewnątrz <xref:System.Windows.Forms.Integration.ElementHost> nie jest obsługiwany. Zagnieżdżania <xref:System.Windows.Forms.Integration.ElementHost> kontrolować wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> również nie jest obsługiwany.  
  
<a name="focus"></a>   
## <a name="focus"></a>Fokus  
 Fokus działa inaczej w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], co oznacza, że skupić się problemy mogą występować w aplikacji hybrydowych. Na przykład, jeśli masz fokus wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu i albo zminimalizować i przywrócić stronę lub Pokaż modalne okno dialogowe można skupić się wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu mogą zostać utracone. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element nadal ma fokus, ale kontrolki wewnątrz jej nie mogą.  
  
 Sprawdzanie poprawności danych dotyczy również fokus. Sprawdzanie poprawności działa w <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, ale nie działa jako karcie poza <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, lub z dwóch różnych <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementów.  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>Mapowanie właściwości  
 Niektóre mapowania właściwości wymagać interpretacji szeroką gamę do zestawiania niepodobnych implementacje między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] technologii. Mapowania właściwości Włącz swój kod, aby zareagować na zmiany w czcionki, kolory i inne właściwości. Ogólnie rzecz biorąc, mapowania właściwości działają przez nasłuchiwanie albo *właściwości*zmienić zdarzenia lub na*właściwości*zmienić wywołań i ustawienie odpowiednie właściwości kontrolki podrzędnej lub jej karty. Aby uzyskać więcej informacji, zobacz [formularzy systemu Windows i mapowania właściwości WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>Właściwości związane z układem hostowaną zawartość  
 Gdy <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> przypisano właściwości, kilka właściwości związane z układem zawartości hostowanej są ustawiane automatycznie. Zmiana tych właściwości zawartości może spowodować nieoczekiwane układu zachowania.  
  
 Hostowanej zawartości jest zadokowany do wypełnienia <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> nadrzędnej. Aby włączyć to zachowanie fill, kilka właściwości są ustawiane podczas ustawiania właściwości podrzędnych. W poniższej tabeli wymieniono, których właściwości zawartości są ustawiane przez <xref:System.Windows.Forms.Integration.ElementHost> i <xref:System.Windows.Forms.Integration.WindowsFormsHost> klasy.  
  
|Klasa hosta|Właściwości zawartości|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Nie należy ustawiać właściwości bezpośrednio na hostowaną zawartość. Aby uzyskać więcej informacji, zobacz [zagadnienia układu elementu WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>Aplikacje nawigacji  
 Aplikacje nawigacji nie może utrzymywać stanu użytkownika. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element odtwarza jego formantów, gdy jest używany w aplikacji nawigacji. Ponowne tworzenie formantów podrzędnych występuje, gdy użytkownik nawiguje przeciwną stronę hostingu <xref:System.Windows.Forms.Integration.WindowsFormsHost> element i zwraca do niego. Zawartość, która została wpisana w przez użytkownika zostaną utracone.  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>Współdziałanie pętli komunikatów  
 Podczas pracy z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pętli komunikatów, wiadomości nie mogą być przetwarzane zgodnie z oczekiwaniami. <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> Metoda jest wywoływana przez <xref:System.Windows.Forms.Integration.WindowsFormsHost> konstruktora. Ta metoda dodaje filtr komunikatu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pętli komunikatów. Wywołuje ten filtr <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> metody Jeśli <xref:System.Windows.Forms.Control?displayProperty=nameWithType> docelowym wiadomości i tłumaczy/wysyła wiadomość.  
  
 Jeśli możesz wyświetlić <xref:System.Windows.Window> w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pętli komunikatów z <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>, nie można niczego wpisywać, chyba że wywołujesz <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> — metoda. <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> Ma metodę <xref:System.Windows.Window> i dodaje <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>, który zmienia trasę klucz powiązane komunikaty, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pętli komunikatów. Aby uzyskać więcej informacji, zobacz [architektura wprowadzania współdziałania WPF i formularze systemu Windows](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>Nieprzezroczystość i tworzenie warstw  
 <xref:System.Windows.Interop.HwndHost> Klasa nie obsługuje tworzenie warstw. Oznacza to, że ustawienie <xref:System.Windows.UIElement.Opacity%2A> właściwość <xref:System.Windows.Forms.Integration.WindowsFormsHost> element nie ma wpływu i mieszania nie nastąpi z innymi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemu windows, które mają <xref:System.Windows.Window.AllowsTransparency%2A> ustawioną `true`.  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Metoda Dispose  
 Nie usuwanie klas prawidłowo można wyciek zasobów. Upewnij się, że w aplikacjach hybrydowego <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> klasy są usuwane, lub można wyciek zasobów. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Usuwa <xref:System.Windows.Forms.Integration.ElementHost> sterować jego niemodalne <xref:System.Windows.Forms.Form> nadrzędnego zostanie zamknięty. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Usuwa <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementów podczas zamykania aplikacji. Umożliwia wyświetlanie <xref:System.Windows.Forms.Integration.WindowsFormsHost> element <xref:System.Windows.Window> w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pętli komunikatów. W takim przypadku kodu nie może otrzymywać powiadomienie, że aplikacja jest zamykana.  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>Włączanie style wizualne  
 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] Visual Style na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant może nie być włączone. <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> Metoda jest wywoływana w szablonie dla [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacji. Mimo że ta metoda nie jest wywoływana domyślnie, jeśli używasz [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] do tworzenia projektu uzyskasz [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual style formantów, jeśli jest dostępny Comctl32.dll w wersji 6.0. Należy wywołać <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda przed utworzeniem dojść w wątku. Aby uzyskać więcej informacji, zobacz [porady: Włączanie style wizualne w aplikacji hybrydowych](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>Licencjonowane formanty  
 Licencjonowane [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty, które wyświetlają informacje o licencji w oknie komunikatu do użytkownika może spowodować nieoczekiwane zachowanie aplikacji hybrydowych. Niektóre licencjonowane formanty Wyświetla okno dialogowe, w odpowiedzi i obsługę tworzenia. Na przykład licencjonowanego formantu może poinformować użytkownika, że wymagana jest licencja lub czy użytkownik ma trzy pozostałe używa wersji próbnej formantu.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Pochodną elementu <xref:System.Windows.Interop.HwndHost> klasy, a formant podrzędny dojścia jest tworzone wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> metody. <xref:System.Windows.Interop.HwndHost> Klasy nie zezwala na komunikaty mają być przetwarzane w <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> metody, ale wyświetlanie okna dialogowego powoduje komunikatów do wysłania. Aby włączyć w tym scenariuszu licencjonowania, należy wywołać <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> metody w formancie przed przypisaniem go jako <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu podrzędnego.  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>Projektant WPF  
 Zawartość WPF można zaprojektować przy użyciu [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]. W poniższych sekcjach wymieniono niektóre typowe problemy, które mogą wystąpić, gdy tworzenie hybrydowych aplikacji z [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent jest ignorowany w czasie projektowania  
 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> Właściwość może nie działać zgodnie z oczekiwaniami w czasie projektowania.  
  
 Jeśli kontrolce WPF nie jest widoczne nadrzędnej, środowisko uruchomieniowe WPF ignoruje <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> wartość. Powód który <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> może zostać zignorowany ponieważ <xref:System.Windows.Forms.Integration.ElementHost> obiekt jest tworzony w oddzielnej <xref:System.AppDomain>. Jednak po uruchomieniu aplikacji, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> działać zgodnie z oczekiwaniami.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Lista błędów w czasie projektowania jest wyświetlany, gdy jest usuwany w folderze obj.  
 Jeśli w folderze obj. zostanie usunięty, pojawi się lista błędów czasu projektowania.  
  
 Podczas projektowania przy użyciu <xref:System.Windows.Forms.Integration.ElementHost>, Projektant formularzy systemu Windows używa wygenerowanych plików w folderze debugowanie czy wydanie w folderze obj. projektu. Jeśli usuniesz te pliki, pojawi się lista błędów czasu projektowania. Aby rozwiązać ten problem, ponownie skompiluj projekt. Aby uzyskać więcej informacji, zobacz [błędy czasu projektowania w narzędziu Projektant dla formularzy systemu Windows](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost i edytora IME  
 Formantów WPF hostowanych w <xref:System.Windows.Forms.Integration.ElementHost> aktualnie nie obsługują <xref:System.Windows.Forms.Control.ImeMode%2A> właściwości. Zmienia się na <xref:System.Windows.Forms.Control.ImeMode%2A> zostaną zignorowane przez formanty hostowanej.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Współdziałanie w Projektancie WPF](http://msdn.microsoft.com/library/2cb7c1ca-2a75-463b-8801-fba81e2b7042)  
 [Architektura danych wejściowych współdziałania dla Windows Forms i WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)  
 [Instrukcje: jak włączyć style wizualne w aplikacji hybrydowej](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)  
 [Zagadnienia dotyczące układu dla elementu WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Mapowanie właściwości Windows Forms i WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Błędy czasu projektowania w narzędziu Projektant dla formularzy Windows Forms](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
