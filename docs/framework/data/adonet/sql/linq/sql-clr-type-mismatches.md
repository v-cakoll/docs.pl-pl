---
title: "Niezgodność typu SQL CLR"
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
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6a027bd898409708dd6800908a6736f5853058df
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="sql-clr-type-mismatches"></a>Niezgodność typu SQL CLR
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]automatyzuje wiele tłumaczenie między model obiektów i SQL Server. Niemniej jednak niektórych sytuacjach uniemożliwiają dokładny tłumaczenia. Te klucza niedopasowania popularne typy środowiska uruchomieniowego (języka wspólnego CLR) języka i typów bazy danych programu SQL Server podsumowano w poniższych sekcjach. Można znaleźć więcej informacji dotyczących mapowania określonego typu i funkcja translacji na [mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) i [typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).  
  
## <a name="data-types"></a>Typy danych  
 Translacja między CLR i SQL Server występuje, gdy zapytanie jest wysyłane do bazy danych, a wyniki są odsyłane do modelu obiektu. Na przykład następujące zapytanie języka Transact-SQL wymaga dwóch konwersji wartości:  
  
```  
Select DateOfBirth From Customer Where CustomerId = @id     
```  
  
 Aby można było wykonać zapytanie w programie SQL Server, należy określić wartość parametru języka Transact-SQL. W tym przykładzie `id` wartość parametru musi najpierw przeliczane z CLR <xref:System.Int32?displayProperty=nameWithType> typu do programu SQL Server `INT` wpisz, aby bazy danych można zrozumieć, co to jest wartość. Następnie można pobrać wyników, programu SQL Server `DateOfBirth` kolumny musi być przekonwertowana z programu SQL Server `DATETIME` typu CLR <xref:System.DateTime?displayProperty=nameWithType> typ do użycia w modelu obiektów. W tym przykładzie typami w modelu obiektu CLR i bazy danych programu SQL Server ma mapowania fizycznych. Jednak nie zawsze jest wielkość liter.  
  
### <a name="missing-counterparts"></a>Brak odpowiedniki  
 Następujące typy nie mają uzasadnione odpowiedniki.  
  
-   W środowisku CLR ma niezgodny <xref:System> przestrzeni nazw:  
  
    -   **Podpisane liczby całkowite**. Zazwyczaj są mapowane te typy ich podpisem odpowiedniki większy rozmiar w celu uniknięcia przepełnienia. Literały można przekonwertować na podpisem liczbowe o tej samej lub mniejszy rozmiar, na podstawie wartości.  
  
    -   **Wartość logiczna**. Mogą być mapowane te typy bitowych lub większą liczbą lub ciągiem. Literał mogą być mapowane na wyrażenie obliczane do tej samej wartości (na przykład `1=1` w języku SQL dla `True` w ze specyfikacją CLS).  
  
    -   **TimeSpan**. Ten typ przedstawia różnicę między dwiema `DateTime` wartości i nie odpowiada `timestamp` programu SQL Server. Środowisko CLR <xref:System.TimeSpan?displayProperty=nameWithType> może również mapować do programu SQL Server `TIME` typu w niektórych przypadkach. SQL Server `TIME` typu była przeznaczona tylko do reprezentowania wartości dodatnie mniej niż 24 godziny. Środowisko CLR <xref:System.TimeSpan> ma o wiele większa zakres.  
  
    > [!NOTE]
    >  Specyficzne dla programu SQL Server [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] typy w <xref:System.Data.SqlTypes> nie są uwzględnione w tym porównania.  
  
