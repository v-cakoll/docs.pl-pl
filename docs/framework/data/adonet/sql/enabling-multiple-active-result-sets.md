---
title: "Włączanie wielu aktywnych zestawów wyników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0235a63a24f81968718d526ff676b023c060b9a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-multiple-active-result-sets"></a>Włączanie wielu aktywnych zestawów wyników
Wiele aktywnych zestawów wyników (MARS) to funkcja, która współdziała z programem SQL Server, aby umożliwić wykonywanie wielu instancji na jedno połączenie. Po włączeniu MARS do użytku z programem SQL Server każdego obiektu polecenia używane dodaje sesji połączenia.  
  
> [!NOTE]
>  Jednej sesji MARS otwiera jedno połączenie logiczne dla MARS do użycia, a następnie jedno połączenie logiczne dla każdego aktywnego polecenia.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Włączanie i wyłączanie MARS w parametrach połączenia  
  
> [!NOTE]
>  Użyj następujących ciągów połączenia przykładu **AdventureWorks** bazy danych programu SQL Server. Podane parametry połączenia założono, że baza danych jest zainstalowana na serwerze o nazwie MSSQL1. Zmodyfikuj parametry połączenia w razie potrzeby dla danego środowiska.  
  
 Funkcja MARS jest domyślnie wyłączone. Można ją włączyć przez dodanie "MultipleActiveResultSets = True" pary — słowo kluczowe parametrów połączenia. "Wartość prawda" jest jedyną poprawną wartością dla włączania elementu MARS. W poniższym przykładzie pokazano sposób nawiązywania połączenia z wystąpieniem programu SQL Server i określić, że powinno być włączone MARS.  
  
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
  
 Można wyłączyć MARS, dodając "MultipleActiveResultSets = False" pary — słowo kluczowe parametrów połączenia. "Fałsz" jest jedyną poprawną wartością dla wyłączenie MARS. Następujący ciąg połączenia pokazano, jak wyłączyć MARS.  
  
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
  
## <a name="special-considerations-when-using-mars"></a>Szczególne zagadnienia dotyczące używania MARS  
 Ogólnie rzecz biorąc istniejące aplikacje nie będą modyfikacji połączenie włączone MARS. Jednak jeśli chcesz używać funkcji MARS w aplikacji, zapoznaj się następujące uwagi.  
  
### <a name="statement-interleaving"></a>Naprzemiennego wykonywania instrukcji  
 Operacje MARS synchronicznie wykonania na serwerze. Instrukcja naprzemiennego wykonywania instrukcji SELECT i BULK INSERT jest dozwolone. Jednak język edycji danych (DML) i instrukcje (DDL) języka definicji danych wykonać automatycznie. Wszystkie instrukcje próby wykonania podczas wykonywania wsadowego atomic są zablokowane. Wykonywanie równoległe na serwerze nie jest funkcją MARS.  
  
 Jeśli dwie partie są przedstawiane w ramach połączenia MARS, jeden z nich zawierający instrukcję SELECT innych zawierająca instrukcję DML DML można rozpocząć wykonywania w ramach wykonywania instrukcji SELECT. Jednak do ukończenia należy uruchomić instrukcji DML, przed instrukcją SELECT może postęp. Jeśli zarówno instrukcje działają w ramach jednej transakcji, zmiany wprowadzone przez instrukcję DML, po uruchomieniu wykonywania instrukcji SELECT nie są widoczne dla operacji odczytu.  
  
 Instrukcję WAITFOR wewnątrz instrukcji SELECT nie yield transakcji, gdy oczekuje, oznacza to, aż do pierwszego wiersza jest generowany. Oznacza to, że nie inne instancje może zostać uruchomiony w ramach tego samego połączenia, gdy oczekuje instrukcji WAITFOR.  
  
### <a name="mars-session-cache"></a>Pamięci podręcznej sesji MARS  
 Po otwarciu połączenia z włączoną MARS, tworzona jest logiczną sesji, która dodaje dodatkowe obciążenie. Aby zminimalizować koszty i zwiększyć wydajność, **SqlClient** buforuje sesji MARS w ciągu połączenia. Pamięć podręczna zawiera maksymalnie 10 sesji MARS. Ta wartość nie jest regulowany użytkownika. Po osiągnięciu limitu czasu sesji zostanie utworzona nowa sesja — nie zostanie wygenerowany błąd. Pamięci podręcznej i zawarte w niej sesji są na połączenie. nie są współdzielone przez połączenia. Po zwolnieniu sesji, chyba że osiągnęła górny limit puli jest zwracana do puli. Jeśli w puli pamięci podręcznej jest pełna, sesja jest zamknięta. Sesji MARS nie wygasa. Obecny one tylko są czyszczone po usunięciu obiektu połączenia. Pamięci podręcznej sesji MARS nie jest załadowane. Jest on załadowany jako aplikacji wymaga więcej sesji.  
  
