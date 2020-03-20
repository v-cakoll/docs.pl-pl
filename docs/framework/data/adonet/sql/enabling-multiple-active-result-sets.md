---
title: Włączanie wielu aktywnych zestawów wyników
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 72125be835298218e5445fe1915d6a17f5008bb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148728"
---
# <a name="enabling-multiple-active-result-sets"></a>Włączanie wielu aktywnych zestawów wyników
Wiele aktywnych zestawów wyników (MARS) to funkcja, która współpracuje z programem SQL Server, aby umożliwić wykonywanie wielu partii na jednym połączeniu. Gdy mars jest włączony do użytku z programem SQL Server, każdy obiekt polecenia używane dodaje sesję do połączenia.  
  
> [!NOTE]
> Pojedyncza sesja MARS otwiera jedno połączenie logiczne dla marsu do użycia, a następnie jedno połączenie logiczne dla każdego aktywnego polecenia.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Włączanie i wyłączanie marsa w ciągu połączenia  
  
> [!NOTE]
> Następujące parametry połączenia używają przykładowej bazy danych **AdventureWorks** dołączonej do programu SQL Server. Podane parametry połączenia zakładają, że baza danych jest zainstalowana na serwerze o nazwie MSSQL1. Zmodyfikuj parametry połączenia zgodnie z oczekiwaniami środowiska.  
  
 Funkcja MARS jest domyślnie wyłączona. Można ją włączyć, dodając parę słów kluczowych "MultipleActiveResultSets=True" do ciągu połączenia. "True" jest jedyną prawidłową wartością włączania mars. W poniższym przykładzie pokazano, jak połączyć się z wystąpieniem programu SQL Server i jak określić, że mars powinien być włączony.  
  
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
  
 Mars można wyłączyć, dodając parę słów kluczowych "MultipleActiveResultSets=False" do ciągu połączenia. "False" jest jedyną prawidłową wartością wyłączania mars. Poniższy parametry połączenia pokazuje, jak wyłączyć MARS.  
  
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
  
## <a name="special-considerations-when-using-mars"></a>Uwagi specjalne podczas korzystania z MARS  
 Ogólnie rzecz biorąc istniejące aplikacje nie powinny wymagać modyfikacji, aby używać połączenia z obsługą mars. Jednak jeśli chcesz używać funkcji MARS w aplikacjach, należy zrozumieć następujące kwestie szczególne.  
  
### <a name="statement-interleaving"></a>Przeplatanie oświadczenia  
 Operacje MARS są wykonywane synchronicznie na serwerze. Dozwolone jest przeplatanie instrukcji select i BULK INSERT. Jednak instrukcje języka manipulowania danymi (DML) i języka definicji danych (DDL) są wykonywane niepodzielnie. Wszelkie instrukcje próby wykonania podczas wykonywania partii atomowej są blokowane. Wykonywanie równoległe na serwerze nie jest funkcją MARS.  
  
 Jeśli dwie partie są przesyłane w ramach połączenia MARS, jeden z nich zawierający select instrukcji, drugi zawierający instrukcję DML, DML można rozpocząć wykonywanie w ramach wykonywania SELECT instrukcji. Jednak instrukcja DML musi zostać ukończona, zanim instrukcja SELECT może poczynić postępy. Jeśli obie instrukcje są uruchomione w ramach tej samej transakcji, wszelkie zmiany wprowadzone przez instrukcję DML po uruchomieniu instrukcji SELECT nie są widoczne dla operacji odczytu.  
  
 Instrukcja WAITFOR wewnątrz instrukcji SELECT nie daje transakcji podczas oczekiwania, czyli do momentu wyprodukowanego pierwszego wiersza. Oznacza to, że żadne inne partie można wykonać w ramach tego samego połączenia, podczas gdy waitfor instrukcja oczekuje.  
  
### <a name="mars-session-cache"></a>Pamięć podręczna sesji MARS  
 Po otwarciu połączenia z włączoną funkcją MARS tworzona jest sesja logiczna, która dodaje dodatkowe obciążenie. Aby zminimalizować obciążenie i zwiększyć wydajność, **SqlClient** buforuje sesję MARS w ramach połączenia. Pamięć podręczna zawiera co najwyżej 10 sesji MARS. Ta wartość nie jest regulowana przez użytkownika. Po osiągnięciu limitu sesji tworzona jest nowa sesja — błąd nie jest generowany. Pamięć podręczna i sesje zawarte w nim są na połączenie; nie są one współużytkowane przez połączenia. Po zwolnieniu sesji jest zwracany do puli, chyba że górny limit puli został osiągnięty. Jeśli pula pamięci podręcznej jest pełna, sesja jest zamknięta. Sesje MARS nie wygasają. Są one czyszczone tylko wtedy, gdy obiekt połączenia jest usuwany. Pamięć podręczna sesji MARS nie jest wstępnie załadowana. Jest ładowany, ponieważ aplikacja wymaga więcej sesji.  
  
