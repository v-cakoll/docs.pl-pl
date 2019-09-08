---
title: Niezgodność typu SQL CLR
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 27708f4bb8e191156f578132602570bc4a6337b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781199"
---
# <a name="sql-clr-type-mismatches"></a>Niezgodność typu SQL CLR

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]automatyzuje większość tłumaczenia między modelem obiektów i SQL Server. Niemniej jednak niektóre sytuacje uniemożliwiają dokładne tłumaczenie. Te klucze nie są zgodne z typami środowiska uruchomieniowego języka wspólnego (CLR) i SQL Server typy baz danych zostały podsumowane w poniższych sekcjach. Więcej szczegółów na temat mapowania określonego typu i tłumaczenia funkcji można znaleźć w [mapowaniu typu SQL-CLR](sql-clr-type-mapping.md) oraz w [funkcjach i typach danych](data-types-and-functions.md).

## <a name="data-types"></a>Typy danych

Tłumaczenie między środowiskiem CLR i SQL Server występuje, gdy zapytanie jest wysyłane do bazy danych, a wyniki są wysyłane z powrotem do modelu obiektów. Na przykład następujące zapytanie w języku Transact-SQL wymaga dwóch konwersji wartości:

```sql
Select DateOfBirth From Customer Where CustomerId = @id
```

Aby można było wykonać zapytanie na SQL Server, należy podać wartość parametru Transact-SQL. W tym przykładzie `id` wartość parametru musi być najpierw przetłumaczona z typu CLR <xref:System.Int32?displayProperty=nameWithType> na typ SQL Server `INT` , aby baza danych mogła zrozumieć, co to jest wartość. Następnie, aby pobrać wyniki, kolumna SQL Server `DateOfBirth` musi być przetłumaczona z typu SQL Server `DATETIME` na typ CLR <xref:System.DateTime?displayProperty=nameWithType> do użycia w modelu obiektów. W tym przykładzie typy w modelu obiektów CLR i SQL Server Database mają naturalne mapowania. Jednak nie zawsze jest to przypadek.

### <a name="missing-counterparts"></a>Brakujące odpowiedniki

Następujące typy nie mają odpowiednich odpowiedników.

- Niezgodności w przestrzeni nazw CLR <xref:System> :

  - **Liczby całkowite bez znaku**. Te typy są zwykle mapowane na ich podpisywane im odpowiedniki o większym rozmiarze, aby uniknąć przepełnienia. Literały mogą być konwertowane na wartość liczbową o takim samym lub mniejszym rozmiarze, na podstawie wartości.

  - **Wartość logiczna**. Te typy mogą być mapowane na wartość bitową lub większą numeryczną lub ciąg. Literał można zamapować na wyrażenie, którego wynikiem jest taka sama wartość (na przykład `1=1` w języku SQL dla `True` języka CLS).

  - Wartość **TimeSpan**. Ten typ reprezentuje różnicę między dwiema `DateTime` wartościami i nie odpowiada `timestamp` SQL Server. Środowisko CLR <xref:System.TimeSpan?displayProperty=nameWithType> może również być mapowane na SQL Server `TIME` typu w niektórych przypadkach. Typ SQL Server `TIME` był przeznaczony tylko do reprezentowania wartości dodatnich mniejszych niż 24 godziny. Środowisko CLR <xref:System.TimeSpan> ma znacznie większy zakres.

  > [!NOTE]
  > W tym porównaniu nie zamieszczono typów <xref:System.Data.SqlTypes> .NET Framework specyficznych dla SQL Server.

- Niezgodności w SQL Server:

  - **Typy znaków o stałej długości**. Język Transact-SQL rozróżnia kategorie Unicode i inne niż Unicode i ma trzy odrębne typy w każdej kategorii: stała długość `nchar` `varchar` / `char`, zmienna długość `nvarchar`i / większy rozmiar `ntext`. / `text` Typy znaków o stałej długości można zamapować na typ CLR <xref:System.Char?displayProperty=nameWithType> w celu pobierania znaków, ale nie są naprawdę zgodne z tym samym typem w konwersji i zachowaniu.

  - **Bit**. Chociaż domena ma taką samą liczbę wartości jak `Nullable<Boolean>`, dwa typy są różne. `bit` `Bit`Pobiera wartości `1` i `0` zamiast `true`i niemożebyćużywanejakoodpowiednikwyrażeńlogicznych./ `false`

  - **Sygnatura czasowa**. W przeciwieństwie do <xref:System.TimeSpan?displayProperty=nameWithType> typu CLR, typ `TIMESTAMP` SQL Server reprezentuje 8-bajtowy numer wygenerowany przez bazę danych unikatową dla każdej aktualizacji i nie jest oparty na różnicy między <xref:System.DateTime> wartościami.

  - **Money** i **smallmoney**. Te typy mogą być mapowane na <xref:System.Decimal> , ale są zasadniczo różne typy i są traktowane jako takie jak funkcje i konwersje oparte na serwerze.

