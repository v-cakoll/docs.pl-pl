---
title: "Generowanie SQL na podstawie drzew poleceń — najlepsze praktyki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d68194ab83a6606337a33668470411ed8b1c6957
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="generating-sql-from-command-trees---best-practices"></a>Generowanie SQL na podstawie drzew poleceń — najlepsze praktyki
Drzew poleceń w danych wyjściowych zapytania modelu ściśle zapytania można wyrazić w języku SQL. Istnieją pewne wyzwania autorzy dostawcy podczas generowania SQL z poziomu drzewa poleceń danych wyjściowych. W tym temacie omówiono te problemy. W następnym temacie dostawcy przykładowych pokazano, jak rozwiązać te problemy.  
  
## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a>Węzły DbExpression grup w instrukcji SQL SELECT  
 Typowy instrukcja SQL zawiera zagnieżdżone struktury następujących kształt:  
  
```  
SELECT …  
FROM …  
WHERE …  
GROUP BY …  
ORDER BY …  
```  
  
 Co najmniej jedną klauzulę może być pusta.  Zagnieżdżona instrukcja SELECT może wystąpić w każdym wierszy.  
  
 Tłumaczenie możliwe z poziomu drzewa poleceń zapytania na instrukcję SQL SELECT dałby w efekcie podzapytania jednej dla każdego operator relacyjny. Jednak, która może spowodować niepotrzebne zagnieżdżonych podzapytań, które mogą być trudny do odczytania.  Na niektóre sklepy danych zapytania mogą działać nieprawidłowo.  
  
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
  
```  
SELECT a.x  
FROM (   SELECT *  
         FROM TableA as b  
         WHERE b.y = 5) as a  
```  
  
 Należy pamiętać, że każdy węzeł wyrażenie relacyjne staje się nowych instrukcję SQL SELECT.  
  
 W związku z tym należy do agregacji tyle węzły wyrażenia jak to możliwe w jednej instrukcji SQL SELECT przy zachowaniu poprawności.  
  
 Wynikiem tych agregacji, na przykład przedstawionych powyżej byłby:  
  
```  
SELECT b.x   
FROM TableA as b  
WHERE b.y = 5  
```  
  
## <a name="flatten-joins-in-a-sql-select-statement"></a>Spłaszczanie sprzężenia w instrukcji SQL SELECT  
 Jeden przypadek sumowania wiele węzłów w jednej instrukcji SQL SELECT jest agregowanie wiele wyrażeń sprzężenia w jednej instrukcji SQL SELECT. DbJoinExpression reprezentuje pojedynczy sprzężenie dwóch parametrów wejściowych. Jednak w ramach jednej instrukcji SQL SELECT, można określić więcej niż jedno połączenie. W takim przypadku sprzężeń są wykonywane w określonej kolejności.  
  
 Pozostanie kręgosłupa sprzężenia, (sprzężenia, które są wyświetlane jako element podrzędny lewego sprzężenia innego) może być łatwiej jako spłaszczone do jednej instrukcji SQL SELECT. Rozważmy na przykład drzewo poleceń następujące zapytania:  
  
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
  
```  
SELECT *  
FROM TableA as b  
LEFT OUTER JOIN TableB as c ON b.y = c.x  
INNER JOIN TableC as d ON b.y = d.z  
```  
  
 Nie można łatwo spłaszczenia sprzężenia kręgosłupa lewego górnego i nie należy próbować spłaszczanie je. Na przykład sprzężenia w następującym zapytaniu polecenie drzewa:  
  
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
  
 Może być przekonwertowana na instrukcję SQL SELECT z podzapytania.  
  
```  
SELECT *  
FROM TableA as a  
INNER JOIN (SELECT *   
   FROM TableB as c   
   LEFT OUTER JOIN TableC as d  
   ON c.y = d.x) as b  
ON b.y = d.z  
```  
  
