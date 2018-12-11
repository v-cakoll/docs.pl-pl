---
title: Niezgodność typu SQL CLR
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 61731c4d9590892bdae8e90717d77b4dddf1d71d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147622"
---
# <a name="sql-clr-type-mismatches"></a>Niezgodność typu SQL CLR
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatyzuje większość tłumaczenie między model obiektu i programu SQL Server. Niemniej jednak czasami uniemożliwić dokładnego tłumaczenia. Tych kluczy niezgodności między wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) typów i typów bazy danych programu SQL Server są podsumowywane w poniższych sekcjach. Można znaleźć więcej szczegółów na temat mapowania określony typ i funkcję tłumaczenia w [mapowanie typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) i [typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).  
  
## <a name="data-types"></a>Typy danych  
 Tłumaczenie między CLR i programu SQL Server występuje, gdy zapytanie jest wysyłane do bazy danych, a wyniki są odsyłane do modelu obiektu. Na przykład poniższe zapytanie Transact-SQL wymaga dwóch konwersji wartości:  
  
```  
Select DateOfBirth From Customer Where CustomerId = @id     
```  
  
 Zapytania mogą być wykonywane w programie SQL Server, należy określić wartość dla parametru języka Transact-SQL. W tym przykładzie `id` wartość parametru, najpierw musi podlegać translacji z aparatu CLR <xref:System.Int32?displayProperty=nameWithType> typu do programu SQL Server `INT` wpisz, aby baza danych może zrozumieć, co to jest wartość. Następnie, aby pobrać wyniki programu SQL Server `DateOfBirth` kolumny musi podlegać translacji z programu SQL Server `DATETIME` typu CLR <xref:System.DateTime?displayProperty=nameWithType> typ do użycia w modelu obiektów. W tym przykładzie typy w modelu obiektów CLR i bazy danych programu SQL Server ma naturalny mapowań. Ale nie zawsze jest to wymagane.  
  
### <a name="missing-counterparts"></a>Brak odpowiedniki  
 Następujące typy nie mają odpowiedniki uzasadnione.  
  
-   Nie jest zgodny w CLR <xref:System> przestrzeni nazw:  
  
    -   **Niepodpisane liczby całkowite**. Zazwyczaj są mapowane te typy odpowiadają elementom podpisem większy rozmiar w celu uniknięcia przepełnienia. Literały mogą być konwertowane na podpisane liczbowy o tej samej lub mniejszym rozmiarze, na podstawie wartości.  
  
    -   **Wartość logiczna**. Te typy mogą być mapowane na bit lub większych numeryczny lub ciąg. Literał można zamapować na wyrażenie obliczane na tę samą wartość (na przykład `1=1` w języku SQL dla `True` w ze specyfikacją CLS).  
  
    -   **Przedział czasu**. Ten typ przedstawia różnicę między dwoma `DateTime` wartości i nie odpowiada żadnemu `timestamp` programu SQL Server. Środowisko CLR <xref:System.TimeSpan?displayProperty=nameWithType> może również mapować do programu SQL Server `TIME` typu w niektórych przypadkach. SQL Server `TIME` typu była przeznaczona tylko do reprezentowania wartości dodatnich mniej niż 24 godziny. Środowisko CLR <xref:System.TimeSpan> ma znacznie większy zakres.  
  
    > [!NOTE]
    >  Specyficzne dla programu SQL Server [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] wpisuje <xref:System.Data.SqlTypes> nie są uwzględnione w tym porównania.  
  
-   Niezgodność w programie SQL Server:  
  
    -   **Stałej długości typów znaków**. Transact-SQL rozróżnia między kategoriami Unicode i innego niż Unicode i ma trzy różne typy w każdej kategorii: stała długość `nchar` / `char`, o zmiennej długości `nvarchar` / `varchar`, i o większym rozmiarze `ntext` / `text`. Typy znaków o stałej długości mógłby być mapowany na środowisko CLR <xref:System.Char?displayProperty=nameWithType> typu pobierania znaków, ale nie naprawdę odpowiadają one tego samego typu w zakresie konwersji i zachowań.  
  
    -   **Bit**. Mimo że `bit` domena ma taką samą liczbę wartości jako `Nullable<Boolean>`, dwa są różnych typów. `Bit` pobiera wartości `1` i `0` zamiast `true` / `false`i nie można użyć jako równoważne wyrażeń logicznych.  
  
    -   **Sygnatura czasowa**. W przeciwieństwie do środowiska CLR <xref:System.TimeSpan?displayProperty=nameWithType> wpisz programu SQL Server `TIMESTAMP` typ reprezentuje 8-bajtowa liczba wygenerowanych przez bazę danych, który jest unikatowy dla każdej aktualizacji i nie jest oparty na różnicę między <xref:System.DateTime> wartości.  
  
    -   **Pieniędzy** i **SmallMoney**. Te typy mogą zostać zmapowane do <xref:System.Decimal> , ale są po prostu różnych typów i są traktowane jako takie konwersje i funkcji na serwerze.  
  