### <a name="multiple-mappings"></a>Wiele mapowań

Istnieje wiele typów danych SQL Server, które można mapować na jeden lub więcej typów danych CLR. Istnieje również wiele typów CLR, które można zamapować na jeden lub więcej typów SQL Server. Chociaż mapowanie może być obsługiwane przez LINQ to SQL, nie oznacza to, że dwa typy mapowane między CLR i SQL Server są idealnym dopasowaniem dokładności, zakresu i semantyki. Niektóre mapowania mogą obejmować różnice w dowolnych lub wszystkich tych wymiarach. Szczegółowe informacje na temat tych potencjalnych różnic można znaleźć w odniesieniu do różnych możliwości mapowania w [mapowaniu typu SQL-CLR](sql-clr-type-mapping.md).

### <a name="user-defined-types"></a>Typy zdefiniowane przez użytkownika

Typy CLR zdefiniowane przez użytkownika zostały zaprojektowane w celu ułatwienia mostkowania przerwy w działaniu systemu. Niemniej jednak są to interesujące problemy związane z przechowywaniem wersji. Zmiana wersji na kliencie może nie być zgodna ze zmianą typu przechowywanego na serwerze bazy danych. Każda taka zmiana powoduje inny niezgodność typów, w którym Semantyka typów może być niezgodna i przerwy w działaniu mogą być widoczne. Kolejne komplikacje występują, ponieważ hierarchie dziedziczenia są refaktoryzacji w kolejnych wersjach.

## <a name="expression-semantics"></a>Semantyka wyrażeń

Oprócz niezgodności parowania między typami CLR i bazy danych, wyrażenia zwiększają złożoność do niezgodności. Niezgodność z semantyką operatora, semantyką funkcji, niejawną konwersją typów i regułami pierwszeństwa należy rozważyć.

Poniższe podsekcje ilustrują niezgodność między podobnymi wyrażeniami. Może być możliwe wygenerowanie wyrażeń SQL, które są semantycznie równoważne z danym wyrażeniem środowiska CLR. Jednakże nie jest jasne, czy różnice semantyczne między wyrazami podobnymi są oczywiste dla użytkownika CLR, a w związku z tym, czy zmiany wymagane dla równoważności semantycznej są zamierzone, czy nie. Jest to szczególnie problem krytyczny, gdy wyrażenie jest oceniane dla zestawu wartości. Widoczność różnic może zależeć od danych i być trudno do zidentyfikowania podczas kodowania i debugowania.

### <a name="null-semantics"></a>Semantyka wartości Null

Wyrażenia SQL zapewniają wielowartościową logikę dla wyrażeń logicznych. Wynik może mieć wartość true, false lub null. Z kolei środowisko CLR Określa wynik wartości logicznej dwuwartościowej w przypadku porównań, w których wartość jest równa null. Rozważmy następujący kod:

