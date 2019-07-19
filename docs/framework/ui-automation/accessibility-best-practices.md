---
title: Najlepsze praktyki dotyczące ułatwień dostępu
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: 0fe09c0c261f36f1e9f241a6a6a8aacf3bf07d29
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331495"
---
# <a name="accessibility-best-practices"></a>Najlepsze praktyki dotyczące ułatwień dostępu
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 Wdrożenie następujących najlepszych rozwiązań w zakresie kontroli lub aplikacji poprawi ich dostępność dla osób korzystających z urządzeń z technologią pomocniczą. Wiele z tych najlepszych rozwiązań koncentruje się [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] na dobrym projekcie. Każde najlepsze rozwiązanie obejmuje informacje o implementacji [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] dla formantów lub aplikacji. W wielu przypadkach pracy, która spełnia te najlepsze rozwiązania, już znajduje się w [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kontrolkach.  
  
<a name="Programmatic_Access"></a>   
## <a name="programmatic-access"></a>Dostęp programistyczny  
 Dostęp programistyczny polega na zapewnieniu, że wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy są oznaczone etykietami, wartości właściwości są ujawniane i wywoływane są odpowiednie zdarzenia. W przypadku [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kontrolek standardowych większość tej pracy jest już wykonywana przez <xref:System.Windows.Automation.Peers.AutomationPeer>program. Niestandardowe kontrolki wymagają dodatkowej pracy, aby zapewnić, że dostęp programistyczny jest prawidłowo zaimplementowany.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>   
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Włącz dostęp programistyczny do wszystkich elementów interfejsu użytkownika i tekstu  
 [!INCLUDE[TLA#tla_ui#initcap](../../../includes/tlasharptla-uisharpinitcap-md.md)]elementy powinny włączać dostęp programistyczny. Jeśli jest formantem standardowym [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] , obsługa dostępu programowego jest zawarta w kontrolce. [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Jeśli formant jest formantem niestandardowym — formantem, który został poddany do podklasy ze wspólnej kontrolki lub kontrolki, która została poddana kontroli, należy sprawdzić <xref:System.Windows.Automation.Peers.AutomationPeer> implementację obszarów, które mogą wymagać modyfikacji.  
  
 Zgodnie z tym najlepszym rozwiązaniem producenci technologii pomocniczej mogą identyfikować elementy produktu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]i manipulować nimi.  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>   
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Umieszczaj nazwy, tytuły i opisy dotyczące obiektów, ramek i stron interfejsu użytkownika  
 Technologie pomocnicze, zwłaszcza czytniki ekranu, wykorzystują tytuł, aby zrozumieć lokalizację ramki, obiektu lub strony w schemacie nawigacji. W związku z tym tytuł musi być bardzo opisowy. Na przykład tytuł strony sieci Web "Strona sieci Web firmy Microsoft" jest bezużyteczny, jeśli użytkownik przejdzie głęboko do określonego obszaru. Opisowy tytuł ma krytyczne znaczenie dla użytkowników niewidomych i niezależnych od czytników zawartości ekranu. Podobnie w przypadku [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Automation.AutomationProperties.NameProperty> formantów i <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> są ważne w przypadku urządzeń z technologią pomocniczą.  
  
 Zgodnie z tym najlepszym rozwiązaniem, technologie wspomagające umożliwiają identyfikowanie i [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] manipulowanie przykładowymi kontrolkami i aplikacjami.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>   
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Upewnij się, że zdarzenia programistyczne są wyzwalane przez wszystkie działania interfejsu użytkownika  
 Zgodnie z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] tym najlepszym rozwiązaniem, technologie wspomagające umożliwiają nasłuchiwanie zmian w programie i powiadamianie użytkownika o tych zmianach.  
  
<a name="User_Settings"></a>   
## <a name="user-settings"></a>Ustawienia użytkownika  
 Najlepszym rozwiązaniem w tej sekcji jest zagwarantowanie, że formanty lub aplikacje nie zastępują ustawień użytkownika.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>   
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Uwzględnij wszystkie ustawienia systemowe i nie zakłócaj działania funkcji ułatwień dostępu  
 Użytkownicy mogą używać panelu sterowania do ustawiania niektórych flag dla całego systemu; inne flagi można ustawić programowo. Tych ustawień nie należy zmieniać przez kontrolki ani aplikacje. Ponadto aplikacje muszą obsługiwać ustawienia ułatwień dostępu dla swojego systemu operacyjnego hosta.  
  
 Zgodnie z tym najlepszym rozwiązaniem użytkownicy mogą ustawiać ustawienia ułatwień dostępu i wiedzieć, że te ustawienia nie zostaną zmienione przez aplikacje.  
  
<a name="Visual_UI_Design"></a>   
## <a name="visual-ui-design"></a>Projekt wizualnego interfejsu użytkownika  
 Najlepsze rozwiązania w tej sekcji zapewniają, że kontrolki lub aplikacje wykorzystują kolor i obrazy efektywnie i mogą być używane przez technologie pomocnicze.  
  
<a name="Don_t_Hard_Code_Colors"></a>   
### <a name="dont-hard-code-colors"></a>Nie należy trwale kodować kolorów  
 Osoby, które są w kolorze niewidomym, mają słabą wizję lub używają czerni i białych ekranów, mogą nie być w stanie używać aplikacji z ustalonymi kolorami.  
  
 Zgodnie z tym najlepszym rozwiązaniem użytkownicy dostosowują kombinacje kolorów na podstawie indywidualnych potrzeb.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>   
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Obsługa duży kontrast i wszystkie atrybuty wyświetlania systemu  
 Aplikacje nie powinny zakłócać ani wyłączać wybranych przez użytkownika ustawień kontrastu systemu, kolorów ani opcji wyświetlania w całym systemie. Ustawienia dotyczące całego systemu przyjęte przez użytkownika rozszerzają dostępność aplikacji, dlatego nie powinny być wyłączone ani nieuznawane przez aplikacje. Kolor powinien być używany w odpowiedniej kombinacji pierwszego planu w tle, aby zapewnić odpowiedni kontrast. Niepowiązane kolory nie powinny być mieszane, a kolory nie powinny być odwrócone.  
  
 Wielu użytkowników wymaga określonych kombinacji o wysokim kontraście, takich jak biały tekst na czarnym tle. Rysowanie odpisano, jako czarny tekst na białym tle powoduje, że tło spada na pierwszy plan i może utrudnić odczyt dla niektórych użytkowników.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>   
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Upewnij się, że wszystkie elementy interfejsu użytkownika są prawidłowo skalowane według dowolnego ustawienia DPI  
 Upewnij się, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] że wszystkie [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] ustawienia mogą być prawidłowo skalowane. Upewnij się również, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] że elementy mieszczą się na ekranie 1024 x 768 i 120 [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)].  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Nawigacja  
 Najlepsze rozwiązania w tej sekcji zapewniają, że nawigacja została zastosowana w przypadku formantów i aplikacji.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>   
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Zapewnianie interfejsu klawiatury dla wszystkich elementów interfejsu użytkownika  
 Tabulatory, szczególnie w przypadku starannego planowania, umożliwiają użytkownikom innym sposobem nawigowania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]po stronie.  
  
 Aplikacje powinny udostępniać następujące interfejsy klawiatury:  
  
