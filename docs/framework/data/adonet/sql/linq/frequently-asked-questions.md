---
title: Często zadawane pytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 3cc879e97438138554f1d39cf588e01bfbba28a6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634706"
---
# <a name="frequently-asked-questions"></a>Często zadawane pytania

W poniższych sekcjach przedstawiono kilka typowych problemów, które mogą wystąpić podczas implementowania LINQ.

[Rozwiązywanie problemów](troubleshooting.md)z dodatkowymi problemami.

## <a name="cannot-connect"></a>Nie można nawiązać połączenia

PYTANIE: Nie mogę nawiązać połączenia z moją bazą danych.

A. Upewnij się, że parametry połączenia są poprawne i że wystąpienie SQL Server jest uruchomione. Należy również pamiętać, że [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wymaga włączenia protokołu potoków nazwanych. Aby uzyskać więcej informacji, zobacz [uczenie się według przewodników](learning-by-walkthroughs.md).

## <a name="changes-to-database-lost"></a>Utracone zmiany w bazie danych

PYTANIE: Po zmianie danych w bazie danych, ale gdy reran moją aplikację, zmiana nie została już tam osiągnięta.

A. Upewnij się, że <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, aby zapisać wyniki w bazie danych.

## <a name="database-connection-open-how-long"></a>Połączenie z bazą danych: Otwórz jak długo?

PYTANIE: Jak długo zostanie otwarte moje połączenie z bazą danych?

A. Połączenie jest zazwyczaj otwarte, dopóki nie zostaną zużyte wyniki zapytania. Jeśli spodziewasz się czasu na przetworzenie wszystkich wyników i nie będzie to odróżnienia od buforowania wyników, Zastosuj <xref:System.Linq.Enumerable.ToList%2A> do zapytania. W typowych scenariuszach, w których każdy obiekt jest przetwarzany tylko jeden raz, model przesyłania strumieniowego jest wyższy zarówno do `DataReader`, jak i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].

Dokładne szczegóły użycia połączenia zależą od następujących:

- Stan połączenia, jeśli <xref:System.Data.Linq.DataContext> jest konstruowany przy użyciu obiektu połączenia.

- Ustawienia parametrów połączenia (na przykład włączenie wielu aktywnych zestawów wyników (MARS). Aby uzyskać więcej informacji, zobacz [wiele aktywnych zestawów wyników (MARS)](../multiple-active-result-sets-mars.md).

## <a name="updating-without-querying"></a>Aktualizowanie bez wykonywania zapytań

PYTANIE: Czy mogę zaktualizować dane tabeli bez uprzedniego zapytania do bazy danych?

A. Mimo że [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie ma poleceń aktualizacji opartych na zestawie, można użyć jednej z następujących technik do aktualizacji bez uprzedniego zapytania:

- Użyj <xref:System.Data.Linq.DataContext.ExecuteCommand%2A>, aby wysłać kod SQL.

- Utwórz nowe wystąpienie obiektu i zainicjuj wszystkie bieżące wartości (pola), które mają wpływ na tę aktualizację. Następnie Dołącz obiekt do <xref:System.Data.Linq.DataContext> przy użyciu <xref:System.Data.Linq.Table%601.Attach%2A> i zmodyfikuj pole, które chcesz zmienić.

## <a name="unexpected-query-results"></a>Nieoczekiwane wyniki zapytania

PYTANIE: Moje zapytanie zwraca nieoczekiwane wyniki. Jak można sprawdzić, co się dzieje?

A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] udostępnia kilka narzędzi do sprawdzania kodu SQL, który generuje. Jednym z najważniejszych jest <xref:System.Data.Linq.DataContext.Log%2A>. Aby uzyskać więcej informacji, zobacz [obsługa debugowania](debugging-support.md).

## <a name="unexpected-stored-procedure-results"></a>Nieoczekiwane wyniki procedury składowanej

PYTANIE: Mam procedurę składowaną, której wartość zwracana jest obliczana przez `MAX()`. Gdy przeciągniesz procedurę składowaną do powierzchni projektanta O/R, wartość zwracana jest niepoprawna.

A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia dwa sposoby zwracania wartości generowanych przez bazę danych zgodnie z procedurami składowanymi:

- Poprzez nadanie nazwy wynikowi wyjściowemu.

- Jawnie określając parametr wyjściowy.

Poniżej przedstawiono przykład niepoprawnych danych wyjściowych. Ponieważ [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie może mapować wyników, zawsze zwraca 0:

```sql
create procedure proc2

as

begin

select max(i) from t where name like 'hello'

end
```

Poniżej znajduje się przykład poprawnych danych wyjściowych przy użyciu parametru wyjściowego:

```sql
create procedure proc2

@result int OUTPUT

as

select @result = MAX(i) from t where name like 'hello'

go
```

Poniżej znajduje się przykład poprawnych danych wyjściowych przez nadanie nazwy wynikowi wyjściowemu:

```sql
create procedure proc2

as

begin

select nax(i) AS MaxResult from t where name like 'hello'

end
```

Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji za pomocą procedur składowanych](customizing-operations-by-using-stored-procedures.md).

## <a name="serialization-errors"></a>Błędy serializacji

PYTANIE: Podczas próby serializacji pojawia się następujący błąd: "Type" System. Data. LINQ. ChangeTracker + StandardChangeTracker "... nie jest oznaczony jako możliwy do serializacji. "

A. Generowanie kodu w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje serializacji <xref:System.Runtime.Serialization.DataContractSerializer>. Nie obsługuje <xref:System.Xml.Serialization.XmlSerializer> ani <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Aby uzyskać więcej informacji, zobacz [serializacji](serialization.md).

## <a name="multiple-dbml-files"></a>Wiele plików DBML

PYTANIE: Gdy mam wiele plików DBML, które współdzielą niektóre tabele, otrzymuję błąd kompilatora.

A. Ustaw **przestrzeń nazw kontekstu** i właściwości **przestrzeni nazw jednostki** z Object Relational Designer na wartość odrębną dla każdego pliku DBML. Takie podejście eliminuje kolizję nazw/przestrzeni nazw.

## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a>Unikanie jawnego ustawienia wartości generowanych przez bazę danych przy wstawianiu lub aktualizacji

PYTANIE: Mam tabelę bazy danych z kolumną `DateCreated`, która domyślnie jest `Getdate()`SQL. Przy próbie wstawienia nowego rekordu przy użyciu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]wartość jest ustawiana na `NULL`. Oczekujemy, że zostanie ona ustawiona na wartość domyślną bazy danych.