### <a name="multiple-mappings"></a>Wiele mapowań  
 Istnieje wiele typów danych programu SQL Server, mapowane na jeden lub więcej typów danych CLR. Istnieje wiele typów CLR, które można zamapować na jeden lub więcej typów programu SQL Server. Mimo że mapowanie może być obsługiwana w składniku LINQ to SQL, nie oznacza to, że dwa typy, które są mapowane między CLR i programu SQL Server są doskonałe dopasowanie, dokładności, zakresu i semantyki. Niektóre mapowania mogą obejmować różnice w wybranych lub wszystkich tych wymiarów. Można znaleźć szczegółowe informacje o tych różnic potencjalnych różne możliwości mapowania na [mapowanie typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
### <a name="user-defined-types"></a>Typy zdefiniowane przez użytkownika  
 Typy CLR zdefiniowane przez użytkownika mają na celu pomóc wypełnić tę przerwę systemu typu. Niemniej jednak ich powierzchni ciekawe problemy dotyczące wersji typu. Zmiana wersji na komputerze klienckim nie może towarzyszyć zmiany w typie przechowywane na serwerze bazy danych. Wszelkie takie zmiany powoduje, że inny niezgodność typów, gdzie semantyka typów mogą być niezgodne i przerwy w wersji może stanie się widoczna. Dalsze komplikacji występują jako hierarchii dziedziczenia są przetwarzane w kolejnych wersjach.  
  
## <a name="expression-semantics"></a>Semantyka wyrażeń  
 Oprócz parowania niezgodność między typami CLR i bazy danych wyrażenia zwiększenia złożoności niezgodność. Należy rozważyć niezgodności w semantyki operatora, semantykę funkcji, niejawna konwersja typu i reguły pierwszeństwa.  
  
 Poniższe podsekcje ilustrują niezgodność między najwyraźniej podobne wyrażenia. Może być można wygenerować wyrażenia SQL, które są semantycznie równoważne z danego wyrażenia CLR. Jednak nie jest jasne czy semantyczne różnice między najwyraźniej podobne wyrażenia są widoczne dla użytkownika CLR i w związku z tym tego, czy zmiany, które są wymagane dla semantyki równoważności mają czy nie. Jest to problem szczególnie istotne, gdy wyrażenie jest obliczane dla zestawu wartości. Wgląd w różnicy może zależeć od danych — i być trudne do zidentyfikowania się podczas kodowania i debugowania.  
  
### <a name="null-semantics"></a>Semantyka wartości null  
 Wyrażenia SQL Podaj przechowywanymi w trzech logiki dla wyrażeń logicznych. Wynik może być wartość true, false lub wartość null. Z drugiej strony CLR określa przechowywanymi w dwóch logiczną wynik porównania używające wartości null. Rozważmy poniższy kod:  
  
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
  
 Podobny problem występuje, przy założeniu, o wynikach binarnego.  
  
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
  
 W poprzednim przypadku otrzymasz równoważne zachowanie w generowanie kodu SQL, ale tłumaczenia nie może być dokładnie odzwierciedlają zamiaru.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie nakłada C# `null` lub Visual Basic `nothing` semantykę porównania w języku SQL. Operatory porównania składniowo są tłumaczone na ich odpowiedniki SQL. Semantyka odzwierciedlają semantyki SQL, zgodnie z definicją ustawienia serwera lub połączenia. Dwie wartości null są uznawane za nierówne w obszarze domyślne ustawienia programu SQL Server, (mimo że można zmienić ustawienia, aby zmienić semantyki). Niezależnie od tego [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie należy wziąć pod uwagę ustawień serwera w translacji zapytania.  
  
 Porównanie z literałem `null` (`nothing`) jest tłumaczona na odpowiednią wersję programu SQL (`is null` lub `is not null`).  
  
 Wartość `null` (`nothing`) w sortowaniu jest zdefiniowany przez program SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie powoduje zmiany sortowania.  
  
### <a name="type-conversion-and-promotion"></a>Konwersja typu i promocji  
 SQL obsługuje bogatego zestawu konwersji niejawnych; w wyrażeniach. Podobne wyrażenia w C# wymaga jawnego rzutowania. Na przykład:  
  
-   `Nvarchar` i `DateTime` można porównać typów w języku SQL bez żadnych jawnych rzutowań; C# wymaga jawnej konwersji.  
  
-   `Decimal` jest niejawnie konwertowany na `DateTime` w języku SQL. C#Nie zezwalaj na niejawną konwersję.  
  
 Podobnie, pierwszeństwo typ w języku Transact-SQL różni się od typu pierwszeństwo w C# ponieważ różni się podstawowy zestaw typów. W rzeczywistości nie ma wyczyść podzbioru/nadzbiór relacji między listami pierwszeństwo. Na przykład porównanie `nvarchar` z `varchar` powoduje, że niejawną konwersję `varchar` wyrażenie `nvarchar`. Środowisko CLR oferuje nie równoważne podwyższania poziomu.  
  
 W prostych przypadkach te różnice spowodować wyrażenia CLR z rzutowania jako nadmiarowe dla odpowiedniego wyrażenia SQL. Co ważniejsze, wyniki pośrednie wyrażenia SQL może być niejawnie promowane do typu, który nie ma odpowiednika dokładne w C#i na odwrót. Ogólne testowanie, debugowanie i sprawdzanie poprawności takich wyrażeń dodaje znaczne obciążenie na użytkownika.  
  
### <a name="collation"></a>Sortowanie  
 Języka Transact-SQL obsługuje sortowanie jawne jako adnotacje do typu ciągu znaków. Te sortowania sprawdzania poprawności pewne porównania. Na przykład porównanie dwóch kolumn przy użyciu innego sortowania jawne, występuje błąd. Użyj typu string znacznie uproszczone CTS nie powoduje takie błędy. Rozważmy następujący przykład:  
  
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
  
 W efekcie powoduje utworzenie listy sortowania *z ograniczeniami typu* nie jest to zastępowalne.  
  
 Podobnie kolejność sortowania może być znacznie różnią się w systemach typu. Różnica ta ma wpływ na sortowanie wyników. <xref:System.Guid> jest sortowany na wszystkich 16-bajtowy według porządku leksykograficznym (`IComparable()`), podczas gdy języka T-SQL porównuje identyfikatorów GUID w następującej kolejności: node(10-15) clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3). Ta kolejność było to SQL w wersji 7.0, gdy generowane NT identyfikatorów GUID miał zamówienie octet. Podejście zapewnia, że identyfikatory GUID generowany w tym samym klastrze węzła pochodzi ze sobą w kolejności sekwencyjnej, zgodnie z sygnatury czasowej. To podejście było również przydatne w przypadku tworzenia indeksów (wstawia stają się dołącza zamiast losowego dla systemu IOs). Kolejność zostało zaszyfrowane później w Windows ze względu na kwestie prywatności, ale SQL muszą zachować zgodność. Obejście polega na użyciu <xref:System.Data.SqlTypes.SqlGuid> zamiast <xref:System.Guid>.  
  
