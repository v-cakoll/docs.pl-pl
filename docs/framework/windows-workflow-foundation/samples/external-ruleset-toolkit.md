---
title: Zewnętrzne Przybornik zestawu reguł
ms.date: 03/30/2017
ms.assetid: a306d283-a031-475e-aa01-9ae86e7adcb0
ms.openlocfilehash: f545d083bb6caf9daca3ce553d0a1ee6711b0062
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584263"
---
# <a name="external-ruleset-toolkit"></a>Zewnętrzne Przybornik zestawu reguł
Zwykle, gdy zasady są używane w aplikacji przepływu pracy, reguły są częścią zestawu. W niektórych przypadkach warto zachować zestawów reguł, niezależnie od zestawu, dzięki czemu mogą być aktualizowane bez ponownego tworzenia i wdrażania zestawu przepływu pracy. Ten przykład umożliwia zarządzanie i Edytuj zestawów reguł w bazie danych i uzyskać dostęp do tych zestawów reguł z przepływu pracy w czasie wykonywania. Umożliwia to uruchamianie wystąpienia przepływu pracy automatycznie zastosować zmian zestaw reguł.

 Przykład zewnętrzne Przybornik zestawu reguł zawiera narzędzie oparte na formularzach Windows, używanej do zarządzania i Edytuj wersje zestawu reguł w bazie danych. Zawiera także działania, a usługa hosta do wykonywania tych zasad.

> [!NOTE]
>  Ten przykładowy skrypt wymaga [programu Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=96181).  
  
 Program Visual Studio udostępnia edytorze zestawu reguł w ramach programu Windows Workflow Foundation (WF). Ten edytor można uruchomić przez dwukrotne kliknięcie `Policy` działania w przepływie pracy; to szereguje zdefiniowany obiekt RuleSet w pliku Rules skojarzone z przepływem pracy ( `Policy` działanie jest uruchamiane wystąpienie zestaw reguł dla przepływu pracy). Plik Rules jest skompilowany w zestawie jako zasób, podczas kompilowania projektu przepływu pracy.  
  
 Składnik to między innymi próbki:  
  
-   Narzędzie interfejsu interfejs graficzny użytkownika zestaw reguł, które służy do edytowania i zarządzanie wersjami zestawu reguł w bazie danych.  
  
-   Usługa zestaw reguł, która jest konfigurowana dla aplikacji hosta i uzyskuje dostęp do zestawów reguł z bazy danych.  
  