A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatycznie obsługuje tę sytuację dla tożsamości (Automatyczne zwiększenie) i ROWGUIDCOL (identyfikator GUID generowany przez bazę danych) i kolumny sygnatur czasowych. W innych przypadkach należy ręcznie ustawić <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> właściwości.

## <a name="multiple-dataloadoptions"></a>Wiele DataLoadOptions

PYTANIE: Czy mogę określić dodatkowe opcje ładowania bez zastępowania pierwszej?

A. Tak. Pierwsze nie jest zastępowane, tak jak w poniższym przykładzie:

```vb
Dim dlo As New DataLoadOptions()
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)
```

```csharp
DataLoadOptions dlo = new DataLoadOptions();
dlo.LoadWith<Order>(o => o.Customer);
dlo.LoadWith<Order>(o => o.OrderDetails);
```

## <a name="errors-using-sql-compact-35"></a>Błędy przy użyciu programu SQL Compact 3,5

PYTANIE: Otrzymuję komunikat o błędzie podczas przeciągania tabel z bazy danych SQL Server Compact 3,5.

A. Object Relational Designer nie obsługuje SQL Server Compact 3,5, chociaż środowisko uruchomieniowe [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] działa. W takiej sytuacji należy utworzyć własne klasy jednostek i dodać odpowiednie atrybuty.

## <a name="errors-in-inheritance-relationships"></a>Błędy w relacjach dziedziczenia

PYTANIE: W Object Relational Designer użyto kształtu dziedziczenie przybornika, aby połączyć dwie jednostki, ale otrzymuję błędy.

A. Tworzenie relacji jest niewystarczające. Należy podać informacje takie jak kolumna rozróżniacza, wartość rozróżniacza klasy bazowej i wartość rozróżniacza klasy pochodnej.

## <a name="provider-model"></a>Model dostawcy

PYTANIE: Czy jest dostępny publiczny model dostawcy?

A. Nie jest dostępny żaden model dostawcy publicznego. W tej chwili [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje tylko SQL Server i SQL Server Compact 3,5.

## <a name="sql-injection-attacks"></a>Ataki z iniekcją SQL

PYTANIE: Jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] chronić przed atakami polegającymi na iniekcji SQL?

A. Iniekcja kodu SQL stanowi znaczne ryzyko dla tradycyjnych zapytań SQL utworzonych przez połączenie danych wejściowych użytkownika. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pozwala uniknąć takiego wstrzyknięcia przy użyciu <xref:System.Data.SqlClient.SqlParameter> w zapytaniach. Dane wejściowe użytkownika są włączane do wartości parametrów. Takie podejście uniemożliwia używanie złośliwych poleceń z poziomu danych wejściowych klienta.

## <a name="changing-read-only-flag-in-dbml-files"></a>Zmiana flagi tylko do odczytu w plikach DBML

PYTANIE: Jak mogę wyeliminować metody ustawiane z niektórych właściwości podczas tworzenia modelu obiektów z pliku DBML?

A. Wykonaj następujące czynności w tym zaawansowanym scenariuszu:

1. W pliku. dbml Zmodyfikuj właściwość, zmieniając flagę <xref:System.Data.Linq.ITable.IsReadOnly%2A>, aby `True`.

