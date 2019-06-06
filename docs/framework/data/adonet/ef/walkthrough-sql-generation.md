---
title: 'Przewodnik: Generowanie kodu SQL'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: 380ab80a577fa103c33328047cd24cce6be5cb6e
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690342"
---
# <a name="walkthrough-sql-generation"></a>Przewodnik: Generowanie kodu SQL

W tym temacie przedstawiono, jak odbywa się generowanie kodu SQL w [dostawcy próbki](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0). Następujące zapytanie SQL jednostki używa modelu, który jest uwzględniona w dostawcy próbki:

```sql
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName
        FROM NorthwindEntities.Products AS P) as j1
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry
            FROM NorthwindEntities.OrderDetails AS OD) as j2
            ON j1.ProductId == j2.ProductId
```

Zapytanie generuje następujące dane wyjściowe polecenia drzewa który jest przekazywane do dostawcy:

```
DbQueryCommandTree
|_Parameters
|_Query : Collection{Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]}
  |_Project
    |_Input : 'Join4'
    | |_InnerJoin
    |   |_Left : 'Join1'
    |   | |_LeftOuterJoin
    |   |   |_Left : 'Extent1'
    |   |   | |_Scan : dbo.Products
    |   |   |_Right : 'Extent2'
    |   |   | |_Scan : dbo.Categories
    |   |   |_JoinCondition
    |   |     |_
    |   |       |_Var(Extent1).CategoryID
    |   |       |_=
    |   |       |_Var(Extent2).CategoryID
    |   |_Right : 'Join3'
    |   | |_LeftOuterJoin
    |   |   |_Left : 'Extent3'
    |   |   | |_Scan : dbo.OrderDetails
    |   |   |_Right : 'Join2'
    |   |   | |_LeftOuterJoin
    |   |   |   |_Left : 'Extent4'
    |   |   |   | |_Scan : dbo.Orders
    |   |   |   |_Right : 'Extent5'
    |   |   |   | |_Scan : dbo.InternationalOrders
    |   |   |   |_JoinCondition
    |   |   |     |_
    |   |   |       |_Var(Extent4).OrderID
    |   |   |       |_=
    |   |   |       |_Var(Extent5).OrderID
    |   |   |_JoinCondition
    |   |     |_
    |   |       |_Var(Extent3).OrderID
    |   |       |_=
    |   |       |_Var(Join2).Extent4.OrderID
    |   |_JoinCondition
    |     |_
    |       |_Var(Join1).Extent1.ProductID
    |       |_=
    |       |_Var(Join3).Extent3.ProductID
    |_Projection
      |_NewInstance : Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]
        |_Column : 'C1'
        | |_1
        |_Column : 'ProductID'
        | |_Var(Join4).Join1.Extent1.ProductID
        |_Column : 'ProductName'
        | |_Var(Join4).Join1.Extent1.ProductName
        |_Column : 'CategoryName'
        | |_Var(Join4).Join1.Extent2.CategoryName
        |_Column : 'ShipCountry'
        | |_Var(Join4).Join3.Join2.Extent4.ShipCountry
        |_Column : 'ProductID1'
          |_Var(Join4).Join3.Extent3.ProductID
```

 W tym temacie opisano, jak tłumaczenie tego drzewa poleceń dane wyjściowe na następujące instrukcje SQL.

