---
title: Włączanie wielu aktywnych zestawów wyników
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 073cd3a57f254f639fac44900ff6bf022e1fb165
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504309"
---
# <a name="enabling-multiple-active-result-sets"></a>Włączanie wielu aktywnych zestawów wyników
Wiele aktywnych zestawów wyników (MARS) jest funkcją, która współdziała z programem SQL Server, aby umożliwić wykonywanie wielu instancji na pojedyncze połączenie. Po włączeniu MARS do użytku z programem SQL Server każdego obiektu polecenia używane dodaje sesji połączenia.  
  
> [!NOTE]
>  Jednej sesji MARS otwiera jedno połączenie logiczne dla MARS do użycia i następnie jedno połączenie logiczne dla każdego aktywnego polecenia.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Włączanie i wyłączanie usług MARS w parametrach połączenia  
  
> [!NOTE]
>  Następujące parametry połączenia, skorzystaj z przykładu **AdventureWorks** bazy danych z programem SQL Server. Parametry połączenia, pod warunkiem przyjęto założenie, że baza danych jest zainstalowana na serwerze o nazwie MSSQL1. Modyfikowanie parametrów połączenia, zgodnie z potrzebami w danym środowisku.  
  
 Funkcja MARS jest domyślnie wyłączone. Można ją włączyć, dodając "MultipleActiveResultSets = True" parę — słowo kluczowe parametrów połączenia. "True" jest jedyną prawidłową wartością włączania MARS. Poniższy przykład pokazuje, jak połączyć się z wystąpieniem programu SQL Server i jak określić, że powinno być włączone MARS.  
  
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
  
 Można wyłączyć MARS, dodając "MultipleActiveResultSets = False" parę — słowo kluczowe parametrów połączenia. "Fałsz" jest jedyną prawidłową wartością dla wyłączenie MARS. Następujące parametry połączenia pokazuje, jak wyłączyć MARS.  
  
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
  
## <a name="special-considerations-when-using-mars"></a>Specjalne uwagi dotyczące korzystania z usług MARS  
 Ogólnie rzecz biorąc istniejące aplikacje nie powinni modyfikacji przy użyciu połączenia z obsługą usług MARS. Jednak jeśli chcesz korzystać z funkcji usług MARS w swoich aplikacjach, należy zrozumieć następujące uwagi.  
  
### <a name="statement-interleaving"></a>Instrukcji z przeplotem  
 Operacje MARS były uruchamiane synchronicznie na serwerze. Instrukcji z przeplotem instrukcji SELECT i BULK INSERT jest dozwolone. Jednak język edycji danych (DML) oraz instrukcje (DDL) języka definicji danych wykonywane atomowo. Instrukcje, wszelkie próby wykonania operacji podczas wykonywania partii atomic są blokowane. Wykonywanie równoległe na serwerze nie jest funkcją MARS.  
  
 Jeśli dwie partie są przesyłane w ramach połączenia MARS, jeden z nich zawierający instrukcję SELECT innych instrukcji DML, zawierającej DML można rozpocząć wykonywania w obrębie wykonywania instrukcji SELECT. Jednak do zakończenia należy uruchomić instrukcji DML, zanim można robić postępów w instrukcji SELECT. Jeśli obie instrukcje są uruchomione w ramach tej samej transakcji, wszelkie zmiany wprowadzone przez instrukcję DML, po uruchomieniu wykonania instrukcji SELECT nie są widoczne dla operacji odczytu.  
  
 Instrukcję WAITFOR wewnątrz instrukcji SELECT nie przekazuje transakcji, gdy trwa oczekiwanie, oznacza to, aż pierwszy wiersz jest generowany. Oznacza to, że nie inne instancje można wykonać w ramach tego samego połączenia, gdy instrukcja WAITFOR oczekuje.  
  
### <a name="mars-session-cache"></a>Pamięci podręcznej sesji MARS  
 Gdy połączenie jest otwarte z włączoną MARS, tworzona jest sesji logicznej, która dodaje dodatkowe obciążenie. Aby zminimalizować koszty i zwiększyć wydajność, **SqlClient** zapisuje w pamięci podręcznej sesji MARS w ramach połączenia. Pamięć podręczna zawiera maksymalnie 10 MARS sesji. Ta wartość nie jest użytkownikiem zmieniane. W przypadku osiągnięcia limitu czasu sesji zostanie utworzona nowa sesja — nie zostanie wygenerowany błąd. Pamięci podręcznej i sesje zawarte w nim znajdują się na połączenie. nie są współdzielone przez połączenia. Sesja jest zwalniana, są zwracane do puli, o ile nie osiągnęła górny limit puli. Jeśli w puli pamięci podręcznej jest pełna, sesja jest zamknięta. Sesje usług MARS nie wygasa. Obecny one tylko są czyszczone po usunięciu obiektu połączenia. Pamięci podręcznej sesji MARS jest nie jest załadowany. Jest on ładowany jako aplikacja wymaga więcej sesji.  
  