### <a name="operator-and-function-differences"></a>Operator i różnice funkcji  
 Operatory i funkcje, które są zasadniczo porównywalne ma semantykę różną kliknięcia. Na przykład:  
  
-   C#Określa semantyki zwarcia opartego na leksykalne Kolejność argumentów dla operatorów logicznych `&&` i `||`. SQL z drugiej strony jest przeznaczona dla zapytania oparte na zestawie i dlatego zapewnia większą swobodę w optymalizatorze podjęcie decyzji, kolejność wykonywania. Implikacje między innymi następujące:  
  
    -   Tłumaczenie semantycznie równoważne wymagałoby "`CASE` ... `WHEN` … `THEN`"skonstruować w języku SQL, aby uniknąć zmianę kolejności wykonywania operand.  
  
    -   Luźne tłumaczenia do `AND` / `OR` operatorów może spowodować nieoczekiwane błędy, jeśli C# wyrażenia opiera się na ocenie drugi operand jest oparty na wynik oceny pierwszy operand.  
  
-   `Round()` funkcja ma semantykę różną [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] i języka T-SQL.  
  
-   Indeks początkowy dla ciągów jest 0 w CLR, ale 1 w języku SQL. W związku z tym każda funkcja, która ma indeks musi tłumaczenia indeksu.  
  
-   Środowisko CLR obsługuje operator modulo (%) dla liczb zmiennoprzecinkowych, ale nie obsługuje programu SQL.  
  
