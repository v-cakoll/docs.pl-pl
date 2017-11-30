---
title: "Zewnętrzne Toolkit zestaw reguł"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a306d283-a031-475e-aa01-9ae86e7adcb0
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9ff7a7e7cfd29ea6e5029219115b4bfff1c6895c
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="external-ruleset-toolkit"></a>Zewnętrzne Toolkit zestaw reguł
Zwykle podczas stosowania reguł aplikacji przepływu pracy, reguły są częścią zestawu. W niektórych scenariuszach można zachować zestawów reguł, niezależnie od zestawu, dzięki czemu mogą być aktualizowane bez ponowne tworzenie i wdrażanie zestawu przepływu pracy. W tym przykładzie pozwala na zarządzanie i edytować zestawów reguł w bazie danych oraz uzyskać dostęp do tych zestawów reguł z przepływu pracy w czasie wykonywania. Dzięki temu uruchomionych wystąpień przepływu pracy automatycznie zastosować zmian zestaw reguł.  
  
 Przykład zewnętrznych narzędzi zestaw reguł zawiera narzędzie oparte na formularzach systemu Windows, które służy do zarządzania i Edytuj zestaw reguł wersji w bazie danych. Zawiera także działania i usługa hosta do wykonywania tych zasad.  
  
> [!NOTE]
>  W tym przykładzie wymaga [programu Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=96181).  
  
 [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)]zawiera Edytor zestaw reguł, w ramach programu Windows Workflow Foundation (WF). Ten edytor można uruchomić przez dwukrotne kliknięcie `Policy` działania w przepływie pracy; go serializuje zdefiniowanych Obiekt RuleSet w pliku Rules skojarzonego z przepływem pracy ( `Policy` działanie jest uruchomione wystąpienie zestaw reguł dla przepływu pracy). Plik Rules jest kompilowany do zestawu jako zasób podczas kompilowania projektu przepływu pracy.  
  
 Składniki następujące przykładowe:  
  
-   Zestaw reguł graficzne narzędzie interfejsu użytkownika służącego do edycji i zarządzanie wersjami zestaw reguł w bazie danych.  
  
-   Usługa zestaw reguł, jest skonfigurowana w aplikacji hosta, który uzyskuje dostęp do zestawów reguł z bazy danych.  
  