-   Niezgodność w programie SQL Server:  
  
    -   **Stałej długości typów znaków**. Transact-SQL rozróżnia kategorii Unicode i z systemem innym niż Unicode i ma trzy różne typy w każdej kategorii: stałej długości `nchar` / `char`, o zmiennej długości `nvarchar` / `varchar`, i o większym rozmiarze `ntext` / `text`. O stałej długości typów znaków mogą zostać zamapowane do środowiska CLR <xref:System.Char?displayProperty=nameWithType> znaków typu pobierania, ale ich nie naprawdę odpowiadają tego samego typu konwersje i zachowania.  
  
    -   **Bit**. Mimo że `bit` domena ma taką samą liczbę wartości jako `Nullable<Boolean>`, są różnych typów. `Bit`pobiera wartości `1` i `0` zamiast `true` / `false`i nie można użyć jako równoważne wyrażeń logicznych.  
  
    -   **Sygnatura czasowa**. W przeciwieństwie do środowiska CLR <xref:System.TimeSpan?displayProperty=nameWithType> typ, programu SQL Server `TIMESTAMP` typu reprezentuje 8-bajtowa liczba wygenerowanych przez bazę danych, która jest unikatowa dla każdej aktualizacji i nie jest oparty na różnicy między <xref:System.DateTime> wartości.  
  
    -   **Oszczędność pieniędzy** i **SmallMoney**. Te typy mogą być mapowane na <xref:System.Decimal> , ale są zasadniczo różne typy i są traktowane jako takie funkcje oparte na serwerze i konwersji.  
  