-   `Like` Operator skutecznie uzyskuje automatyczne przeciążenia oparte na niejawne konwersje. Mimo że `Like` zdefiniowano operator może działać w typów ciągów znaków, niejawna konwersja z typów liczbowych lub `DateTime` typy umożliwia tych typów innych niż ciąg do użycia z `Like` równie dobrze. W CTS porównywalnych niejawne konwersje nie istnieją. W związku z tym potrzebne są dodatkowe przeciążenia.  
  
    > [!NOTE]
    >  To `Like` operator zachowanie dotyczy C# tylko Visual Basic `Like` — słowo kluczowe pozostaje niezmieniony.  
  
-   Przepełnienie zawsze ewidencjonowane SQL, ale musi on być jawnie określone w C# (nie w Visual Basic) w celu uniknięcia zapętlenia. Biorąc pod uwagę kolumn liczb całkowitych, C1, C2 i C3, jeśli C1 + C2 jest przechowywany w C3 (aktualizację T Ustaw C3 = C1 + C2).  
  
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
  
-   SQL wykonuje operacje arytmetyczne symetrycznego zaokrąglania podczas [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] banker używa przez zaokrąglenie. Zobacz artykuł bazy wiedzy 196652, aby uzyskać więcej informacji.  
  
-   Porównywanie ciągów znaków są domyślnie dla typowych ustawień regionalnych, bez uwzględniania wielkości liter w języku SQL. W języku Visual Basic, a w C#, ich jest rozróżniana wielkość liter. Na przykład `s == "Food"` (`s = "Food"` w języku Visual Basic) i `s == "Food"` może przynieść różne wyniki, jeśli `s` jest `food`.  
  
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
  
-   Operatory / funkcje stosowane do argumentów typu znaków o stałej długości w języku SQL mają znacząco różną semantykę, niż te same operatory/funkcje stosowane do środowiska CLR <xref:System.String?displayProperty=nameWithType>. Może to także wyświetlane jako rozszerzenie Brak problemu odpowiednika omówione w sekcji o typach.  
  
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
  
     Podobny problem występuje, za pomocą ciągów.  
  
    ```  
    create table T6 (  
        Col1      nchar(4)  
        Col2       nchar(4)  
    )  
    Insert into T6 values ('a', 'b');  
    Select Col1+Col2 from T6  
    -- Returns concatenation of padded strings "a   b   " and not "ab".  
    ```  
  
 Podsumowując zawiłe tłumaczenia mogą być wymagane dla wyrażenia CLR i dodatkowe funkcje operatorów może być konieczne ujawniać funkcjonalność SQL.  
  
### <a name="type-casting"></a>Rzutowanie typów  
 W C# a w bazach SQL, użytkownicy mogą przesłaniać semantyki domyślne wyrażeń przy użyciu typu jawnego rzutowania (`Cast` i `Convert`). Jednak udostępnianie tej funkcji przez granicę systemu typu stanowi dilemma. Rzutowanie SQL, który zapewnia semantykę, żądany nie można łatwo przekształcić na odpowiedni C# rzutowania. Z drugiej strony C# cast nie można bezpośrednio przetłumaczyć równoważne SQL rzutowanie ze względu na niezgodność typu, brak odpowiedniki i hierarchie pierwszeństwo innego typu. Istnieje zależność między Uwidacznianie typu niezgodność systemu i utraty zasilania znaczące wyrażenia.  
  
 W innych przypadkach rzutowanie typów nie mogą być wymagane w domenie, albo do sprawdzania poprawności wyrażenia, ale mogą być wymagane, aby upewnić się, że mapowanie innych niż domyślne jest prawidłowo stosowane do wyrażenia.  
  
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
 Ewidencjonowanie aktywności dla niektórych SQL Server CLR różnice typu może spowodować spadek wydajności przy przekraczaniu między CLR i programu SQL Server typu systemów. Następujące przykładowe scenariusze wpływające na wydajność:  
  
-   Wymusić kolejności oceny dla logicznej i/lub operatorów  
  
-   Generowanie kodu SQL, aby wymusić kolejności oceny predykatu ogranicza możliwość Optymalizator SQL.  
  
-   Konwersje typów czy wprowadzony przez kompilator CLR lub implementacja obiektowo-relacyjny kwerendy może ograniczać użycie indeksu.  
  
     Na przykład  
  
    ```  
    -- Table DDL  
    create table T5 (  
        Col1      varchar(100)  
    )  
    ```  
  
     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]  
  
     Należy wziąć pod uwagę Translacja wyrażeń `(s = SOME_STRING_CONSTANT)`.  
  
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
  
 Oprócz semantyczne różnice należy wziąć pod uwagę wpływ na wydajność przy przekraczaniu między programu SQL Server i systemów typu CLR. Dla dużych zestawów danych takie problemy z wydajnością można określić, czy aplikacja ma do wdrożenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
