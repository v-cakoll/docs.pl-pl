---
title: Generowanie kodu SQL na podstawie drzew poleceń — najlepsze rozwiązania
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 6ac46b577f071bca6c79e23b8b77f9b267ac879b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369672"
---
# <a name="generating-sql-from-command-trees---best-practices"></a>Generowanie kodu SQL na podstawie drzew poleceń — najlepsze rozwiązania

Drzew poleceń kwerendy danych wyjściowych dokładnie modelowały zapytania można wyrazić w języku SQL. Istnieją pewne typowe wyzwania dla dostawcy modułów zapisujących podczas generowania SQL z poziomu drzewa poleceń w danych wyjściowych. W tym temacie omówiono te wyzwania. W następnym temacie dostawcy przykładowych pokazano, jak te wyzwania.

## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a>Grupowanie węzłów DbExpression w instrukcji SQL SELECT

Typowe instrukcji SQL ma zagnieżdżonej struktury kształtu następujące:

```sql
SELECT …
FROM …
WHERE …
GROUP BY …
ORDER BY …
```

Jeden lub więcej klauzul, może być pusta.  Użycie zagnieżdżonej instrukcji SELECT może wystąpić w dowolnym wierszu.

Możliwe tłumaczenie zapytania drzewa poleceń na instrukcję SQL SELECT dałby w efekcie podzapytania jeden dla każdego operator relacyjny. Jednakże, co może spowodować niepotrzebne zagnieżdżonych podzapytań, które byłyby trudne do odczytania.  Na niektóre magazyny danych zapytanie może działać nieprawidłowo.

Na przykład należy wziąć pod uwagę następujące drzewo poleceń zapytania

```
Project (
a.x,
   a = Filter(
      b.y = 5,
      b = Scan("TableA")
   )
)
```

Tłumaczenie nieefektywne dałby w efekcie:

```sql
SELECT a.x
FROM (   SELECT *
         FROM TableA as b
         WHERE b.y = 5) as a
```

Należy pamiętać, że każdy węzeł wyrażenie relacyjne staje się nowych instrukcji SQL SELECT.

W związku z tym należy zagregować dowolną liczbę węzłów wyrażenia jak to możliwe w pojedynczej instrukcji SQL SELECT przy jednoczesnym zachowaniu poprawności.

Będzie wynik takiego agregacji, na przykład przedstawiony powyżej:

```sql
SELECT b.x
FROM TableA as b
WHERE b.y = 5
```

## <a name="flatten-joins-in-a-sql-select-statement"></a>Spłaszczanie sprzężenia w instrukcji SQL SELECT

Jeden przypadek agregowanie wielu węzłów w pojedynczej instrukcji SQL SELECT jest agregowanie wielu wyrażeniach sprzężenia w pojedynczej instrukcji SQL SELECT. DbJoinExpression reprezentuje pojedynczy łączenia dwóch wartościach wejściowych. Jednak w ramach pojedynczej instrukcji SQL SELECT, można określić więcej niż jedno połączenie. W takim przypadku sprzężeń są wykonywane w określonej kolejności.

Pozostanie grzbietu sprzężeń, (sprzężenia, które są wyświetlane jako element podrzędny lewego sprzężenia innego) może być łatwiej jako spłaszczone do pojedynczą instrukcję SQL SELECT. Na przykład należy wziąć pod uwagę następujące drzewo poleceń kwerendy:

```
InnerJoin(
   a = LeftOuterJoin(
   b = Extent("TableA")
   c = Extent("TableB")
   ON b.y = c.x ),
   d = Extent("TableC")
   ON a.b.y = d.z
)
```

Może zostać poprawnie przetłumaczony na:

```sql
SELECT *
FROM TableA as b
LEFT OUTER JOIN TableB as c ON b.y = c.x
INNER JOIN TableC as d ON b.y = d.z
```

Jednak sprzężeń grzbietu — po lewej stronie nie można łatwo spłaszczone i nie należy próbować spłaszczanie ich. Na przykład sprzężeń w następującym zapytaniu polecenie drzewa:

```
InnerJoin(
   a = Extent("TableA")
   b = LeftOuterJoin(
   c = Extent("TableB")
   d = Extent("TableC")
   ON c.y = d.x),
   ON a.z = b.c.y
)
```

Może zostać przetłumaczone na instrukcję SQL SELECT podzapytaniu.

```sql
SELECT *
FROM TableA as a
INNER JOIN (SELECT *
   FROM TableB as c
   LEFT OUTER JOIN TableC as d
   ON c.y = d.x) as b
ON b.y = d.z
```

## <a name="input-alias-redirecting"></a>Wprowadź Alias przekierowania folderu

