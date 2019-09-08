---
title: Włączanie wielu aktywnych zestawów wyników
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 1f8cb573d051970414f3962057f6329683eea5bd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782396"
---
# <a name="enabling-multiple-active-result-sets"></a>Włączanie wielu aktywnych zestawów wyników
Wiele aktywnych zestawów wyników (MARS) to funkcja, która współpracuje z SQL Server, aby umożliwić wykonywanie wielu partii na jednym połączeniu. Gdy Usługa MARS jest włączona do użytku z SQL Server, każdy użyty obiekt polecenia dodaje sesję do połączenia.  
  
> [!NOTE]
> Pojedyncza sesja MARS otwiera jedno połączenie logiczne dla MARS do użycia, a następnie jedno połączenie logiczne dla każdego aktywnego polecenia.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Włączanie i wyłączanie MARS w parametrach połączenia  
  
> [!NOTE]
> Poniższe parametry połączenia korzystają z przykładowej bazy danych **AdventureWorks** dołączonej do SQL Server. W określonych parametrach połączenia przyjęto założenie, że baza danych jest zainstalowana na serwerze o nazwie MSSQL1. Zmodyfikuj parametry połączenia jako niezbędne dla danego środowiska.  
  
 Funkcja MARS jest domyślnie wyłączona. Można ją włączyć, dodając parę słów kluczowych "MultipleActiveResultSets = true" do parametrów połączenia. Wartość "true" jest jedyną prawidłową wartością dla włączania MARS. Poniższy przykład pokazuje, jak nawiązać połączenie z wystąpieniem SQL Server i jak określić, że Usługa MARS powinna być włączona.  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 Można wyłączyć usługę MARS, dodając parę słów kluczowych "MultipleActiveResultSets = false" do parametrów połączenia. Wartość "false" jest jedyną prawidłową wartością do wyłączania usługi MARS. Poniższe parametry połączenia pokazują, jak wyłączyć usługę MARS.  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a>Specjalne uwagi dotyczące korzystania z usługi MARS  
 Ogólnie rzecz biorąc, istniejące aplikacje nie powinny wymagać modyfikacji w celu korzystania z połączenia z obsługą usługi MARS. Jeśli jednak chcesz korzystać z funkcji MARS w aplikacjach, należy zapoznać się z następującymi kwestiami szczególnymi.  
  
### <a name="statement-interleaving"></a>Przeplot instrukcji  
 Operacje MARS są wykonywane synchronicznie na serwerze. Wychodzące instrukcji SELECT i BULK INSERT są dozwolone. Jednak instrukcje języka manipulowania danymi (DML) i języka definicji danych (DDL) wykonują niepodzielną. Wszystkie instrukcje, które próbują wykonać podczas wykonywania niepodzielnej partii, są blokowane. Wykonywanie równoległe na serwerze nie jest funkcją MARS.  
  
 Jeśli dwie partie są przesyłane w ramach połączenia MARS, jeden z nich zawierający instrukcję SELECT, drugi zawierający instrukcję DML, może rozpocząć wykonywanie w ramach wykonywania instrukcji SELECT. Jednakże instrukcja DML musi być uruchamiana do zakończenia przed wykonaniem instrukcji SELECT. Jeśli obie te instrukcje są uruchomione w ramach tej samej transakcji, wszelkie zmiany wprowadzone przez instrukcję DML po rozpoczęciu wykonywania instrukcji SELECT nie są widoczne dla operacji odczytu.  
  
 Instrukcja WAITFOR wewnątrz instrukcji SELECT nie zwraca transakcji w oczekiwany sposób, czyli do momentu utworzenia pierwszego wiersza. Oznacza to, że żadne inne partie nie mogą być wykonywane w ramach tego samego połączenia podczas oczekiwania instrukcji WAITFOR.  
  
### <a name="mars-session-cache"></a>Pamięć podręczna sesji MARS  
 Po otwarciu połączenia z włączonym usługą MARS zostanie utworzona sesja logiczna, która dodaje dodatkowe obciążenie. Aby zminimalizować obciążenie i zwiększyć wydajność, **Klient SqlClient** buforuje sesję Mars w ramach połączenia. Pamięć podręczna zawiera maksymalnie 10 sesji MARS. Ta wartość nie jest dostosowywana do użytkownika. Jeśli limit sesji zostanie osiągnięty, zostanie utworzona nowa sesja — błąd nie zostanie wygenerowany. Pamięć podręczna i sesje zawarte w niej są przyłączone do połączenia; nie są one udostępniane między połączeniami. Po wydaniu sesji jest ona zwracana do puli, chyba że górny limit puli został osiągnięty. Jeśli pula pamięci podręcznej jest pełna, sesja zostanie zamknięta. Sesje MARS nie wygasną. Są czyszczone tylko wtedy, gdy obiekt połączenia zostanie usunięty. Pamięć podręczna sesji MARS nie jest wstępnie załadowana. Jest ona ładowana, ponieważ aplikacja wymaga więcej sesji.  
  
