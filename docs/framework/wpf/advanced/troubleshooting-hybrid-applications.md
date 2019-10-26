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
ms.openlocfilehash: 541d71efa66d14855704797892cac68799215159
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919757"
---
# <a name="troubleshooting-hybrid-applications"></a>Rozwiązywanie problemów aplikacji hybrydowych
<a name="introduction"></a>W tym temacie wymieniono niektóre typowe problemy, które mogą wystąpić podczas tworzenia aplikacji hybrydowych, które korzystają z technologii [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  

<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>Nakładające się kontrolki  
 Kontrolki mogą nie nakładać się zgodnie z oczekiwaniami. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] używa oddzielnego parametru HWND dla każdej kontrolki. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa jednego elementu HWND dla całej zawartości na stronie. Ta różnica między implementacjami powoduje nieoczekiwane nakładanie się zachowań.  
  
 Kontrolka [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hostowana w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawsze pojawia się na podstawie zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość hostowana w kontrolce <xref:System.Windows.Forms.Integration.ElementHost> jest wyświetlana w porządku osi z kontrolki <xref:System.Windows.Forms.Integration.ElementHost>. Możliwe jest nakładanie się <xref:System.Windows.Forms.Integration.ElementHost> formantów, ale hostowana zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie jest łączona ani nie działa.  
  
<a name="child_property"></a>   
## <a name="child-property"></a>Właściwość podrzędna  
 Klasy <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> mogą obsługiwać tylko jedną kontrolkę podrzędną lub element. Aby hostować więcej niż jeden formant lub element, należy użyć kontenera jako zawartości podrzędnej. Na przykład można dodać przycisk [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] i kontrolki pola wyboru do kontrolki <xref:System.Windows.Forms.Panel?displayProperty=nameWithType>, a następnie przypisać panel do właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> kontrolki <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Nie można jednak dodać przycisku i kontrolek pola wyboru oddzielnie do tej samej kontrolki <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
<a name="scaling"></a>   
## <a name="scaling"></a>Ponowne  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mają różne modele skalowania. Niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przekształceń skalowania mają znaczenie dla [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów, ale inne nie. Na przykład skalowanie kontrolki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] na 0 będzie możliwe, ale jeśli spróbujesz skalować tę samą kontrolkę z powrotem do wartości innej niż zero, rozmiar kontrolki pozostanie 0. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące układu dla elementu WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>   
## <a name="adapter"></a>Adapter  
 Podczas pracy z klasami <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> mogą wystąpić problemy, ponieważ zawierają one ukryty kontener. Klasy <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> mają ukryty kontener o nazwie *adapter*, którego używają do obsługi zawartości. Dla elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> adapter pochodzi z klasy <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType>. Dla formantu <xref:System.Windows.Forms.Integration.ElementHost>, karta pochodzi od elementu <xref:System.Windows.Controls.DockPanel>. Gdy widzisz odwołania do karty w innych tematach międzyoperacyjnych, ten kontener jest omawiany w tym scenariuszu.  
  
<a name="nesting"></a>   
## <a name="nesting"></a>Zagnieżdżania  
 Zagnieżdżanie elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> wewnątrz kontrolki <xref:System.Windows.Forms.Integration.ElementHost> nie jest obsługiwane. Zagnieżdżanie formantu <xref:System.Windows.Forms.Integration.ElementHost> wewnątrz elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> nie jest również obsługiwane.  
  
<a name="focus"></a>   
## <a name="focus"></a>Fokus  
 Fokus działa inaczej w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], co oznacza, że problemy z fokusem mogą wystąpić w aplikacji hybrydowej. Na przykład jeśli masz fokus wewnątrz elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>, a ty i przywróćesz stronę lub Pokaż modalne okno dialogowe, fokus wewnątrz elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> może zostać utracony. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> nadal ma fokus, ale formant wewnątrz niego może nie.  
  
 Sprawdzanie poprawności danych jest również zależne od fokusu. Walidacja działa w <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemencie, ale nie działa w postaci karty z elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> lub między dwoma różnymi <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementami.  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>Mapowanie właściwości  
 Niektóre mapowania właściwości wymagają obszernej interpretacji do mostkowania niepodobnych implementacji między [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] technologii. Mapowania właściwości umożliwiają kodowi reagowanie na zmiany w czcionkach, kolorach i innych właściwościach. Ogólnie rzecz biorąc, mapowania właściwości działają przez nasłuchiwanie zdarzeń ze zmienionymi *właściwościami*lub na wywołania zmiany*Właściwości*oraz ustawienie odpowiednich właściwości na formancie podrzędnym lub jego karcie. Aby uzyskać więcej informacji, zobacz [Windows Forms i mapowanie właściwości WPF](windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>Właściwości dotyczące układu dla hostowanej zawartości  
 Po przypisaniu właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> lub <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> kilka właściwości związanych z układem zawartości hostowanej jest ustawiany automatycznie. Zmiana tych właściwości zawartości może spowodować nieoczekiwane zachowanie układu.  
  
 Hostowana zawartość jest zadokowana w celu wypełnienia <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> elementu nadrzędnego. Aby włączyć to zachowanie wypełnienia, podczas ustawiania właściwości podrzędnej są ustawiane kilka właściwości. W poniższej tabeli wymieniono właściwości zawartości, które są ustawiane przez klasy <xref:System.Windows.Forms.Integration.ElementHost> i <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
|Klasa hosta|Właściwości zawartości|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Nie ustawiaj tych właściwości bezpośrednio w hostowanej zawartości. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące układu dla elementu WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>Aplikacje nawigacyjne  
 Aplikacje nawigacji mogą nie obsługiwać stanu użytkownika. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> ponownie tworzy jego kontrolki, gdy jest używany w aplikacji nawigacyjnej. Ponowne tworzenie formantów podrzędnych odbywa się, gdy użytkownik nawiguje poza stroną hostującym <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, a następnie zwraca do niego. Zawartość wprowadzona przez użytkownika zostanie utracona.  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>Międzyoperacyjna pętla komunikatów  
 Podczas pracy z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pętlami komunikatów, komunikaty mogą nie być przetwarzane zgodnie z oczekiwaniami. Metoda <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> jest wywoływana przez konstruktora <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Ta metoda dodaje filtr komunikatów do pętli komunikatów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ten filtr wywołuje metodę <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>, jeśli <xref:System.Windows.Forms.Control?displayProperty=nameWithType> był elementem docelowym komunikatu i tłumaczy/wysyła komunikat.  
  
 W przypadku pokazywania <xref:System.Windows.Window> w pętli komunikatów [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] z <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>, nie można wpisać niczego, chyba że zostanie wywołana metoda <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>. Metoda <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> przyjmuje <xref:System.Windows.Window> i dodaje <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>, który przekieruje komunikaty powiązane z kluczami do pętli komunikatów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Aby uzyskać więcej informacji, zobacz [Architektura danych wejściowych współdziałania między Windows Forms i WPF](windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>Nieprzezroczystość i warstwowe  
 Klasa <xref:System.Windows.Interop.HwndHost> nie obsługuje warstw. Oznacza to, że ustawienie właściwości <xref:System.Windows.UIElement.Opacity%2A> w elemencie <xref:System.Windows.Forms.Integration.WindowsFormsHost> nie ma żadnego efektu i żadne mieszanie nie zostanie wykonane z innymi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows, które mają <xref:System.Windows.Window.AllowsTransparency%2A> ustawione na `true`.  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Zużyt  
 Klasy niezbyt dobrze nie mogą wyciekać zasobów. W aplikacjach hybrydowych upewnij się, że klasy <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> są usuwane lub można wyciekować zasoby. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] usuwa <xref:System.Windows.Forms.Integration.ElementHost> kontrolki po zamknięciu niemodalnego <xref:System.Windows.Forms.Form> nadrzędnego. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usuwa elementy <xref:System.Windows.Forms.Integration.WindowsFormsHost>, gdy aplikacja zostanie zamknięta. Istnieje możliwość wyświetlenia elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> w <xref:System.Windows.Window> w pętli wiadomości [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. W takim przypadku kod może nie otrzymywać powiadomień o zamknięciu aplikacji.  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>Włączanie stylów wizualnych  
 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] style wizualizacji w kontrolce [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] może nie być włączona. Metoda <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> jest wywoływana w szablonie dla aplikacji [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Chociaż ta metoda nie jest wywoływana domyślnie, jeśli używasz programu Visual Studio do tworzenia projektu, uzyskasz [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] style wizualizacji dla kontrolek, jeśli dostępna jest wersja 6,0 programu comctl32. dll. Należy wywołać metodę <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> przed utworzeniem uchwytów w wątku. Aby uzyskać więcej informacji, zobacz [jak: włączyć style wizualne w aplikacji hybrydowej](how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>Licencjonowane kontrolki  
 Licencjonowane [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolki wyświetlające informacje licencyjne w oknie komunikatu dla użytkownika mogą spowodować nieoczekiwane zachowanie aplikacji hybrydowej. Niektóre licencjonowane kontrolki wyświetlają okno dialogowe w odpowiedzi na tworzenie uchwytów. Na przykład licencjonowana kontrolka może poinformować użytkownika, że licencja jest wymagana lub że użytkownik ma trzy pozostałe zastosowania w wersji próbnej.  
  
 Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> dziedziczy z klasy <xref:System.Windows.Interop.HwndHost>, a dojście formantu podrzędnego jest tworzone wewnątrz metody <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>. Klasa <xref:System.Windows.Interop.HwndHost> nie zezwala na przetwarzanie komunikatów w metodzie <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>, ale wyświetlanie okna dialogowego powoduje wysłanie komunikatów. Aby włączyć ten scenariusz licencjonowania, wywołaj metodę <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> na kontrolce przed przypisaniem jej jako elementu podrzędnego <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>Projektant WPF  
 Zawartość WPF można zaprojektować za pomocą [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]. W poniższych sekcjach wymieniono typowe problemy, które mogą wystąpić podczas tworzenia aplikacji hybrydowych przy użyciu [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent jest ignorowany w czasie projektowania  
 Właściwość <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> może nie zadziałała zgodnie z oczekiwaniami w czasie projektowania.  
  
 Jeśli formant WPF nie znajduje się w widocznym elemencie nadrzędnym, środowisko uruchomieniowe WPF ignoruje wartość <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>. Przyczyną, że <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> może być ignorowany, jest to, że <xref:System.Windows.Forms.Integration.ElementHost> obiekt jest tworzony w osobnym <xref:System.AppDomain>. Jednak po uruchomieniu aplikacji <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> działa zgodnie z oczekiwaniami.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Lista błędów czasu projektowania pojawia się po usunięciu folderu obj  
 Jeśli folder obj zostanie usunięty, pojawi się Lista błędów czasu projektowania.  
  
 Podczas projektowania przy użyciu <xref:System.Windows.Forms.Integration.ElementHost>Projektant formularzy systemu Windows używa wygenerowanych plików w folderze Debug lub Release w folderze obj projektu. Po usunięciu tych plików zostanie wyświetlona Lista błędów czasu projektowania. Aby rozwiązać ten problem, ponownie skompiluj projekt. Aby uzyskać więcej informacji, zobacz [Błędy czasu projektowania w Projektant formularzy systemu Windows](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost i IME  
 Formanty WPF hostowane w <xref:System.Windows.Forms.Integration.ElementHost> obecnie nie obsługują właściwości <xref:System.Windows.Forms.Control.ImeMode%2A>. Zmiany w <xref:System.Windows.Forms.Control.ImeMode%2A> zostaną zignorowane przez obsługiwane formanty.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Współdziałanie w projektancie WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Architektura danych wejściowych współdziałania dla Windows Forms i WPF](windows-forms-and-wpf-interoperability-input-architecture.md)
- [Instrukcje: jak włączyć style wizualne w aplikacji hybrydowej](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [Zagadnienia dotyczące układu dla elementu WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Mapowanie właściwości Windows Forms i WPF](windows-forms-and-wpf-property-mapping.md)
- [Błędy czasu projektowania w narzędziu Projektant dla formularzy Windows Forms](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [Migracja i współdziałanie](migration-and-interoperability.md)
