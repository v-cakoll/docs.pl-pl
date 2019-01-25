---
title: Korzystanie z automatyzacji interfejsu użytkownika do testów automatycznych
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 023c85591ba484e0b8f97a8ef71a4f65a2f05ffb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691791"
---
# <a name="using-ui-automation-for-automated-testing"></a>Korzystanie z automatyzacji interfejsu użytkownika do testów automatycznych
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten przegląd zawiera opis sposobu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] może być przydatne jako umożliwiająca dostęp programowy w zautomatyzowane testowania scenariuszy.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] udostępnia model obiektu ujednolicone, który umożliwia obsługę [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] struktury do udostępnienia złożone i zaawansowane funkcje w sposób dostępny i łatwy sposób automatycznego.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] został opracowany jako następca [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] istniejącej struktury służy do stanowią rozwiązanie dla udostępnienie aplikacji i formantów. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] nie zaprojektowano pod kątem automatyzacji testów, należy pamiętać, mimo że przekształciła się w tej roli z powodu bardzo podobne wymagania dotyczące ułatwień dostępu i automatyzacji. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], oprócz zapewniania rozwiązań bardziej precyzyjnych ułatwień dostępu, jest również specjalnie przeznaczona do zapewnia niezawodne funkcje potrzeby testowania automatycznego. Na przykład [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] opiera się na jeden interfejs do udostępnienia informacji na temat interfejsu użytkownika i zbierać informacje wymagane przez na produktów. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] oddziela dwa modele.  
  
 Dostawcy i klienta, które są wymagane do zaimplementowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] się przydatne jako narzędzia do testów automatycznych. Dostawcy automatyzacji interfejsu użytkownika są aplikacje, takie jak Microsoft Word, Excel, i inne aplikacje innych firm lub formanty w oparciu [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] systemu operacyjnego. Klienci automatyzacji interfejsu użytkownika obejmują skryptów zautomatyzowanych testów i technologii pomocniczej aplikacji.  
  
> [!NOTE]
>  W tym omówieniu zamierzeniu prezentować nowe i ulepszone automatycznego testowania możliwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. W tym omówieniu nie jest przeznaczona do zapewnienia informacji na temat dostępności funkcji i nie zajmie się ułatwień dostępu inne niż w przypadku, gdy to konieczne.  
  
