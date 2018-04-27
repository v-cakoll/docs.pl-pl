---
title: Korzystanie z automatyzacji interfejsu użytkownika do testów automatycznych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
caps.latest.revision: 26
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 6539829feacf8c9a5c9c1339df299a21ac5fe64f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="using-ui-automation-for-automated-testing"></a>Korzystanie z automatyzacji interfejsu użytkownika do testów automatycznych
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten przegląd zawiera opis sposobu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] można użyteczne jako platforma dostęp programowy w zautomatyzować testowania scenariuszy.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zapewnia ujednolicone obiektu modelu, który włącza wszystkie [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] struktury udostępniać złożone i zaawansowane funkcje w sposób dostępny i łatwo automatycznych.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] został opracowany jako następnika do [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] istniejące ramy zaprojektowano w celu stanowią rozwiązanie dla Udostępnianie formantów i aplikacji. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] nie został zaprojektowany przy użyciu automatyzacji testów na uwadze, nawet jeśli jego ewoluował w tej roli z powodu bardzo podobne wymagania dotyczące ułatwień dostępu i automatyzacji. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], oprócz rozwiązania bardziej precyzyjnych ułatwień dostępu, jest również zaprojektowane specjalnie zapewniają niezawodne funkcje testowanie automatyczne. Na przykład [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] zależy od jednego interfejsu zarówno ujawnienie informacji o Interfejsie użytkownika i zbierać informacje wymagane przez na produkty; [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] oddziela dwa modele.  
  
 Zarówno dostawcy i klienta, które są wymagane do zaimplementowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] się przydatne jako narzędzie testów automatycznych. Dostawcy automatyzacji interfejsu użytkownika są aplikacje, takie jak Microsoft Word, Excel, i na podstawie innych aplikacji innych firm lub kontrolki [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] systemu operacyjnego. Klienci automatyzacji interfejsu użytkownika obejmują ułatwianiem aplikacje i skrypty testów automatycznych.  
  
> [!NOTE]
>  To omówienie zamierzeniu prezentować nowe i ulepszone automatyczne testowanie możliwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. W tym omówieniu nie mają na celu dostarczenie informacji na temat dostępności funkcji a nie zajmie ułatwień dostępu innych niż w przypadku, gdy to konieczne.  
  
<a name="Using_UI_Automation_During_Development"></a>   
## <a name="ui-automation-in-a-provider"></a>Automatyzacja interfejsu użytkownika w dostawcy  
 Aby uzyskać [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] do automatyzacji, Deweloper aplikacji lub kontroli należy przyjrzeć się co można wykonać akcje usługi przez użytkownika końcowego na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] przy użyciu standardowych interakcji klawiatury i myszy.  
  
 Raz te klucza akcje zostały określone w odpowiedniej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorce (oznacza to, wzorce kontrolki, które duplikatów, funkcje i zachowanie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] element) powinny być implementowane w formancie. Na przykład interakcji użytkowników z kontrolki pola kombi (na przykład Uruchom okno dialogowe), które zwykle obejmuje rozwijanie i zwijanie pole kombi, aby ukryć lub wyświetlić listę elementów, wybierając element z listy lub dodanie nowej wartości za pomocą klawiatury.  
  
> [!NOTE]
>  Z innymi modelami ułatwień dostępu deweloperzy należy zebrać informacje bezpośrednio z poszczególnych przycisków, menu lub inne formanty. Niestety co typ formantu polega na dziesiątki niewielkich zmian. Innymi słowy nawet dziesięć zmian przycisk może wszystkie działają tak samo i wykonać taką samą funkcję, ich muszą wszystkie być traktowane jako unikatowy kontrolki. Nie istnieje sposób wiedzieć, czy formanty działają tak samo. Wzorce formantu zostały zaprojektowane do reprezentowania tych zachowań wspólnych formantu. Aby uzyskać więcej informacji, zobacz [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="Implementing_UI_Automation"></a>   
### <a name="implementing-ui-automation"></a>Implementacja automatyzacji interfejsu użytkownika  
 Jak wspomniano wcześniej, bez ujednoliconego modelu udostępniane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], narzędzia testowania i deweloperów są wymagane do znajomości ujawnić właściwości i zachowania formantów w ramach tej informacji określonej struktury. Ponieważ może istnieć kilka różnych platform interfejsu użytkownika występuje w dowolnym momencie jednego systemu operacyjnego, w tym [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], i [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)], może być lada wyzwanie testowanie wielu aplikacji z formantami, które wydają się podobne . Na przykład poniższa tabela przedstawia nazwy właściwości określonej struktury wymagany do pobrania skojarzony z kontrolką przycisku nazwę (lub tekst) i zawiera pojedynczy równoważne [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości.  
  
|Automatyzacja interfejsu użytkownika — typ formantu|Framework interfejsu użytkownika|Określoną właściwość Framework|Właściwości automatyzacji interfejsu użytkownika|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Przycisk|Windows Presentation Foundation|Zawartość|NameProperty|  
|Przycisk|Win32|Podpis|NameProperty|  
|Obraz|HTML|ALT|NameProperty|  
  
 Dostawcy automatyzacji interfejsu użytkownika są zobowiązani do mapowania właściwości określonej struktury ich formantów odpowiednikiem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości.  
  
 Informacje dotyczące implementacji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] u dostawcy można znaleźć w folderze [dostawcy automatyzacji interfejsu użytkownika do kodu zarządzanego](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md). Informacje dotyczące implementacji wzorców formantu są dostępne w [wzorce formantów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) i [wzorzec tekstu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-text-pattern.md).  
  
