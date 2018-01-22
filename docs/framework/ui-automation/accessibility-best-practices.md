---
title: "Najlepsze praktyki dotyczące ułatwień dostępu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 61f9ca1e8a79942b04afd8628282ceeb1e1b4b51
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="accessibility-best-practices"></a>Najlepsze praktyki dotyczące ułatwień dostępu
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Implementowanie następujących najlepszych rozwiązań w formantach lub aplikacji spowoduje zwiększenie ich dostępność dla osób, które używają [!INCLUDE[TLA#tla_at](../../../includes/tlasharptla-at-md.md)] urządzeń. Wiele z tych rozwiązań skupić się na dobrej [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] projektu. Każdy najlepsze rozwiązanie zawiera informacje implementacji dla [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] formanty lub aplikacji. W wielu przypadkach pracy, aby spełnić następujące najlepsze rozwiązania jest już uwzględniony w [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kontrolki.  
  
<a name="Programmatic_Access"></a>   
## <a name="programmatic-access"></a>Programowy dostęp  
 Dostęp programistyczny obejmuje zapewnienie, że wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy są oznaczone jako wartości właściwości są widoczne i pojawienia się odpowiednie zdarzenia. Dla standardowej [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] formantów, większość tę pracę już odbywa się za pośrednictwem <xref:System.Windows.Automation.Peers.AutomationPeer>. Formanty niestandardowe wymagają dodatkowej pracy, aby upewnić się, że dostęp programistyczny jest poprawnie zaimplementowana.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>   
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Włącz dostęp programistyczny do wszystkich elementów interfejsu użytkownika i tekstu  
 [!INCLUDE[TLA#tla_ui#initcap](../../../includes/tlasharptla-uisharpinitcap-md.md)]elementy należy włączyć dostęp programistyczny. Jeśli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jest standardem [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] sterowania, pomocy technicznej dla dostęp programistyczny znajduje się w formancie. Jeśli formant jest formant niestandardowy — formant, który został podklasą klasy z formantu wspólnego lub formant, który został podklasy formantu — a następnie możesz musi sprawdzić <xref:System.Windows.Automation.Peers.AutomationPeer> implementacji dla obszarów, które mogą wymagać modyfikacji.  
  
 Po tym najlepszym rozwiązaniem umożliwia [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] dostawcy, aby zidentyfikować i modyfikowania elementów na produkt [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>   
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Umieść na obiekty interfejsu użytkownika, ramek i stron nazwy, tytuły i opisy  
 Technologie pomocnicze, szczególnie czytników ekranu, użyj tytuł zrozumienie lokalizację ramki, obiektu lub strony w schemacie nawigacji. W związku z tym musi być bardzo opisowy tytuł. Na przykład tytuł strony sieci Web z "Microsoft strony sieci Web" są bezużyteczne, jeśli użytkownik ma przeszedł głęboko niektórych do określonego obszaru. Bardzo ważne dla użytkowników, którzy są ukryte i zależą od czytników ekranu jest opisowy tytuł. Podobnie dla [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] formantów, <xref:System.Windows.Automation.AutomationProperties.NameProperty> i <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> są ważne w przypadku [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] urządzenia.  
  
 Po tym najlepszym rozwiązaniem umożliwia [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]s, aby zidentyfikować i manipulowania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] w formantach próbki i aplikacji.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>   
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Upewnij się, że programowe zdarzenia są wyzwalane przez wszystkie działania interfejsu użytkownika  
 Po tym najlepszym rozwiązaniem umożliwia [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)]s do nasłuchiwania zmian w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] i powiadomienie użytkownika o tych zmianach.  
  
<a name="User_Settings"></a>   
## <a name="user-settings"></a>Ustawienia użytkownika  
 Najlepszym rozwiązaniem w tej sekcji gwarantuje, że kontrolki lub aplikacje nie zastępują ustawienia użytkownika.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>   
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Szanujemy wszystkie ustawienia systemowe i nie zakłóca funkcje ułatwień dostępu  
 Użytkownicy mogą używać Panelu sterowania, można ustawić niektórych flag systemowe; inne flagi można skonfigurować programowo. Te ustawienia nie powinny być zmieniane przez formanty lub aplikacji. Ponadto aplikacje muszą obsługiwać ułatwień ich systemu operacyjnego hosta.  
  
 Po tym najlepszym rozwiązaniem umożliwia użytkownikom ustawienia ułatwień dostępu i dowiedzieć się, że te ustawienia nie zostaną zmienione przez aplikacje.  
  
<a name="Visual_UI_Design"></a>   
## <a name="visual-ui-design"></a>Projekt graficzny interfejs użytkownika  
 Najlepsze rozwiązania w tej sekcji upewnij się, że formanty lub aplikacje wykorzystywać kolorów i obrazów i mogą być używane przez [!INCLUDE[TLA2#tla_at#plural](../../../includes/tla2sharptla-atsharpplural-md.md)].  
  
<a name="Don_t_Hard_Code_Colors"></a>   
### <a name="dont-hard-code-colors"></a>Nie należy trwale kodować kolorów  
 Osoby, które są rozróżniać kolorów, mieć niedowidzących lub korzystają z ekranu i czarnych może okazać się niemożliwe do używania aplikacji z wpisaną na stałe.  
  
 Po tym najlepszym rozwiązaniem umożliwia użytkownikom dostosowanie kombinacji kolorów, na podstawie indywidualnych potrzeb.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>   
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Obsługuje duży kontrast i wszystkich atrybutów wyświetlania systemu  
 Aplikacje nie powinny zakłócać lub Wyłącz ustawienia kontrastu wybrane przez użytkownika, systemowe, wybór kolorów lub innych ustawienia wyświetlania całego systemu oraz atrybuty. Ustawienia systemowe zaakceptowany przez użytkownika ułatwień dostępu aplikacji, tak, aby nie powinny być wyłączone ani pomijane przez aplikacje. Kolor stosuje się w ich poprawnej kombinacji pierwszego planu w tle do zapewnienia prawidłowego kontrastu. Nie były mieszane niepowiązanych kolorów i kolory zawartego.  
  
 W przypadku wielu użytkowników wymagają określonej kombinacji dużego kontrastu, takich jak białego tekstu na czarnym tle. Rysowanie te odwróconej, jako czarny tekst na białe tło powoduje, że tło przenikać za pośrednictwem pierwszego planu i może utrudnić odczytu dla niektórych użytkowników.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>   
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Upewnij się, wszystkie interfejsu użytkownika poprawnie skaluje przez każde ustawienie DPI  
 Upewnij się, że wszystkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] poprawnie można skalować według dowolnej [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] ustawienie. Ponadto upewnij się, że [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy mieści się w ekranu 1024 x 768 120 [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)].  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Nawigacji  
 Najlepsze rozwiązania w tej sekcji upewnij się, że nawigacji został rozwiązany dla formantów i aplikacji.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>   
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Udostępniają interfejs klawiatury dla wszystkich elementów interfejsu użytkownika  
 Tabulatory, szczególnie w przypadku precyzyjnie zaplanowane zapewniają użytkownikom innym sposobem nawigowania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Aplikacje powinny dostarczyć następujące interfejsy klawiatury:  
  
-   tabulatorów dla wszystkich kontrolek, które użytkownik może interakcyjnie, takie jak przyciski, linki lub pola listy  
  
-   kolejność tabulacji logiczne  
  
<a name="Show_the_Keyboard_Focus"></a>   
### <a name="show-the-keyboard-focus"></a>Pokaż fokus klawiatury  
 Użytkownicy muszą dowiedzieć, obiektu, który ma fokus klawiatury, tak aby ich przewidywać wpływu ich naciśnięcia klawiszy. Aby wyróżnić fokus klawiatury, użyj kolory, czcionki lub graficznych, takich jak prostokąty lub powiększenia. Aby wyróżnić komputerowi fokus klawiatury, zmień woluminu, wysokości lub odcieni jakości.  
  
 Aby uniknąć pomyłek, aplikacje powinny Ukryj wszystkie wskaźniki fokus visual i dim wybrane opcje, które znajdują się w nieaktywne systemu windows (lub okienka).  
  
 Aplikacje należy wykonać następujące czynności z fokusem klawiatury:  
  
-   jeden element powinien zawsze mieć fokus klawiatury  
  
-   fokus klawiatury powinny być widoczne i oczywiste  
  
-   Wybór i/lub elementy ukierunkowanych powinien być wizualnie zaznaczony  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>   
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Obsługa standardów nawigacji i schematów Nawigacja zaawansowane  
 Różne aspekty nawigacji klawiatury zapewniają różne sposoby, aby umożliwić użytkownikom przechodzenie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Aplikacje powinny dostarczyć następujące interfejsy klawiatury:  
  
-   klawiaturowe i klawisze dostępu podkreślony dla wszystkich poleceń menu i formantów  
  
-   skróty klawiaturowe do ważne łączy  
  
-   wszystkie elementy menu mają klucz dostępu; wszystkie przyciski mieć klawisze skrótów, wszystkie polecenia klawiszem skrótu.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>   
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Nie należy zezwalać myszy lokalizacji zakłócać nawigacji klawiatury  
 Lokalizacja myszy nie zakłóca nawigacji klawiatury. Na przykład, jeśli wskaźnik myszy zostanie umieszczony zwrócono komunikatu i użytkownik jest nawigacja przy użyciu klawiatury, kliknięcie nie powinno się zdarzyć, chyba że zainicjowanej przez użytkownika.  
  
<a name="Multimodal_Interface"></a>   
## <a name="multimodal-interface"></a>Interfejs multimodalny  
 Najlepsze rozwiązania w tej sekcji upewnij się, że aplikacji [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] obejmuje alternatywy dla elementów wizualnych.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>   
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Dostarcza odpowiedniki wybierane przez użytkownika dla elementów nietekstowych  
 Dla każdego elementu nietekstowych Podaj odpowiednika wybierane przez użytkownika tekstu, zapisy lub opisów audio, takie jak tekst alternatywny, podpisy lub wizualne.  
  
 Elementy tekstu nie obejmują szeroki zakres [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów w tym: obrazów, regiony mapy obrazu, animacji, aplety, ramki, skryptów, graficznego przycisków, dźwięki, autonomicznej plików audio i wideo. Elementy tekstu nie są ważne, które zawierają informacje, mowy lub ogólne informacje audio, że użytkownik musi mieć dostęp do Aby zrozumieć, zawartość [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>   
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Użyj koloru, ale również alternatywę dla koloru  
 Użyj koloru do zwiększenia oraz usprawnić przywołują informacje wyświetlone w inny sposób, ale nie komunikują się informacji przez tylko przy użyciu kolorów. Użytkownicy, którzy są rozróżniać kolorów lub mają monochromatyczny wyświetlania muszą alternatyw kolorów.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>   
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Użyj standardowych interfejsów API wejściowych z wywołań niezależnych od urządzenia  
 Wywołania niezależnych od urządzenia zapewnienia równości funkcji klawiaturę i mysz, zapewniając [!INCLUDE[TLA2#tla_at](../../../includes/tla2sharptla-at-md.md)] z potrzebne informacje o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.Peers>  
 [Formant niestandardowy NumericUpDown motywu i przykładowe Obsługa automatyzacji interfejsu użytkownika](http://msdn.microsoft.com/library/9aed3c10-68eb-419e-a57f-1d2af15a8253)  
 [Wskazówki dotyczące projektowania interfejsu użytkownika klawiatury](http://msdn2.microsoft.com/library/ms971323.aspx)
