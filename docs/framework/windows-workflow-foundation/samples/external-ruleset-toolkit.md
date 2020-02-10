---
title: Zewnętrzne przybornik zestawu reguł
ms.date: 03/30/2017
ms.assetid: a306d283-a031-475e-aa01-9ae86e7adcb0
ms.openlocfilehash: eb59b02d469788b23126f4e02c5b7ae5a63081f0
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094673"
---
# <a name="external-ruleset-toolkit"></a>Zewnętrzne przybornik zestawu reguł

Zwykle gdy reguły są używane w aplikacji przepływu pracy, reguły są częścią zestawu. W niektórych scenariuszach warto zachować zestawy reguł niezależnie od zestawu, aby można je było aktualizować bez konieczności ponownego kompilowania i wdrażania zestawu przepływu pracy. Ten przykład umożliwia zarządzanie zestawami reguł w bazie danych i ich edytowanie oraz uzyskiwanie dostępu do tych zestawów reguł z przepływu pracy w czasie wykonywania. Dzięki temu uruchomione wystąpienia przepływu pracy mogą automatycznie uwzględniać zmiany zestawu reguł.

Zewnętrzny zestaw narzędzi Toolkit zawiera narzędzie oparte na Windows Forms, które służy do zarządzania wersjami zestawów reguł w bazie danych i ich edytowania. Obejmuje ona również działanie i usługę hosta do wykonywania tych reguł.

> [!NOTE]
> Ten przykład wymaga [Microsoft SQL Server](/sql).

Program Visual Studio udostępnia Edytor zestawu reguł w ramach Windows Workflow Foundation (WF). Możesz uruchomić tego edytora przez dwukrotne kliknięcie działania `Policy` w przepływie pracy; deserializacji zdefiniowanego obiektu zestawu reguł do pliku reguł skojarzonego z przepływem pracy (działanie `Policy` uruchamia wystąpienie zestawu reguł dla przepływu pracy). Plik. Rules jest kompilowany do zestawu jako zasób podczas budowania projektu przepływu pracy.

Składniki tego przykładu obejmują:

- Graficzny interfejs użytkownika zestawu reguł, za pomocą którego można edytować wersje zestawu reguł i zarządzać nimi w bazie danych.

- Usługa zestawu reguł, która jest skonfigurowana dla aplikacji hosta i uzyskuje dostęp do zestawów reguł z bazy danych.

- Działanie `ExternalPolicy`, które żąda zestawu reguł z usługi zestawu reguł i uruchamia zestaw reguł dla przepływu pracy.

Interakcje składników są pokazane na poniższej ilustracji. Poniższe sekcje opisują każdy składnik.

