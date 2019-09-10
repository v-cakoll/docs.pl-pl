---
title: Znane problemy klienta SQL dla programu Entity Framework
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: 18e3ad59af4014086bd475815011b6008bcb5052
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854552"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>Znane problemy klienta SQL dla programu Entity Framework
W tej sekcji opisano znane problemy związane z .NET Framework Dostawca danych dla SQL Server (SqlClient).  
  
## <a name="trailing-spaces-in-string-functions"></a>Spacje końcowe w funkcjach ciągów  
 SQL Server ignoruje końcowe spacje w wartościach ciągu. W związku z tym, przekazanie końcowych spacji w ciągu może prowadzić do nieprzewidzianych wyników, nawet niepowodzeń.  
  
 Jeśli musisz mieć spacje końcowe w ciągu, rozważ dołączenie znaku odstępu na końcu, tak aby SQL Server nie przycinał ciągu. Jeśli spacje końcowe nie są wymagane, powinny być obcinane przed przekazaniem potoku zapytania.  
  
## <a name="right-function"></a>RIGHT — funkcja  
 Jeśli wartość nie`null` jest przekazana jako pierwszy argument, a wartość 0 jest przekazana jako drugi argument do `RIGHT(nvarchar(max)`, 0`)` lub `RIGHT(varchar(max)` `empty` , 0`)`, `NULL` zostanie zwrócona wartość zamiast ciągu.  
  
## <a name="cross-and-outer-apply-operators"></a>Operatory zastosowania krzyżowe i zewnętrzne  
 Operatory zastosowania krzyżowe i zewnętrzne zostały wprowadzone w SQL Server 2005. W niektórych przypadkach potok zapytania może utworzyć instrukcję języka Transact-SQL, która zawiera operator Apply i/lub OUTER APPLY. Ponieważ niektórzy dostawcy zaplecza, w tym wersje SQL Server wcześniejsze niż SQL Server 2005, nie obsługują tych operatorów, takie zapytania nie mogą być wykonywane w tych dostawcach zaplecza.  
  
 Poniżej przedstawiono niektóre typowe scenariusze, które mogą prowadzić do obecności operatora KRZYŻowego zastosowania i/lub zewnętrznego zastosowania operatorów w kwerendzie wyjściowej:  
  
- Skorelowane podzapytanie ze stronicowaniem.  
  
- `AnyElement` Za pośrednictwem skorelowanego podzapytania lub kolekcji utworzonej przez nawigację.  
  
- Zapytania LINQ używające metod grupowania, które akceptują selektor elementu.  
  
- Zapytanie, w którym jest jawnie określone zastosowanie krzyżowe lub zewnętrzne  
  
- Zapytanie, które ma konstrukcję DEREF dla konstrukcji REF.  
  
## <a name="skip-operator"></a>Operator SKIP  
 W przypadku korzystania z SQL Server 2000 przy użyciu polecenia Pomiń z KOLEJNOŚCIą według w przypadku kolumn niebędących kolumnami klucza mogą zostać zwrócone nieprawidłowe wyniki. Jeśli kolumna niebędąca kluczem zawiera zduplikowane dane, może zostać pominięta więcej niż określona liczba wierszy. Wynika to z tego, jak POMIJAnie jest tłumaczone dla SQL Server 2000. Na przykład w poniższym zapytaniu można pominąć więcej niż pięć wierszy, jeśli `E.NonKeyColumn` mają zduplikowane wartości:  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>Kierowanie do poprawnej wersji SQL Server  
 Entity Framework jest celem zapytania Transact-SQL na podstawie wersji SQL Server określonej w `ProviderManifestToken` atrybucie elementu schematu w pliku modelu magazynu (. ssdl). Ta wersja może różnić się od wersji rzeczywistego SQL Server, z którą nawiązano połączenie. Na przykład jeśli używasz SQL Server 2005, ale `ProviderManifestToken` atrybut jest ustawiony na 2008, wygenerowane zapytanie Transact-SQL może nie zostać wykonane na serwerze. Na przykład zapytanie korzystające z nowych typów dat, które zostały wprowadzone w SQL Server 2008, nie będzie wykonywane we wcześniejszych wersjach SQL Server. Jeśli używasz SQL Server 2005, ale `ProviderManifestToken` atrybut ma ustawioną wartość 2000, wygenerowane zapytanie Transact-SQL może być mniej zoptymalizowane lub można napotkać wyjątek informujący, że zapytanie nie jest obsługiwane. Aby uzyskać więcej informacji, zobacz sekcję operatory zastosowania krzyżowe i zewnętrzne we wcześniejszej części tego tematu.  
  
 Niektóre zachowania bazy danych zależą od poziomu zgodności ustawionego na bazę danych. `ProviderManifestToken` Jeśli atrybut jest ustawiony na 2005, a wersja SQL Server to 2005, ale poziom zgodności bazy danych jest ustawiony na "80" (SQL Server 2000), wygenerowany język Transact-SQL będzie ukierunkowany na SQL Server 2005, ale może nie działać zgodnie z oczekiwaniami z powodu ustawienie poziomu zgodności. Na przykład można utracić informacje o uporządkowaniu, jeśli nazwa kolumny na liście ORDER BY jest zgodna z nazwą kolumny w selektorze.  
  
## <a name="nested-queries-in-projection"></a>Zagnieżdżone zapytania w projekcji  
 Zagnieżdżone zapytania w klauzuli projekcji mogą zostać przetłumaczone na zapytania o produkty kartezjańskiego na serwerze. Na niektórych serwerach zaplecza, w tym serwera magazynem, może to spowodować, że tabela TempDB będzie dość duża. Może to zmniejszyć wydajność serwera.  
  
 Poniżej znajduje się przykład zagnieżdżonego zapytania w klauzuli projekcji:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>Wartości tożsamości identyfikatorów GUID generowanych przez serwer  
 Entity Framework obsługuje wartości tożsamości typu GUID generowany przez serwer, ale dostawca musi obsługiwać zwracanie wartości tożsamości generowanej przez serwer po wstawieniu wiersza. Począwszy od SQL Server 2005, można zwrócić typ GUID wygenerowany przez serwer w bazie danych SQL Server za pomocą [klauzuli OUTPUT](https://go.microsoft.com/fwlink/?LinkId=169400) .  
  
## <a name="see-also"></a>Zobacz także

- [Element SqlClient programu Entity Framework](sqlclient-for-the-entity-framework.md)
- [Znane problemy i zagadnienia dotyczące w składniku LINQ to Entities](./language-reference/known-issues-and-considerations-in-linq-to-entities.md)
