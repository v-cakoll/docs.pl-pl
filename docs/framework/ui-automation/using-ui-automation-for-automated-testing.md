---
title: Korzystanie z automatyzacji interfejsu użytkownika do testów automatycznych
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
ms.openlocfilehash: 59c4076712823faa1602448653680a31b8cd8c69
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741068"
---
# <a name="using-ui-automation-for-automated-testing"></a>Korzystanie z automatyzacji interfejsu użytkownika do testów automatycznych
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym omówieniu opisano, jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] może być przydatna jako struktura dostępu programistycznego w scenariuszach zautomatyzowanych testów.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zapewnia ujednolicony model obiektów, który umożliwia wszystkim [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] platformom uwidocznienie złożonych i bogatych funkcji w dostępnym i łatwym w użyciu sposób.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] został utworzony jako następca usługi Microsoft Active Accessibility. Active Accessibility to istniejąca platforma służąca do udostępniania rozwiązań do udostępniania kontrolek i aplikacji. Funkcja Active Accessibility nie została zaprojektowana z myślą o automatyzacji testów, nawet jeśli została rozwinięta w ramach tej roli ze względu na bardzo podobne wymagania dotyczące ułatwień dostępu i automatyzacji. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], oprócz zapewniania bardziej zaawansowanych rozwiązań dla ułatwień dostępu, został również zaprojektowany specjalnie w celu zapewnienia niezawodnej funkcjonalności zautomatyzowanego testowania. Na przykład usługa Active Accessibility polega na pojedynczym interfejsie, aby ujawnić informacje o interfejsie użytkownika i zebrać informacje, które są konieczne w produktach. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] oddziela dwa modele.  
  
 Zarówno dostawca, jak i klient muszą zaimplementować [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], aby był przydatny jako narzędzie do testowania automatycznego. Dostawcy automatyzacji interfejsu użytkownika to takie aplikacje, jak program Microsoft Word, program Excel i inne aplikacje lub formanty innych firm oparte na systemie operacyjnym Microsoft Windows. Klienci automatyzacji interfejsu użytkownika obejmują automatyczne Skrypty testowe i aplikacje technologii pomocniczych.  
  
> [!NOTE]
> Zamiarem tego omówienia jest zaprezentowanie nowych i ulepszonych funkcji automatycznego testowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Ten przegląd nie jest przeznaczony do udostępniania informacji o funkcjach ułatwień dostępu i nie będzie mógł uzyskać dostępu, jeśli jest to konieczne.  
  
## <a name="ui-automation-in-a-provider"></a>Automatyzacja interfejsu użytkownika w dostawcy  
 Aby [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] być zautomatyzowane, Deweloper aplikacji lub kontrolki musi sprawdzić, jakie akcje może wykonać użytkownik końcowy na obiekcie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] przy użyciu standardowej klawiatury i interakcji z myszą.  
  
 Po zidentyfikowaniu tych kluczowych akcji, odpowiednie wzorce kontroli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (czyli wzorce kontrolki, które duplikują funkcjonalność i zachowanie elementu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]), powinny być zaimplementowane na formancie. Na przykład interakcja użytkownika z kontrolką pola kombi (na przykład okna dialogowego uruchamiania) zwykle polega na rozwijaniu i zwijaniu pola kombi, aby ukryć lub wyświetlić listę elementów, wybierając element z tej listy lub dodając nową wartość za pomocą wprowadzania z klawiatury.  
  
> [!NOTE]
> W przypadku innych modeli ułatwień dostępu deweloperzy muszą zbierać informacje bezpośrednio z poszczególnych przycisków, menu lub innych kontrolek. Niestety, każdy typ kontrolki zawiera dziesiątki drobnych różnic. Innymi słowy, mimo że dziesięć odmian przycisku może działać w ten sam sposób i wykonać tę samą funkcję, muszą one być traktowane jako unikatowe formanty. Nie ma możliwości, aby wiedzieć, że te kontrolki są funkcjonalnie równoważne. Wzorce formantów zostały opracowane w celu reprezentowania tych typowych zachowań kontroli. Aby uzyskać więcej informacji, zobacz [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md).  
  
### <a name="implementing-ui-automation"></a>Implementowanie automatyzacji interfejsu użytkownika  
 Jak wspomniano wcześniej, bez jednolitego modelu zapewnianego przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], narzędzia testowe i deweloperzy muszą znać informacje specyficzne dla platformy, aby uwidocznić właściwości i zachowania kontroli w tej strukturze. Ponieważ w systemach operacyjnych Windows istnieje kilka różnych struktur interfejsu użytkownika, w tym Win32, [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]i Windows Presentation Foundation (WPF), może to być zadanie zniechęcające do testowania wielu aplikacji z kontrolkami, które wyglądają podobnie. Na przykład poniższa tabela zawiera opis nazw właściwości specyficznych dla platformy wymaganych do pobrania nazwy (lub tekstu) skojarzonej z kontrolką przycisku i pokazuje właściwość o pojedynczej równoważnej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|Typ formantu automatyzacji interfejsu użytkownika|Struktura interfejsu użytkownika|Właściwość specyficzne dla platformy|Właściwość automatyzacji interfejsu użytkownika|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Przycisk|Windows Presentation Foundation|Zawartość|NameProperty|  
