---
title: Korzystanie z automatyzacji interfejsu użytkownika do testów automatycznych
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
ms.openlocfilehash: 3fb5d1107a2dacdc4dfd2210322c312becdfd90b
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566946"
---
# <a name="using-ui-automation-for-automated-testing"></a>Korzystanie z automatyzacji interfejsu użytkownika do testów automatycznych
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym omówieniu opisano [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , jak program może być przydatny jako platforma dostępu programistycznego w scenariuszach zautomatyzowanych testów.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zapewnia ujednolicony model obiektów, który umożliwia [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] wszystkim platformom uwidocznienie złożonych i bogatych funkcji w dostępnym i łatwym w użyciu sposób.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]został opracowany jako następca usługi Microsoft Active Accessibility. Active Accessibility to istniejąca platforma służąca do udostępniania rozwiązań do udostępniania kontrolek i aplikacji. Funkcja Active Accessibility nie została zaprojektowana z myślą o automatyzacji testów, nawet jeśli została rozwinięta w ramach tej roli ze względu na bardzo podobne wymagania dotyczące ułatwień dostępu i automatyzacji. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Oprócz zapewniania bardziej zaawansowanych rozwiązań dla ułatwień dostępu, jest również przeznaczony do zapewnienia niezawodnej funkcjonalności zautomatyzowanego testowania. Na przykład usługa Active Accessibility polega na pojedynczym interfejsie, aby ujawnić informacje o interfejsie użytkownika i zebrać informacje, które są konieczne w produktach. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] oddziela dwa modele.  
  
 Zarówno dostawca, jak i klient muszą zaimplementować [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , aby był on przydatny jako narzędzie do testowania automatycznego. Dostawcy automatyzacji interfejsu użytkownika to takie aplikacje, jak program Microsoft Word, program Excel i inne aplikacje lub formanty innych firm oparte [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] na systemie operacyjnym. Klienci automatyzacji interfejsu użytkownika obejmują automatyczne Skrypty testowe i aplikacje technologii pomocniczych.  
  
> [!NOTE]
>  Zamiarem tego omówienia jest zaprezentowanie nowych i ulepszonych funkcji automatycznego testowania programu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Ten przegląd nie jest przeznaczony do udostępniania informacji o funkcjach ułatwień dostępu i nie będzie mógł uzyskać dostępu, jeśli jest to konieczne.  
  
<a name="Using_UI_Automation_During_Development"></a>   
## <a name="ui-automation-in-a-provider"></a>Automatyzacja interfejsu użytkownika w dostawcy  
 Aby program był zautomatyzowany, Deweloper aplikacji lub kontrolki musi przyjrzeć się czynnościom, które mogą wykonywać użytkownicy końcowi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] na obiekcie przy użyciu standardowej klawiatury i interakcji z myszą. [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]  
  
 Po zidentyfikowaniu tych kluczowych akcji należy zaimplementować odpowiednie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wzorce kontroli (czyli wzorce kontrolki, które duplikują funkcje i zachowanie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementu). Na przykład interakcja użytkownika z kontrolką pola kombi (na przykład okna dialogowego uruchamiania) zwykle polega na rozwijaniu i zwijaniu pola kombi, aby ukryć lub wyświetlić listę elementów, wybierając element z tej listy lub dodając nową wartość za pomocą wprowadzania z klawiatury.  
  