### <a name="thread-safety"></a>Bezpieczeństwo wątków  
 Operacje MARS nie są bezpieczne dla wątków.  
  
### <a name="connection-pooling"></a>Pula połączeń  
 Połączenia z obsługą mars są połączone jak każde inne połączenie. Jeśli aplikacja otworzy dwa połączenia, jedno z włączoną funkcją MARS i jedno z wyłączonym marsem, dwa połączenia znajdują się w oddzielnych pulach. Aby uzyskać więcej informacji, zobacz [Sql Server Connection Pooling (ADO.NET)](../sql-server-connection-pooling.md).  
  
### <a name="sql-server-batch-execution-environment"></a>Środowisko wykonywania wsadowego programu SQL Server  
 Po otwarciu połączenia jest definiowane środowisko domyślne. To środowisko jest następnie kopiowane do logicznej sesji MARS.  
  
 Środowisko wykonywania partii zawiera następujące składniki:  
  
- Ustaw opcje (na przykład ANSI_NULLS, DATE_FORMAT, język, teksty)  
  
- Kontekst zabezpieczeń (rola użytkownika/aplikacji)  
  
- Kontekst bazy danych (bieżąca baza danych)  
  
- Zmienne stanu wykonania (na@ERRORprzykład@ROWCOUNT@@FETCH_STATUS @IDENTITY, @ , @ )  
  
- Tabele tymczasowe najwyższego poziomu  
  
 W przypadku marsa domyślne środowisko wykonywania jest skojarzone z połączeniem. Każda nowa partia, która rozpoczyna wykonywanie w ramach danego połączenia otrzymuje kopię środowiska domyślnego. Za każdym razem, gdy kod jest wykonywany w ramach danej partii, wszystkie zmiany wprowadzone w środowisku są ograniczone do określonej partii. Po zakończeniu wykonywania ustawienia wykonywania są kopiowane do środowiska domyślnego. W przypadku pojedynczej partii wydawania kilku poleceń, które mają być wykonywane sekwencyjnie w ramach tej samej transakcji, semantyka są takie same jak te, które są udostępniane przez połączenia z udziałem wcześniejszych klientów lub serwerów.  
  
### <a name="parallel-execution"></a>Równoległego  
 Mars nie jest przeznaczony do usuwania wszystkich wymagań dla wielu połączeń w aplikacji. Jeśli aplikacja wymaga prawdziwego równoległego wykonywania poleceń względem serwera, należy użyć wielu połączeń.  
  
 Rozważmy na przykład następujący scenariusz. Two command objects are created, one for processing a result set and another for updating data; mają wspólne połączenie przez MARS. W tym scenariuszu `Transaction`.`Commit` kończy się niepowodzeniem w aktualizacji, dopóki wszystkie wyniki nie zostaną odczytane na pierwszym obiekcie polecenia, co daje następujący wyjątek:  
  
 Komunikat: Kontekst transakcji używany przez inną sesję.  
  
 Źródło: Dostawca danych .NET SqlClient  
  
 Oczekiwano: (null)  
  
 Odebrane: System.Data.SqlClient.SqlException  
  
 Istnieją trzy opcje obsługi tego scenariusza:  
  
1. Uruchom transakcję po utworzeniu czytnika, tak aby nie była częścią transakcji. Każda aktualizacja staje się wtedy własną transakcją.  
  
2. Zaobrobić całą pracę po zamknięciu czytnika. Ma to potencjał dla znacznej partii aktualizacji.  
  
3. Nie używaj MARS; zamiast tego należy użyć oddzielnego połączenia dla każdego obiektu polecenia, tak jak miało to być przed mars.  
  
### <a name="detecting-mars-support"></a>Wykrywanie obsługi mars  
 Aplikacja może sprawdzić mars obsługi, `SqlConnection.ServerVersion` odczytając wartość. Główna liczba powinna wynosić 9 dla programu SQL Server 2005 i 10 dla programu SQL Server 2008.  
  
## <a name="see-also"></a>Zobacz też

- [Wiele aktywnych zestawów wyników (MARS)](multiple-active-result-sets-mars.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
