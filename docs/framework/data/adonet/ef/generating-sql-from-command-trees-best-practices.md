---
title: Generowanie kodu SQL na podstawie drzew poleceń — najlepsze praktyki
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 869722b91550855a184a74e706271c3e2d417b84
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039995"
---
# <a name="generating-sql-from-command-trees---best-practices"></a>Generowanie kodu SQL na podstawie drzew poleceń — najlepsze praktyki

Drzewa poleceń zapytania danych wyjściowych ściśle modelują zapytania można wyrazić elementu w SQL. Jednak istnieją pewne typowe wyzwania dla autorów dostawcy podczas generowania kodu SQL z drzewa poleceń wyjściowych. W tym temacie omówiono te wyzwania. W następnym temacie Przykładowy dostawca pokazuje, jak rozwiązać te wyzwania.

## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a>Grupuj węzły DbExpression w instrukcji SELECT języka SQL

Typowa instrukcja SQL ma zagnieżdżoną strukturę następującego kształtu:

```sql
SELECT …
FROM …
WHERE …
GROUP BY …
ORDER BY …
```

Co najmniej jedna klauzula może być pusta.  Zagnieżdżona instrukcja SELECT może wystąpić w dowolnym z wierszy.

Możliwe tłumaczenie drzewa poleceń zapytania do instrukcji SQL SELECT spowoduje utworzenie jednego podzapytania dla każdego operatora relacyjnego. Jednak może to spowodować niepotrzebne zagnieżdżone podzapytania, które byłyby trudne do odczytania.  W niektórych magazynach danych zapytanie może działać nieprawidłowo.

Rozważmy na przykład następujące drzewo poleceń zapytania

```csharp
Project (
a.x,
   a = Filter(
      b.y = 5,
      b = Scan("TableA")
   )
)
```

Niewydajne tłumaczenie spowoduje wygenerowanie:

```sql
SELECT a.x
FROM (   SELECT *
         FROM TableA as b
         WHERE b.y = 5) as a
```

Należy zauważyć, że każdy węzeł wyrażenia relacyjnego zostanie nowym instrukcją SELECT języka SQL.

W związku z tym ważne jest, aby w jednej instrukcji SQL SELECT agregować tyle węzłów wyrażenia, jak to możliwe, jednocześnie zachowując poprawność.

Wynikiem takiej agregacji dla przykładu przedstawionego powyżej byłoby:

```sql
SELECT b.x
FROM TableA as b
WHERE b.y = 5
```

## <a name="flatten-joins-in-a-sql-select-statement"></a>Spłaszczanie sprzężeń w instrukcji SELECT języka SQL

Jednym z przypadków agregowania wielu węzłów w jednej instrukcji SQL SELECT jest agregowanie wielu wyrażeń sprzężenia do jednej instrukcji SELECT języka SQL. DbJoinExpression reprezentuje jedno sprzężenie między dwoma danymi wejściowymi. Jednakże w ramach jednej instrukcji SELECT języka SQL można określić więcej niż jedno sprzężenie. W takim przypadku sprzężenia są wykonywane w określonej kolejności.

Lewe sprzężenie z lewej strony (sprzężenia, które pojawiają się jako lewy element podrzędny innego sprzężenia), można łatwiej spłaszczyć do jednej instrukcji SELECT języka SQL. Rozważmy na przykład następujące drzewo poleceń zapytania:

```csharp
InnerJoin(
   a = LeftOuterJoin(
   b = Extent("TableA")
   c = Extent("TableB")
   ON b.y = c.x ),
   d = Extent("TableC")
   ON a.b.y = d.z
)
```

Można to prawidłowo przetłumaczyć na:

```sql
SELECT *
FROM TableA as b
LEFT OUTER JOIN TableB as c ON b.y = c.x
INNER JOIN TableC as d ON b.y = d.z
```

Nielewe sprzężenia kręgosłupa nie mogą być jednak w łatwy sposób spłaszczone i nie należy próbować ich spłaszczać. Na przykład sprzężenia w następującym drzewie poleceń zapytania:

```csharp
InnerJoin(
   a = Extent("TableA")
   b = LeftOuterJoin(
   c = Extent("TableB")
   d = Extent("TableC")
   ON c.y = d.x),
   ON a.z = b.c.y
)
```

Zostałyby przetłumaczone na instrukcję SELECT języka SQL z podzapytaniem.

```sql
SELECT *
FROM TableA as a
INNER JOIN (SELECT *
   FROM TableB as c
   LEFT OUTER JOIN TableC as d
   ON c.y = d.x) as b
ON b.y = d.z
```