|Przycisk|Win32|Podpis|NameProperty|  
|Obraz|HTML|+|NameProperty|  
  
 Dostawcy automatyzacji interfejsu użytkownika są odpowiedzialni za mapowanie właściwości charakterystycznych dla struktury ich formantów na równoważne właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 Informacje dotyczące implementowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w dostawcy można znaleźć w temacie [dostawcy automatyzacji interfejsu użytkownika dla kodu zarządzanego](ui-automation-providers-for-managed-code.md). Informacje na temat implementowania wzorców formantów są dostępne w wzorcach [kontrolek Automatyzacja interfejsu użytkownika](ui-automation-control-patterns.md) i we [wzorcu tekstu automatyzacji interfejsu użytkownika](ui-automation-text-pattern.md).  
  
## <a name="ui-automation-in-a-client"></a>Automatyzacja interfejsu użytkownika w kliencie  
 Celem wielu zautomatyzowanych narzędzi testowych i scenariuszy jest spójne i powtarzalne manipulowanie interfejsem użytkownika. Może to dotyczyć testów jednostkowych specyficznych dla kontroli przez nagrywanie i odtwarzanie skryptów testowych, które iterją przez szereg działań ogólnych w grupie formantów.  
  
 Komplikacja, która wynika z zautomatyzowanych aplikacji, jest trudna do synchronizowania testów z dynamicznym elementem docelowym. Na przykład kontrolka pole listy, taka jak zawarta w Menedżerze zadań systemu Windows, wyświetla listę aktualnie uruchomionych aplikacji. Ponieważ elementy w polu listy są aktualizowane dynamicznie poza kontrolą aplikacji testowej, próba powtórzenia wyboru określonego elementu w polu listy z jakąkolwiek spójnością jest niemożliwe. Podobne problemy mogą również wystąpić podczas próby powtórzenia prostych zmian fokusu w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], który jest poza kontrolą aplikacji testowej.  
  
### <a name="programmatic-access"></a>Dostęp programowy  
 Dostęp programistyczny umożliwia imitację, poprzez kod, wszelką interakcję i środowisko udostępniane przez tradycyjne mysz i wprowadzanie z klawiatury. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] umożliwia programistyczny dostęp za poorednictwem pięciu składników:  
  