```sql
SELECT
1 AS [C1],
[Extent1].[ProductID] AS [ProductID],
[Extent1].[ProductName] AS [ProductName],
[Extent2].[CategoryName] AS [CategoryName],
[Join3].[ShipCountry] AS [ShipCountry],
[Join3].[ProductID] AS [ProductID1]
FROM   [dbo].[Products] AS [Extent1]
LEFT OUTER JOIN [dbo].[Categories] AS [Extent2] ON [Extent1].[CategoryID] = [Extent2].[CategoryID]
INNER JOIN
(SELECT [Extent3].[OrderID] AS [OrderID1], [Extent3].[ProductID] AS [ProductID], [Extent3].[UnitPrice] AS [UnitPrice], [Extent3].[Quantity] AS [Quantity], [Extent3].[Discount] AS [Discount], [Join2].[OrderID2], [Join2].[CustomerID], [Join2].[EmployeeID], [Join2].[OrderDate], [Join2].[RequiredDate], [Join2].[ShippedDate], [Join2].[Freight], [Join2].[ShipName], [Join2].[ShipAddress], [Join2].[ShipCity], [Join2].[ShipRegion], [Join2].[ShipPostalCode], [Join2].[ShipCountry], [Join2].[OrderID3], [Join2].[CustomsDescription], [Join2].[ExciseTax]
FROM  [dbo].[OrderDetails] AS [Extent3]
LEFT OUTER JOIN
      (SELECT [Extent4].[OrderID] AS [OrderID2], [Extent4].[CustomerID] AS [CustomerID], [Extent4].[EmployeeID] AS [EmployeeID], [Extent4].[OrderDate] AS [OrderDate], [Extent4].[RequiredDate] AS [RequiredDate], [Extent4].[ShippedDate] AS [ShippedDate], [Extent4].[Freight] AS [Freight], [Extent4].[ShipName] AS [ShipName], [Extent4].[ShipAddress] AS [ShipAddress], [Extent4].[ShipCity] AS [ShipCity], [Extent4].[ShipRegion] AS [ShipRegion], [Extent4].[ShipPostalCode] AS [ShipPostalCode], [Extent4].[ShipCountry] AS [ShipCountry], [Extent5].[OrderID] AS [OrderID3], [Extent5].[CustomsDescription] AS [CustomsDescription], [Extent5].[ExciseTax] AS [ExciseTax]
FROM  [dbo].[Orders] AS [Extent4]
LEFT OUTER JOIN [dbo].[InternationalOrders] AS [Extent5] ON [Extent4].[OrderID] = [Extent5].[OrderID]
      ) AS [Join2] ON [Extent3].[OrderID] = [Join2].[OrderID2]
   ) AS [Join3] ON [Extent1].[ProductID] = [Join3].[ProductID]
```

## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a>Pierwsza faza generowanie kodu SQL: Odwiedzający drzewa wyrażeń

Na poniższym rysunku przedstawiono początkowy stan pusty obiekt odwiedzający.  W tym temacie są wyświetlane tylko te właściwości, które są istotne dla wyjaśnienie wskazówki.