## <a name="input-alias-redirecting"></a>Przekierowanie wejściowej aliasu

Aby wyjaśnić przekierowanie aliasów wejściowych, należy rozważyć strukturę wyrażeń relacyjnych, takich jak DbFilterExpression, DbProjectExpression, obiekt DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupAggregate, DbApplyExpression i DbSkipExpression.

Każdy z tych typów ma jedną lub więcej właściwości wejściowych, które opisują kolekcję wejściową, a zmienna powiązania odpowiadająca każdemu danemu wejściu jest używana do reprezentowania każdego elementu danych wejściowych podczas przechodzenia do kolekcji. Zmienna Binding jest używana podczas odwoływania się do elementu wejściowego, na przykład we właściwości predykatu DbFilterExpression lub właściwości projekcji DbProjectExpression.

Podczas agregowania bardziej relacyjnych węzłów wyrażeń do pojedynczej instrukcji SELECT języka SQL i oceniania wyrażenia, które jest częścią wyrażenia relacyjnego (na przykład część właściwości projekcji DbProjectExpression), zmienna powiązania, której używa może nie jest taki sam jak alias danych wejściowych, ponieważ wiele powiązań wyrażeń może być przekierowanych do jednego zakresu.  Ten problem jest nazywany zmiana nazw aliasu.

Rozważmy pierwszy przykład w tym temacie. Jeśli wykonujesz translację algorytmie i przetłumaczmy projekcję a. x (DbPropertyExpression (a, x)), jest ona poprawna, aby przetłumaczyć ją na `a.x`, ponieważ jako "a" aliasuje dane wejściowe w celu dopasowania do zmiennej powiązania.  Jednak podczas agregowania węzłów do pojedynczej instrukcji SELECT języka SQL należy przetłumaczyć te same DbPropertyExpression na `b.x`, ponieważ dane wejściowe mają alias "b".

## <a name="join-alias-flattening"></a>Przyłączanie spłaszczania aliasów

W przeciwieństwie do dowolnego innego wyrażenia relacyjnego w drzewie poleceń wyjściowych, DbJoinExpression wyprowadza typ wyniku, który jest wiersz składający się z dwóch kolumn, z których każdy odpowiada jednemu z danych wejściowych. Gdy DbPropertyExpression jest zbudowany w celu uzyskania dostępu do właściwości skalarnej pochodzącej z sprzężenia, znajduje się na innej DbPropertyExpression.

Przykłady obejmują "a. b. y" w przykładach 2 i "b. c. y" w przykładzie 3. Jednak w odpowiednich instrukcjach SQL są one określane jako "b. y". Ta zmiana aliasu jest nazywana spłaszczaniem aliasu sprzężenia.

## <a name="column-name-and-extent-alias-renaming"></a>Zmiana nazwy kolumny i zakresu aliasu

Jeśli zapytanie SELECT SQL z funkcją Join musi zostać wykonane z projekcją, podczas wyliczania wszystkich uczestniczących kolumn w danych wejściowych może wystąpić kolizja nazw, ponieważ więcej niż jeden element wejściowy może mieć taką samą nazwę kolumny. Użyj innej nazwy dla kolumny, aby uniknąć kolizji.

Ponadto podczas spłaszczania sprzężeń, uczestniczące tabele (lub podzapytania) mogą spowodować konflikt aliasów, w przypadku których należy zmienić nazwy.

## <a name="avoid-select-"></a>Unikaj ZAZNACZania *

Nie należy używać `SELECT *` do wybierania z tabel podstawowych. Model magazynu w aplikacji Entity Framework może zawierać tylko podzestaw kolumn znajdujących się w tabeli bazy danych. W takim przypadku `SELECT *` może wygenerować niepoprawny wynik. Zamiast tego należy określić wszystkie kolumny uczestniczące przy użyciu nazw kolumn z typu wynik wyrażeń uczestniczących.

## <a name="reuse-of-expressions"></a>Ponowne użycie wyrażeń

Wyrażenia mogą być ponownie używane w drzewie poleceń zapytania przekazanym przez Entity Framework. Nie należy zakładać, że każde wyrażenie pojawia się tylko raz w drzewie poleceń zapytania.

## <a name="mapping-primitive-types"></a>Mapowanie typów pierwotnych

Podczas mapowania typów koncepcyjnych (EDM) na typy dostawców należy mapować do najszerszego typu (Int32), aby można było dopasować wszystkie możliwe wartości. Należy również unikać mapowania do typów, które nie mogą być używane dla wielu operacji, takich jak typy obiektów BLOB (na przykład `ntext` w SQL Server).

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu SQL](sql-generation.md)