-   `ExternalPolicy` Działanie, które żądania zestaw reguł z usługi zestaw reguł i jest uruchamiana zestaw reguł dla przepływu pracy.  
  
 Interakcja składników jest pokazany na rysunku 1. W kolejnych sekcjach opisano każdego składnika.  
  
 ![Omówienie pojęć zewnętrznych Przykładowy zestaw reguł](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesettoolkitsampleoverview.gif "RuleSetToolkitSampleOverview")  
  
 Rysunek 1: Omówienie przykładowej  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ExternalRuleSetToolKit`  
  
## <a name="ruleset-tool"></a>Narzędzie zestaw reguł  
 Zrzut ekranu narzędzia zestaw reguł jest pokazany na rysunku 2. Z **magazynu reguły** menu można załadować dostępnych zestawów reguł z bazy danych i zapisać zmodyfikowanych zestawów reguł w magazynie. Plik konfiguracji aplikacji zawiera parametry połączenia bazy danych dla bazy danych zestaw reguł. Po uruchomieniu narzędzia automatycznie ładuje zestawów reguł z bazy danych skonfigurowane.  
  
 ![Zewnętrzne RuleSet Toolket przykładowe dane wyjściowe](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesetbrowser.gif "RuleSetBrowser")  
  
 Rysunek 2: Przeglądarki zestaw reguł  
  
 Narzędzie RuleSet dotyczy numery wersji głównej i pomocniczej zestawów reguł, umożliwiając jednocześnie Obsługa i przechowywać wiele wersji (Narzędzie konfiguracji blokowania lub innych zapewnia funkcje zarządzania, oprócz możliwości przechowywania wersji). Za pomocą narzędzia, możesz utworzyć nowe wersje RuleSet lub usunąć istniejące wersje. Po kliknięciu **nowy**, narzędzie tworzy nową nazwę zestaw reguł i ma zastosowanie w wersji 1.0. Po skopiowaniu wersji narzędzie tworzy kopię wybranej wersji zestaw reguł, reguły zawarte w tym i przypisuje numery wersji nowy, unikatowy. Numery wersji te są oparte na numery wersji istniejących zestawów reguł. Można zmienić liczby nazwa i wersja zestaw reguł przy użyciu skojarzonymi polami w formularzu.  
  
 Po kliknięciu **Edycja reguł**, zostanie uruchomiony Edytor zestaw reguł, jak pokazano na rysunku 3.  
  
 ![Zewnętrzne RuleSet Toolkit przykładowe dane wyjściowe](../../../../docs/framework/windows-workflow-foundation/samples/media/ruleseteditor.gif "RuleSetEditor")  
  
 Rysunek 3: Zestaw reguł edytora  
  
 To jest ponownie hosting okno dialogowe Edytor, który jest częścią programu Windows Workflow Foundation [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] dodatku. Zapewnia te same funkcje, w tym obsługę funkcji Intellisense. Reguły są tworzone na typ docelowy (takich jak przepływ pracy), który jest skojarzony z RuleSet w narzędziu; Po kliknięciu **Przeglądaj** w oknie dialogowym Narzędzia główne, **selektor typu przepływupracy/** zostanie wyświetlone okno dialogowe, jak pokazano na rysunku 4.  
  
 ![Przepływ pracy &#47; Typ zaznaczenia](../../../../docs/framework/windows-workflow-foundation/samples/media/71f08d57-e8f2-499e-8151-ece2cbdcabfd.gif "71f08d57-e8f2-499e-8151-ece2cbdcabfd")  
  
 Rysunek 4: Selektor typu/przepływu pracy  
  
 Można użyć **selektor typu przepływupracy/** okna dialogowego, aby określić zestaw i określonego typu w tym zestawie. Ten typ jest typem docelowym, względem którego zasady zostały utworzone (i uruchom). W wielu przypadkach typ docelowy jest przepływu pracy lub innego typu działania. Można jednak uruchomić zestaw reguł dla dowolnego typu .NET.  
  
 Ścieżka do pliku zestawu i typ `name are stored with the` zestaw reguł w bazie danych, dzięki czemu przy zestaw reguł są pobierane z bazy danych, narzędzie próbuje automatycznie załadować typ docelowy.  
  
 Po kliknięciu **OK** w **selektor typu przepływupracy/** okna dialogowego i sprawdza poprawność wybranego typu przed zestaw reguł, aby upewnić się, że typ docelowy ma wszystkie elementy członkowskie przywoływany przez zasady. Błędy są wyświetlane w **błędy sprawdzania poprawności** okna dialogowego (patrz rysunek 5). Możesz kontynuować zmiany, pomimo błędy, lub kliknij przycisk **anulować**. Z **narzędzia** menu w oknie dialogowym Narzędzia główne, można kliknąć **weryfikacji** ponownego sprawdzania poprawności wersji RuleSet przed działania docelowego.  
  
 ![Błędy sprawdzania poprawności z zewnętrznego próbki RuleSet](../../../../docs/framework/windows-workflow-foundation/samples/media/validationerrorsruleset.png "ValidationErrorsRuleSet")  
  
 Rysunek 5: Błędy sprawdzania poprawności  
  
 Z **danych** menu Narzędzia, można importować i eksportować zestawów reguł. Po kliknięciu **importu**, pojawi się okno dialogowe selektor plików, w którym można wybrać plik rules. Może to być lub może nie być plik początkowo utworzony w [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]. Plik Rules powinien zawierać serializacji `RuleDefinitions` wystąpienia, które zawiera kolekcję warunków i kolekcję zestawów reguł. Narzędzie nie używa Kolekcja warunków, ale używa `RuleDefinitions` format Rules, aby zezwolić na interakcję z [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] środowiska.  
  
 Po wybraniu pliku Rules **selektora RuleSet** zostanie wyświetlone okno dialogowe (patrz rysunek 6). Okno dialogowe umożliwia Wybierz zestawy reguł z pliku, który chcesz zaimportować (wartość domyślna Określa wszystkie zestawy reguł). Zestawy reguł w pliku Rules nie mają numery wersji, ponieważ ich wersji w ramach projektu WF jest taka sama jak wersja zestawu. Podczas procesu importowania narzędzie automatycznie przypisuje dalej dostępne główny numer wersji (które można zmienić po zaimportowaniu); można wyświetlić numery wersji przypisanej **selektora RuleSet** listy.  
  
 Dla każdego zestaw reguł, który importuje narzędzie próbował zlokalizować skojarzony typ z folderu bin\Debug znajdujące się w lokalizacji pliku Rules (jeśli istnieje), na podstawie elementów członkowskich używane w zestaw reguł. Jeśli narzędzie wykryje wiele typów zgodnych, próbuje wybrać typ na podstawie dopasowania między Rules nazwę pliku i nazwy typu (na przykład `Workflow1` typ odpowiada Workflow1.rules). Istnieje wiele dopasowań, monit o wybranie typu. Jeśli ten mechanizm automatycznej identyfikacji nie powiedzie się, można znaleźć zgodnego zestawu lub typu, a następnie po zaimportowaniu można kliknąć **Przeglądaj** w oknie dialogowym Narzędzia główne, aby przejść do skojarzonego typu.  
  
 ![Zestaw reguł selektora](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesetselector.gif "RuleSetSelector")  
  
 Rysunek 6: Selektor RuleSet  
  
 Po kliknięciu **eksportu danych** menu głównego narzędzia **selektora RuleSet** zostanie wyświetlone okno dialogowe, w którym można określić zestawów reguł z bazy danych, która powinna być wyeksportowane. Po kliknięciu **OK**, **Zapisz plik** zostanie wyświetlone okno dialogowe, w którym można określić nazwę i lokalizację pliku wynikowego rules. Ponieważ plik Rules nie zawiera informacje o wersji, można wybrać tylko jedną wersję RuleSet o danej nazwie zestaw reguł.  
  
## <a name="policyfromservice-activity"></a>Działanie PolicyFromService  
 Kod `PolicyFromService` działania jest prosta. Podobne jak w przypadku działa `Policy` działanie dostępne z WF, ale zamiast pobierania docelowy zestaw reguł z pliku Rules, wywołuje usługi hosta do uzyskania wystąpienia zestaw reguł. Następnie uruchamia zestaw reguł przed wystąpienia działania głównego przepływu pracy.  
  
 Aby użyć działania w przepływie pracy, Dodaj odwołanie do `PolicyActivities` i `RuleSetService` zestawy z projektu przepływu pracy. Zapoznaj się z procedurą na końcu tego tematu, aby uzyskać informacje dotyczące sposobu dodawania działań do przybornika.  
  
 Po umieszczeniu działanie w przepływie pracy, należy podać nazwę zestaw reguł do uruchomienia. Wprowadź nazwę jako wartość literału lub powiązać zmiennej przepływu pracy lub właściwość innego działania. Opcjonalnie można wprowadzić numery wersji określonego zestaw reguł, które powinny być uruchamiane. Pozostawienie wartość domyślna 0 dla numerów wersji głównej i pomocniczej numer najnowszej wersji w bazie danych jest teraz udostępniana automatycznie dla działania.  
  
## <a name="ruleset-service"></a>Zestaw reguł usługi  
 Usługa jest odpowiedzialna za pobieranie określonych wersji zestaw reguł z bazy danych i przywróceniem go do wywoływania działania. Wspomnianej wcześniej, jeśli wartości wersji głównej i pomocniczej przekazano `GetRuleSet` wywołania są obie 0, usługa pobiera najnowsza wersja. W tym momencie jest bez buforowania definicje RuleSet lub wystąpień; Podobnie jest Brak funkcji do oznaczenia wersji RuleSet jako "wdrożone", aby odróżnić je od zestawów reguł w toku.  
  
 Usługa dostępu do bazy danych należy skonfigurować na hoście przy użyciu pliku konfiguracji aplikacji.  
  
#### <a name="to-run-the-tool"></a>Aby uruchomić narzędzie  
  
1.  Folder, który konfiguruje tabeli zestaw reguł używany przez usługę i przez narzędzie znajduje się plik Setup.sql. Możesz uruchomić plik wsadowy Setup.cmd do tworzenia bazy danych reguły na SQL Express i zdefiniować tabelę zestaw reguł.  
  
2.  Jeśli edycja pliku wsadowego lub Setup.sql i określ nie należy używać programu SQL Express lub można umieścić w tabeli w bazie danych o nazwie coś innego niż `Rules`, pliki konfiguracji aplikacji w narzędziu zestaw reguł i `UsageSample` projekty powinny być edytowane o takim samym informacje.  
  
3.  Po uruchomieniu skryptu Setup.sql można tworzyć `ExternalRuleSetToolkit` rozwiązania, a następnie uruchom zestaw reguł narzędzia z projektu ExternalRuleSetTool.  
  
4.  `RuleSetToolkitUsageSample` Rozwiązanie sekwencyjnych Aplikacja konsoli przepływu pracy zawiera przykładowy przepływ pracy. Przepływ pracy składa się z `PolicyFromService` działania i dwie zmienne `orderValue` i `discount`, względem którego element docelowy zestaw reguł jest uruchamiana.  
  
5.  Aby użyć przykładowego, kompilacji `RuleSetToolkitUsageSample` rozwiązania. Następnie z menu głównego narzędzia zestaw reguł, kliknij przycisk **importowania danych** i wskaż plik DiscountRuleSet.rules w folderze RuleSetToolkitUsageSample. Kliknij przycisk **zapisem magazynu reguły** menu opcję, aby zapisać zaimportowany zestaw reguł do bazy danych.  
  
6.  Ponieważ `PolicyActivities` odwołuje się do zestawu z przykładowy projekt przepływu pracy `PolicyFromService` działania zostanie wyświetlony w przepływie pracy. Nie, ale ma w przyborniku domyślnie. Aby dodać go do przybornika, wykonaj następujące czynności:  
  
    -   Kliknij prawym przyciskiem myszy przybornika i wybierz **wybierz elementy** (może to potrwać kilka minut).  
  
    -   Gdy **wybierz elementy przybornika** zostanie wyświetlone okno dialogowe, kliknij przycisk **działania** kartę.  
  
    -   Przejdź do `PolicyActivities` zestawu w `ExternalRuleSetToolkit` rozwiązanie i kliknij przycisk **Otwórz**.  
  
    -   Upewnij się, że `PolicyFromService` działania jest zaznaczona w **wybierz elementy przybornika** okna dialogowego, a następnie kliknij przycisk **OK**.  
  
    -   Działanie powinien zostać wyświetlony w przyborniku w **składniki RuleSetToolkitUsageSample** kategorii.  
  
7.  Usługa zestaw reguł jest już skonfigurowana na hoście aplikacji konsoli przy użyciu następujących instrukcji w pliku Program.cs.  
  
    ```  
    workflowRuntime.AddService(new RuleSetService());  
    ```  
  
8.  Można również skonfigurować usługę na hoście przy użyciu pliku konfiguracji; Zobacz szczegółowe informacje można znaleźć w dokumentacji zestawu SDK.  
  
9. Plik konfiguracji aplikacji jest dodawane do projektu przepływu pracy, aby określić parametry połączenia dla bazy danych mają być używane przez usługę. Powinno to być te same parametry połączenia używane przez narzędzie zestaw reguł, które bazy danych, która zawiera tabelę zestaw reguł.  
  
10. Teraz możesz uruchomić `RuleSetToolkitUsageSample` projektu, jak w przypadku innych aplikacji konsolowej przepływu pracy. Naciśnij klawisz F5 lub Ctrl + F5 w [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] lub uruchom plik RuleSetToolkitUsageSample.exe bezpośrednio.  
  
    > [!NOTE]
    >  Należy zamknąć narzędzie zestaw reguł, aby ponownie skompilować próbki użycia, ponieważ narzędzie ładuje zestaw próbki użycia.