[!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
[!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]

```sql
-- Assume col1 and col2 are integer columns with null values.
-- Assume that ANSI null behavior has not been explicitly
--  turned off.
Select …
From …
Where col1 = col2
-- Evaluates to null, not true and the corresponding row is not
--   selected.
-- To obtain matching behavior (i -> col1, j -> col2) change
--   the query to the following:
Select …
From …
Where
    col1 = col2
or (col1 is null and col2 is null)
-- (Visual Basic 'Nothing'.)
```

Podobny problem występuje z założeniem dotyczącym wyników dwóch wartości.

[!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
[!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]

```sql
-- Assume col1 and col2 are nullable columns.
-- Assume that ANSI null behavior has not been explicitly
--   turned off.
Select …
From …
Where
    col1 = col2
or col1 != col2
-- Visual Basic: col1 <> col2.

-- Excludes the case where the boolean expression evaluates
--   to null. Therefore the where clause does not always
--   evaluate to true.
```

W poprzednim przypadku można uzyskać równoważne zachowanie podczas generowania kodu SQL, ale tłumaczenie może nie odzwierciedlać zamierzonego celu.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie nakłada C# `null` ani nie Visual Basic `nothing` semantyki porównania w SQL. Operatory porównania są syntaktycznie przetłumaczone na ich odpowiedniki języka SQL. Semantyka odzwierciedla semantykę SQL zgodnie z definicją serwera lub ustawienia połączenia. Dwie wartości null są uznawane za nierówne w domyślnych ustawieniach SQL Server (chociaż można zmienić ustawienia w celu zmiany semantyki). Bez względu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] na to, czy ustawienia serwera nie są uwzględniane w tłumaczeniu zapytań.

Porównanie z literałem `null` (`nothing`) jest tłumaczone na odpowiednią wersję SQL (`is null` lub `is not null`).

Wartość `null` (`nothing`) w sortowaniu jest definiowana przez SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie zmienia sortowania.

### <a name="type-conversion-and-promotion"></a>Konwersja i promocja typu

SQL obsługuje bogaty zestaw niejawnych konwersji w wyrażeniach. Podobne wyrażenia w C# programie wymagają jawnego rzutowania. Na przykład:

- `Nvarchar`typy `DateTime` i można porównać w języku SQL bez żadnych jawnych rzutowania; C# wymaga jawnej konwersji.

- `Decimal`jest niejawnie konwertowany `DateTime` na w programie SQL Server. C#nie zezwala na niejawną konwersję.

Analogicznie, pierwszeństwo typów w języku Transact-SQL różni się C# od priorytetu typu w, ponieważ podstawowy zestaw typów jest inny. W rzeczywistości nie istnieje relacja Wyczyść podzbiór/nadzbiór z listy pierwszeństwa. Na `nvarchar` przykład porównanie `varchar` z wystąpieniem powoduje niejawną konwersję `varchar` wyrażenia na `nvarchar`. Środowisko CLR nie zapewnia równoważnej promocji.

W prostych przypadkach te różnice powodują, że wyrażenia CLR z rzutowania są nadmiarowe dla odpowiedniego wyrażenia SQL. Co ważniejsze, pośrednie wyniki wyrażenia SQL mogą zostać niejawnie podwyższone do typu, który nie ma dokładnego odpowiednika w C#i na odwrót. Ogólnie, testowanie, debugowanie i sprawdzanie poprawności takich wyrażeń zwiększa duże obciążenie użytkownika.

### <a name="collation"></a>Sortowanie

Język Transact-SQL obsługuje jawne sortowania jako adnotacje w typach ciągów znaków. Te sortowania określają prawidłowość niektórych porównań. Na przykład porównywanie dwóch kolumn z różnymi jawnymi sortowaniami jest błędem. Użycie znacznie uproszczonego typu ciągu CTS nie powoduje błędów. Rozważmy następujący przykład:

```sql
create table T2 (
    Col1 nvarchar(10),
    Col2      nvarchar(10) collate Latin_general_ci_as
)
```

[!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
[!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]

```sql
Select …
From …
Where Col1 = Col2
-- Error, collation conflict.
```

W efekcie Podklauzula sortowania tworzy *ograniczony typ* , który nie jest zamienny.

Podobnie porządek sortowania może być znacząco różny w systemach typów. Różnica ta ma wpływ na sortowanie wyników. <xref:System.Guid>jest sortowany dla wszystkich 16 bajtów według kolejności leksykograficznych`IComparable()`(), podczas gdy język T-SQL porównuje identyfikatory GUID w następującej kolejności: node (10-15), Clock-SEQ (8-9), Time-High (6-7), Time-Mid (4-5), czas-niski (0-3). Takie porządkowanie zostało wykonane w programie SQL 7,0, gdy identyfikatory GUID generowane przez NT mają takie zamówienie oktetowe. Podejście to gwarantuje, że identyfikatory GUID wygenerowane w tym samym klastrze węzłów zostały połączone w kolejności sekwencyjnej zgodnie z sygnaturą czasową. Podejście było również przydatne do kompilowania indeksów (wstawiane są dołączenia zamiast losowego systemu IOs). Zamówienie zostało zaszyfrowane później w systemie Windows z powodu kwestii związanych z ochroną prywatności, ale program SQL Server musi zachować zgodność. Obejściem jest użycie <xref:System.Data.SqlTypes.SqlGuid> <xref:System.Guid>zamiast.

### <a name="operator-and-function-differences"></a>Różnice między operatorami i funkcjami

Operatory i funkcje, które są zasadniczo porównywalne, mają zbliżoną inną semantykę. Na przykład:

- C#Określa semantykę krótkiego obwodu opartą na leksykalnej kolejności operandów `&&` dla `||`operatorów logicznych i. Program SQL z drugiej strony jest przeznaczony dla zapytań opartych na zestawie i dlatego zapewnia większą swobodę dla Optymalizatora decydującego o kolejności wykonywania. Poniżej wymieniono niektóre konsekwencje:

  - Semantycznie równoważne tłumaczenie wymaga "`CASE` ... `WHEN` … `THEN`"konstrukcja w języku SQL, aby uniknąć zmiany kolejności wykonywania operacji.

  - `AND` Luźne tłumaczenie / operatorów`OR` może spowodować nieoczekiwane błędy, C# Jeśli wyrażenie polega na ocenie drugiego operandu na podstawie wyniku oceny pierwszego operandu.

- `Round()`Funkcja ma inną semantykę w .NET Framework i w języku T-SQL.

- Początkowy indeks dla ciągów ma wartość 0 w CLR, ale 1 w SQL. W związku z tym każda funkcja, która ma indeks, wymaga tłumaczenia indeksu.

- Środowisko CLR obsługuje operator modułu ("%") dla liczb zmiennoprzecinkowych, ale nie jest on obsługiwany przez program SQL.

- `Like` Operator efektywnie uzyskuje automatyczne przeciążenia na podstawie niejawnych konwersji. Mimo że `DateTime` `Like` operator jest zdefiniowany do działania w typach ciągów znaków, niejawna konwersja z typów numerycznych lub typów pozwala na użycie tych typów niebędących ciągami. `Like` W programie CTS porównywalne konwersje niejawne nie istnieją. W związku z tym konieczne są dodatkowe przeciążenia.

    > [!NOTE]
    > To `Like` zachowanie operatora ma zastosowanie C# tylko do słowa kluczowego Visual Basic `Like` bez zmian.

- Przepełnienie jest zawsze sprawdzane w języku SQL, ale musi być C# jawnie określone w (nie w Visual Basic), aby uniknąć wraparound. Podano kolumny liczb całkowitych C1, C2 i C3, jeśli C1 + C2 jest przechowywany w C3 (aktualizacja T zestawu C3 = C1 + C2).

    ```sql
    create table T3 (
        Col1      integer,
        Col2      integer
    )
    insert into T3 (col1, col2) values (2147483647, 5)
    -- Valid values: max integer value and 5.
    select * from T3 where col1 + col2 < 0
    -- Produces arithmetic overflow error.
    ```

[!code-csharp[DLinqMismatch#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#5)]
[!code-vb[DLinqMismatch#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#5)]

- Funkcja SQL wykonuje symetryczne zaokrąglenie arytmetyczne, podczas gdy .NET Framework używa zaokrągleń przez Bank. Więcej informacji można znaleźć w artykule bazy wiedzy 196652.

- Domyślnie w przypadku wspólnych ustawień regionalnych porównania ciągów znaków nie uwzględniają wielkości liter w SQL. W Visual Basic i w C#programie jest rozróżniana wielkość liter. `s == "Food"` Na przykład `food`(`s = "Food"` w Visual Basic) i mogą `s == "Food"` dać różne wyniki, jeśli `s` jest.

    ```sql
    -- Assume default US-English locale (case insensitive).
    create table T4 (
        Col1      nvarchar (256)
    )
    insert into T4 values (‘Food’)
    insert into T4 values (‘FOOD’)
    select * from T4 where Col1 = ‘food’
    -- Both the rows are returned because of case-insensitive matching.
    ```

[!code-csharp[DLinqMismatch#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#6)]
[!code-vb[DLinqMismatch#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#6)]

- Operatory/funkcje zastosowane do argumentów typu o stałej długości w programie SQL mają znacznie inną semantykę niż te same operatory/funkcje zastosowane do środowiska <xref:System.String?displayProperty=nameWithType>CLR. Może to również być widoczne jako rozszerzenie brakującego, odpowiadającego problemu omówionego w sekcji Informacje o typach.

    ```sql
    create table T4 (
        Col1      nchar(4)
    )
    Insert into T5(Col1) values ('21');
    Insert into T5(Col1) values ('1021');
    Select * from T5 where Col1 like '%1'
    -- Only the second row with Col1 = '1021' is returned.
    -- Not the first row!
    ```

     [!code-csharp[DLinqMismatch#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#7)]
     [!code-vb[DLinqMismatch#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#7)]

     Podobny problem występuje w przypadku łączenia ciągów.

    ```sql
    create table T6 (
        Col1      nchar(4)
        Col2       nchar(4)
    )
    Insert into T6 values ('a', 'b');
    Select Col1+Col2 from T6
    -- Returns concatenation of padded strings "a   b   " and not "ab".
    ```

Podsumowując, tłumaczenie zawiłe może być wymagane dla wyrażeń CLR, a dodatkowe operatory/funkcje mogą być niezbędne do udostępnienia funkcji SQL.

### <a name="type-casting"></a>Rzutowanie typu

W C# programie i w języku SQL użytkownicy mogą zastąpić domyślną semantykę wyrażeń przy użyciu jawnych rzutowania typu (`Cast` i `Convert`). Jednak udostępnienie tej funkcji w granicach systemu typów stanowi dylematem. Rzutowanie kodu SQL, które zapewnia odpowiednią semantykę, nie może być łatwo przetłumaczone na odpowiednie C# rzutowanie. Z drugiej strony C# rzutowanie nie może być bezpośrednio przetłumaczone na równoważne rzutowanie SQL ze względu na niezgodności typów, brakujące odpowiedniki i różne hierarchie pierwszeństwa typu. Istnieje kompromis między ujawnieniem niezgodności systemu typów i utratą znaczących możliwości wyrażenia.

W innych przypadkach rzutowanie typów może nie być potrzebne w żadnej domenie do walidacji wyrażenia, ale może być wymagane, aby upewnić się, że mapowanie inne niż domyślne jest prawidłowo stosowane do wyrażenia.

```sql
-- Example from "Non-default Mapping" section extended
create table T5 (
    Col1      nvarchar(10),
    Col2      nvarchar(10)
)
Insert into T5(col1, col2) values (‘3’, ‘2’);
```

[!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
[!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]

```sql
Select *
From T5
Where Col1 + Col2 > 4
-- "Col1 + Col2" expr evaluates to '32'
```

## <a name="performance-issues"></a>Problemy z wydajnością

Księgowanie niektórych różnic typu SQL Server-CLR może spowodować spadek wydajności w przypadku przekroczenia między systemami typów CLR i SQL Server. Oto przykładowe scenariusze wpływające na wydajność:

- Wymuszona kolejność obliczeń dla operatorów logicznych i/or

- Generowanie kodu SQL w celu wymuszenia kolejności szacowania predykatu ogranicza możliwość korzystania z programu SQL Optymalizatora.

- Konwersje typu, wprowadzone przez kompilator CLR lub przez implementację zapytania Object-relacyjnego, mogą ograniczać użycie indeksu.

     Na przykład

    ```sql
    -- Table DDL
    create table T5 (
        Col1      varchar(100)
    )
    ```

     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]

     Rozważ tłumaczenie wyrażenia `(s = SOME_STRING_CONSTANT)`.

    ```sql
    -- Corresponding part of SQL where clause
    Where …
    Col1 = SOME_STRING_CONSTANT
    -- This expression is of the form <varchar> = <nvarchar>.
    -- Hence SQL introduces a conversion from varchar to nvarchar,
    --   resulting in
    Where …
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT
    -- Cannot use the index for column Col1 for some implementations.
    ```

Oprócz różnic semantycznych należy wziąć pod uwagę wpływ na wydajność w przypadku przekroczenia między SQL Server i systemami typów CLR. W przypadku dużych zestawów danych takie problemy z wydajnością mogą określić, czy aplikacja jest wdrażana.

## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](background-information.md)