![Diagram przedstawiający przykładowe Omówienie zestawu narzędzi zewnętrznych zestawów reguł.](./media/external-ruleset-toolkit/ruleset-toolkit-overview.gif)

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ExternalRuleSetToolKit`

## <a name="ruleset-tool"></a>Narzędzie zestawu reguł

Poniższy obraz przedstawia zrzut ekranu narzędzia zestawu reguł. Z menu **Magazyn reguł** można załadować dostępne zestaw reguł z bazy danych i zapisać zmodyfikowane zestaw reguł z powrotem do sklepu. Plik konfiguracji aplikacji zawiera parametry połączenia bazy danych dla bazy danych zestawu reguł. Po uruchomieniu narzędzia automatycznie ładuje zestaw reguł ze skonfigurowanej bazy danych.

![Zrzut ekranu przedstawiający przeglądarkę zestawów reguł.](./media/external-ruleset-toolkit/ruleset-browser-dialog.gif)

Narzędzie zestawu reguł stosuje do zestawów reguł główne i pomocnicze numery wersji, co pozwala na równoczesne przechowywanie i zapisywanie wielu wersji (Narzędzie to nie zapewnia blokowania ani innych funkcji zarządzania konfiguracją oprócz możliwości obsługi wersji). Za pomocą narzędzia można tworzyć nowe wersje zestawu reguł lub usuwać istniejące. Po kliknięciu przycisku **Nowy**Narzędzie utworzy nową nazwę zestawu reguł i zastosuje wersję 1,0. Podczas kopiowania wersji narzędzie tworzy kopię wybranej wersji zestawu reguł, łącznie z zawartymi regułami i przypisuje nowe, unikatowe numery wersji. Numery wersji są oparte na numerach wersji istniejących zestawów reguł. Można zmienić nazwę zestawu reguł i numery wersji przy użyciu skojarzonych pól w formularzu.

Po kliknięciu przycisku **Edytuj reguły**zostanie uruchomiony Edytor zestawów reguł, jak pokazano na poniższej ilustracji:

![Zrzut ekranu przedstawiający Edytor zestawu reguł.](./media/external-ruleset-toolkit/ruleset-editor-dialog.gif)

Jest to ponowne hosting okna dialogowego edytora, które jest częścią dodatku Windows Workflow Foundation Visual Studio. Zapewnia ona te same funkcje, w tym obsługę technologii IntelliSense. Reguły są tworzone względem typu docelowego (takiego jak przepływ pracy), który jest skojarzony z zestawem reguł w narzędziu; Po kliknięciu przycisku **Przeglądaj** w oknie dialogowym Narzędzia główne zostanie wyświetlone okno dialogowe **selektora przepływu pracy/typu** , jak pokazano na rysunku 4.

![Wybór &#47;typu przepływu pracy](./media/71f08d57-e8f2-499e-8151-ece2cbdcabfd.gif "71f08d57-e8f2-499e-8151-ece2cbdcabfd")

Rysunek 4. selektor przepływu pracy/typu

Za pomocą okna dialogowego **selektora przepływu pracy/typu** można określić zestaw i określony typ w tym zestawie. Ten typ jest typem docelowym, względem którego zostały utworzone reguły (i uruchom). W wielu przypadkach typ docelowy to przepływ pracy lub inny typ działania. Można jednak uruchomić zestaw reguł dla dowolnego typu .NET.

Ścieżka do pliku zestawu i typ `name are stored with the` zestaw reguł w bazie danych, dzięki czemu po pobraniu zestawu reguł z bazy danych Narzędzie próbuje automatycznie załadować typ docelowy.

Po kliknięciu przycisku **OK** w oknie dialogowym **selektora przepływu pracy i typu** sprawdzana jest Walidacja wybranego typu względem zestawu reguł, aby upewnić się, że typ docelowy ma wszystkie elementy członkowskie, do których odwołują się reguły. Błędy są wyświetlane w oknie dialogowym **błędy walidacji** . Możesz wybrać opcję kontynuowania zmiany pomimo błędów lub kliknąć przycisk **Anuluj**. W menu **Narzędzia** w oknie dialogowym Narzędzia główne możesz kliknąć przycisk **Weryfikuj** , aby ponownie sprawdzić wersję zestawu reguł względem działania docelowego.

![Zrzut ekranu przedstawiający okno dialogowe błędy walidacji.](./media/external-ruleset-toolkit/validation-errors-dialog.png)

Z menu **dane** w narzędziu można importować i eksportować zestaw reguł. Po kliknięciu przycisku **Importuj**zostanie wyświetlone okno dialogowe Wybieranie plików, w którym można wybrać plik. rules. Może to być lub nie jest to plik początkowo utworzony w programie Visual Studio. Plik. rules powinien zawierać serializowane wystąpienie `RuleDefinitions`, które zawiera kolekcję warunków i kolekcję zestawów reguł. Narzędzie nie używa kolekcji warunków, ale używa formatu `RuleDefinitions`. rules, aby zezwolić na interakcję ze środowiskiem programu Visual Studio.

Po wybraniu pliku reguł zostanie wyświetlone okno dialogowe **Selektor zestawu reguł** . Możesz użyć okna dialogowego, aby wybrać zestaw reguł z pliku, który ma zostać zaimportowany (domyślnie określa wszystkie zestaw reguł). Zestawy reguł w pliku reguł nie mają numerów wersji, ponieważ ich przechowywanie wersji w projekcie WF jest takie samo jak wersja zestawu. W trakcie procesu importowania narzędzie automatycznie przypisuje następny dostępny numer wersji głównej (który można zmienić po zaimportowaniu). numery przypisanych wersji są widoczne na liście **selektora zestawów reguł** .

Dla każdego importowanego zestawu reguł Narzędzie próbuje zlokalizować skojarzony typ z folderu bin\Debug w lokalizacji pliku. rules (jeśli istnieje), na podstawie elementów członkowskich użytych w zestawie reguł. Jeśli narzędzie znajdzie wiele pasujących typów, próbuje wybrać typ na podstawie dopasowania między nazwą pliku reguł a nazwą typu (na przykład typ `Workflow1` odpowiada Workflow1. Rules). W przypadku istnienia wielu dopasowań zostanie wyświetlony monit o wybranie typu. Jeśli ten mechanizm autoidentyfikacji nie będzie mógł zlokalizować zgodnego zestawu lub typu, po zaimportowaniu można kliknąć przycisk **Przeglądaj** w oknie dialogowym głównym narzędzia, aby przejść do odpowiedniego typu. Na poniższej ilustracji przedstawiono selektor zestawu reguł:

![Zrzut ekranu przedstawiający okno dialogowe selektora zestawu reguł.](./media/external-ruleset-toolkit/ruleset-selector-dialog.gif)

Po kliknięciu przycisku **Eksportuj dane** z menu głównego narzędzia zostanie wyświetlone okno dialogowe **Selektor zestawu reguł** , w którym można określić zestaw reguł z bazy danych, która ma zostać wyeksportowana. Kliknięcie przycisku **OK**spowoduje wyświetlenie okna dialogowego **Zapisz plik** , w którym można określić nazwę i lokalizację pliku. reguł. Ponieważ plik. rules nie zawiera informacji o wersji, można wybrać tylko jedną wersję zestawu reguł o danej nazwie.

## <a name="policyfromservice-activity"></a>Działanie PolicyFromService

Kod działania `PolicyFromService` jest prosty. Działa podobnie jak działanie `Policy` dostarczone z WF, ale zamiast pobierania zestawu reguł docelowych z pliku reguł wywołuje usługę hosta, aby uzyskać wystąpienie zestawu reguł. Następnie uruchamia zestaw reguł w odniesieniu do głównego wystąpienia działania przepływu pracy.

Aby użyć działania w przepływie pracy, Dodaj odwołanie do `PolicyActivities` i `RuleSetService` zestawów z projektu przepływu pracy. Zapoznaj się z procedurą na końcu tego tematu, aby zapoznać się z omówieniem dodawania działania do przybornika.

Po umieszczeniu działania w przepływie pracy należy podać nazwę zestawu reguł, który ma zostać uruchomiony. Możesz wprowadzić nazwę jako wartość literału lub powiązać ją z zmienną lub właściwością przepływu pracy. Opcjonalnie możesz wprowadzić numery wersji dla określonego zestawu reguł, który ma zostać uruchomiony. Jeśli pozostawisz wartość domyślną 0 dla numerów wersji głównych i pomocniczych, numer najnowszej wersji w bazie danych zostanie automatycznie udostępniony dla działania.

## <a name="ruleset-service"></a>Usługa zestawu reguł

Usługa jest odpowiedzialna za pobranie określonej wersji zestawu reguł z bazy danych i zwrócenie jej do działania wywołującego. Jak wspomniano wcześniej, jeśli wartości głównej i pomocniczej wersji przesłane w wywołaniu `GetRuleSet` są równe 0, usługa Pobiera najnowszą wersję. W tym momencie nie istnieje buforowanie definicji zestawu reguł ani wystąpień; Podobnie nie ma żadnych funkcji do oznaczania wersji zestawu reguł jako "wdrożone", aby odróżnić je od zestawów reguł w toku.

Baza danych, do której ma dostęp usługa, powinna być skonfigurowana na hoście przy użyciu pliku konfiguracji aplikacji.

#### <a name="to-run-the-tool"></a>Aby uruchomić narzędzie

1. Folder, który konfiguruje tabelę zestawu reguł użytą przez narzędzie, a usługa zawiera plik Setup. SQL. Można uruchomić plik wsadowy Setup. cmd, aby utworzyć bazę danych reguł w programie SQL Express i skonfigurować tabelę zestawu reguł.

2. Jeśli edytujesz plik wsadowy lub Setup. SQL i określisz, że nie użyjesz programu SQL Express lub umieścisz tabelę w bazie danych o nazwie innej niż `Rules`, pliki konfiguracyjne aplikacji w narzędziu zestawu reguł i projekty `UsageSample` powinny być edytowane przy użyciu tych samych informacji.

3. Po uruchomieniu skryptu Setup. SQL można skompilować `ExternalRuleSetToolkit` rozwiązanie, a następnie uruchomić narzędzie zestawu reguł z projektu ExternalRuleSetTool.

4. `RuleSetToolkitUsageSample` rozwiązanie aplikacji konsolowej sekwencyjnego przepływu pracy zawiera przykładowy przepływ pracy. Przepływ pracy składa się z działania `PolicyFromService` i dwóch zmiennych, `orderValue` i `discount`, względem których jest uruchamiany docelowy zestaw reguł.

5. Aby użyć przykładu, skompiluj rozwiązanie `RuleSetToolkitUsageSample`. Następnie w menu głównym narzędzia zestawu reguł kliknij pozycję **dane — Importuj** i wskaż plik DiscountRuleSet. rules w folderze RuleSetToolkitUsageSample. Kliknij opcję **Magazyn reguł — Zapisz** , aby zapisać zaimportowany zestaw reguł do bazy danych programu.

6. Ponieważ zestaw `PolicyActivities` jest przywoływany z przykładowego projektu przepływu pracy, działanie `PolicyFromService` pojawia się w przepływie pracy. Nie jest jednak domyślnie wyświetlana w przyborniku. Aby dodać go do przybornika, wykonaj następujące czynności:

    - Kliknij prawym przyciskiem myszy Przybornik i wybierz pozycję **Wybierz elementy** (może to chwilę potrwać).

    - Gdy zostanie wyświetlone okno dialogowe **Wybierz elementy przybornika** , kliknij kartę **działania** .

    - Przejdź do zestawu `PolicyActivities` w rozwiązaniu `ExternalRuleSetToolkit` i kliknij przycisk **Otwórz**.

    - Upewnij się, że działanie `PolicyFromService` zostało zaznaczone w oknie dialogowym **Wybierz elementy przybornika** , a następnie kliknij przycisk **OK**.

    - Działanie powinno teraz pojawić się w przyborniku w kategorii **składniki RuleSetToolkitUsageSample** .

7. Usługa zestawu reguł jest już skonfigurowana na hoście aplikacji konsoli za pomocą następującej instrukcji w Program.cs.

    ```csharp
    workflowRuntime.AddService(new RuleSetService());
    ```

8. Możesz również skonfigurować usługę na hoście przy użyciu pliku konfiguracji; Szczegółowe informacje znajdują się w dokumentacji zestawu SDK.

9. Plik konfiguracji aplikacji zostanie dodany do projektu przepływu pracy, aby określić parametry połączenia dla bazy danych, która ma być używana przez usługę. Powinny to być te same parametry połączenia, które są używane przez narzędzie zestawu reguł, które wskazuje na bazę danych, która zawiera tabelę zestawu reguł.

10. Teraz można uruchomić projekt `RuleSetToolkitUsageSample` tak samo jak w przypadku każdej innej aplikacji konsolowej przepływu pracy. Naciśnij klawisz F5 lub CTRL + F5 w programie Visual Studio lub Uruchom bezpośrednio plik RuleSetToolkitUsageSample. exe.

    > [!NOTE]
    > Należy zamknąć narzędzie zestawu reguł, aby ponownie skompilować przykład użycia, ponieważ narzędzie ładuje przykładowy zestaw użycia.