- tabulatory dla wszystkich kontrolek, z którymi użytkownik może korzystać, takich jak przyciski, linki lub pola listy  
  
- kolejność tabulacji logicznej  
  
<a name="Show_the_Keyboard_Focus"></a>   
### <a name="show-the-keyboard-focus"></a>Pokaż fokus klawiatury  
 Użytkownicy muszą wiedzieć, który obiekt ma fokus klawiatury, aby można było przewidzieć efekt ich naciśnięć klawiszy. Aby wyróżnić fokus klawiatury, Użyj kolorów, czcionek lub grafiki, takich jak prostokąty lub powiększenia. Aby audibly wyróżnić fokus klawiatury, Zmień głośność, gęstość lub tony.  
  
 Aby uniknąć pomyłek, aplikacje powinny ukrywać wszystkie wskaźniki fokusu wizualnego i przyciemniać zaznaczenia, które znajdują się w nieaktywnym systemie Windows (lub okienka).  
  
 Aplikacje powinny wykonać następujące czynności z fokusem klawiatury:  
  
- jeden element powinien zawsze mieć fokus klawiatury  
  
- fokus klawiatury powinien być widoczny i oczywisty  
  
- Wybory i/lub elementy skoncentrowane powinny być wyróżnione wizualnie  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>   
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Obsługuj standardy nawigacji i zaawansowane schematy nawigacji  
 Różne aspekty nawigacji klawiaturowej zapewniają różne sposoby nawigowania po [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]stronie użytkownika.  
  
 Aplikacje powinny udostępniać następujące interfejsy klawiatury:  
  