## <a name="input-alias-redirecting"></a>Wprowadź Alias przekierowania folderu  
 Wyjaśnienie, przekierowywanie alias wejściowy, należy wziąć pod uwagę struktury relacyjne wyrażeń, takie jak DbFilterExpression DbProjectExpression, obiekt DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, metody DbApplyExpression, i DbSkipExpression.  
  
 Każdego z tych typów ma co najmniej jednej właściwości danych wejściowych, opisujących kolekcja wejściowa i zmiennej powiązanie odpowiadający każdej danych wejściowych jest używana do reprezentowania każdy element dane wejściowe podczas przechodzenia kolekcji. Zmienna powiązania jest używany podczas odwoływania się do elementu wejściowego, na przykład w przypadku właściwości predykatu DbFilterExpression lub właściwości projekcji DbProjectExpression.  
  
 Gdy może agregowanie wyrażenie relacyjne większą liczbę węzłów w jednej instrukcji SQL SELECT, a obliczenia wyrażenia będącej częścią wyrażenie relacyjne (na przykład część właściwości projekcji DbProjectExpression) używa zmiennej powiązania nie być taka sama jak alias danych wejściowych, wiele powiązań wyrażenie musi być przekierowywane na jednym zakresie.  Ten problem jest nazywany, zmiana nazwy aliasu.  
  
 Rozważmy przykład pierwszy w tym temacie. Jeśli podczas tłumaczenia prosty i tłumaczenia projekcji "a.x" (DbPropertyExpression (, x)), są prawidłowe do tłumaczenia go do `a.x` ponieważ mamy alias wejściowy jako "a" na zgodne powiązanie zmiennej.  Jednak podczas agregowania obu węzłów w jednej instrukcji SQL SELECT, potrzebne jest tłumaczenie tego samego DbPropertyExpression do `b.x`, jak dane wejściowe były używane z aliasem na "b".  
  
## <a name="join-alias-flattening"></a>Dołącz spłaszczanie aliasu  
 W odróżnieniu od żadnych innych wyrażenie relacyjne w danych wyjściowych polecenia drzewa DbJoinExpression generuje typ wyniku, który wiersz składający się z dwóch kolumn, z których każdy odpowiada jednej z jej danych wejściowych. DbPropertyExpresssion korzysta z wbudowanej dostępu do właściwości skalarnej pochodzące z sprzężenia, jest za pośrednictwem innego DbPropertyExpresssion.  
  
 Przykładami "a.b.y" w przykładzie 2 i "b.c.y" w przykładzie 3. Jednak w odpowiedniej instrukcji SQL te są określane jako "b.y". Aliasów ponowna nosi nazwę spłaszczanie alias sprzężenia.  
  
## <a name="column-name-and-extent-alias-renaming"></a>Nazwa kolumny i zakres Alias zmiana nazwy  
 Jeśli kwerendę SQL SELECT z sprzężenia ma zostać wykonane z projekcji, podczas wyliczania wszystkich uczestniczących kolumn danych wejściowych, kolizję nazw mogą wystąpić, jako więcej niż jedno wejście mogą mieć takiej samej nazwie kolumny. Użyj innej nazwy dla kolumny, która umożliwi uniknięcie kolizji.  
  
 Ponadto podczas spłaszczania sprzężenia, tabele (ani podzapytań) może być kolizji aliasy, w którym przypadek te muszą zostać zmienione.  
  
## <a name="avoid-select-"></a>Unikaj SELECT *  
 Nie używaj `SELECT *` można wybierać z tabel podstawowych. W modelu magazynu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji może zawierać tylko podzestaw kolumn, które znajdują się w tabeli bazy danych. W takim przypadku `SELECT *` może powodować niepoprawne wyniki. Zamiast tego należy określić wszystkich uczestniczących kolumn za pomocą nazwy kolumn typu wyniku uczestniczących wyrażeń.  
  
## <a name="reuse-of-expressions"></a>Ponowne użycie wyrażenia  
 Wyrażenia może nastąpić w drzewie poleceń zapytania przekazany przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Nie należy zakładać, każde wyrażenie jest wyświetlany w drzewie poleceń zapytania tylko raz.  
  
## <a name="mapping-primitive-types"></a>Typy pierwotne mapowania  
 Podczas mapowania koncepcyjnej typów (EDM) do dostawcy typów tak, aby dopasować wszystkich możliwych wartości powinny mapy typowi najszerszych (Int32). Ponadto uniknąć mapowania typów, których nie można używać w wielu operacjach, takich jak typy obiektów BLOB (na przykład `ntext` w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]).  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie kodu SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