- Drzewo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ułatwia nawigację przez strukturę [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Drzewo jest kompilowane z kolekcji. Aby uzyskać więcej informacji, zobacz [drzewo automatyzacji interfejsu użytkownika — omówienie](ui-automation-tree-overview.md)  
  
- Elementy automatyzacji są poszczególnymi składnikami w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Mogą one być często bardziej szczegółowe niż Właściwość hWnd. Aby uzyskać więcej informacji, zobacz [typy formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md).  
  
- Właściwości automatyzacji zawierają określone informacje o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementach. Aby uzyskać więcej informacji, zobacz [Omówienie właściwości automatyzacji interfejsu użytkownika](ui-automation-properties-overview.md).  
  
- Wzorce kontrolki definiują konkretny aspekt funkcjonalności formantu; mogą one składać się z informacji o właściwości, metodzie, zdarzeniu i strukturze. Aby uzyskać więcej informacji, zobacz [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md).  
  
- Zdarzenia automatyzacji udostępniają powiadomienia i informacje o zdarzeniach. Aby uzyskać więcej informacji, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
### <a name="key-properties-for-test-automation"></a>Właściwości klucza dla automatyzacji testów  
 Możliwość jednoznacznego identyfikowania i późniejszego lokalizowania kontroli w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] stanowi podstawę dla zautomatyzowanych aplikacji testowych, które będą działać na tym [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Istnieje kilka [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] właściwości używanych przez klientów i dostawców, które pomagają w tym.  
  
#### <a name="automationid"></a>AutomationID  
 Jednoznacznie identyfikuje element automatyzacji na podstawie jego elementów równorzędnych. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> nie jest zlokalizowana, w przeciwieństwie do właściwości, takiej jak <xref:System.Windows.Automation.AutomationElement.NameProperty>, która jest zazwyczaj lokalizowana, jeśli produkt zostanie wysłany w wielu językach. Zobacz [Używanie właściwości AutomationID](use-the-automationid-property.md).  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> nie gwarantuje unikatowej tożsamości w całym drzewie automatyzacji. Na przykład aplikacja może zawierać formant menu z wieloma elementami menu najwyższego poziomu, które z kolei mają wiele elementów menu podrzędnych. Te elementy menu pomocniczego mogą być identyfikowane przez schemat generyczny, taki jak "Item1 —, Item 2, Item3 — itp.", co umożliwia duplikowanie identyfikatorów dla elementów podrzędnych w elementach menu najwyższego poziomu.  
  
#### <a name="controltype"></a>ControlType  
 Identyfikuje typ formantu reprezentowanego przez element automatyzacji. Istotne informacje można wywnioskować na podstawie wiedzy o typie formantu. Zobacz [typy formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>NameProperty  
 Jest to ciąg tekstowy, który identyfikuje lub objaśnia formant. <xref:System.Windows.Automation.AutomationElement.NameProperty> należy używać ostrożnie, ponieważ może być zlokalizowany. Zobacz [Omówienie właściwości automatyzacji interfejsu użytkownika](ui-automation-properties-overview.md).  
  
### <a name="implementing-ui-automation-in-a-test-application"></a>Implementowanie automatyzacji interfejsu użytkownika w aplikacji testowej  
  
|||  
|-|-|  
|Dodaj odwołania automatyzacji interfejsu użytkownika.|Biblioteka DLL [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wymagana dla klientów automatyzacji interfejsu użytkownika jest wymieniona tutaj.<br /><br /> -UIAutomationClient. dll zapewnia dostęp do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] interfejsów API po stronie klienta.<br />-UIAutomationClientSideProvider. dll zapewnia możliwość automatyzowania formantów Win32. Zobacz [Obsługa automatyzacji interfejsu użytkownika dla standardowych kontrolek](ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes. dll zapewnia dostęp do określonych typów zdefiniowanych w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|Dodaj przestrzeń nazw <xref:System.Windows.Automation>.|Ta przestrzeń nazw zawiera wszystkich klientów automatyzacji interfejsu użytkownika, które muszą korzystać z możliwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] z wyjątkiem obsługi tekstu.|  
|Dodaj przestrzeń nazw <xref:System.Windows.Automation.Text>.|Ta przestrzeń nazw zawiera wszystko, co klienci automatyzacji interfejsu użytkownika muszą używać funkcji obsługi tekstu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|Znajdowanie formantów interesujących|Skrypty testów automatycznych lokalizują elementy automatyzacji interfejsu użytkownika, które reprezentują kontrolki interesujące w drzewie automatyzacji.<br /><br /> Istnieje wiele sposobów uzyskiwania elementów automatyzacji interfejsu użytkownika z kodem.<br /><br /> -Zbadaj [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] przy użyciu instrukcji <xref:System.Windows.Automation.Condition>. Zwykle jest to miejsce, w którym jest używany <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> neutralny od języka. **Uwaga:**  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> można uzyskać za pomocą narzędzia, takiego jak program sprawdzając. exe, który może itemize [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości formantu. <br /><br /> — Użyj klasy <xref:System.Windows.Automation.TreeWalker>, aby przechodzenie do całego drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] lub jego podzbioru.<br />-Śledź fokus.<br />— Użyj wartości hWnd formantu.<br />— Użyj lokalizacji ekranu, na przykład lokalizacji kursora myszy.<br /><br /> Zobacz [Uzyskiwanie elementów automatyzacji interfejsu użytkownika](obtaining-ui-automation-elements.md)|  
|Uzyskiwanie wzorców kontroli|Wzorce kontroli uwidaczniają typowe zachowania dla kontrolek podobnych funkcjonalnie.<br /><br /> Po znalezieniu kontrolek, które wymagają testowania, skrypty testów automatycznych uzyskują wzorce kontroli interesujące z tych elementów automatyzacji interfejsu użytkownika. Na przykład <xref:System.Windows.Automation.InvokePattern> wzorzec kontroli dla typowych funkcji przycisków lub wzorzec kontrolki <xref:System.Windows.Automation.WindowPattern> dla funkcji okna.<br /><br /> Zobacz [Omówienie wzorców kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-patterns-overview.md).|  
|Automatyzacja interfejsu użytkownika|Skrypty testów automatycznych mogą teraz kontrolować wszelkie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] zainteresowania z poziomu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Framework przy użyciu informacji i funkcji uwidocznionych przez wzorce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
  
## <a name="related-tools-and-technologies"></a>Powiązane narzędzia i technologie  
 Istnieje kilka powiązanych narzędzi i technologii, które obsługują automatyczne testowanie przy użyciu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
- Program bada. exe to graficzny interfejs użytkownika (GUI), którego można użyć do zebrania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacji na temat tworzenia i debugowania aplikacji zarówno dla dostawcy, jak i dla klienta. W Windows SDK znajduje się plik Inspekcja. exe.  
  
- MSAABridge udostępnia informacje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do klientów usługi Active Accessibility. Głównym celem mostkowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do aktywnego ułatwienia dostępu jest umożliwienie istniejącym aktywnym klientom dostępności możliwości współdziałania z dowolnymi platformami, które mają zaimplementowany [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
## <a name="security"></a>Zabezpieczenia  
 Informacje o zabezpieczeniach znajdują się w temacie [Omówienie zabezpieczeń automatyzacji interfejsu użytkownika](ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe założenia automatyzacji interfejsu użytkownika](index.md)