2. Dodaj klasę częściową. Utwórz konstruktora z parametrami dla elementów członkowskich tylko do odczytu.

3. Sprawdź domyślną wartość <xref:System.Data.Linq.Mapping.UpdateCheck> (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>), aby określić, czy jest to poprawna wartość dla aplikacji.

    > [!CAUTION]
    > Jeśli używasz Object Relational Designer w programie Visual Studio, zmiany mogą zostać nadpisywane.

## <a name="aptca"></a>APTCA

PYTANIE: Czy system. Data. LINQ oznaczono do użycia przez częściowo zaufany kod?

A. Tak, zestaw system. Data. LINQ. dll znajduje się wśród zestawów .NET Framework oznaczonych atrybutem <xref:System.Security.AllowPartiallyTrustedCallersAttribute>. Bez oznaczania, zestawy w .NET Framework są przeznaczone do użycia tylko przez w pełni zaufany kod.

Głównym scenariuszem w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], aby zezwolić częściowo zaufanym obiektom wywołującym na dostęp do zestawu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] z aplikacji sieci Web, gdzie konfiguracja *zaufania* jest średnia.

## <a name="mapping-data-from-multiple-tables"></a>Mapowanie danych z wielu tabel

PYTANIE: Dane w mojej jednostce pochodzą z wielu tabel. Jak mogę ją zmapować?

A. Możesz utworzyć widok w bazie danych i zmapować jednostkę do widoku. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje ten sam kod SQL dla widoków, tak jak w przypadku tabel.

> [!NOTE]
> Korzystanie z widoków w tym scenariuszu ma pewne ograniczenia. To podejście jest najbardziej bezpieczne, gdy operacje wykonywane na <xref:System.Data.Linq.Table%601> są obsługiwane przez widok podstawowy. Tylko ty wiesz, które operacje są zamierzone. Na przykład większość aplikacji jest tylko do odczytu, a inny numer pokaźną wykonuje `Create`/`Update`/operacje `Delete` przy użyciu procedur składowanych w widokach.

## <a name="connection-pooling"></a>Pula połączeń

PYTANIE: Czy istnieje konstrukcja, która może pomóc w <xref:System.Data.Linq.DataContext> pule?

A. Nie próbuj ponownie używać wystąpień <xref:System.Data.Linq.DataContext>. Każda <xref:System.Data.Linq.DataContext> utrzymuje stan (łącznie z pamięcią podręczną tożsamości) dla jednej konkretnej sesji edytowania/zapytań. Aby uzyskać nowe wystąpienia na podstawie bieżącego stanu bazy danych, Użyj nowego <xref:System.Data.Linq.DataContext>.

Nadal można używać podstawowej puli połączeń ADO.NET. Aby uzyskać więcej informacji, zobacz [SQL Servering pooling (ADO.NET)](../../sql-server-connection-pooling.md).

## <a name="second-datacontext-is-not-updated"></a>Drugi element DataContext nie został zaktualizowany

PYTANIE: Użyto jednego wystąpienia <xref:System.Data.Linq.DataContext> do przechowywania wartości w bazie danych. Jednak druga <xref:System.Data.Linq.DataContext> w tej samej bazie danych nie odzwierciedla zaktualizowanych wartości. Drugie wystąpienie <xref:System.Data.Linq.DataContext> prawdopodobnie zwraca zbuforowane wartości.

A. To zachowanie jest zgodne z założeniami. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nadal zwracają te same wystąpienia/wartości, które zostały wydane w pierwszym wystąpieniu. Podczas wprowadzania aktualizacji należy użyć optymistycznej współbieżności. Oryginalne dane są używane do sprawdzania stanu bieżącego bazy danych w celu potwierdzenia, że nadal nie są zmieniane. Jeśli uległy zmianie, wystąpi konflikt i aplikacja musi je rozwiązać. Jedną z opcji aplikacji jest zresetowanie oryginalnego stanu do bieżącego stanu bazy danych i ponowne wypróbowanie aktualizacji. Aby uzyskać więcej informacji, zobacz [How to: Manage konflikts Change](how-to-manage-change-conflicts.md).

Możesz również ustawić <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> na false, co spowoduje wyłączenie buforowania i śledzenie zmian. Następnie można pobrać najnowsze wartości przy każdym zapytaniu.

## <a name="cannot-call-submitchanges-in-read-only-mode"></a>Nie można wywołać SubmitChanges w trybie tylko do odczytu

PYTANIE: Gdy próbuję wywołać <xref:System.Data.Linq.DataContext.SubmitChanges%2A> w trybie tylko do odczytu, pojawia się błąd.

A. Tryb tylko do odczytu wyłącza możliwość śledzenia zmian w kontekście.

## <a name="see-also"></a>Zobacz także

- [Tematy pomocy](reference.md)
- [Rozwiązywanie problemów](troubleshooting.md)
- [Zabezpieczenia w składniku LINQ to SQL](security-in-linq-to-sql.md)