<a name="Using_UI_Automation_During_Development"></a>   
## <a name="ui-automation-in-a-provider"></a>Automatyzacja interfejsu użytkownika w dostawcy  
 Aby uzyskać [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] do automatyzacji, Deweloper aplikacji lub kontrolki musi przeanalizować, co można wykonać akcje, które użytkownik końcowy na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] przy użyciu standardowych interakcji klawiatury i myszy.  
  
 Po tych klucz akcje zostały określone w odpowiednich [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorców (czyli wzorce kontrolki towarzyszących do dublowania funkcji i zachowania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementu) powinny być zrealizowane w formancie. Na przykład interakcji użytkownika z kontrolki pola kombi (na przykład Uruchom okno dialogowe) zwykle obejmuje rozwijanie i zwijanie pola kombi, aby ukryć lub wyświetlić listę elementów, wybranie elementu z listy lub dodanie nowej wartości przy użyciu danych wprowadzonych z klawiatury.  
  
> [!NOTE]
>  Z innymi modelami ułatwień dostępu deweloperów należy zebrać informacje bezpośrednio z poszczególnych przyciski, menu i innych kontrolek. Niestety każdy typ kontrolki jest dostępna w wielu niewielkich zmian. Innymi słowy mimo że dziesięć, iż różne wersje przycisk mogą wszystkie działają tak samo pełnią taką samą funkcję, ich muszą wszystkie być traktowane jako unikatowymi formantami. Nie istnieje żaden sposób, aby dowiedzieć się, że te formanty są funkcjonalnie równoważne. Wzorce kontrolek zostały opracowane do reprezentowania tych wspólnych zachowań kontroli. Aby uzyskać więcej informacji, zobacz [Przegląd wzorców kontrolki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="Implementing_UI_Automation"></a>   
### <a name="implementing-ui-automation"></a>Implementowanie automatyzacji interfejsu użytkownika  
 Jak wspomniano wcześniej, bez ujednoliconego modelu, dostarczone przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], narzędzi do testowania i deweloperów musi wiedzieć informacje dotyczące framework, aby udostępnić właściwości i zachowania formantów w tej struktury. Ponieważ może istnieć kilka różnych platform tworzenia interfejsu użytkownika obecne w dowolnym momencie pojedynczy systemów operacyjnych Windows, w tym [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], a Windows Presentation Foundation (WPF), może być czasochłonnym zadaniem do testowania wielu aplikacji formanty, które wydają się podobne. Na przykład poniższa tabela przedstawia nazwy właściwości określonej platformy, wymagany do pobrania nazwy (lub tekst), skojarzony formant przycisku i zawiera pojedynczy równoważne [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości.  
  
|Automatyzacja interfejsu użytkownika — typ formantu|Struktury interfejsu użytkownika|Framework określoną właściwość.|Właściwości automatyzacji interfejsu użytkownika|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Przycisk|Windows Presentation Foundation|Zawartość|NameProperty|  
|Przycisk|Win32|Podpis|NameProperty|  
|Obraz|HTML|ALT|NameProperty|  
  
 Dostawcy automatyzacji interfejsu użytkownika jest odpowiedzialny za Mapowanie właściwości specyficzne dla framework ich formantów do równowartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości.  
  
 Informacji dotyczących implementowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dostawcy można znaleźć w folderze [dostawcy automatyzacji interfejsu użytkownika dla zarządzanego kodu](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md). Informacji dotyczących implementowania wzorców kontrolek znajduje się w temacie [wzorce kontrolek automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) i [wzorzec tekstu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-text-pattern.md).  
  
<a name="Testing_with_UI_Automation"></a>   
## <a name="ui-automation-in-a-client"></a>Automatyzacja interfejsu użytkownika w kliencie WPF  
 Celem wiele scenariuszy i narzędzia do testów automatycznych jest manipulowanie spójnego i powtarzalnego interfejsu użytkownika. Może to obejmować określonych kontrolek poprzez nagrywanie i odtwarzanie testów skryptów, które przechodzą przez szereg ogólnego akcje na grupy formantów testów jednostkowych.  
  
 Kompilacji, wynikającej z automatycznych aplikacji jest trudności synchronizowanie testu z obiektem docelowym dynamicznych. Na przykład pole listy, takich jak zawartą w Menedżerze zadań Windows, który wyświetla listę aktualnie uruchomionych aplikacji. Ponieważ elementy w polu listy są aktualizowane dynamicznie poza kontrolą aplikacji testowej, podejmuje próbę powtórzenia zaznaczenie konkretny element w polu listy, z dowolnym spójności jest niemożliwe. Podobne problemy również mogą wystąpić, gdy podejmuje próbę powtórzenia zmianie fokusu proste w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jest poza kontrolą aplikacji testowej.  
  
<a name="Programmatic_Access"></a>   
### <a name="programmatic-access"></a>Dostęp programowy  
 Dostęp programowy umożliwia naśladowania przy użyciu kodu, dowolnego interakcji i środowisko udostępnianych przez tradycyjną mysz i klawiatura, danych wejściowych. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Umożliwia dostęp programowy za pośrednictwem pięć składników:  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewa ułatwia nawigację struktury [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Drzewo została stworzona z kolekcji hWnd firmy. Aby uzyskać więcej informacji, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
  
-   Po elementach automatyzacji są poszczególne składniki w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Mogą one często bardziej szczegółowe niż hWnd. Aby uzyskać więcej informacji, zobacz [Przegląd typów kontroli automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
-   Właściwości automatyzacji zawierają szczegółowe informacje o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów. Aby uzyskać więcej informacji, zobacz [Przegląd właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
-   Wzorce kontrolki zdefiniować danego aspekt funkcjonalności formantu. może składać się z właściwości, metody, zdarzenia i informacje o strukturze. Aby uzyskać więcej informacji, zobacz [Przegląd wzorców kontrolki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
-   Właściwości zdarzeń automatyzacji zapewniają powiadomienia o zdarzeniach i informacji. Aby uzyskać więcej informacji, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Key_properties_critical_to_test_automation"></a>   
### <a name="key-properties-for-test-automation"></a>Właściwości klucza do automatyzacji testów  
 Możliwość jednoznacznie zidentyfikować i następnie Znajdź wszystkie kontrolki [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] stanowi podstawę dla testów automatycznych aplikacji do działania na tym [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Istnieje kilka [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] używane przez klientów i dostawców, które pomagają w tej właściwości.  
  
#### <a name="automationid"></a>AutomationID  
 Jednoznacznie identyfikuje element automatyzacji z jego elementów równorzędnych. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> nie jest zlokalizowana, w odróżnieniu od właściwości takich jak <xref:System.Windows.Automation.AutomationElement.NameProperty> , jest zazwyczaj zlokalizowane, jeśli produkt pobiera dostarczane w wielu językach. Zobacz [Użyj właściwości AutomationID](../../../docs/framework/ui-automation/use-the-automationid-property.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> nie gwarantuje unikatową tożsamość w drzewie usługi automation. Na przykład aplikacja może zawierać formant menu z wieloma elementami menu najwyższego poziomu, które z kolei ma wiele elementów menu podrzędne. Te elementy menu dodatkowej mogą być określane przez schemat ogólnych, takich jak "Item1 — element 2, item3 —, itd.", umożliwiając zduplikowanych identyfikatorów dla dzieci różnych elementów menu górnego poziomu.  
  
#### <a name="controltype"></a>ControlType  
 Określa typ kontrolki, reprezentowane przez element automatyzacji. Z wiedzy typu kontrolki można wywnioskować istotnych informacji. Zobacz [kontrolek automatyzacji interfejsu użytkownika typy Przegląd](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>NameProperty  
 Jest to ciąg tekstowy, który identyfikuje lub objaśnienie formantu. <xref:System.Windows.Automation.AutomationElement.NameProperty> należy używać ostrożnie, ponieważ może być lokalizowany. Zobacz [Przegląd właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="Steps_Required_To_Automate_the_UI_in_a_Test_Application"></a>   
### <a name="implementing-ui-automation-in-a-test-application"></a>Implementowanie automatyzacji interfejsu użytkownika w aplikacji testowej  
  
|||  
|-|-|  
|Dodaj odwołania do automatyzacji interfejsu użytkownika.|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Dll użytkownika niezbędne dla klientów automatyzacji interfejsu użytkownika są wymienione w tym miejscu.<br /><br /> -UIAutomationClient.dll zapewnia dostęp do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] interfejsów API po stronie klienta.<br />-UIAutomationClientSideProvider.dll zapewnia możliwość automatyzacji [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrolki. Zobacz [Obsługa automatyzacji interfejsu użytkownika dla standardowych kontrolek](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes.dll zapewnia dostęp do określonych typów zdefiniowanych w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|Dodaj <xref:System.Windows.Automation> przestrzeni nazw.|Ta przestrzeń nazw zawiera wszystko, co klienci automatyzacji interfejsu użytkownika muszą korzystać z możliwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] z wyjątkiem obsługi tekstu.|  
|Dodaj <xref:System.Windows.Automation.Text> przestrzeni nazw.|Ta przestrzeń nazw zawiera wszystko, czego potrzeba klientów automatyzacji interfejsu użytkownika na wykorzystanie możliwości programu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługi tekstu.|  
|Znajdowanie kontrolki zainteresowań|Zautomatyzowany test skryptów zlokalizuj po elementach automatyzacji interfejsu użytkownika, które reprezentują formanty zainteresowania w obrębie drzewa automatyzacji.<br /><br /> Istnieje wiele sposobów, aby uzyskać przy użyciu kodu po elementach automatyzacji interfejsu użytkownika.<br /><br /> -Zapytania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] przy użyciu <xref:System.Windows.Automation.Condition> instrukcji. Jest to zazwyczaj gdy niezależny od języka <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> jest używany. **Uwaga:**  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> Można uzyskać za pomocą narzędzia takiego jak Inspect.exe umożliwiającą Pozycjonuj [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości formantu. <br /><br /> -Użyj <xref:System.Windows.Automation.TreeWalker> klasy na przechodzenie przez całą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa lub jego podzbioru.<br />— Śledzenie fokusu.<br />— Użyj hWnd formantu.<br />— Użyj lokalizacji ekranu, takie jak lokalizacja kursora myszy.<br /><br /> Zobacz [uzyskiwanie elementów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)|  
|Obtain Control Patterns|Wzorce kontrolki udostępnić wspólny zbiór wykonywanych czynności podobne formantów.<br /><br /> Po zlokalizowaniu formantów, które wymagają testowania, skryptów zautomatyzowanych testów, należy uzyskać wzorców kontrolek zainteresowania z tych elementów automatyzacji interfejsu użytkownika. Na przykład <xref:System.Windows.Automation.InvokePattern> — wzorzec kontrolki przycisku typowych funkcji lub <xref:System.Windows.Automation.WindowPattern> — wzorzec kontrolki dla funkcji okna.<br /><br /> Zobacz [wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).|  
|Automatyzacja interfejsu użytkownika|Skrypty testów automatycznych teraz można kontrolować dowolne [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] zainteresowania z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] framework przy użyciu informacji i funkcji udostępnianych przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorców.|  
  
<a name="Supporting_tools"></a>   
## <a name="related-tools-and-technologies"></a>Pokrewne narzędzia i technologie  
 Istnieje wiele powiązanych narzędzi i technologii, które obsługują testy zautomatyzowane za pomocą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
-   Jest Inspect.exe [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)] aplikacji, który może służyć do zbierania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacje o dostawcy i klienta programowanie i debugowanie. Inspect.exe znajduje się w [!INCLUDE[TLA#tla_winfxsdk](../../../includes/tlasharptla-winfxsdk-md.md)].  
  
-   Udostępnia MSAABridge [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacje [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klientów. Podstawowym celem mostkowanie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] jest umożliwienie istniejące [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klientom możliwość interakcji z dowolnej platformy, które ma zaimplementowany [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Security"></a>   
## <a name="security"></a>Zabezpieczenia  
 Aby uzyskać informacje o zabezpieczeniach, zobacz [Przegląd zabezpieczeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Zobacz także
- [Podstawowe założenia automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/index.md)
