---
title: Najlepsze praktyki dotyczące ułatwień dostępu
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: c6f0f31260ffae43e59703ef53dd7ef30a73320b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180297"
---
# <a name="accessibility-best-practices"></a>Najlepsze praktyki dotyczące ułatwień dostępu
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Wdrożenie następujących najlepszych rozwiązań w formanty lub aplikacji poprawi ich dostępność dla osób korzystających z urządzeń technologii ułatwień dostępu. Wiele z tych najlepszych praktyk [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] koncentruje się na dobrym projektowaniu. Każde najlepsze rozwiązanie obejmuje [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] informacje o implementacji formanty lub aplikacji. W wielu przypadkach praca w celu spełnienia tych najlepszych [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] praktyk jest już uwzględniona w formanty.  
  
<a name="Programmatic_Access"></a>
## <a name="programmatic-access"></a>Dostęp programowy  
 Dostęp programowy obejmuje zapewnienie, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] że wszystkie elementy są oznaczone etykietą, wartości właściwości są widoczne i odpowiednie zdarzenia są wywoływane. W [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] przypadku standardowych elementów sterujących <xref:System.Windows.Automation.Peers.AutomationPeer>większość tych prac jest już wykonywana za pośrednictwem . Formanty niestandardowe wymagają dodatkowej pracy, aby upewnić się, że dostęp programowy jest poprawnie zaimplementowany.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Włącz dostęp programowy do wszystkich elementów interfejsu użytkownika i tekstu  
 Elementy interfejsu użytkownika powinny włączyć dostęp programowy. Jeśli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jest to [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] standardowy formant, obsługa dostępu programowego jest uwzględniona w formancie. Jeśli formant jest formantem niestandardowym — formantem, który został sklasyfikowany z formantu wspólnego lub <xref:System.Windows.Automation.Peers.AutomationPeer> formantu, który został podklasyfikowany z control — należy sprawdzić implementację dla obszarów, które mogą wymagać modyfikacji.  
  
 Przestrzeganie tej najlepszej praktyki umożliwia dostawcom technologii ułatwieńcowych identyfikowanie i manipulowanie elementami [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]produktu.  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Umieszczanie nazw, tytułów i opisów w obiektach interfejsu użytkownika, ramkach i stronach  
 Technologie pomocnicze, zwłaszcza czytniki ekranu, używają tytułu do zrozumienia lokalizacji ramki, obiektu lub strony w schemacie nawigacyjnym. Dlatego tytuł musi być bardzo opisowy. Na przykład tytuł strony sieci Web "Microsoft Web Page" jest bezużyteczny, jeśli użytkownik przeszedł głęboko do określonego obszaru. Opisowy tytuł ma kluczowe znaczenie dla użytkowników niewidomych i zależnych od czytników ekranu. Podobnie dla [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] kontroli <xref:System.Windows.Automation.AutomationProperties.NameProperty> i <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> są ważne dla urządzeń technologii pomocniczych.  
  
 Zgodnie z tą najlepszą praktyką umożliwia technologii [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ułatwień w identyfikowaniu i manipulowaniu w przykładowych formantach i aplikacjach.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Upewnij się, że zdarzenia programowe są wyzwalane przez wszystkie działania interfejsu użytkownika  
 Zgodnie z tą najlepszą praktyką umożliwia technologii [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ułatwień wsłuchiwać się w zmiany i powiadamiać użytkownika o tych zmianach.  
  
<a name="User_Settings"></a>
## <a name="user-settings"></a>Ustawienia użytkownika  
 Najlepsze rozwiązanie w tej sekcji gwarantuje, że formanty lub aplikacje nie zastępują ustawień użytkownika.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Przestrzegaj wszystkich ustawień całego systemu i nie zakłócaj funkcji ułatwień dostępu  
 Użytkownicy mogą używać Panelu sterowania do ustawiania niektórych flag dla całego systemu; inne flagi można ustawić programowo. Te ustawienia nie powinny być zmieniane przez formanty lub aplikacje. Ponadto aplikacje muszą obsługiwać ustawienia ułatwień dostępu ich systemu operacyjnego hosta.  
  
 Zgodnie z tą najlepszą praktyką pozwala użytkownikom ustawić ustawienia ułatwień dostępu i wiedzieć, że te ustawienia nie zostaną zmienione przez aplikacje.  
  
<a name="Visual_UI_Design"></a>
## <a name="visual-ui-design"></a>Projekt interfejsu użytkownika wizualnego  
 Najważniejsze wskazówki w tej sekcji zapewniają, że formanty lub aplikacje używają kolorów i obrazów skutecznie i mogą być używane przez technologie ułatwień dostępu.  
  
<a name="Don_t_Hard_Code_Colors"></a>
### <a name="dont-hard-code-colors"></a>Nie należy trwale kodować kolorów  
 Osoby niewidome, niedowidzące lub korzystające z czarno-białego ekranu mogą nie być w stanie korzystać z aplikacji z kolorami zakodowanych na twardo.  
  
 Przestrzeganie tej najlepszej praktyki umożliwia użytkownikom dostosowanie kombinacji kolorów w zależności od indywidualnych potrzeb.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Obsługa wysokiego kontrastu i wszystkich atrybutów wyświetlania systemu  
 Aplikacje nie powinny zakłócać ani wyłączać wybranych przez użytkownika ustawień kontrastu dla całego systemu, wyboru kolorów ani innych ustawień i atrybutów wyświetlania całego systemu. Ustawienia ogólnosystemowe przyjęte przez użytkownika zwiększają dostępność aplikacji, dzięki czemu nie powinny być wyłączone ani ignorowane przez aplikacje. Kolor powinien być używany w ich poprawnej kombinacji pierwszego planu na tle, aby zapewnić odpowiedni kontrast. Niepowiązanych kolorów nie należy mieszać, a kolory nie powinny być odwracane.  
  
 Wielu użytkowników wymaga określonych kombinacji o wysokim kontraście, takich jak biały tekst na czarnym tle. Rysowanie tych odwróconych, ponieważ czarny tekst na białym tle powoduje, że tło spada na pierwszym planie i może utrudnić czytanie niektórym użytkownikom.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Upewnij się, że wszystkie interfejsy użytkownika są poprawnie skalowane przez dowolne ustawienie DPI  
 Upewnij się, że wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] mogą poprawnie skalować się za pomocą dowolnych punktów na cal (dpi). Upewnij się [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] również, że elementy mieszczą się na ekranie o rozdzielczości 1024 x 768 i 120 punktów na cal (dpi).  
  
<a name="Navigation"></a>
## <a name="navigation"></a>Nawigacja  
 Najważniejsze wskazówki w tej sekcji upewnij się, że nawigacja została skierowana do formantów i aplikacji.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Udostępnij interfejs klawiatury dla wszystkich elementów interfejsu użytkownika  
 Tabulatory, zwłaszcza gdy są starannie zaplanowane, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]dają użytkownikom inny sposób poruszania się po pliku .  
  
 Aplikacje powinny dostarczać następujące interfejsy klawiatury:  
  