### <a name="thread-safety"></a>Bezpieczeństwo wątków  
 Operacje MARS nie są bezpieczne wątkowo.  
  
### <a name="connection-pooling"></a>Pula połączeń  
 Połączenia z obsługą usługi MARS są umieszczane w puli, podobnie jak inne połączenia. Jeśli aplikacja otworzy dwa połączenia, jeden z włączonym usługą MARS i jeden z wyłączonym MARS, dwa połączenia są w różnych pulach. Aby uzyskać więcej informacji, zobacz [SQL Servering pooling (ADO.NET)](../sql-server-connection-pooling.md).  
  
### <a name="sql-server-batch-execution-environment"></a>SQL Server środowiska wykonawczego partii  
 Po otwarciu połączenia jest zdefiniowane środowisko domyślne. To środowisko jest następnie kopiowane do logicznej sesji MARS.  
  
 Środowisko wykonywania wsadowego obejmuje następujące składniki:  
  
- Ustawianie opcji (na przykład ANSI_NULLS, DATE_FORMAT, LANGUAGE, wartość PARAMETRU TEXTSIZE)  
  
- Kontekst zabezpieczeń (rola użytkownika/aplikacji)  
  
- Kontekst bazy danych (bieżąca baza danych)  
  
- Zmienne stanu wykonania (@ERRORna przykład @, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)  
  
- Tymczasowe tabele najwyższego poziomu  
  
 W przypadku usługi MARS do połączenia jest skojarzone domyślne środowisko wykonawcze. Każda nowa partia, która rozpoczyna wykonywanie w ramach danego połączenia, otrzymuje kopię domyślnego środowiska. Za każdym razem, gdy kod jest wykonywany w ramach danej partii, wszystkie zmiany wprowadzone w środowisku są ograniczone do określonej partii. Po zakończeniu wykonywania ustawienia wykonywania są kopiowane do środowiska domyślnego. W przypadku pojedynczej partii, która wystawia kilka poleceń, które mają być wykonywane sekwencyjnie w ramach tej samej transakcji, semantyka jest taka sama jak w przypadku połączeń obejmujących wcześniejszych klientów lub serwery.  
  
### <a name="parallel-execution"></a>Wykonywanie równoległe  
 Usługa MARS nie została zaprojektowana, aby usunąć wszystkie wymagania dotyczące wielu połączeń w aplikacji. Jeśli aplikacja wymaga prawdziwie równoległego wykonywania poleceń na serwerze, należy użyć wielu połączeń.  
  
 Rozważmy na przykład Poniższy scenariusz. Tworzone są dwa obiekty poleceń: jeden do przetwarzania zestawu wyników i drugi do aktualizowania danych; korzystają one ze wspólnego połączenia za pośrednictwem protokołu MARS. W tym scenariuszu `Transaction`.`Commit` Niepowodzenie w aktualizacji, dopóki wszystkie wyniki nie zostaną odczytane z pierwszego obiektu polecenia, co spowoduje następujący wyjątek:  
  
 Komunikat: Kontekst transakcji jest używany przez inną sesję.  
  
 Źródło: Dostawca danych SqlClient platformy .NET  
  
 Oczekiwano: (wartość null)  
  
 Odbieranie System.Data.SqlClient.SqlException  
  
 Istnieją trzy opcje obsługi tego scenariusza:  
  
1. Rozpocznij transakcję po utworzeniu czytnika, aby nie była częścią transakcji. Każda aktualizacja zmieni się na własną transakcję.  
  
2. Zatwierdź wszystkie prace po zamknięciu czytnika. Jest to możliwe w przypadku znacznej partii aktualizacji.  
  
3. Nie używaj MARS; Zamiast tego należy użyć oddzielnego połączenia dla każdego obiektu polecenia, tak jak przed MARS.  
  
### <a name="detecting-mars-support"></a>Wykrywanie obsługi MARS  
 Aplikacja może sprawdzić obsługę Mars, odczytując `SqlConnection.ServerVersion` wartość. Liczba główna powinna wynosić 9 dla SQL Server 2005 i 10 dla SQL Server 2008.  
  
## <a name="see-also"></a>Zobacz także

- [Wiele aktywnych zestawów wyników (MARS)](multiple-active-result-sets-mars.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