- klawisze skrótów i podkreślone klawisze dostępu dla wszystkich poleceń, menu i kontrolek  
  
- skróty klawiaturowe do ważnych linków  
  
- wszystkie elementy menu mają klucz dostępu; wszystkie przyciski mają klawisze skrótów, a wszystkie polecenia mają klawisz akceleratora.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>   
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Nie Zezwalaj na zakłócanie lokalizacji myszy przy użyciu klawiatury  
 Lokalizacja myszy nie powinna zakłócać nawigowania po klawiaturze. Na przykład, jeśli mysz jest ustawiona na zwrócono komunikatu, a użytkownik przechodzi przy użyciu klawiatury, kliknięcie myszą nie powinno nastąpić, chyba że zostanie zainicjowany przez użytkownika.  
  
<a name="Multimodal_Interface"></a>   
## <a name="multimodal-interface"></a>Multimodal, interfejs  
 Najlepsze rozwiązania w tej sekcji zapewniają, że [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] aplikacja zawiera alternatywy dla elementów wizualizacji.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>   
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Zapewnianie odpowiedników wybieranych przez użytkownika dla elementów innych niż tekstowe  
 Dla każdego elementu nie będącego tekstem, należy wybrać odpowiedni dla użytkownika tekst, transkrypcje lub opisy audio, takie jak tekst alternatywny, napisy lub wizualne Opinie.  
  
 Elementy inne niż tekstowe obejmują szeroką gamę [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów, takich jak obrazy, regiony mapy obrazu, animacje, applety, ramki, skrypty, przyciski graficzne, dźwięki, autonomiczne pliki audio i wideo. Elementy inne niż tekstowe są ważne, gdy zawierają informacje wizualne, mowę lub ogólne informacje o dźwięku, do których użytkownik potrzebuje dostępu, aby zrozumieć zawartość [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]programu.  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>   
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Użyj koloru, ale również Podaj alternatywy dla koloru  
 Użyj koloru, aby ulepszyć, wyróżnić lub powtórzyć powtarzanie informacji, które są wyświetlane w inny sposób, ale nie Komunikuj się z informacjami przy użyciu samego koloru. Użytkownicy, którzy są kolorami niewidomymi lub mają wyświetlacz monochromatyczny, potrzebują alternatywy do kolorowania.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>   
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Używanie standardowych interfejsów API wejścia z wywołaniami niezależnymi od urządzenia  
 Wywołania niezależne od urządzenia zapewniają równość funkcji klawiatury i myszy, a jednocześnie zapewniają technologię pomocniczą z wymaganymi informacjami [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]o programie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.Peers>
- [NumericUpDown kontrolkę niestandardową z motywem i przykładem obsługi automatyzacji interfejsu użytkownika](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))
- [Wskazówki dotyczące projektowania interfejsu użytkownika klawiatury](https://docs.microsoft.com/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
