---
title: "Wskazówki: Generowanie kodu SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c3d952c2a9e8f1199fa8ef4b6181dabcfbcc4012
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-sql-generation"></a>Wskazówki: Generowanie kodu SQL
W tym temacie przedstawiono, jak generowanie kodu SQL występuje w [dostawcy próbki](http://go.microsoft.com/fwlink/?LinkId=180616). Następujące zapytanie SQL jednostki korzysta z modelu, który jest dołączony do dostawcy próbki:  
  
```  
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId  
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName  
        FROM NorthwindEntities.Products AS P) as j1  
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry  
            FROM NorthwindEntities.OrderDetails AS OD) as j2  
            ON j1.ProductId == j2.ProductId   
```  
  
 Kwerenda zwraca następujące drzewo dane wyjściowe polecenia są przekazywane do dostawcy:  
  
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
  
 W tym temacie opisano, jak tłumaczenie tego drzewa poleceń dane wyjściowe do następujących instrukcji SQL.  
  
```  
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
  
## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a>Pierwszą fazę generowanie kodu SQL: odwiedzający wyrażenie drzewa  
 Na poniższym rysunku przedstawiono początkowy stan pusty obiekt odwiedzający.  W tym temacie przedstawiono wyjaśnienie wskazówki dotyczące właściwości.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")  
  
 Po odwiedzeniu węzła projektu VisitInputExpression jest wywoływana przez jego danych wejściowych (Join4), która wyzwala odwiedziny Join4 przez metodę VisitJoinExpression. Ponieważ jest to najwyżej sprzężenia, IsParentAJoin zwraca wartość false i nowych SqlSelectStatement (SelectStatement0) jest tworzony i wypychana na stosie instrukcji SELECT. Ponadto nowy zakres (scope0) została wprowadzona w tabeli symboli. Przed odwiedzenia pierwszy danych wejściowych (lewych) sprzężenia 'true' spoczywa na stosie IsParentAJoin. Tuż przed odwiedzenia Join1, czyli po lewej stronie wprowadzania Join4 stan obiektu odwiedzającego jest pokazany na rysunku dalej.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")  
  
 Gdy odwiedź sprzężenie metoda jest wywoływana przez Join4 IsParentAJoin ma wartość true, w związku z tym ponownie używa bieżącej instrukcji select SelectStatement0. Nowy zakres jest wprowadzona (Zakres1). Przed jego lewy element podrzędny, Extent1, odwiedzając innego true spoczywa na stosie IsParentAJoin.  
  
 Po odwiedzeniu Extent1, ponieważ IsParentAJoin zwraca wartość true, zwraca SqlBuilder, zawierający "[dbo]. [Produkty] ". Zwraca formantu do metody odwiedzający Join4. Wpis jest zdjęte ze stosu z IsParentAJoin i ProcessJoinInputResult jest wywoływana, które dołącza odwiedzający Extent1 do klauzuli From SelectStatement0 wynik. Nowy z symbolu, symbol_Extent1, dla nazwy powiązania wejściowego "Extent1" został utworzony, dodane do FromExtents SelectStatement0, a także "Jako" i symbol_Extent1 są dołączane do klauzuli from. Nowy wpis jest dodawany do AllExtentNames do "Extent1" o wartości 0. Nowy wpis zostanie dodany do bieżącego zakresu w tabeli symboli do skojarzenia z jego symbol_Extent1 symbol "Extent1". Symbol_Extent1 jest także dodawane do AllJoinExtents z SqlSelectStatement.  
  
 Przed odwiedzenia odpowiednie dane wejściowe z Join1 "LEFT OUTER JOIN" zostanie dodany do klauzuli From SelectStatement0. Ponieważ odpowiednie dane wejściowe to wyrażenie skanowania, true ponownie spoczywa na stos IsParentAJoin. Stan przed odwiedzający odpowiednie dane wejściowe, jak pokazano na rysunku dalej.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")  
  
 Dane wejściowe są przetwarzane w taki sam sposób jak po lewej stronie dane wejściowe. Stan po odwiedzeniu odpowiednie dane wejściowe pokazano na rysunku dalej.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")  
  
 Następny "false" spoczywa na stosie IsParentAJoin i Var(Extent1) warunek sprzężenia. CategoryID == Var(Extent2). CategoryID jest przetwarzany. Var(Extenent1) jest rozpoznać < symbol_Extent1 > po sprawdzeniu się w tabeli symboli. Ponieważ wystąpienie nie zostanie rozwiązany do symbolu proste, w wyniku przetworzenia Var(Extent1). CategoryID, SqlBuilder z \<symbol1 >. " Zwracany jest identyfikatorem kategorii". Podobnie po stronie porównania jest przetwarzany i wynik odwiedzający warunek sprzężenia jest dołączany do klauzuli FROM SelectStatement1, a wartość "false" jest zdjęte ze stosu ze stosu IsParentAJoin.  
  
 O tym Join1 zostały całkowicie przetworzone, a zakres jest zdjęte ze stosu z tabelą symboli.  
  
 Zwraca sterowania do przetwarzania Join4, nadrzędny Join1. Ponieważ podrzędne ponownie użyć instrukcji Select, zakresy Join1 są zastępowane jeden symbol sprzężenia < joinSymbol_Join1 >. Także nowy wpis jest dodawany do tabeli symboli, aby skojarzyć Join1 z < joinSymbol_Join1 >.  
  
 Następny węzeł przetwarzania jest Join3, drugi podrzędnym Join4. Po wykonaniu prawy element podrzędny, "false" spoczywa na stos IsParentAJoin. Następny rysunek przedstawia stan osoby odwiedzającej jest możliwe w tym momencie.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")  
  
 Dla Join3 IsParentAJoin zwraca wartość false i należy uruchomić nowe SqlSelectStatement (SelectStatement1) i wypchnąć go na stosie. Przetwarzanie będzie kontynuowane, jak z poprzedniej poprzedniej sprzężenia, nowego zakresu spoczywa na stosie i elementy podrzędne są przetwarzane. Lewy element podrzędny jest zakres (Extent3) i prawy element podrzędny sprzężenia (Join2), którą należy uruchomić nowe SqlSelectStatement: SelectStatement2. Elementy podrzędne na Join2 są również zakresy i są agregowane do SelectStatement2.  
  
 Stan obiektu odwiedzającego prawa po odwiedzeniu Join2, ale przed jego przetwarzanie końcowe (ProcessJoinInputResult) jest wykonywane jest pokazywana w następny rysunek:  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")  
  
 Na poprzedniej ilustracji SelectStatement2 jest wyświetlana jako przestawne wolnego ponieważ został zdjęte ze stosu poza stosu, ale nie została jeszcze post przetworzone przez element nadrzędny. Wymaga do dodania do części od elementu nadrzędnego, ale nie jest pełną instrukcję SQL bez klauzuli SELECT. Tak w tym momencie domyślne kolumny (wszystkie kolumny tworzone przez komponenty) są dodawane do listy wyboru przez metodę AddDefaultColumns. AddDefaultColumns przechodzi przez symbole w FromExtents i dla każdego symbolu dodaje wszystkie kolumny w zakresie. Dla symbolu proste wygląda na typ symbolu do pobrania jego właściwości mają zostać dodane. Wypełnia słownik AllColumnNames z nazw kolumn. Ukończono SelectStatement2 jest dołączany do klauzuli FROM SelectStatement1.  
  
 Następnie jest tworzony nowy symbol sprzężenia, do reprezentowania Join2, jest oznaczony jako zagnieżdżony sprzężenia i dodane do AllJoinExtents SelectStatement1 i dodane do tabeli symboli.  Teraz warunek sprzężenia Join3, Var(Extent3). OrderID = Var(Join2). Extent4.OrderID, musi być przetwarzane. Przetwarzanie z lewej strony jest podobny do Join1 warunek sprzężenia. Jednak przetwarzanie prawo i po stronie "Var(Join2). Extent4.OrderID"jest inny, ponieważ spłaszczanie sprzężenia jest wymagana.  
  
 Następny rysunek przedstawia stan prawa odwiedzający przed DbPropertyExpression "Var(Join2). Extent4.OrderID"jest przetwarzany.  
  
 Należy rozważyć sposób "Var(Join2). Odwiedzenia Extent4.OrderID". Pierwsza strona, właściwości wystąpienia "Var(Join2). Extent4 "odwiedzenia, który jest inny DbPropertyExpression i najpierw odwiedza wystąpienia"Var(Join2)". W górnym większości zakresie w tabeli symboli "Join2" jest rozpoznawany jako < joinSymbol_join2 >. W metodzie odwiedziny dla DbPropertyExpression przetwarzania "Var(Join2). Extent4 "należy zauważyć, że symbol sprzężenia został zwrócony podczas odwiedzania wystąpienie i spłaszczania jest wymagana.  
  
 Ponieważ jest zagnieżdżony sprzężenia, możemy wyszukiwania właściwości "Extent4" w słowniku NameToExtent symbolu sprzężenia, odpowiada < symbol_Extent4 > i zwraca nowy SymbolPair (< joinSymbol_join2 >, < symbol_Extent4 >). Ponieważ parę symbol jest zwracana z przetwarzanie wystąpienia "Var(Join2). Extent4.OrderID"właściwości"OrderID"jest rozwiązany z ColumnPart pary tego symbolu (< symbol_Extent4 >) z listą kolumn zakresu, który reprezentuje. Dlatego "Var(Join2). Extent4.OrderID"zostanie rozwiązany do {< joinSymbol_Join2 >". ", < symbol_OrderID >}.  
  
 Warunek sprzężenia Join4 podobnie jest przetwarzany. Formant zwraca do metody VisitInputExpression przetwarzania górnej większości projektu. Patrzeć FromExtents z SelectStatement0 zwrócone, danych wejściowych jest rozpoznawany jako sprzężenia i usuwa oryginalny zakres i zastępuje je nowy zakres symbolem tylko sprzężenia. Zaktualizowano także tabeli symboli, a następne projekcji częścią projektu jest przetwarzany. Rozpoznawanie właściwości i spłaszczanie zakresów sprzężenia jest zgodnie z wcześniejszym opisem.  
  
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
  
### <a name="second-phase-of-sql-generation-generating-the-string-command"></a>Drugi etap generowanie kodu SQL: generowanie polecenie String  
 Na drugim etapie tworzących rzeczywiste nazwy symboli i skupimy symboli reprezentujący kolumny o nazwie "OrderID", jak w przypadku tej konflikt musi zostać rozpoznane. Te zostały wyróżnione SqlSelectStatement. Należy pamiętać, że sufiksy używane na ilustracji są tylko, aby podkreślić, że są one różnych wystąpień, aby nie reprezentują wszelkie nowe nazwy, ponieważ w tej etap nazwy końcowego (być może różnymi tworzą oryginalnej nazwy) nie został jeszcze przypisany.  
  
 Symbol pierwszy znaleziony, która musi zostać zmienione jest < symbol_OrderID >. Nie przypisano jej nową nazwę jako "OrderID1", 1 jest oznaczony jako ostatniego używać sufiksu dla "OrderID" oraz symbol jest oznaczony jako nie wymagające zmiany nazwy. Następnie to pierwsze użycie < symbol_OrderID_2 > zostanie znaleziony. Jest zmieniana na używają sufiksu dostępne dalej ("OrderID2") i ponownie oznaczony jako nie wymagające zmiany nazwy, tak, aby następnym służy on nie uzyskać zmieniona. Jest to realizowane dla < symbol_OrderID_3 > zbyt.  
  
 Na koniec drugiej fazy jest generowany końcowej instrukcji SQL.  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie kodu SQL w dostawcy próbki](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