### <a name="multiple-mappings"></a>Wiele mapowań  
 Istnieje wiele typów danych programu SQL Server, które można mapować na co najmniej jeden typ danych CLR. Istnieje wiele typów CLR, które można mapować na co najmniej jeden typ SQL Server. Mimo że mapowanie może być obsługiwana w składniku LINQ to SQL, oznacza to, że dwa typy mapowane między CLR i SQL Server nie są doskonałe dopasowanie dokładność, zakresu i semantyki. Niektóre mapowania mogą obejmować różnice w całości lub części tych wymiarów. Dla różnych możliwości mapowania na można znaleźć szczegółowe informacje o tych potencjalne różnice [mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
### <a name="user-defined-types"></a>Typy definiowane przez użytkownika  
 Typy danych zdefiniowane przez użytkownika CLR pozwalają rozbieżność system typu. Niemniej jednak ich powierzchni interesujące problemy dotyczące wersji typu. Zmiana wersji na kliencie może nie można dopasować poprzez zmianę typu przechowywane na serwerze bazy danych. Taka zmiana powoduje, że inny niezgodność typów, gdzie semantyka typów mogą nie być zgodne, a przerwa wersji mogą być widoczne. Dalsze komplikacji występować hierarchii dziedziczenia są refaktoryzowane w kolejnych wersjach.  
  
## <a name="expression-semantics"></a>Semantyka wyrażeń  
 Oprócz parowania niezgodność typów CLR i bazy danych wyrażenia zwiększenia złożoności niezgodność. Należy rozważyć użycie niezgodności semantyki operatora, semantyki funkcja niejawna konwersja typu i pierwszeństwo reguły.  
  
 Poniższe podpunkty ilustrują niezgodność między najwyraźniej podobne wyrażenia. Może być można wygenerować wyrażenia SQL, które są równoważne semantycznie danego wyrażenia CLR. Jednak nie jest jasne czy semantycznego różnice między najwyraźniej podobne wyrażenia mają manipulacji użytkownikowi CLR, i w związku z tym czy zmiany, które są wymagane do pełnienia roli równoważnika semantycznego lub nie. Jest to problem krytyczne znaczenie, gdy wyrażenie jest obliczane dla zestawu wartości. Widoczność różnica może zależą od danych - i jest trudne do zidentyfikowania podczas kodowania i debugowanie.  
  
### <a name="null-semantics"></a>Semantyka wartości null  
 Wyrażenia SQL Podaj przechowywanymi w trzech logiki dla wyrażeń logicznych. Może to spowodować powstanie wartość true, false lub wartość null. Z kolei CLR określa przechowywanymi na dwa logiczne wynik porównania obejmujące wartości null. Rozważmy następujący kod:  
  
 [!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
 [!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]  
  
```  
-- Assume col1 and col2 are integer columns with null values.   
-- Assume that ANSI null behavior has not been explicitly  
--    turned off.  
Select …  
From …  
Where col1 = col2  
-- Evaluates to null, not true and the corresponding row is not  
--     selected.  
-- To obtain matching behavior (i -> col1, j -> col2) change  
--     the query to the following:  
Select …  
From …  
Where  
    col1 = col2   
or (col1 is null and col2 is null)  
-- (Visual Basic 'Nothing'.)  
```  
  
 Podobne problem występuje, przy założeniu o wynikach binarnego.  
  
 [!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
 [!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]  
  
```  
-- Assume col1 and col2 are nullable columns.  
-- Assume that ANSI null behavior has not been explicitly  
--     turned off.  
Select …  
From …  
Where  
    col1 = col2        
or col1 != col2  
-- Visual Basic: col1 <> col2.  
  
-- Excludes the case where the boolean expression evaluates  
--     to null. Therefore the where clause does not always  
--     evaluate to true.  
```  
  
 W przypadku poprzednich można uzyskać równoważne zachowanie podczas generowania SQL, ale translację dokładnie nie uwzględnia masz zamiar.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie nakłada C# `null` lub [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `nothing` semantykę porównania SQL. Operatory porównania składniowo są przekształcane na ich odpowiedniki SQL. Semantyka odzwierciedlają semantyki SQL, zgodnie z ustawieniami serwera lub połączenia. Dwie wartości null są traktowane jako nierówne w domyślnych ustawień programu SQL Server (mimo że można zmienić ustawienia, aby zmienić semantykę). Niezależnie od tego [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie należy wziąć pod uwagę ustawień serwera w Translacja zapytania.  
  
 Porównanie z literałem `null` (`nothing`) jest translacja do odpowiedniej wersji programu SQL (`is null` lub `is not null`).  
  
 Wartość `null` (`nothing`) w sortowaniu jest zdefiniowany przez program SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie ulega zmianie sortowania.  
  
### <a name="type-conversion-and-promotion"></a>Konwersja typów i podwyższenie poziomu  
 SQL obsługuje bogaty zestaw niejawne konwersje w wyrażeniach. Podobne wyrażenia w języku C# wymaga jawnego rzutowania. Na przykład:  
  
-   `Nvarchar`i `DateTime` typy mogą być porównywane w języku SQL bez żadnych jawnego rzutowania; C# wymaga jawnej konwersji.  
  
-   `Decimal`jest niejawnie przekonwertowana na `DateTime` w języku SQL. C# nie pozwala na niejawną konwersję.  
  
 Podobnie typu pierwszeństwo w języku Transact-SQL różni się od typu pierwszeństwo w języku C#, ponieważ różni się podstawowy zestaw typów. W rzeczywistości istnieje żadna relacja wyczyść podzestawu/nadzbiorem między listami pierwszeństwo. Na przykład porównanie `nvarchar` z `varchar` powoduje, że niejawnej konwersji wartości `varchar` wyrażenie `nvarchar`. Środowisko CLR udostępnia nie równoważne podwyższania poziomu.  
  
 W prostych przypadkach te różnice spowodować wyrażenia CLR z rzutowania być nadmiarowe dla odpowiedniego wyrażenia SQL. Co więcej, pośrednich wyników wyrażenie SQL może niejawnie podwyższony do typu, który nie ma odpowiednika dokładne w języku C# i na odwrót. Ogólne testowania, debugowania i sprawdzania poprawności takich wyrażeń dodaje znaczne obciążenie na użytkownika.  
  
### <a name="collation"></a>Sortowanie  
 Transact-SQL obsługuje sortowanie jawne jako adnotacje typów ciąg znaków. Te sortowania sprawdzania poprawności niektórych porównania. Na przykład dwie kolumny z różnych opcji sortowania jawne porównanie, występuje błąd. Użyj typu string znacznie uproszczony CTS nie powoduje takie błędy. Rozważmy następujący przykład:  
  
```  
create table T2 (  
    Col1 nvarchar(10),  
    Col2      nvarchar(10) collate Latin_general_ci_as  
)  
```  
  
 [!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
 [!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]  
  
```  
Select …  
From …  
Where Col1 = Col2  
-- Error, collation conflict.  
```  
  
 W efekcie tworzy podklauzuli sortowania *ograniczone typu* nie jest to podstawienia.  
  
 Podobnie kolejność sortowania może być znacznie różni się we wszystkich systemach typu. Ta różnica dotyczy sortowania wyników. <xref:System.Guid>jest sortowany na wszystkich 16 bajtów według kolejności lexicographic (`IComparable()`), podczas gdy T-SQL porównuje identyfikatorów GUID w następującej kolejności: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3). Ta kolejność została wykonana w programie SQL 7.0, gdy generowane NT identyfikatorów GUID ma kolejności octet. Podejście zapewnić, że identyfikatorów GUID generowane podczas tego samego węzła klastra pochodzi ze sobą w kolejności sekwencyjnej, zgodnie z sygnatury czasowej. Podejście było również przydatne w przypadku tworzenia indeksów (wstawia stają się dołącza zamiast losowych operacji We-Wy). Kolejność zostało zaszyfrowane później w systemie Windows z powodu prywatności, ale SQL musi zapewnić zgodność. Obejście tego problemu jest użycie <xref:System.Data.SqlTypes.SqlGuid> zamiast <xref:System.Guid>.  
  
### <a name="operator-and-function-differences"></a>Operator i różnice funkcji  
 Operatory i funkcje, które są zasadniczo porównywalne ma semantykę różną pisowni. Na przykład:  
  
-   C# określa semantyki zwarcia oparte na leksykalne Kolejność argumentów operacji dla operatorów logicznych `&&` i `||`. SQL z drugiej strony jest przeznaczony dla zapytań na podstawie zestawu, dlatego zapewnia większą swobodę Optymalizator określić kolejność wykonywania. Konsekwencje między innymi następujące:  
  
    -   Wymaga tłumaczenia semantycznie równoważne "`CASE` ... `WHEN` … `THEN`"tworzenia instrukcji SQL, aby uniknąć zmianę kolejności wykonywania argument.  
  
    -   Luźne tłumaczenia na język `AND` / `OR` operatory może spowodować nieoczekiwane błędy, jeśli wyrażenie C# zależy oceny drugiego operandu na wynikiem obliczania pierwszego argumentu operacji.  
  
-   `Round()`funkcja ma semantykę różną w [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] w T-SQL.  
  
-   Indeks początkowy dla ciągów jest 0 w środowisku CLR, lecz 1 w języku SQL. W związku z tym każda funkcja, która ma indeks musi tłumaczenia indeksu.  
  
-   Środowisko CLR obsługuje operator modulo (%) na liczby zmiennoprzecinkowe, ale nie będzie SQL.  
  
-   `Like` Operator skutecznie uzyskuje automatyczne przeciążenia oparte na niejawną konwersję. Mimo że `Like` operator jest zdefiniowana do działania na typy ciąg znaków, niejawna konwersja z typu liczbowego lub `DateTime` typy umożliwia dla tych typów innych niż ciąg do użycia z `Like` równie dobrze. W CTS można porównywać pod względem niejawne konwersje nie istnieją. W związku z tym potrzebne są dodatkowe przeciążenia.  
  
    > [!NOTE]
    >  To `Like` operator zachowanie dotyczy C# Visual Basic `Like` — słowo kluczowe jest bez zmian.  
  
-   Przepełnienie zawsze ewidencjonowane SQL, ale musi być jawnie określona w języku C# (nie w [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) w celu uniknięcia wraparound. Podane kolumny całkowitą C1, C2 i C3, jeśli C1 + C2 jest przechowywany w C3 (C3 ustawić T aktualizacji = C1 + C2).  
  
    ```  
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
  
-   SQL wykonuje arytmetyczne symetrycznego zaokrąglania podczas [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] banker używa obiektu zaokrąglania. Zobacz artykuł bazy wiedzy 196652, aby uzyskać więcej informacji.  
  
-   Domyślnie dla typowych ustawień regionalnych bez uwzględniania wielkości liter w programie SQL są porównania ciągu znaków. W języku Visual Basic i C# są one z uwzględnieniem wielkości liter. Na przykład `s == "Food"` (`s = "Food"` w [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) i `s == "Food"` może spowodować uzyskanie innych wyników, jeśli `s` jest `food`.  
  
    ```  
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
  
-   Operatory / funkcji stosowane do argumentów typu znak o stałej długości w języku SQL ma semantykę znacznie różni się od tego samego operatory/funkcje stosowane do środowiska CLR <xref:System.String?displayProperty=nameWithType>. Można to także wyświetlane jako rozszerzenie Brak problemu odpowiednikiem omówionych w sekcji o typach.  
  
    ```  
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
  
     Podobne problemu z ciągów.  
  
    ```  
    create table T6 (  
        Col1      nchar(4)  
        Col2       nchar(4)  
    )  
    Insert into T6 values ('a', 'b');  
    Select Col1+Col2 from T6  
    -- Returns concatenation of padded strings "a   b   " and not "ab".  
    ```  
  
 Podsumowując zwichrowanych tłumaczenia mogą być wymagane dla wyrażeń CLR i dodatkowe operatory/funkcje mogą być niezbędne do udostępnienia funkcji SQL.  
  
### <a name="type-casting"></a>Rzutowanie typów  
 W języku C# i SQL, użytkownicy mogą zastępować domyślne semantyka wyrażeń przy użyciu typu jawnego rzutowania (`Cast` i `Convert`). Jednak udostępnianie tej możliwości granicy system typu stanowi dilemma. Rzutowanie SQL udostępniający żądaną semantyki nie można przetłumaczyć łatwe do odpowiedniego języka C# rzutowania. Z drugiej strony rzutowania C# nie można bezpośrednio przetłumaczyć równoważne SQL rzutowania z powodu niezgodności typów, brak odpowiedników i hierarchie pierwszeństwo innego typu. Istnieje zależność między udostępnianie niezgodność typów systemu i utraty zasilania znaczących wyrażenia.  
  
 W pozostałych przypadkach rzutowanie typów nie mogą być wymagane w domenie albo do sprawdzania poprawności wyrażenia, ale może być konieczne upewnij się, że mapowanie z systemem innym niż domyślny jest poprawnie zastosowana do wyrażenia.  
  
```  
-- Example from "Non-default Mapping" section extended  
create table T5 (  
    Col1      nvarchar(10),  
    Col2      nvarchar(10)  
)  
Insert into T5(col1, col2) values (‘3’, ‘2’);  
```  
  
 [!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
 [!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]  
  
```  
Select *  
From T5  
Where Col1 + Col2 > 4     
-- "Col1 + Col2" expr evaluates to '32'   
```  
  
## <a name="performance-issues"></a>Problemy z wydajnością  
 Ewidencjonowanie aktywności dla niektórych programu SQL Server — CLR różnice typu może resut w spadek wydajności przy przekraczaniu między CLR i SQL Server typu systemów. Następujące przykładowe scenariusze wpływające na wydajność:  
  
-   Wymusić kolejności oceny dla logicznej i/lub operatory  
  
-   Generowanie instrukcji SQL, aby wymusić kolejności oceny predykatu ogranicza możliwość Optymalizator SQL.  
  
-   Konwersje typów, czy wprowadzone przez kompilator CLR lub przez implementację obiektu relacyjnego zapytania może ograniczać użycie indeksu.  
  
     Na przykład  
  
    ```  
    -- Table DDL  
    create table T5 (  
        Col1      varchar(100)  
    )  
    ```  
  
     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]  
  
     Należy wziąć pod uwagę tłumaczenia wyrażenia `(s = SOME_STRING_CONSTANT)`.  
  
    ```  
    -- Corresponding part of SQL where clause  
    Where …  
    Col1 = SOME_STRING_CONSTANT  
    -- This expression is of the form <varchar> = <nvarchar>.  
    -- Hence SQL introduces a conversion from varchar to nvarchar,  
    --     resulting in  
    Where …  
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT  
    -- Cannot use the index for column Col1 for some implementations.  
    ```  
  
 Oprócz semantycznego różnice należy wziąć pod uwagę wpływ na wydajność przy przekraczaniu między serwerem SQL i CLR typu systemów. Dla dużych zestawów danych takie problemy z wydajnością można określić, czy aplikacja jest możliwy do wdrożenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