-   `ExternalPolicy` Działania, żądania zestaw reguł z usługi zestaw reguł, która jest uruchamiana zestaw reguł dla przepływu pracy.  
  
 Interakcja składników przedstawiono na rysunku 1. W kolejnych sekcjach opisano każdego składnika.  
  
 ![Omówienie pojęć dotyczących zewnętrznych Przykładowy zestaw reguł](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesettoolkitsampleoverview.gif "RuleSetToolkitSampleOverview")  
  
 Rysunek 1: Omówienie przykładowych  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ExternalRuleSetToolKit`  
  
## <a name="ruleset-tool"></a>Narzędzia zestawu reguł  
 Zrzut ekranu narzędzia do zestaw reguł jest pokazany na rysunku 2. Z **Store reguły** menu, można załadować dostępne zestawy reguł z bazy danych i zapisać zmodyfikowane zestawów reguł do sklepu. Plik konfiguracji aplikacji zawiera parametry połączenia bazy danych dla bazy danych zestaw reguł. Możesz uruchomić to narzędzie, automatycznie ładuje zestawy reguł z bazy danych skonfigurowane.  
  
 ![Dnia zewnętrzny zestaw reguł Toolket przykładowe dane wyjściowe](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesetbrowser.gif "RuleSetBrowser")  
  
 Rysunek 2: Zestaw reguł przeglądarki  
  
 Narzędzie RuleSet dotyczy numery wersji głównych i pomocniczych zestawów reguł, umożliwiając jednocześnie obsługiwać i przechowywać wiele wersji (to narzędzie zawiera bez blokowania lub innych konfiguracji funkcji zarządzania, oprócz możliwości przechowywania wersji). Za pomocą narzędzia, możesz utworzyć nowe wersje zestawu reguł lub usunąć istniejące wersje. Po kliknięciu **New**, narzędzie tworzy nową nazwę zestawu reguł i stosuje w wersji 1.0. Podczas kopiowania wersję narzędzia tworzy kopię wybranej wersji zestawu reguł, włączając reguły zawarte i przypisuje numery wersji nowych, unikatowych. Te numery wersji są oparte na numery wersji istniejących zestawów reguł. Można zmienić numery nazwą i wersją zestawu reguł przy użyciu skojarzonego pola w formularzu.  
  
 Po kliknięciu **Edycja reguł**, uruchomiony Edytor zestawu reguł, jak pokazano na rysunku 3.  
  
 ![Zewnętrzne Przybornik zestawu przykładowych danych wyjściowych](../../../../docs/framework/windows-workflow-foundation/samples/media/ruleseteditor.gif "RuleSetEditor")  
  
 Rysunek 3: Zestaw reguł edytora  
  
 Jest to, ponownie hostingu okno dialogowe Edytor, który jest częścią dodatku Windows Workflow Foundation programu Visual Studio. Zapewnia te same funkcje, w tym obsługę funkcji Intellisense. Zasady są tworzone na typ docelowy (np. przepływ pracy), który jest skojarzony z zestawu reguł w narzędziu; Po kliknięciu **Przeglądaj** w oknie dialogowym Narzędzia główne **selektor przepływu pracy i typu** zostanie wyświetlone okno dialogowe, jak pokazano na rysunku 4.  
  
 ![Przepływ pracy &#47;wpisz wybór](../../../../docs/framework/windows-workflow-foundation/samples/media/71f08d57-e8f2-499e-8151-ece2cbdcabfd.gif "71f08d57-e8f2-499e-8151-ece2cbdcabfd")  
  
 Rysunek 4: Wybór przepływu pracy/typu  
  
 Możesz użyć **selektor przepływu pracy i typu** okna dialogowego, aby określić zestaw i określonego typu, w tym zestawie. Ten typ jest typem docelowym, względem którego zasady są tworzone (i uruchom). W wielu przypadkach typ docelowy jest przepływ pracy lub innego typu działania. Można jednak uruchomić zestaw reguł, dla dowolnego typu .NET.  
  
 Ścieżka do pliku zestawu i typu `name are stored with the` zestaw reguł w bazie danych, tak, aby przy zestaw reguł są pobierane z bazy danych, narzędzie próbuje automatycznie załadować typ docelowy.  
  
 Po kliknięciu **OK** w **selektor przepływu pracy i typu** okno dialogowe, sprawdza poprawność wybranego typu względem zestaw reguł, aby upewnić się, że typ docelowy wszystkie elementy członkowskie przywoływany przez zasady. Błędy są wyświetlane w **błędy sprawdzania poprawności** okna dialogowego (zobacz rysunek 5). Można kontynuować zmiany, pomimo błędów, lub kliknij przycisk **anulować**. Z **narzędzia** menu w oknie dialogowym Narzędzia główne, możesz kliknąć pozycję **weryfikacji** do ponownego sprawdzania poprawności wersji zestaw reguł względem działanie docelowe.  
  
 ![Błędy sprawdzania poprawności z zewnętrznego zestawu reguł próbki](../../../../docs/framework/windows-workflow-foundation/samples/media/validationerrorsruleset.png "ValidationErrorsRuleSet")  
  
 Rysunek 5: Błędy sprawdzania poprawności  
  
 Z **danych** menu Narzędzia, można importować i eksportować zestawów reguł. Po kliknięciu **importu**, pojawi się okno dialogowe selektora plików, w którym można wybrać plik rules. To może lub nie może być plikiem początkowo utworzona w programie Visual Studio. Ten plik Rules powinien zawierać Zserializowany obiekt `RuleDefinitions` wystąpienia, które zawiera kolekcję warunków i kolekcji zestawów reguł. Narzędzie nie używa Kolekcja warunków, ale zajmuje `RuleDefinitions` format Rules umożliwiające interakcje ze środowiskiem programu Visual Studio.  
  
 Po wybraniu pliku Rules **selektor RuleSet** zostanie wyświetlone okno dialogowe (patrz rysunek 6). Okno dialogowe umożliwia wybieranie zestawów reguł z pliku, który chcesz zaimportować (wartość domyślna Określa wszystkie zestawy reguł). Zestawy reguł w pliku Rules nie mają numery wersji, ponieważ ich przechowywanie wersji w ramach projektu WF jest taka sama jak wersja zestawu. Podczas procesu importowania narzędzie automatycznie przypisuje następny dostępny główny numer wersji (która może zostać zmieniona po zaimportowaniu); można wyświetlić numery wersji przypisane w **selektor RuleSet** listy.  
  
 Dla każdego zestawu reguł, który importuje narzędzie spróbuje znaleźć skojarzony typ z folderu bin\Debug znajdujące się w lokalizacji pliku Rules (jeśli istnieje), na podstawie elementów członkowskich, używany w zestawie reguł. Jeśli narzędzie wykryje wiele typów zgodnych, próbuje wybierz typ na podstawie dopasowania między nazwę typu i nazwę pliku Rules (na przykład `Workflow1` typ odpowiada Workflow1.rules). Jeśli istnieje wiele dopasowań, pojawia się monit o wybranie typu. Jeśli ten mechanizm automatycznej identyfikacji nie znajdzie zgodnego zestawu lub typu, a następnie po zaimportowaniu można kliknąć **Przeglądaj** w oknie dialogowym Narzędzia główne, aby przejść do skojarzonego typu.  
  
 ![Selektor zestawu reguł](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesetselector.gif "RuleSetSelector")  
  
 Rysunek 6: Zestaw reguł selektora  
  
 Po kliknięciu **Eksport danych** menu głównego narzędzia **selektor RuleSet** zostanie wyświetlone okno dialogowe, w którym można określić zestawy reguł z bazy danych, które powinny być wyeksportowane. Po kliknięciu **OK**, **Zapisz plik** zostanie wyświetlone okno dialogowe, w którym można określić nazwę i lokalizację pliku wynikowego rules. Ponieważ plik Rules nie zawiera informacji o wersji, można wybrać tylko jedną wersję zestawu reguł o danej nazwie zestawu reguł.  
  
## <a name="policyfromservice-activity"></a>Działanie PolicyFromService  
 Kod `PolicyFromService` działania jest proste. Jak działa `Policy` działanie jest dostępne przy użyciu programu WF, ale zamiast pobieranie docelowy zestaw reguł z pliku Rules, wywołuje usługę hosta, do uzyskania wystąpienia zestaw reguł. Następnie uruchamia zestaw reguł względem wystąpienia działania głównego przepływu pracy.  
  
 Aby użyć działania w przepływie pracy, należy dodać odwołanie do `PolicyActivities` i `RuleSetService` zestawów z projektu przepływu pracy. Zapoznaj się z procedurą na końcu tego tematu, aby uzyskać informacje dotyczące sposobu dodawania działań do przybornika.  
  
 Po umieszczeniu działania w przepływie pracy, należy podać nazwę zestawu reguł do uruchomienia. Wprowadź nazwę jako wartości literału lub powiązać zmiennej przepływu pracy lub właściwość kolejnego działania. Opcjonalnie można wprowadzić numery wersji określonego zestawu reguł, który powinien zostać uruchomiony. Pozostawienie wartości domyślnej 0 dla numerów wersji głównych i pomocniczych numer najnowszej wersji w bazie danych jest dostarczana automatycznie dla działania.  
  
## <a name="ruleset-service"></a>Zestaw reguł usługi  
 Usługa jest odpowiedzialna za pobieranie określonej wersji zestawu reguł z bazy danych i przywróceniem go do wywoływania działania. Jak wspomniano, jeśli przekazany wartości wersji głównych i pomocniczych `GetRuleSet` wywołania są oba 0, usługa pobierze najnowszą wersję. W tym momencie nie występuje buforowanie definicji zestawu reguł lub wystąpień; Podobnie nie istnieją żadne funkcje do oznaczania wersji zestaw reguł jako "wdrożone", aby odróżnić je od zestawów reguł w toku.  
  
 Bazy danych można uzyskać dostęp przez usługę, należy skonfigurować na hoście przy użyciu pliku konfiguracji aplikacji.  
  
#### <a name="to-run-the-tool"></a>Aby uruchomić narzędzie  
  
1.  Folder, który konfiguruje Tabela zestaw reguł, używana przez narzędzia i usługi zawiera plik Setup.sql. Możesz uruchomić plik wsadowy plik Setup.cmd do tworzenia bazy danych reguły na program SQL Express i konfigurowanie tabeli zestaw reguł.  
  
2.  Jeśli poddasz edycji pliku wsadowego lub Setup.sql i określ nie należy używać programu SQL Express lub do umieszczenia w tabeli w bazie danych o nazwie coś innego niż `Rules`, pliki konfiguracji aplikacji w narzędziu zestaw reguł i `UsageSample` projektów powinny być edytowane o takiej samej informacje.  
  
3.  Po uruchomieniu skryptu Setup.sql, można tworzyć `ExternalRuleSetToolkit` rozwiązania, a następnie uruchom zestaw reguł narzędzia z projektu ExternalRuleSetTool.  
  
4.  `RuleSetToolkitUsageSample` Rozwiązanie sekwencyjne Aplikacja konsoli przepływu pracy zawiera przykładowy przepływ pracy. Przepływ pracy składa się z `PolicyFromService` działanie i dwie zmienne `orderValue` i `discount`, względem którego działa docelowy zestaw reguł.  
  
5.  Aby korzystać z przykładu, kompilacji `RuleSetToolkitUsageSample` rozwiązania. Następnie z menu głównego narzędzia zestaw reguł, kliknij przycisk **importowania danych** i wskaż plik DiscountRuleSet.rules w folderze RuleSetToolkitUsageSample. Kliknij przycisk **zapisem Store reguły** opcję menu, aby zapisać zaimportowany zestaw reguł w bazie danych.  
  
6.  Ponieważ `PolicyActivities` odwołuje się do zestawu z przykładowego projektu przepływu pracy `PolicyFromService` działanie pojawiło się w przepływie pracy. Nie, jednak wydaje w przyborniku domyślnie. Aby dodać go do przybornika, wykonaj następujące czynności:  
  
    -   Kliknij prawym przyciskiem myszy przybornika, a następnie wybierz pozycję **wybierz elementy** (może to potrwać chwilę).  
  
    -   Gdy **wybierz elementy przybornika** zostanie wyświetlone okno dialogowe, kliknij przycisk **działania** kartę.  
  
    -   Przejdź do `PolicyActivities` zestawu w `ExternalRuleSetToolkit` rozwiązań i kliknij przycisk **Otwórz**.  
  
    -   Upewnij się, że `PolicyFromService` wybrano działania **wybierz elementy przybornika** okna dialogowego, a następnie kliknij przycisk **OK**.  
  
    -   Działanie powinien zostać wyświetlony na przybornika w **składniki RuleSetToolkitUsageSample** kategorii.  
  
7.  Usługa zestaw reguł jest już skonfigurowany na hoście aplikacji konsoli przy użyciu następujących instrukcji w pliku Program.cs.  
  
    ```  
    workflowRuntime.AddService(new RuleSetService());  
    ```  
  
8.  Można również skonfigurować usługę na hoście przy użyciu pliku konfiguracji; można znaleźć w dokumentacji zestawu SDK, aby uzyskać szczegółowe informacje.  
  
9. Plik konfiguracji aplikacji zostanie dodany do projektu przepływu pracy, aby określić parametry połączenia dla bazy danych, który będzie używany przez usługę. Powinna to być parametry połączenia używane przez narzędzie zestaw reguł, które wskazują na bazę danych, zawierającą tabelę zestaw reguł.  
  
10. Możesz teraz uruchomić `RuleSetToolkitUsageSample` projektu, jak w przypadku innych aplikacji konsoli przepływu pracy. Naciśnij klawisz F5 lub Ctrl + F5 w programie Visual Studio lub uruchom plik RuleSetToolkitUsageSample.exe bezpośrednio.  
  
    > [!NOTE]
    >  Należy zamknąć narzędzie zestaw reguł, aby ponownie skompilować przykład użycia, ponieważ narzędzie ładuje zestaw próbki użycia.