---
title: 'Przewodnik: Generowanie kodu SQL'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: 09b5a3c2dea5cd0483d617ee8064b41dc19c3374
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248288"
---
# <a name="walkthrough-sql-generation"></a>Przewodnik: Generowanie kodu SQL

W tym temacie przedstawiono sposób generowania kodu SQL w [przykładowym dostawcy](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0). Poniższe zapytanie Entity SQL używa modelu dołączonego do przykładowego dostawcy:

```sql
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName
        FROM NorthwindEntities.Products AS P) as j1
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry
            FROM NorthwindEntities.OrderDetails AS OD) as j2
            ON j1.ProductId == j2.ProductId
```

Zapytanie generuje następujące drzewo poleceń wyjściowych, które są przekazywane do dostawcy:

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

 W tym temacie opisano sposób tłumaczenia tego drzewa poleceń wyjściowych na następujące instrukcje języka SQL.

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

## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a>Pierwsza faza generowania kodu SQL: Odwiedzanie drzewa wyrażeń

Na poniższej ilustracji przedstawiono początkowy pusty stan osoby odwiedzającej.  W tym temacie są wyświetlane tylko właściwości odpowiednie dla wyjaśnienia przewodnika.

![Diagram](./media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")

Gdy jest odwiedzany węzeł projektu, VisitInputExpression jest wywoływana nad jego danymi wejściowymi (Join4), które wyzwalają odwiedzanie Join4 przez metodę VisitJoinExpression. Ponieważ jest to przyłączanie do góry, IsParentAJoin zwraca wartość false, a nowy SqlSelectStatement (SelectStatement0) jest tworzony i wypychany na stosie instrukcji SELECT. Ponadto w tabeli symboli wprowadzono nowy zakres (scope0). Przed pierwszym (lewym) wejściem sprzężenia zostanie odwiedzana wartość "prawda" jest wypychana na stosie IsParentAJoin. Bezpośrednio przed Join1, który jest po lewej stronie Join4, jest odwiedzany, a stan osoby odwiedzającej jest jak pokazano na następnej ilustracji.

![Diagram](./media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")

Gdy wywoływana jest metoda dołączania za pośrednictwem Join4, IsParentAJoin ma wartość true, dlatego ponownie używa bieżącej instrukcji SELECT SelectStatement0. Wprowadzono nowy zakres (zakres1). Przed odwiedzeniem jego lewego elementu podrzędnego Extent1, inne prawdziwe jest wypychane na stosie IsParentAJoin.

Gdy Extent1 jest odwiedzany, ponieważ IsParentAJoin zwraca wartość true, zwraca element SqlBuilder zawierający "[dbo]. [Produkty] ". Kontrolka powraca do metody odwiedzającej Join4. Wpis jest zdjęte z IsParentAJoin, a ProcessJoinInputResult jest wywoływany, co powoduje dołączenie wyniku odwiedzania Extent1 do klauzuli FROM elementu SelectStatement0. Zostanie utworzony nowy symbol z symbol_Extent1, dla nazwy powiązania wejściowego "Extent1", dodany do FromExtents of SelectStatement0, a także "As" i symbol_Extent1, są dołączane do klauzuli FROM. Nowy wpis zostanie dodany do AllExtentNames dla "Extent1" z wartością 0. Nowy wpis zostanie dodany do bieżącego zakresu w tabeli symboli, aby skojarzyć "Extent1" z jego symbolem symbol_Extent1. Symbol_Extent1 jest również dodawany do AllJoinExtents SqlSelectStatement.

Przed odwiedzeniem prawego wejścia Join1 "lewe SPRZĘŻENIe zewnętrzne" jest dodawane do klauzuli FROM SelectStatement0. Ponieważ prawidłowe dane wejściowe są wyrażeniu skanowania, wartość true jest ponownie wypychana do stosu IsParentAJoin. Przed odpisaniem właściwych danych wejściowych, jak pokazano na następnej ilustracji.

![Diagram](./media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")

Prawidłowe dane wejściowe są przetwarzane w taki sam sposób, jak lewe dane wejściowe. Stan po odwiedzeniu prawego wejścia jest pokazywany na następnym rysunku.

![Diagram](./media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")

Następny "false" jest wypychany na stosie IsParentAJoin i warunku sprzężenia var (Extent1). IDKategorii = = var (Extent2). Identyfikator IDKategorii jest przetwarzany. Var (Extent1) jest rozpoznawana \<do symbol_Extent1 > Po odszukaniu w tabeli symboli. Ponieważ wystąpienie jest rozpoznawane jako prosty symbol, w wyniku przetwarzania var (Extent1). IDKategorii, element SqlBuilder z \<symbol1 > ". IDKategorii jest zwracany. Podobnie druga Strona porównania jest przetwarzana, a wynik przeszukiwania warunku sprzężenia jest dołączany do klauzuli FROM elementu SelectStatement1, a wartość "false" jest zdjęte ze stosu IsParentAJoin.

Dzięki temu Join1 został całkowicie przetworzony i zakres jest zdjęte z tabeli symboli.

Kontrolka powraca do przetwarzania Join4, nadrzędnego elementu Join1. Ponieważ element podrzędny ponownie użył instrukcji SELECT, zakresy Join1 są zastępowane pojedynczym symbolem \<sprzężenia joinSymbol_Join1 >. Ponadto do tabeli symboli zostanie dodany nowy wpis, aby skojarzyć Join1 z \<joinSymbol_Join1 >.

Następny węzeł do przetworzenia to Join3, drugi element podrzędny Join4. Ponieważ jest to prawy element podrzędny, "false" jest wypychany do stosu IsParentAJoin. Stan odwiedzającego w tym punkcie przedstawiono na następnej ilustracji.

![Diagram](./media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")

W przypadku Join3 funkcja IsParentAJoin zwraca wartość false i musi uruchomić nową SqlSelectStatement (SelectStatement1) i wypchnąć ją na stosie. Przetwarzanie będzie kontynuowane, jak poprzednio poprzednie sprzężenia, nowy zakres jest wypychany na stosie, a elementy podrzędne są przetwarzane. Lewy element podrzędny jest zakresem (Extent3), a prawy element podrzędny to sprzężenie (Join2), które również musi rozpocząć nową SqlSelectStatement: SelectStatement2. Elementy podrzędne w Join2 są również zakresami i są agregowane w SelectStatement2.

Stan odwiedzania po Join2 jest odwiedzany, ale przed rozpoczęciem jego przetwarzania post (ProcessJoinInputResult) pokazano na następnej ilustracji:

![Diagram](./media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")

Na powyższym rysunku SelectStatement2 jest pokazywany jako wolny swobodny, ponieważ został zdjęte poza stosem, ale nie został jeszcze przetworzony przez element nadrzędny. Należy dodać go do elementu z częścią nadrzędnej, ale nie jest to kompletna instrukcja SQL bez klauzuli SELECT. Dlatego w tym momencie domyślne kolumny (wszystkie kolumny utworzone przez dane wejściowe) są dodawane do listy wyboru przez metodę AddDefaultColumns. AddDefaultColumns wykonuje iterację symboli w FromExtents i dla każdego symbolu dodaje wszystkie kolumny, które zostały wprowadzone do zakresu. Dla prostego symbolu sprawdza typ symbolu, aby pobrać wszystkie jego właściwości do dodania. Wypełnia również słownik AllColumnNames nazwami kolumn. Ukończony SelectStatement2 jest dołączany do klauzuli FROM SelectStatement1.

Następnie nowy symbol sprzężenia jest tworzony w celu reprezentowania Join2, zostanie oznaczony jako zagnieżdżone sprzężenie i dodany do AllJoinExtents SelectStatement1 i dodany do tabeli symboli.  Teraz warunek sprzężenia Join3, VAR (Extent3). IDZamówienia = var (Join2). Extent4. IDZamówienia, musi zostać przetworzony. Przetwarzanie lewej strony jest podobne do warunku sprzężenia Join1. Jednak przetwarzanie po prawej stronie "var (Join2). Extent4. IDZamówienia "różni się, ponieważ jest wymagane spłaszczanie sprzężenia.

Następny rysunek przedstawia stan odwiedzających bezpośrednio przed DbPropertyExpression "var (Join2). Extent4. IDZamówienia "jest przetwarzana.

Rozważ, jak "var (Join2). Extent4. IDZamówienia "jest odwiedzana. Najpierw Właściwość wystąpienia "var (Join2). Extent4 "jest odwiedzana, która jest kolejną DbPropertyExpression i najpierw odwiedza swoje wystąpienie" var (Join2) ". W najbardziej najwyższym zakresie w tabeli symboli "Join2" jest rozpoznawana jako \<joinSymbol_join2 >. W metodzie zapoznaj się z DbPropertyExpression przetwarzaniem "var (Join2). Extent4 "Zwróć uwagę, że symbol sprzężenia został zwrócony podczas odwiedzania wystąpienia i jest wymagane spłaszczonie.

Ponieważ jest to zagnieżdżony element join, należy wyszukać Właściwość "Extent4" w słowniku NameToExtent symbolu sprzężenia, rozwiązać ją na \<symbol_Extent4 > i zwrócić nową SymbolPair (\<joinSymbol_join2 >, \<symbol_Extent4 >). Ponieważ para symboli jest zwracana z przetwarzania wystąpienia "var (Join2). Extent4. IDZamówienia ", właściwość" IDZamówienia "jest rozpoznawana z ColumnPart tej pary symboli (\<symbol_Extent4 >), która zawiera listę kolumn w zakresie, który reprezentuje. Tak więc, "var (Join2). Extent4. IDZamówienia "jest rozpoznawana jako \<{joinSymbol_Join2 >,". " \<, symbol_OrderID >}.

Warunek sprzężenia Join4 jest przetwarzany podobnie. Kontrolka powraca do metody VisitInputExpression, która przetworzyła najwyższy projekt. Patrząc na FromExtents zwróconej SelectStatement0, dane wejściowe są identyfikowane jako sprzężenie i usuwają oryginalne zakresy i zastępuje je nowym zakresem, tylko symbolem sprzężenia. Tabela symboli jest również aktualizowana, a następnie zostanie przetworzona część projekcji projektu. Rozpoznawanie właściwości i spłaszczenie zakresów sprzężenia jest zgodnie z wcześniejszym opisem.

![Diagram](./media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")

Na koniec jest tworzony następujący SqlSelectStatement:

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

### <a name="second-phase-of-sql-generation-generating-the-string-command"></a>Druga faza generowania kodu SQL: Generowanie ciągu polecenia

Druga faza tworzy rzeczywiste nazwy symboli i koncentruje się na symbolach reprezentujących kolumny o nazwie "IDZamówienia", tak jak w tym przypadku należy rozwiązać konflikt. Są one wyróżnione w SqlSelectStatement. Należy pamiętać, że sufiksy używane na rysunku są tylko podkreślenia, że są to różne wystąpienia, a nie do reprezentowania żadnych nowych nazw, tak jak na tym etapie ich ostateczne nazwy (prawdopodobnie różne w postaci oryginalnych nazw) nie zostały jeszcze przypisane.

Pierwszy znaleziony symbol, którego nazwę należy zmienić, to \<symbol_OrderID >. Nowa nazwa jest przypisana jako "OrderID1", 1 jest oznaczona jako ostatni używany sufiks dla "IDZamówienia" i symbol jest oznaczony jako niewymagające zmiany nazwy. Następnie zostanie znalezione pierwsze użycie \<symbol_OrderID_2 >. Nazwa zostanie zmieniona, aby użyć następnego dostępnego sufiksu ("OrderID2"), a następnie ponownie oznaczona jako niewymagające zmiany nazwy, więc przy następnym użyciu nie zostanie zmieniona nazwa. Jest to wykonywane tylko \<w przypadku symbol_OrderID_3 >.

Na końcu drugiej fazy jest generowana Ostatnia instrukcja SQL.

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu SQL w dostawcy próbki](sql-generation-in-the-sample-provider.md)