Aby wyjaśnić, przekierowywanie alias danych wejściowych, należy wziąć pod uwagę Struktura wyrażeń relacyjnych, takich jak DbFilterExpression DbProjectExpression, obiekt DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, metody DbApplyExpression, i DbSkipExpression.

Każdy z tych typów ma jedną lub więcej właściwości danych wejściowych, które opisują kolekcję danych wejściowych, a zmienna powiązania odpowiadający każdej danych wejściowych jest używana do reprezentowania każdy element te dane wejściowe podczas przechodzenia kolekcji. Zmienna powiązania jest używana przy odwoływaniu się do elementu danych wejściowych, na przykład w predykacie własności DbFilterExpression lub właściwości projekcji DbProjectExpression.

Podczas agregowania więcej węzłów wyrażenie relacyjne w pojedynczej instrukcji SQL SELECT i ocenianie wyrażenia, który jest częścią wyrażenie relacyjne (na przykład część właściwości projekcji DbProjectExpression) Zmienna powiązania, która używa może nie być taka sama jak alias danych wejściowych, jak wiele powiązań wyrażenie musi zostać przekierowany do jednego zakresu.  Ten problem jest wywoływana, zmiana nazwy aliasu.

Należy wziąć pod uwagę pierwszego przykładu w tym temacie. Jeśli podczas tłumaczenia naiwni i tłumaczenie projekcji "a.x" (DbPropertyExpression (, x)), jest poprawna do tłumaczenia go do `a.x` dysponujemy alias danych wejściowych jako "a", aby dopasować zmienna powiązania.  Jednak podczas agregowania obu węzłów w pojedynczej instrukcji SQL SELECT, potrzebne jest tłumaczenie tych samych DbPropertyExpression do `b.x`, jak dane wejściowe były aliasem znakiem "b".

## <a name="join-alias-flattening"></a>Dołącz do spłaszczanie aliasu

W odróżnieniu od wszelkich innych wyrażenie relacyjne w danych wyjściowych polecenia drzewa DbJoinExpression danych wyjściowych typu wyniku, który jest wiersz składający się z dwóch kolumn, z których każdy odpowiada jednej z danych wejściowych. DbPropertyExpression został opracowany pod kątem dostępu do właściwości skalarne pochodzące z sprzężenia, jest za pośrednictwem innego DbPropertyExpression.

Przykłady obejmują "a.b.y" w przykładzie 2 i "b.c.y" w przykładzie 3. Jednak w odpowiedniej instrukcji SQL są one określane jako "b.y". Aliasów re nosi nazwę spłaszczanie alias sprzężenia.

## <a name="column-name-and-extent-alias-renaming"></a>Nazwa kolumny i zakresu, Alias zmiana nazwy

Jeśli kwerendę SQL SELECT z sprzężenia ma zostać wykonane z projekcją, podczas wyliczania wszystkich kolumn uczestniczących w programie z wprowadzonymi danymi, może wystąpić kolizja nazwy, jako więcej niż jeden zestaw danych wejściowych może mieć taką samą nazwę kolumny. Użyj innej nazwy dla kolumny, aby uniknąć kolizji.

Ponadto podczas spłaszczanie sprzężeń, tabele (ani podzapytań) może być kolizji aliasy, w którym zamierzone, Zapisz te potrzeby można zmienić jego nazwy.

## <a name="avoid-select-"></a>Należy unikać SELECT *

Nie używaj `SELECT *` dokonania wyboru z tabel podstawowych. Model magazynu w [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji mogą zawierać tylko podzbiór kolumn, które znajdują się w tabeli bazy danych. W tym przypadku `SELECT *` może wygenerować niepoprawny wynik. Zamiast tego należy określić wszystkich kolumn uczestniczących w programie przy użyciu nazwy kolumn z typu wyniku wyrażenia uczestniczących w programie.

## <a name="reuse-of-expressions"></a>Ponowne użycie wyrażeń

Wyrażenia może zostać ponownie użyte w drzewo poleceń zapytania, które są przekazywane przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Nie należy zakładać, każde wyrażenie jest wyświetlany w drzewie polecenia kwerendy tylko raz.

## <a name="mapping-primitive-types"></a>Mapowanie typów pierwotnych

Podczas mapowania koncepcyjny typów (EDM struktury) do dostawcy typów, powinny być mapowane do najszerszego typu (Int32) tak, aby dopasować wszystkich możliwych wartości. Ponadto należy unikać mapowanie dla typów, których nie można używać w wielu operacjach, takich jak typy obiektów BLOB (na przykład `ntext` w programie SQL Server).

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