### <a name="thread-safety"></a>Bezpieczeństwo wątków  
 Operacje MARS nie są wątkowo.  
  
### <a name="connection-pooling"></a>Pula połączeń  
 Włączone MARS połączeń są grupowane w pulach podobnie jak inne połączenia. Jeśli aplikacja zostanie otwarta dwóch połączeń: jedna z MARS włączone, a druga MARS wyłączone dwa połączenia znajdują się w oddzielnych pul. Aby uzyskać więcej informacji, zobacz [programu SQL Server połączenia puli (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="sql-server-batch-execution-environment"></a>Środowisko wykonywania wsadowego serwera SQL  
 Po otwarciu połączenia jest zdefiniowana środowiska domyślnego. To środowisko jest następnie kopiowana do sesji logicznej MARS.  
  
 Środowisko wykonawcze usługi batch obejmuje następujące składniki:  
  
-   Ustawianie opcji (na przykład ANSI_NULLS DATE_FORMAT, języka, wartość parametru TEXTSIZE)  
  
-   Kontekst zabezpieczeń (rola użytkownika/aplikacji)  
  
-   Kontekst bazy danych (bieżącej bazy danych)  
  
-   Zmienne stanu wykonywania (na przykład @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)  
  
-   Tabele tymczasowe najwyższego poziomu  
  
 Za pomocą usług MARS domyślne środowisko wykonywania jest skojarzona z połączeniem. Co nową partię, który rozpoczyna wykonywanie w ramach danego połączenia otrzymuje kopię środowiska domyślnego. Zawsze, gdy kod jest wykonywany w danej partii, wszystkie zmiany wprowadzone w środowisku są ograniczone do określonej usługi batch. Po zakończeniu wykonywania, ustawienia wykonywania są kopiowane do środowiska domyślnego. W przypadku jednej partii wystawianie kilka poleceń do wykonania po kolei w ramach tej samej transakcji semantyka są takie same, jak udostępniany przez połączeń obejmujących starszych klientów lub serwerów.  
  
### <a name="parallel-execution"></a>Wykonywanie równoległe  
 MARS nie jest przeznaczony do usunięcia wszystkich wymagań dla wielu połączeń w aplikacji. Jeśli aplikacja musi prawdziwe równoległe wykonywanie poleceń na serwerze, należy użyć wielu połączeń.  
  
 Na przykład rozważmy następujący scenariusz. Polecenie tworzone są dwa obiekty, jeden dla przetwarzania zestawu wyników i inny wpis dla aktualizacji danych. współużytkują one typowe połączenia przez MARS. W tym scenariuszu `Transaction`.`Commit` kończy się niepowodzeniem po aktualizacji do momentu odczytania wszystkich wyników na pierwszy obiekt polecenia reaguje następujący wyjątek:  
  
 Komunikat o błędzie: Kontekst transakcji jest używany przez inną sesję.  
  
 Źródło: Dostawca danych SqlClient programu .net  
  
 Oczekiwano: (null)  
  
 Received: System.Data.SqlClient.SqlException  
  
 Dostępne są trzy opcje do obsługi tego scenariusza:  
  
1.  Uruchomić transakcję po utworzeniu czytnika, tak aby nie jest częścią transakcji. Każda aktualizacja staje się własną transakcji.  
  
2.  Zatwierdź całą pracę po czytnik jest zamykany. To może potencjalnie znaczny partii aktualizacji.  
  
3.  Nie używaj MARS; Zamiast tego użyć osobnego połączenia dla każdego obiektu polecenia, podobnie jak przed MARS.  
  
### <a name="detecting-mars-support"></a>Wykrywanie MARS pomocy technicznej  
 Aplikację można sprawdzić MARS pomocy technicznej, czytając `SqlConnection.ServerVersion` wartość. Numer główny powinna być 9 dla programu SQL Server 2005 i 10 programu SQL Server 2008.  
  
## <a name="see-also"></a>Zobacz też  
 [Wiele aktywnych zestawów wyników (MARS)](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