- dla wszystkich formantów, z którymi użytkownik może wchodzić w interakcje, takich jak przyciski, łącza lub pola listy  
  
- logiczna kolejność kart  
  
<a name="Show_the_Keyboard_Focus"></a>
### <a name="show-the-keyboard-focus"></a>Pokaż fokus klawiatury  
 Użytkownicy muszą wiedzieć, który obiekt ma fokus klawiatury, aby mogli przewidzieć efekt ich naciśnięcia klawiszy. Aby wyróżnić fokus klawiatury, użyj kolorów, czcionek lub grafiki, takich jak prostokąty lub powiększenie. Aby wyraźnie podświetlić ostrość klawiatury, zmień głośność, wysokość lub jakość tonu.  
  
 Aby uniknąć nieporozumień, aplikacje powinny ukrywać wszystkie wskaźniki ostrości wizualnej i przyciemniać zaznaczenia, które znajdują się w nieaktywnych oknach (lub okienkach).  
  
 Aplikacje powinny wykonywać następujące czynności za pomocą fokusu klawiatury:  
  
- jeden element powinien zawsze mieć fokus klawiatury  
  
- fokus klawiatury powinien być widoczny i oczywisty  
  
- wybrane i/lub skupione elementy powinny być podświetlone wizualnie  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Obsługa standardów nawigacji i zaawansowanych schematów nawigacji  
 Różne aspekty nawigacji za pomocą klawiatury [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]zapewniają użytkownikom różne sposoby poruszania się po pliku .  
  
 Aplikacje powinny dostarczać następujące interfejsy klawiatury:  
  
- klawisze skrótów i podkreślone klawisze dostępu dla wszystkich poleceń, menu i elementów sterujących  
  
- skróty klawiaturowe do ważnych linków  
  
- wszystkie elementy menu mają klucz dostępu; wszystkie przyciski mają klawisze akceleratora, wszystkie polecenia mają klucz akceleratora.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Nie pozwól, aby lokalizacja myszy zakłócała nawigację za pomocą klawiatury  
 Lokalizacja myszy nie powinna zakłócać nawigacji za pomocą klawiatury. Na przykład jeśli mysz jest gdzieś pozycjonowana, a użytkownik porusza się za pomocą klawiatury, kliknięcie myszą nie powinno się zdarzyć, chyba że zostanie zainicjowane przez użytkownika.  
  
<a name="Multimodal_Interface"></a>
## <a name="multimodal-interface"></a>Interfejs multimodalny  
 Najlepsze rozwiązania w tej sekcji [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] upewnij się, że aplikacja zawiera alternatywy dla elementów wizualnych.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Podaj ekwiwalenty do wyboru przez użytkownika dla elementów nietekstowych  
 Dla każdego elementu nietekstowego podaj odpowiednik tekstu, transkrypcji lub opisów audio, takich jak tekst alternatywny, podpisy lub wizualne sprzężenie zwrotne.  
  
 Elementy nietekstowe obejmują [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] szeroki zakres elementów, w tym: obrazy, obszary mapy obrazów, animacje, aplety, ramki, skrypty, przyciski graficzne, dźwięki, autonomiczne pliki audio i wideo. Elementy nietekstowe są ważne, gdy zawierają informacje wizualne, mowę lub ogólne informacje dźwiękowe, do których użytkownik potrzebuje dostępu, aby zrozumieć zawartość [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]pliku .  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Użyj koloru, ale także podaj alternatywy dla koloru  
 Użyj koloru, aby poprawić, podkreślić lub powtórzyć informacje wyświetlane w inny sposób, ale nie przekazuj informacji za pomocą samego koloru. Użytkownicy, którzy są niewidomi kolorowi lub mają wyświetlacz monochromatyczny, potrzebują alternatywy dla koloru.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Używanie standardowych interfejsów API wejściowych z wywołaniami niezależnymi od urządzenia  
 Połączenia niezależne od urządzenia zapewniają równość klawiatury i myszy, zapewniając [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]jednocześnie technologię wspomagającą z potrzebnymi informacjami na temat .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.Peers>
- [Kontrolka niestandardowa NumericUpDown z przykładem obsługi automatyzacji interfejsu użytkownika](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))
- [Wskazówki dotyczące projektowania interfejsu użytkownika klawiatury](https://docs.microsoft.com/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