> [!NOTE]
>  W przypadku innych modeli ułatwień dostępu deweloperzy muszą zbierać informacje bezpośrednio z poszczególnych przycisków, menu lub innych kontrolek. Niestety, każdy typ kontrolki zawiera dziesiątki drobnych różnic. Innymi słowy, mimo że dziesięć odmian przycisku może działać w ten sam sposób i wykonać tę samą funkcję, muszą one być traktowane jako unikatowe formanty. Nie ma możliwości, aby wiedzieć, że te kontrolki są funkcjonalnie równoważne. Wzorce formantów zostały opracowane w celu reprezentowania tych typowych zachowań kontroli. Aby uzyskać więcej informacji, zobacz [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="Implementing_UI_Automation"></a>   
### <a name="implementing-ui-automation"></a>Implementowanie automatyzacji interfejsu użytkownika  
 Jak wspomniano wcześniej, bez jednolitego modelu dostarczonego [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]przez, narzędzia testowe i deweloperzy muszą znać informacje specyficzne dla platformy, aby uwidocznić właściwości i zachowania kontroli w tej strukturze. Ponieważ w systemach operacyjnych Windows może istnieć kilka różnych struktur interfejsu użytkownika, takich jak [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]i Windows Presentation Foundation (WPF), może to być zadanie zniechęcające do testowania wielu aplikacji za pomocą kontrolki, które wyglądają podobnie. Na przykład poniższa tabela zawiera opis nazw właściwości specyficznych dla platformy wymaganych do pobrania nazwy (lub tekstu) skojarzonej z kontrolką przycisku i pokazuje właściwość o pojedynczej równoważnej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
|Typ formantu automatyzacji interfejsu użytkownika|Struktura interfejsu użytkownika|Właściwość specyficzne dla platformy|Właściwość automatyzacji interfejsu użytkownika|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Przycisk|Windows Presentation Foundation|Zawartość|NameProperty|  
|Przycisk|Win32|Podpis|NameProperty|  
|Obraz|HTML|+|NameProperty|  
  
 Dostawcy automatyzacji interfejsu użytkownika są odpowiedzialni za mapowanie właściwości charakterystycznych dla struktury ich formantów na równoważne [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości.  
  
 Informacje dotyczące implementowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w dostawcy można znaleźć w temacie [dostawcy automatyzacji interfejsu użytkownika dla kodu zarządzanego](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md). Informacje na temat implementowania wzorców formantów są dostępne w wzorcach [kontrolek Automatyzacja interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) i we [wzorcu tekstu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-text-pattern.md).  
  
<a name="Testing_with_UI_Automation"></a>   
## <a name="ui-automation-in-a-client"></a>Automatyzacja interfejsu użytkownika w kliencie  
 Celem wielu zautomatyzowanych narzędzi testowych i scenariuszy jest spójne i powtarzalne manipulowanie interfejsem użytkownika. Może to dotyczyć testów jednostkowych specyficznych dla kontroli przez nagrywanie i odtwarzanie skryptów testowych, które iterją przez szereg działań ogólnych w grupie formantów.  
  
 Komplikacja, która wynika z zautomatyzowanych aplikacji, jest trudna do synchronizowania testów z dynamicznym elementem docelowym. Na przykład kontrolka pole listy, taka jak zawarta w Menedżerze zadań systemu Windows, wyświetla listę aktualnie uruchomionych aplikacji. Ponieważ elementy w polu listy są aktualizowane dynamicznie poza kontrolą aplikacji testowej, próba powtórzenia wyboru określonego elementu w polu listy z jakąkolwiek spójnością jest niemożliwe. Podobne problemy mogą również wystąpić podczas próby powtórzenia prostych zmian fokusu w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elemencie, który jest poza kontrolą aplikacji testowej.  
  
<a name="Programmatic_Access"></a>   
### <a name="programmatic-access"></a>Dostęp programistyczny  
 Dostęp programistyczny umożliwia imitację, poprzez kod, wszelką interakcję i środowisko udostępniane przez tradycyjne mysz i wprowadzanie z klawiatury. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umożliwia dostęp programistyczny przez pięć składników:  
  
- Drzewo ułatwia nawigację przez strukturę [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewo jest kompilowane z kolekcji. Aby uzyskać więcej informacji, zobacz [drzewo automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
  
- Elementy automatyzacji to poszczególne składniki w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Mogą one być często bardziej szczegółowe niż Właściwość hWnd. Aby uzyskać więcej informacji, zobacz [typy formantów automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
- Właściwości automatyzacji zawierają określone informacje o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementach. Aby uzyskać więcej informacji, zobacz [Omówienie właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
- Wzorce kontrolki definiują konkretny aspekt funkcjonalności formantu; mogą one składać się z informacji o właściwości, metodzie, zdarzeniu i strukturze. Aby uzyskać więcej informacji, zobacz [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
- Zdarzenia automatyzacji udostępniają powiadomienia i informacje o zdarzeniach. Aby uzyskać więcej informacji, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Key_properties_critical_to_test_automation"></a>   
### <a name="key-properties-for-test-automation"></a>Właściwości klucza dla automatyzacji testów  
 Możliwość jednoznacznego identyfikowania i późniejszego lokalizowania kontroli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] w ramach programu stanowi podstawę do działania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]zautomatyzowanych aplikacji testowych. Klienci i dostawcy [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] mogą korzystać z kilku właściwości.  
  
#### <a name="automationid"></a>AutomationID  
 Jednoznacznie identyfikuje element automatyzacji na podstawie jego elementów równorzędnych. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>nie jest zlokalizowany, w przeciwieństwie do właściwości <xref:System.Windows.Automation.AutomationElement.NameProperty> , takiej jak zwykle jest lokalizowany, jeśli produkt zostanie wysłany w wielu językach. Zobacz [Używanie właściwości AutomationID](../../../docs/framework/ui-automation/use-the-automationid-property.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>nie gwarantuje unikatowej tożsamości w całym drzewie automatyzacji. Na przykład aplikacja może zawierać formant menu z wieloma elementami menu najwyższego poziomu, które z kolei mają wiele elementów menu podrzędnych. Te elementy menu pomocniczego mogą być identyfikowane przez schemat generyczny, taki jak "Item1 —, Item 2, Item3 — itp.", co umożliwia duplikowanie identyfikatorów dla elementów podrzędnych w elementach menu najwyższego poziomu.  
  
#### <a name="controltype"></a>ControlType  
 Identyfikuje typ formantu reprezentowanego przez element automatyzacji. Istotne informacje można wywnioskować na podstawie wiedzy o typie formantu. Zobacz [typy formantów automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>NameProperty  
 Jest to ciąg tekstowy, który identyfikuje lub objaśnia formant. <xref:System.Windows.Automation.AutomationElement.NameProperty>powinien być używany z zachowaniem ostrożności, ponieważ może być zlokalizowany. Zobacz [Omówienie właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="Steps_Required_To_Automate_the_UI_in_a_Test_Application"></a>   
### <a name="implementing-ui-automation-in-a-test-application"></a>Implementowanie automatyzacji interfejsu użytkownika w aplikacji testowej  
  
|||  
|-|-|  
|Dodaj odwołania automatyzacji interfejsu użytkownika.|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Biblioteka DLL niezbędna dla klientów automatyzacji interfejsu użytkownika jest wymieniona tutaj.<br /><br /> -UIAutomationClient. dll zapewnia dostęp do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] interfejsów API po stronie klienta.<br />-UIAutomationClientSideProvider. dll zapewnia możliwość automatyzowania [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrolek. Zobacz [Obsługa automatyzacji interfejsu użytkownika dla standardowych kontrolek](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes. dll zapewnia dostęp do określonych typów zdefiniowanych w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation> Dodaj przestrzeń nazw.|Ta przestrzeń nazw zawiera wszystkich klientów automatyzacji interfejsu użytkownika, które muszą korzystać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] z funkcji obsługi tekstu poza tekstem.|  
|<xref:System.Windows.Automation.Text> Dodaj przestrzeń nazw.|Ta przestrzeń nazw zawiera wszystko, co klienci automatyzacji interfejsu użytkownika muszą korzystać z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] możliwości obsługi tekstu.|  
|Znajdowanie formantów interesujących|Skrypty testów automatycznych lokalizują elementy automatyzacji interfejsu użytkownika, które reprezentują kontrolki interesujące w drzewie automatyzacji.<br /><br /> Istnieje wiele sposobów uzyskiwania elementów automatyzacji interfejsu użytkownika z kodem.<br /><br /> -Query [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Automation.Condition> instrukcji using. Zwykle jest to miejsce, w którym <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> jest używany niezależny od języka. **Uwaga:**  Można uzyskać za pomocą narzędzia, takiego jak program sprawdzając. exe, który może [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] itemize właściwości formantu. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> <br /><br /> — Użyj <xref:System.Windows.Automation.TreeWalker> klasy, aby przechodzenie do całego [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa lub jego podzbioru.<br />-Śledź fokus.<br />— Użyj wartości hWnd formantu.<br />— Użyj lokalizacji ekranu, na przykład lokalizacji kursora myszy.<br /><br /> Zobacz [Uzyskiwanie elementów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)|  
|Uzyskiwanie wzorców kontroli|Wzorce kontroli uwidaczniają typowe zachowania dla kontrolek podobnych funkcjonalnie.<br /><br /> Po znalezieniu kontrolek, które wymagają testowania, skrypty testów automatycznych uzyskują wzorce kontroli interesujące z tych elementów automatyzacji interfejsu użytkownika. Na przykład <xref:System.Windows.Automation.InvokePattern> wzorzec kontrolki dla typowych funkcji przycisków <xref:System.Windows.Automation.WindowPattern> lub wzorzec kontrolki dla funkcji okna.<br /><br /> Zobacz [Omówienie wzorców kontrolek automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).|  
|Automatyzacja interfejsu użytkownika|Skrypty testów automatycznych mogą teraz kontrolować dowolne [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] zainteresowania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] z platformy przy użyciu informacji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] i funkcji udostępnianych przez wzorce kontrolek.|  
  
<a name="Supporting_tools"></a>   
## <a name="related-tools-and-technologies"></a>Powiązane narzędzia i technologie  
 Istnieje kilka powiązanych narzędzi i technologii, które obsługują automatyczne testowanie przy użyciu programu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
- Inspekcja. exe jest aplikacją graficznego interfejsu użytkownika (GUI), za pomocą której można [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zbierać informacje zarówno na potrzeby tworzenia dostawcy, jak i debugowania. W Windows SDK znajduje się plik Inspekcja. exe.  
  
- MSAABridge udostępnia [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacje dla klientów usługi Active Accessibility. Głównym celem mostkowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] funkcji Active Accessibility jest umożliwienie istniejącym aktywnym klientom dostępności możliwości współdziałania z dowolnymi wdrożonymi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]platformami.  
  
<a name="Security"></a>   
## <a name="security"></a>Zabezpieczenia  
 Informacje o zabezpieczeniach znajdują się w temacie [Omówienie zabezpieczeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe założenia automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/index.md)
