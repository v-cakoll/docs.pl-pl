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
ms.openlocfilehash: b85a607d2e44d6253359a81118f90e6ee05d2d3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187325"
---
# <a name="troubleshooting-hybrid-applications"></a>Rozwiązywanie problemów aplikacji hybrydowych
<a name="introduction"></a>W tym temacie wymieniono niektóre typowe problemy, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mogą wystąpić podczas tworzenia aplikacji hybrydowych, które używają zarówno technologii Windows Forms.  

<a name="overlapping_controls"></a>
## <a name="overlapping-controls"></a>Nakładające się kontrolki  
 Formanty nie mogą nakładać się zgodnie z oczekiwaniami. Formularze systemu Windows używa oddzielnego HWND dla każdego formantu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]używa jednego HWND dla całej zawartości na stronie. Ta różnica w implementacji powoduje nieoczekiwane nakładające się zachowania.  
  
 Formant Formularzy systemu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows hostowany [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawsze pojawia się na zawartości.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawartość hostowana <xref:System.Windows.Forms.Integration.ElementHost> w formancie pojawia się <xref:System.Windows.Forms.Integration.ElementHost> w kolejności z formantu. Istnieje możliwość nakładania <xref:System.Windows.Forms.Integration.ElementHost> formantów, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ale hostowana zawartość nie łączy ani nie wchodzi w interakcje.  
  
<a name="child_property"></a>
## <a name="child-property"></a>Właściwość podrzędna  
 I <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost> klasy mogą obsługiwać tylko jeden formant podrzędny lub element. Aby hostować więcej niż jeden formant lub element, należy użyć kontenera jako zawartości podrzędnej. Można na przykład dodać przycisk Formularze systemu <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> Windows i kontrolki pola <xref:System.Windows.Forms.Integration.WindowsFormsHost> wyboru <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> do formantu, a następnie przypisać panel do właściwości formantu. Nie można jednak dodać formanty przycisku <xref:System.Windows.Forms.Integration.WindowsFormsHost> i pola wyboru oddzielnie do tego samego formantu.  
  
<a name="scaling"></a>
## <a name="scaling"></a>Skalowanie  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]i Windows Forms mają różne modele skalowania. Niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przekształcenia skalowania mają znaczenie dla formantów Windows Forms, ale inne nie. Na przykład skalowanie formantu Windows Forms do 0 będzie działać, ale jeśli spróbujesz skalować ten sam formant z powrotem do wartości niezerowej, rozmiar formantu pozostanie 0. Aby uzyskać więcej informacji, zobacz [Zagadnienia dotyczące układu elementu WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>
## <a name="adapter"></a>Adapter  
 Może wystąpić zamieszanie podczas <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost> pracy i klas, ponieważ zawierają one ukryty kontener. Zarówno <xref:System.Windows.Forms.Integration.WindowsFormsHost> i <xref:System.Windows.Forms.Integration.ElementHost> klasy mają ukryty kontener, o nazwie *karty*, które używają do hosta zawartości. Dla <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu karty pochodzi od <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> klasy. Dla <xref:System.Windows.Forms.Integration.ElementHost> formantu karty pochodzi <xref:System.Windows.Controls.DockPanel> od elementu. Po wyświetleniu odwołań do karty w innych tematach współpracy, ten kontener jest o omawiane.  
  
<a name="nesting"></a>
## <a name="nesting"></a>Zagnieżdżanie  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Zagnieżdżanie <xref:System.Windows.Forms.Integration.ElementHost> elementu wewnątrz formantu nie jest obsługiwane. <xref:System.Windows.Forms.Integration.ElementHost> Zagnieżdżanie <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu wewnątrz elementu również nie jest obsługiwane.  
  
<a name="focus"></a>
## <a name="focus"></a>Ostrości  
 Fokus działa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inaczej w formularzach systemu Windows, co oznacza, że problemy z fokusem mogą wystąpić w aplikacji hybrydowej. Na przykład jeśli masz fokus wewnątrz <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu i albo zminimalizować i przywrócić stronę lub pokazać <xref:System.Windows.Forms.Integration.WindowsFormsHost> modalne okno dialogowe, fokus wewnątrz elementu może zostać utracone. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> nadal ma fokus, ale formant wewnątrz może nie.  
  
 Sprawdzanie poprawności danych zależy również od fokusu. Sprawdzanie poprawności <xref:System.Windows.Forms.Integration.WindowsFormsHost> działa w elemencie, ale nie <xref:System.Windows.Forms.Integration.WindowsFormsHost> działa jak kartę <xref:System.Windows.Forms.Integration.WindowsFormsHost> z elementu lub między dwoma różnymi elementami.  
  
<a name="property_mapping"></a>
## <a name="property-mapping"></a>Mapowanie właściwości  
 Niektóre mapowania właściwości wymagają szerokiej interpretacji, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] połączyć różne implementacje między technologiami windows forms i Windows Forms. Mapowania właściwości umożliwiają kod reagować na zmiany czcionek, kolorów i innych właściwości. Ogólnie rzecz biorąc mapowania właściwości działają przez nasłuchiwanie zdarzeń zmienionej *właściwości*lub na*wywołaniach*zmienionych właściwości i ustawienie odpowiednich właściwości na formancie podrzędnym lub jego karcie. Aby uzyskać więcej informacji, zobacz [Formularze systemu Windows i mapowanie właściwości WPF](windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>
## <a name="layout-related-properties-on-hosted-content"></a>Właściwości związane z układem w zawartości hosted  
 Po <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> przypisaniu właściwości lub <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> właściwości automatycznie ustawia się kilka właściwości związanych z układem w hostowanym pliku. Zmiana tych właściwości zawartości może spowodować nieoczekiwane zachowania układu.  
  
 Hostowana zawartość jest zadokowana, aby wypełnić i <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost> nadrzędną. Aby włączyć to zachowanie wypełniania, kilka właściwości są ustawiane podczas ustawiania właściwości podrzędnej. W poniższej tabeli wymieniono właściwości <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Integration.WindowsFormsHost> zawartości, które są ustawiane przez i klasy.  
  
|Klasa hosta|Właściwości zawartości|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Nie należy ustawiać tych właściwości bezpośrednio na hostowanej zawartości. Aby uzyskać więcej informacji, zobacz [Zagadnienia dotyczące układu elementu WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>
## <a name="navigation-applications"></a>Aplikacje nawigacyjne  
 Aplikacje nawigacyjne mogą nie zachowywać stanu użytkownika. Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> odtwarza jego formantów, gdy jest używany w aplikacji nawigacji. Ponownetworzenie formantów podrzędnych występuje, gdy <xref:System.Windows.Forms.Integration.WindowsFormsHost> użytkownik przechodzi z dala od strony hosting elementu, a następnie zwraca do niego. Wszelkie treści wpisane przez użytkownika zostaną utracone.  
  
<a name="message_loop_interoperation"></a>
## <a name="message-loop-interoperation"></a>Interoperacyjności pętli komunikatów  
 Podczas pracy z pętlami komunikatów windows forms wiadomości mogą nie być przetwarzane zgodnie z oczekiwaniami. Metoda <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> jest wywoływana <xref:System.Windows.Forms.Integration.WindowsFormsHost> przez konstruktora. Ta metoda dodaje filtr [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wiadomości do pętli wiadomości. Ten filtr <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> wywołuje metodę, jeśli <xref:System.Windows.Forms.Control?displayProperty=nameWithType> był celem wiadomości i tłumaczy/wysyła wiadomość.  
  
 Jeśli zostanie <xref:System.Windows.Window> wyświetlony w pętli komunikatów windows forms z <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> nie można wpisać niczego, chyba że wywołanie metody. Metoda <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> przyjmuje <xref:System.Windows.Window> i dodaje <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>, który przekierowuje wiadomości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] związane z kluczem do pętli wiadomości. Aby uzyskać więcej informacji, zobacz [Formularze systemu Windows i architektura wprowadzania interoperacyjności WPF](windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>
## <a name="opacity-and-layering"></a>Krycie i nakładanie warstw  
 Klasa <xref:System.Windows.Interop.HwndHost> nie obsługuje warstw. Oznacza to, <xref:System.Windows.UIElement.Opacity%2A> że ustawienie <xref:System.Windows.Forms.Integration.WindowsFormsHost> właściwości na elemencie nie ma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wpływu <xref:System.Windows.Window.AllowsTransparency%2A> i `true`nie nastąpi mieszanie z innymi oknami, które zostały ustawione na .  
  
<a name="dispose"></a>
## <a name="dispose"></a>Dispose  
 Nie utylizacji klas prawidłowo może wyciek zasobów. W aplikacjach hybrydowych upewnij <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost> się, że i klasy są usuwane lub można przeciek zasobów. Windows Forms <xref:System.Windows.Forms.Integration.ElementHost> usuwa formanty po <xref:System.Windows.Forms.Form> zamknięciu nadrzędnego niemodalnego. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]usuwa <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy po zamknięciu aplikacji. Istnieje możliwość wyświetlenia <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Window> w pętli komunikatów formularzy systemu Windows. W takim przypadku kod może nie odbierać powiadomienia, że aplikacja jest zamykana.  
  
<a name="enabling_visual_styles"></a>
## <a name="enabling-visual-styles"></a>Włączanie stylów wizualnych  
 Style wizualne systemu Microsoft Windows XP w formancie Windows Forms mogą nie być włączone. Metoda <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> jest wywoływana w szablonie dla aplikacji Windows Forms. Mimo że ta metoda nie jest wywoływana domyślnie, jeśli używasz programu Visual Studio do utworzenia projektu, otrzymasz microsoft Windows XP style wizualne dla formantów, jeśli wersja 6.0 comctl32.dll jest dostępna. Należy wywołać <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metodę przed uchwyty są tworzone w wątku. Aby uzyskać więcej informacji, zobacz [Jak: Włączanie stylów wizualnych w aplikacji hybrydowej](how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>
## <a name="licensed-controls"></a>Licencjonowane kontrolki  
 Licencjonowane formularze systemu Windows formanty, które wyświetlają informacje o licencjonowaniu w oknie komunikatu dla użytkownika może spowodować nieoczekiwane zachowanie aplikacji hybrydowej. Niektóre licencjonowane formanty pokazują okno dialogowe w odpowiedzi na obsługę tworzenia. Na przykład licencjonowany formant może poinformować użytkownika, że licencja jest wymagana lub że użytkownik ma trzy pozostałe zastosowania próbne formantu.  
  
 Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> pochodzi z <xref:System.Windows.Interop.HwndHost> klasy, a dojście formantu <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> podrzędnego jest tworzony wewnątrz metody. Klasa <xref:System.Windows.Interop.HwndHost> nie zezwala na przetwarzanie wiadomości <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> w metodzie, ale wyświetlanie okna dialogowego powoduje, że wiadomości mają być wysyłane. Aby włączyć ten scenariusz licencjonowania, należy wywołać <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> metodę <xref:System.Windows.Forms.Integration.WindowsFormsHost> na formancie przed przypisaniem go jako element podrzędny elementu.  
  
<a name="wpf_designer"></a>
## <a name="wpf-designer"></a>Projektant WPF  
 Zawartość WPF można zaprojektować przy użyciu WPF Designer dla programu Visual Studio. W poniższych sekcjach przedstawiono niektóre typowe problemy, które mogą wystąpić podczas tworzenia aplikacji hybrydowych za pomocą Projektanta WPF.  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent jest ignorowany w czasie projektowania  
 Właściwość <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> może nie działać zgodnie z oczekiwaniami w czasie projektowania.  
  
 Jeśli WPF formantu nie jest na widocznym elementem <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> nadrzędnym, środowisko wykonawcze WPF ignoruje wartość. Powodem, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> który może być <xref:System.Windows.Forms.Integration.ElementHost> ignorowany, jest <xref:System.AppDomain>to, że obiekt jest tworzony w osobnym pliku . Jednak po uruchomieniu aplikacji <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> działa zgodnie z oczekiwaniami.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Lista błędów w czasie projektowania pojawia się po usunięciu folderu obj  
 Jeśli folder obj zostanie usunięty, zostanie wyświetlona lista błędów czasu projektowania.  
  
 Podczas projektowania <xref:System.Windows.Forms.Integration.ElementHost>przy użyciu projektanta formularzy systemu Windows w folderze Debugowanie lub wydanie w folderze obj projektu. Jeśli usuniesz te pliki, zostanie wyświetlona lista błędów czasu projektowania. Aby rozwiązać ten problem, odbuduj projekt. Aby uzyskać więcej informacji, zobacz [Błędy czasu projektowania w Projektancie formularzy systemu Windows](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>
## <a name="elementhost-and-ime"></a>ElementHost i IME  
 Formanty WPF <xref:System.Windows.Forms.Integration.ElementHost> hostowane w obecnie <xref:System.Windows.Forms.Control.ImeMode%2A> nie obsługują właściwości. Zmiany <xref:System.Windows.Forms.Control.ImeMode%2A> zostaną zignorowane przez hostowane formanty.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Interoperacyjność w projektancie WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Architektura danych wejściowych współdziałania dla Windows Forms i WPF](windows-forms-and-wpf-interoperability-input-architecture.md)
- [Instrukcje: jak włączyć style wizualne w aplikacji hybrydowej](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [Zagadnienia dotyczące układu dla elementu WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Mapowanie właściwości Windows Forms i WPF](windows-forms-and-wpf-property-mapping.md)
- [Błędy czasu projektowania w narzędziu Projektant dla formularzy systemu Windows](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [Migracja i współdziałanie](migration-and-interoperability.md)