![Diagram](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")

Po odwiedzeniu węzła projektu VisitInputExpression jest wywoływana za pośrednictwem danych wejściowych (Join4), co powoduje wyzwolenie wizyty Join4 przez metodę VisitJoinExpression. Ponieważ jest elementem najwyższego poziomu sprzężenia, IsParentAJoin zwraca wartość false, a nowe SqlSelectStatement (SelectStatement0) zostanie utworzony i wypchnięty na stos instrukcji SELECT. Ponadto nowego zakresu (scope0) jest wprowadzana w tabeli symboli. Przed odwiedzeniu pierwsze dane wejściowe (po lewej stronie) sprzężenia 'true' są wypychane na stos IsParentAJoin. Po prawej, zanim odwiedzeniu Join1, czyli po lewej stronie dane wejściowe Join4 stan odwiedzający jest, jak pokazano na poniższej ilustracji.

![Diagram](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")

Gdy odwiedza sprzężenia metoda jest wywoływana za pośrednictwem Join4 IsParentAJoin ma wartość true, dlatego ponownie używa bieżącej instrukcji select SelectStatement0. Nowy zakres jest podana (Zakres1). Przed jego podrzędny po lewej stronie Extent1, odwiedzając inną wartość PRAWDA jest wypychane na stos IsParentAJoin.

Po odwiedzeniu Extent1, ponieważ IsParentAJoin zwraca wartość true, zwraca SqlBuilder, zawierające "[dbo]. [Products] ". Formant powraca do metody, odwiedzając Join4. Wpis zostanie zdjęte z IsParentAJoin i ProcessJoinInputResult nosi nazwę, która dołącza odwiedzający Extent1 do klauzuli From SelectStatement0 wynik. Nowe z symboli, symbol_Extent1, nazwa powiązania danych wejściowych "Extent1" jest utworzony, dodawane do FromExtents SelectStatement0, a także "Jako" i symbol_Extent1 są dołączane do klauzuli from. Nowy wpis jest dodawany do AllExtentNames dla "Extent1" o wartości 0. Nowy wpis jest dodawany do bieżącego zakresu w tabeli symboli, aby skojarzyć "Extent1" z jej symbol_Extent1 symboli. Symbol_Extent1 jest także dodawane do AllJoinExtents z SqlSelectStatement.

Zanim odwiedzeniu prawym wejściem Join1 "LEFT OUTER JOIN" zostanie dodany do klauzuli From SelectStatement0. Ponieważ odpowiednie dane wejściowe to wyrażenie skanowania, true zostanie ponownie przypisany do stosu IsParentAJoin. Stan przed odwiedzający odpowiednie dane wejściowe, jak pokazano na poniższej ilustracji.

![Diagram](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")

Odpowiednie dane wejściowe są przetwarzane w taki sam sposób, jak po lewej stronie dane wejściowe. Na kolejnej ilustracji przedstawiono stanu po odwiedzeniu odpowiednie dane wejściowe.

![Diagram](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")

Dalej "false" są wypychane na stos IsParentAJoin i Var(Extent1) warunek sprzężenia. CategoryID == Var(Extent2). CategoryID jest przetwarzany. Var(Extenent1) jest rozwiązywana \<symbol_Extent1 > po wyszukiwania w tabeli symboli. Ponieważ wystąpienie nie zostanie rozwiązany do symbolu proste w wyniku przetworzenia Var(Extent1). CategoryID, SqlBuilder z \<symbol1 >. " Zwracany jest CategoryID". Podobnie po stronie porównania jest przetwarzany, a wynik odwiedzający warunek sprzężenia jest dołączany do klauzuli FROM SelectStatement1, a wartość "false" zostanie zdjęte ze stosu IsParentAJoin.

Dzięki temu Join1 całkowicie zostały przetworzone i zakresem są zdjęte ze stosu z tabelą symboli.

Formant powraca do przetwarzania Join4, nadrzędny Join1. Ponieważ element podrzędny ponownie użyty w instrukcji Select, zakresów Join1 są zastępowane pojedynczego symbolu sprzężenia \<joinSymbol_Join1 >. Również nowy wpis zostanie dodany do tabeli symboli, aby skojarzyć Join1 z \<joinSymbol_Join1 >.

Następny węzeł przetwarzania jest Join3, drugi element podrzędny Join4. Ponieważ jest prawo podrzędnych, "false" zostanie przypisany do stosu IsParentAJoin. Następny rysunek przedstawia stanu obiektu odwiedzającego, w tym momencie.

![Diagram](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")

Dla Join3 IsParentAJoin zwraca wartość false i musi uruchomić nowy SqlSelectStatement (SelectStatement1) i wypchnąć je na stosie. Przetwarzanie będzie kontynuowane, jak za pomocą poprzedniego poprzedniego sprzężeń, nowego zakresu są wypychane na stosie i elementy podrzędne są przetwarzane. Po lewej stronie podrzędny jest zakres (Extent3) i odpowiednie podrzędny jest elementem sprzężenia (Join2) również potrzebuje, aby rozpocząć nowy SqlSelectStatement: SelectStatement2. Elementy podrzędne na Join2 są również zakresów i są agregowane do SelectStatement2.

Po odwiedzeniu Join2, ale przed jego przetwarzanie końcowe (ProcessJoinInputResult) odbywa się stan obiektu odwiedzającego po prawej stronie jest wyświetlany na poniższej ilustracji:

![Diagram](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")

Na poprzednim rysunku SelectStatement2 zostanie wyświetlone jako wolne liczb zmiennoprzecinkowych ponieważ był zdjęte ze stosu poza stosu, ale nie została jeszcze wpis przetwarzane przez nadrzędne. Jego musi zostać dodane do FROM części nadrzędnej, ale nie jest pełną instrukcję SQL bez klauzuli SELECT. Tak w tym momencie domyślnych kolumn (wszystkie kolumny zwracane przez jego danych wejściowych) są dodawane do listy wyboru przez metodę AddDefaultColumns. AddDefaultColumns iteruje symboli w FromExtents i dla każdego symbolu dodaje wszystkie kolumny w zakresie. Dla symbolu prosty wygląda na typ symbolu do pobrania jego właściwości mają zostać dodane. Wypełnia ono słownika AllColumnNames nazwami kolumn. Ukończone SelectStatement2 jest dołączany do klauzuli FROM SelectStatement1.

Następnie nowy symbol sprzężenia jest tworzone do reprezentowania Join2, jest oznaczona jako zagnieżdżonego sprzężenia i dodane do AllJoinExtents SelectStatement1 i dodane do tabeli symboli.  Teraz warunek sprzężenia Join3, Var(Extent3). OrderID = Var(Join2). Extent4.OrderID, musi być przetwarzane. Przetwarzanie po lewej stronie jest podobny do warunku join Join1. Jednak przetwarzanie po prawej stronie i po stronie "Var(Join2). Extent4.OrderID"jest inny, ponieważ spłaszczanie sprzężenia jest wymagana.

Następny rysunek przedstawia stan obiektu odwiedzającego po prawej stronie przed DbPropertyExpression "Var(Join2). Extent4.OrderID"jest przetwarzany.

Należy wziąć pod uwagę sposób "Var(Join2). Odwiedzeniu Extent4.OrderID". Pierwszy, właściwość wystąpienia "Var(Join2). Extent4 "odwiedzenia, który jest inny DbPropertyExpression i najpierw odwiedza jego wystąpienie"Var(Join2)". W górnym większość zakresie w tabeli symboli "Join2" jest rozpoznawana jako \<joinSymbol_join2 >. W metodzie odwiedziny dla DbPropertyExpression przetwarzania "Var(Join2). Extent4 "należy zauważyć, że symbol sprzężenia został zwrócony podczas odwiedzania wystąpienia i spłaszczanie nie jest wymagana.

Ponieważ jest zagnieżdżonego sprzężenia, firma Microsoft wyszukać właściwość "Extent4" w słowniku NameToExtent symbolu sprzężenia, rozwiązać go do \<symbol_Extent4 > i zwracają nowe SymbolPair (\<joinSymbol_join2 >, \<symbol_Extent4 >). Ponieważ pary symbol jest zwracany z przetwarzania wystąpienia "Var(Join2). Extent4.OrderID"właściwości"OrderID"jest rozwiązany z ColumnPart tej pary symbol (\<symbol_Extent4 >), który ma listy kolumn o zakresie, czyli przedstawia liczbę. Dlatego "Var(Join2). Extent4.OrderID"nie zostanie rozwiązany do { \<joinSymbol_Join2 >,". ", \<symbol_OrderID >}.

Warunek sprzężenia Join4 podobnie jest przetwarzany. Formant powraca do metody VisitInputExpression, który przetwarzał u góry większości projektów. Patrząc FromExtents elementu zwróconego SelectStatement0, danych wejściowych jest identyfikowany jako sprzężenia i usuwa oryginalny zakresów i zastępuje je nowy zakres symbolem po prostu sprzężenia. Zaktualizowano także tabeli symboli, a następnie jest przetwarzany projekcji częścią projektu. Rozpoznawanie właściwości i spłaszczanie zakresów sprzężenia jest zgodnie z wcześniejszym opisem.

![Diagram](../../../../../docs/framework/data/adonet/ef/media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")

Na koniec jest generowany SqlSelectStatement następujące:

```
SELECT:
  "1", " AS ", "[C1]",
  <symbol_Extent1>, ".", "[ProductID]", " AS ", "[ProductID]",
  <symbol_Extent1>, ".", "[ProductName]", " AS ", "[ProductName]",
  <symbol_Extent2>, ".", "[CategoryName]", " AS ", "[CategoryName]",
  <joinSymbol_Join3>, ".", <symbol_ShipCountry>, " AS ", "[ShipCountry]",
  <joinSymbol_Join3>, ".", <symbol_ProductID>, " AS ", "[ProductID1]"
FROM: "[dbo].[Products]", " AS ", <symbol_Extent1>,
        "LEFT OUTER JOIN ""[dbo].[Categories]", " AS ", <symbol_Extent2>, " ON ", <symbol_Extent1>, ".", "[CategoryID]", " = ", <symbol_Extent2>, ".", "[CategoryID]",
        "INNER JOIN ",
        " (", SELECT:
           <symbol_Extent3>, ".", "[OrderID]", " AS ", <symbol_OrderID>, ",
              <symbol_Extent3>, ".", "[ProductID]", " AS ", <symbol_ProductID>, ...,
         <joinSymbol_Join2>, ".", <symbol_OrderID_2>, ", ",
           <joinSymbol_Join2>, ".", <symbol_CustomerID>, ....,
        <joinSymbol_Join2>, ".", <symbol_OrderID_3>,
<joinSymbol_Join2>, ".", <symbol_CustomsDescription>,
<joinSymbol_Join2>, ".", <symbol_ExciseTax>
FROM: "[dbo].[OrderDetails]", " AS ", <symbol_Extent3>,
"LEFT OUTER JOIN ",
" (", SELECT:
<symbol_Extent4>, ".", "[OrderID]", " AS ", <symbol_OrderID_2>,
<symbol_Extent4>, ".", "[CustomerID]", " AS ", <symbol_CustomerID>, ...
<symbol_Extent5>, ".", "[OrderID]", " AS ", <symbol_OrderID_3>,
<symbol_Extent5>, ".", "[CustomsDescription]", " AS ", <symbol_CustomsDescription>,
<symbol_Extent5>, ".", "[ExciseTax]", " AS ", <symbol_ExciseTax>
FROM: "[dbo].[Orders]", " AS ", <symbol_Extent4>,
"LEFT OUTER JOIN ", , "[dbo].[InternationalOrders]", " AS ", <symbol_Extent5>,
" ON ", <symbol_Extent4>, ".", "[OrderID]", " = ", , <symbol_Extent5>, ".", "[OrderID]"
" )", " AS ", <joinSymbol_Join2>, " ON ", , , <symbol_Extent3>, ".", "[OrderID]", " = ", , <joinSymbol_Join2>, ".", <symbol_OrderID_2>
" )", " AS ", <joinSymbol_Join3>, " ON ", , , <symbol_Extent1>, ".", "[ProductID]", " = ", , <joinSymbol_Join3>, ".", <symbol_ProductID>
```

### <a name="second-phase-of-sql-generation-generating-the-string-command"></a>Drugi etap generowanie kodu SQL: Generowanie ciągu polecenia

Drugi etap tworzy rzeczywiste nazwy symboli, a tylko skupimy się na symbole reprezentujący kolumn o nazwach "OrderID", jak w przypadku, ten konflikt musi zostać rozpoznane. Te zostały wyróżnione SqlSelectStatement. Należy pamiętać, że sufiksy używane na ilustracji są tylko po to, aby podkreślić, że są one w różnych wystąpieniach, aby nie przedstawiają żadnych nowych nazw w tym testowanie ich końcowego nazwy (być może różnymi tworzą oryginalne nazwy) nie został jeszcze przypisany.

Pierwszym symbolem znaleziono, który wymaga zmiany nazwy jest \<symbol_OrderID >. Nie przypisano jej nową nazwę jako "OrderID1", 1 jest oznaczony jako ostatni umożliwiający sufiks "OrderID" i symbol jest oznaczony jako nie wymagające zmiany nazwy. Następnie, pierwsze użycie \<symbol_OrderID_2 > zostanie znaleziony. Jest zmieniana na Użyj następnej sufiksu dostępne ("OrderID2") i ponownie oznaczenie nie musi, zmiana nazwy, tak, aby następnym razem, gdy jest używany go nie uzyskać zmieniono jego nazwę. Jest to wykonywane \<symbol_OrderID_3 > zbyt.

Na końcu drugiej fazy generowany jest ostatnim instrukcji SQL.

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu SQL w dostawcy próbki](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
