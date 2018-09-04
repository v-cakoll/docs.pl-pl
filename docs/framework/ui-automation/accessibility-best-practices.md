---
title: Najlepsze praktyki dotyczące ułatwień dostępu
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 9b451e0c66d2c595826e90debfcb0fb3a2602fec
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502429"
---
# <a name="accessibility-best-practices"></a>Najlepsze praktyki dotyczące ułatwień dostępu
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Implementacja następujących najlepszych rozwiązań w kontrolkach lub aplikacji spowoduje zwiększenie ich dostępność dla osób, które używają [!INCLUDE[TLA#tla_at](../../../includes/tlasharptla-at-md.md)] urządzeń. Wiele z tych najlepszych rozwiązań skupić się na dobrze [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] projektu. Każdy najlepsze rozwiązanie zawiera informacje o implementacji dla [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] kontrolki lub aplikacji. W wielu przypadkach, pracy w celu spełnienia tych najlepszych rozwiązań jest już uwzględniony w [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kontrolki.  
  
<a name="Programmatic_Access"></a>   
## <a name="programmatic-access"></a>Dostęp programowy  
 Dostęp programowy obejmuje zapewnienie, że wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy są oznaczone jako wartości właściwości są widoczne i odpowiednie zdarzenia są wywoływane. Dla warstwy standardowej [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] formantów, większość tę pracę już odbywa się za pośrednictwem <xref:System.Windows.Automation.Peers.AutomationPeer>. Formanty niestandardowe wymagają dodatkowej pracy, aby upewnić się, że dostęp programowy jest implementowana prawidłowo.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>   
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Włącz dostęp programowy do wszystkich elementów interfejsu użytkownika i tekstu  
 [!INCLUDE[TLA#tla_ui#initcap](../../../includes/tlasharptla-uisharpinitcap-md.md)] elementy należy włączyć dostęp programistyczny. Jeśli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jest standardem [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] sterowania, pomoc techniczna dotycząca dostęp programowy znajduje się w kontrolce. Jeśli kontrolka jest formant niestandardowy — formant, który został podklasą klasy z formantu wspólnego lub formantu, który ma zostały należy do podklasy z kontroli — wówczas użytkownik musi sprawdzić <xref:System.Windows.Automation.Peers.AutomationPeer> implementacji dla obszarów, które mogą wymagać modyfikacji.  
  
 Zastosowanie tego najlepszego rozwiązania pozwala [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] dostawców, aby zidentyfikować i manipulować elementami swojego produktu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>   
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Umieszczenie nazwy, tytuły i opisy na stronach obiektów interfejsu użytkownika i ramek  
 Technologiami pomocniczymi, szczególnie czytniki zawartości ekranu, użyj tytuł, aby zrozumieć lokalizację ramki, obiektu lub strony w schemacie nawigacji. W związku z tym musi być bardzo opisowy tytuł. Na przykład tytuł strony sieci Web z "stronę internetową firmy Microsoft" jest bezcelowe, jeśli użytkownik ma głęboko przeszedł do niektórych określonego obszaru. Opisowy tytuł jest krytyczny dla użytkowników, którzy są niewidome i są zależne od czytniki zawartości ekranu. Podobnie, aby uzyskać [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] kontrolek <xref:System.Windows.Automation.AutomationProperties.NameProperty> i <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> są ważne w przypadku [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] urządzenia.  
  
 Zastosowanie tego najlepszego rozwiązania pozwala [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]s, aby zidentyfikować i manipulowania nimi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] w aplikacji i formantów próbki.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>   
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Upewnij się, że programowe zdarzenia są wyzwalane przez wszystkie działania interfejsu użytkownika  
 Zastosowanie tego najlepszego rozwiązania pozwala [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]s do nasłuchiwania pod kątem zmian w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] i powiadomienie użytkownika o tych zmianach.  
  
<a name="User_Settings"></a>   
## <a name="user-settings"></a>Ustawienia użytkownika  
 Najlepszym rozwiązaniem w tej sekcji gwarantuje, że formanty lub aplikacje nie zastępują ustawienia użytkownika.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>   
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Szanujemy wszystkie ustawienia systemowe i nie zakłóca funkcje ułatwień dostępu  
 Użytkownicy mogą używać Panelu sterowania, można ustawić niektóre flagi całego systemu; inne flagi, można ustawić programowo. Te ustawienia nie powinny być zmieniane przez formanty lub aplikacji. Ponadto aplikacje muszą obsługiwać ustawienia ułatwień dostępu systemu operacyjnego hosta.  
  
 Po tym najlepszym rozwiązaniem umożliwia użytkownikom ustawienia ułatwień dostępu i dowiedzieć się, że te ustawienia nie zostaną zmienione przez aplikacje.  
  
<a name="Visual_UI_Design"></a>   
## <a name="visual-ui-design"></a>Projekt graficzny interfejs użytkownika  
 Najlepsze rozwiązania w tej sekcji upewnij się, że kontrolki lub aplikacji efektywnego wykorzystania koloru i obrazy mogą być używane przez [!INCLUDE[TLA2#tla_at#plural](../../../includes/tla2sharptla-atsharpplural-md.md)].  
  
<a name="Don_t_Hard_Code_Colors"></a>   
### <a name="dont-hard-code-colors"></a>Nie należy trwale kodować kolorów  
 Osoby, które mają kolor niewidome, niedowidzące lub korzystasz z czarno-biały ekranu może okazać się niemożliwe aplikacji za pomocą zakodowanych kolorów.  
  
 Po tym najlepszym rozwiązaniem pozwala użytkownikom na dostosowanie kombinacji kolorów na podstawie indywidualnych potrzeb.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>   
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Obsługuje duży kontrast i wszystkich atrybutów wyświetlania systemu  
 Aplikacje nie zakłócać ani wyłączyć ustawienia kontrastu wybrane przez użytkownika, systemowe, wybór koloru lub inne ustawienia wyświetlania całego systemu i atrybutów. Ustawienia systemowe przyjęte przez użytkownika, zwiększyć dostępność aplikacji, tak, aby nie powinny być wyłączone ani ignorowane przez aplikacje. Kolor stosuje się w ich poprawnej kombinacji pierwszego planu na tle zapewnienie odpowiedniego kontrast. Kolory niepowiązane nie powinien mieszane i kolory zawartego.  
  
 Wielu użytkowników wymagają konkretnej ich kombinacji dużego kontrastu, takich jak białego tekstu na czarnym tle. Rysowanie te odwróconej, jako czarny tekst na białym tle powoduje, że tło spadu za pośrednictwem pierwszego planu i może utrudnić odczytu dla niektórych użytkowników.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>   
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Upewnij się, wszystkie interfejsu użytkownika jest skalowana poprawnie przez każde ustawienie DPI  
 Upewnij się, że wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prawidłowo skalować według dowolnej [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] ustawienie. Ponadto upewnij się, że [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów mieszczą się w ekranu 1024 x 768 120 [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)].  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Nawigacja  
 Najlepsze rozwiązania w tej sekcji upewnij się, że nawigacji został rozwiązany dla aplikacji i formantów.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>   
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Zapewnia interfejs klawiatury dla wszystkich elementów interfejsu użytkownika  
 Tabulatorów, szczególnie w przypadku, gdy starannie zaplanowana użytkownikom innym sposobem, aby przejść [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Aplikacje powinny oferują następujące interfejsy klawiatury:  
  
-   tabulatorów dla wszystkich kontrolek, które użytkownik może wchodzić w interakcje, takie jak przyciski, łączy i pola listy  
  
-   kolejność tabulacji logiczne  
  
<a name="Show_the_Keyboard_Focus"></a>   
### <a name="show-the-keyboard-focus"></a>Pokaż fokus klawiatury  
 Użytkownicy muszą znać obiektu, który ma fokus klawiatury, dzięki czemu mogą one przewidywać efekt ich naciśnięć klawiszy. Aby wyróżnić fokus klawiatury, za pomocą kolorów, czcionek grafiki, takich jak prostokąty lub powiększenia. Aby komputerowi wyróżnić fokus klawiatury, zmień woluminu, pomysłu lub odcieni jakości.  
  
 Aby uniknąć nieporozumień, aplikacje powinny ukryć wszystkie wskaźniki fokusu visual i dim wybrane opcje, które znajdują się w nieaktywne systemu windows (lub okienka).  
  
 Aplikacje należy wykonać następujące czynności z fokusem klawiatury:  
  
-   jeden element zawsze powinien mieć fokus klawiatury  
  
-   fokus klawiatury powinno być widoczne i oczywisty  
  
-   wybrane opcje i/lub elementy ukierunkowanych powinien być wizualnie wyróżniony  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>   
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Obsługa standardów nawigacji i schematy nawigacji zaawansowane  
 Różne aspekty klawiatury zapewnia różne sposoby umożliwiające użytkownikom przechodzenie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Aplikacje powinny oferują następujące interfejsy klawiatury:  
  
-   klawisze skrótów i klawisze dostępu podkreślony dla wszystkich poleceń menu i kontrolek  
  
-   skróty klawiaturowe do ważne linki  
  
-   wszystkie elementy menu mają klucz dostępu; wszystkie przyciski mieć klawiszy skrótów, wszystkie polecenia klawisza skrótu.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>   
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Nie pozwól myszy lokalizacji kolidować z klawiatury  
 Nawigowanie przy użyciu klawiatury nie zakłóca położeniu wskaźnika myszy. Aby uzyskać przykład, jeśli wskaźnik myszy zostanie umieszczony w innym, a użytkownik przechodzi za pomocą klawiatury, kliknięcie myszą nie ma się zdarzyć, chyba że zainicjowanej przez użytkownika.  
  
<a name="Multimodal_Interface"></a>   
## <a name="multimodal-interface"></a>Interfejs multimodalny  
 Najlepsze rozwiązania w tej sekcji upewnij się, że aplikacji [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] obejmuje alternatywy dla elementów wizualnych.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>   
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Podaj odpowiedniki wybierane przez użytkownika dla elementów innych niż tekst  
 Dla każdego elementu-text Obejmij odpowiednik wybierane przez użytkownika tekst, zapisy i opisów audio, takie jak tekst alternatywny, podpisów lub wizualną opinię.  
  
 Elementy tekstowe nie obejmuje szerokiej gamy [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy w tym: obrazy, regiony na mapie obrazu, animacji, aplety, ramki, skrypty, przyciski graficzny, dźwięki, autonomiczne pliki audio i wideo. Elementy inne niż tekstowe są ważne w przypadku, gdy zawierają one informacje wizualne, mowy lub ogólne informacje audio, że użytkownik musi mieć dostęp do Aby zrozumieć zawartość [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>   
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Użyj koloru, ale także dostarczają alternatywy dla koloru  
 Użyj kolor, aby zwiększyć oraz usprawnić przywołują informacje wyświetlane w inny sposób, ale nie komunikują się informacji przez tylko przy użyciu kolorów. Użytkownicy, którzy mają kolor niewidome lub mają monochromatycznym muszą alternatywy dla koloru.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>   
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Użyj standardowych interfejsów API danych wejściowych z wywołaniami niezależnych od urządzenia  
 Wywołania niezależnych od urządzenia zapewnienia równości funkcji klawiatury i myszy, przy jednoczesnym zapewnieniu [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] z wymaganych informacji o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.Peers>  
 [Formant NumericUpDown niestandardowe z motywu i przykładowe Obsługa automatyzacji interfejsu użytkownika](https://msdn.microsoft.com/library/9aed3c10-68eb-419e-a57f-1d2af15a8253)  
 [Wytyczne dotyczące projektowania interfejsu użytkownika dla klawiatury](http://msdn2.microsoft.com/library/ms971323.aspx)