### <a name="thread-safety"></a>Bezpieczeństwo wątków  
 Operacje MARS nie są wątkowo.  
  
### <a name="connection-pooling"></a>Pula połączeń  
 Włączone MARS połączeń są grupowane w pulach podobnie jak inne połączenie. Jeśli aplikacja otwiera dwa połączenia, jeden z MARS włączone i jeden z MARS wyłączone, dwa połączenia są w osobnych pulach. Aby uzyskać więcej informacji, zobacz [programu SQL Server połączenia buforowanie (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="sql-server-batch-execution-environment"></a>Środowiska wykonania programu SQL Server partii  
 Po otwarciu połączenia jest zdefiniowana domyślnego środowiska. To środowisko jest następnie skopiowana do logicznego sesji MARS.  
  
 Środowiska wykonawczego wsadowego obejmuje następujące składniki:  
  
-   Ustawianie opcji (na przykład ANSI_NULLS, DATE_FORMAT, języka, wartość parametru TEXTSIZE)  
  
-   Kontekst zabezpieczeń (rola użytkownika/aplikacji)  
  
-   Kontekst bazy danych (bieżącej bazy danych)  
  
-   Zmienne stanu wykonywania (na przykład @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)  
  
-   Tabele tymczasowe najwyższego poziomu  
  
 Z MARS środowiska wykonawczego domyślny jest skojarzona z połączeniem. Co nowego zadania wsadowego, który rozpoczyna wykonywanie w ramach danego połączenia wysyłana kopia domyślnego środowiska. Zawsze, gdy kod jest wykonywane w ramach danej partii, wszystkie zmiany wprowadzone do środowiska dostosowanych do określonego zadania wsadowego. Po zakończeniu wykonywania, wykonanie ustawienia są kopiowane do domyślnego środowiska. W przypadku pojedynczej partii wystawiania kilka poleceń do wykonania po kolei w tej samej transakcji semantyki są takie same jak te udostępniane przez połączeń obejmujących starszych klientów lub serwerów.  
  
### <a name="parallel-execution"></a>Wykonywanie równoległe  
 MARS nie jest przeznaczony do usunięcia wszystkich wymagań dotyczących wiele połączeń w aplikacji. Jeśli aplikacja wymaga true równoległe wykonywanie polecenia na serwerze, należy używać wielu połączeń.  
  
 Na przykład rozważmy następujący scenariusz. Dwa obiekty polecenia są tworzone, jeden dla przetwarzania zestawu wyników i drugi dla aktualizowania danych. mają wspólnego połączenia za pośrednictwem MARS. W tym scenariuszu `Transaction`.`Commit` kończy się niepowodzeniem przy aktualizacji do momentu odczytania wszystkich wyników na pierwszy obiekt polecenia reaguje następujący wyjątek:  
  
 Komunikat o błędzie: Kontekst transakcji jest używany przez inną sesję.  
  
 Źródło: Dostawca danych SqlClient programu .net  
  
 Oczekiwano: (null)  
  
 Odebrano: System.Data.SqlClient.SqlException  
  
 Dostępne są trzy opcje do obsługi tego scenariusza:  
  
1.  Uruchom transakcji po utworzeniu czytnik, dzięki czemu nie jest częścią transakcji. Każda aktualizacja staje się własną transakcji.  
  
2.  Zatwierdź wszystkie wykonywane po czytnik jest zamknięty. To może potencjalnie znaczny pakietu aktualizacji.  
  
3.  Nie używaj MARS; Zamiast tego użyć osobnego połączenia dla każdego obiektu polecenia, podobnie jak przed MARS.  
  
### <a name="detecting-mars-support"></a>Wykrywanie MARS pomocy technicznej  
 Aplikację można sprawdzić MARS obsługuje odczytując `SqlConnection.ServerVersion` wartość. Główny numer powinna być 9 dla programu SQL Server 2005 i 10 dla programu SQL Server 2008.  
  
## <a name="see-also"></a>Zobacz też  
 [Wiele aktywnych zestawów wyników (MARS)](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