<a name="Testing_with_UI_Automation"></a>   
## <a name="ui-automation-in-a-client"></a>Automatyzacja interfejsu użytkownika na kliencie  
 Celem wielu narzędzi testu automatycznego i scenariusze jest spójne i powtarzalne manipulacji interfejsu użytkownika. Może to obejmować określonych formantów za pomocą rejestrowaniem i odtwarzaniem testu skryptów, które iterację serii ogólnego działania grupy formantów testowania jednostek.  
  
 Complication, która wynika z automatycznych aplikacji jest trudności synchronizowanie testu z elementem docelowym dynamicznej. Na przykład pole listy, taki jak zawarte w Menedżerze zadań systemu Windows, który wyświetla listę aktualnie uruchomionych aplikacji. Ponieważ elementy w polu listy są aktualizowane dynamicznie poza kontrolą aplikacji testu, próbę powtórzenia zaznaczenie konkretny element w polu listy o dowolnym spójności jest niemożliwe. Podobne zagadnienia również mogą wystąpić przy próbie Powtórz fokus prostych zmian w [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jest poza kontrolą aplikacji testu.  
  
<a name="Programmatic_Access"></a>   
### <a name="programmatic-access"></a>Programowy dostęp  
 Dostęp programistyczny zapewnia możliwość naśladującej za pomocą kodu, interakcji z i środowisko udostępnianych przez tradycyjny myszy i klawiatury. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Umożliwia dostęp programistyczny do pięciu składniki:  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Drzewa, ułatwia nawigację struktury [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Drzewo składa się z kolekcji hWnd firmy. Aby uzyskać więcej informacji, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
  
-   Automatyzacja elementy są poszczególne składniki [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Mogą one często bardziej szczegółowego niż hWnd. Aby uzyskać więcej informacji, zobacz [Przegląd typów formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
-   Właściwości automatyzacji zapewniają szczegółowe informacje o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementów. Aby uzyskać więcej informacji, zobacz [Przegląd właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
-   Wzorce formantu zdefiniuj aspektom funkcjonalności formantu. może składać się z właściwości, metody, zdarzeń i informacje o strukturze. Aby uzyskać więcej informacji, zobacz [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
-   Zdarzenia automatyzacji udostępniają powiadomienia o zdarzeniach i informacje. Aby uzyskać więcej informacji, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Key_properties_critical_to_test_automation"></a>   
### <a name="key-properties-for-test-automation"></a>Właściwości klucza dla testów automatycznych  
 Możliwość jednoznacznie zidentyfikować, a następnie odnaleźć żadnego formantu, w ramach [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] stanowi podstawę dla testów automatycznych aplikacji do działania na tym [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Istnieje kilka [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] używane przez klientów i dostawców, które pomagają w tej właściwości.  
  
#### <a name="automationid"></a>AutomationID  
 Unikatowo identyfikuje element automatyzacji z jego elementów równorzędnych. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> nie jest lokalizowany, w odróżnieniu od właściwości takich jak <xref:System.Windows.Automation.AutomationElement.NameProperty> która zwykle jest zlokalizowana Jeśli produkt pobiera wysłane w wielu językach. Zobacz [Użyj właściwości AutomationID](../../../docs/framework/ui-automation/use-the-automationid-property.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> nie gwarantuje unikatową tożsamość w drzewie automatyzacji. Na przykład aplikacja może zawierać formant menu z wieloma elementami menu najwyższego poziomu, które z kolei ma wiele elementów menu podrzędnego. Te elementy menu dodatkowej mogą zostać zidentyfikowane na podstawie ogólnego schemat, takiego jak "Item1, element 2, Item3, itp.", dzięki czemu zduplikowane identyfikatory elementów podrzędnych dla elementów menu najwyższego poziomu.  
  
#### <a name="controltype"></a>ControlType  
 Określa typ formantu reprezentowany przez element automatyzacji. Istotne informacje można wywnioskować na podstawie wiedzy na temat typu formantu. Zobacz [omówienie typy formantów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>NameProperty  
 Jest to ciąg tekstowy, który identyfikuje lub objaśnienie formantu. <xref:System.Windows.Automation.AutomationElement.NameProperty> należy używać ostrożnie, ponieważ może być lokalizowany. Zobacz [Przegląd właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="Steps_Required_To_Automate_the_UI_in_a_Test_Application"></a>   
### <a name="implementing-ui-automation-in-a-test-application"></a>Implementacja automatyzacji interfejsu użytkownika w aplikacji testu  
  
|||  
|-|-|  
|Dodaj odwołania do automatyzacji interfejsu użytkownika.|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Dll na potrzeby dla klientów automatyzacji interfejsu użytkownika są wyświetlane tutaj.<br /><br /> -UIAutomationClient.dll zapewnia dostęp do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] interfejsów API klienta.<br />-UIAutomationClientSideProvider.dll umożliwia automatyzację [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrolki. Zobacz [Obsługa automatyzacji interfejsu użytkownika dla formantów standardowych](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes.dll zapewnia dostęp do określonych typów zdefiniowanych w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|Dodaj <xref:System.Windows.Automation> przestrzeni nazw.|Ta przestrzeń nazw zawiera wszystko, co potrzebne klienci automatyzacji interfejsu użytkownika do korzystania z funkcji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] z wyjątkiem obsługi tekstu.|  
|Dodaj <xref:System.Windows.Automation.Text> przestrzeni nazw.|Ta przestrzeń nazw zawiera wszystkie potrzeby klientów automatyzacji interfejsu użytkownika, do korzystania z funkcji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Obsługa tekstu.|  
|Znajdź formanty zainteresowań|Skrypty testu automatycznego zlokalizować elementów automatyzacji interfejsu użytkownika, które reprezentują formanty odsetek w obrębie drzewa automatyzacji.<br /><br /> Istnieje wiele sposobów uzyskiwanie elementów automatyzacji interfejsu użytkownika z kodem.<br /><br /> -Zapytania [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] przy użyciu <xref:System.Windows.Automation.Condition> instrukcji. Jest to zazwyczaj gdy niezależnego od języka <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> jest używany. **Uwaga:** <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> można uzyskać za pomocą narzędzia, takiego jak Inspect.exe umożliwiającą Podziel na pozycje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości formantu. <br /><br /> -Użyj <xref:System.Windows.Automation.TreeWalker> klasy przejść przez cały [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa lub ich podzestaw.<br />-Śledzenia fokusu.<br />-Użyj hWnd formantu.<br />-Użyj lokalizacji ekranu, takie jak lokalizacja kursora myszy.<br /><br /> Zobacz [uzyskiwanie elementów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)|  
|Uzyskaj wzorce formantu|Wzorce formantu ujawnia zachowań wspólnych dla formantów podobne.<br /><br /> Po zlokalizowaniu formantów, które wymagają testowania, skrypty testów automatycznych uzyskać wzorców formantu odsetek z tych elementów automatyzacji interfejsu użytkownika. Na przykład <xref:System.Windows.Automation.InvokePattern> — wzorzec formantu przycisku typowych funkcji lub <xref:System.Windows.Automation.WindowPattern> wzorca kontrolki okna funkcji.<br /><br /> Zobacz [wzorce formantów automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).|  
|Automatyzacji interfejsu użytkownika|Skrypty testu automatycznego teraz można kontrolować żadnego [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] płynących z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] framework przy użyciu informacji i funkcji udostępnianych przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorce.|  
  
<a name="Supporting_tools"></a>   
## <a name="related-tools-and-technologies"></a>Pokrewne narzędzia i technologie  
 Istnieje wiele powiązanych narzędzia i technologie, które obsługują testów automatycznych z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
-   Jest Inspect.exe [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)] aplikacji, który może służyć do zbierania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacje o dostawcy i klienta programowanie i debugowanie. Inspect.exe znajduje się w [!INCLUDE[TLA#tla_winfxsdk](../../../includes/tlasharptla-winfxsdk-md.md)].  
  
-   Przedstawia MSAABridge [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacji do [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klientów. Podstawowym celem mostkowania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] jest umożliwienie istniejących [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klientom możliwość interakcji z dowolnym platforma, która została zaimplementowana [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Security"></a>   
## <a name="security"></a>Zabezpieczenia  
 Aby uzyskać informacje o zabezpieczeniach, zobacz [Przegląd zabezpieczeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe założenia automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/index.md)
