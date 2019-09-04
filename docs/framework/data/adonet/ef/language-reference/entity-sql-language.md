---
title: Język Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: a2e4b7245dbfccf7864481b52a0e868a85efbca6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251019"
---
# <a name="entity-sql-language"></a>Język Entity SQL
Entity SQL to język zapytań niezależnych od magazynu, podobny do SQL. Entity SQL umożliwia wykonywanie zapytań dotyczących danych jednostki jako obiektów lub w formie tabelarycznej. Należy rozważyć użycie Entity SQL w następujących przypadkach:  
  
- Gdy zapytanie musi być skonstruowane dynamicznie w czasie wykonywania. W takim przypadku należy również rozważyć użycie metod <xref:System.Data.Objects.ObjectQuery%601> konstruktora zapytań zamiast konstruowania Entity SQL ciągu zapytania w czasie wykonywania.  
  
- Jeśli chcesz zdefiniować zapytanie jako część definicji modelu. Tylko Entity SQL jest obsługiwane w modelu danych. Aby uzyskać więcej informacji, zobacz [QueryView element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)  
  
- W przypadku używania EntityClient do zwracania danych jednostki tylko do odczytu jako zestawów wierszy przy <xref:System.Data.EntityClient.EntityDataReader>użyciu. Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](../entityclient-provider-for-the-entity-framework.md).  
  
- Jeśli już jesteś ekspertem w językach zapytań opartych na języku SQL, Entity SQL mogą być najbardziej naturalne.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Używanie Entity SQL z dostawcą EntityClient  
 Jeśli chcesz użyć Entity SQL z dostawcą EntityClient, zobacz następujące tematy, aby uzyskać więcej informacji:  
  
 [Dostawca EntityClient dla programu Entity Framework](../entityclient-provider-for-the-entity-framework.md)  
  
 [Instrukcje: Tworzenie parametrów połączenia usługi EntityConnection](../how-to-build-an-entityconnection-connection-string.md)  
  
 [Instrukcje: Wykonywanie zapytania, które zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Instrukcje: Wykonaj zapytanie zwracające wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Instrukcje: Wykonaj zapytanie zwracające wyniki RefType](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Instrukcje: Wykonaj zapytanie zwracające typy złożone](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Instrukcje: Wykonaj zapytanie zwracające kolekcje zagnieżdżone](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Instrukcje: Wykonywanie zapytania Entity SQL sparametryzowanego przy użyciu EntityCommand](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Instrukcje: Wykonaj sparametryzowane procedury składowane za pomocą EntityCommand](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Instrukcje: Wykonywanie zapytania polimorficznego](../how-to-execute-a-polymorphic-query.md)  
  
 [Instrukcje: Nawigowanie po relacjach za pomocą operatora nawigacji](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Używanie Entity SQL z kwerendami obiektów  
 Jeśli chcesz użyć Entity SQL z kwerendami obiektów, zobacz następujące tematy, aby uzyskać więcej informacji:  
  
 [Instrukcje: Wykonywanie zapytania, które zwraca obiekty typu Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))  
  
 [Instrukcje: Wykonaj zapytanie parametryczne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))  
  
 [Instrukcje: Nawigowanie po relacjach przy użyciu właściwości nawigacji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))  
  
 [Instrukcje: Wywoływanie funkcji zdefiniowanej przez użytkownika](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 [Instrukcje: Filtrowanie danych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))  
  
 [Instrukcje: Sortuj dane](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))  
  
 [Instrukcje: Grupuj dane](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))  
  
 [Instrukcje: Agregowanie danych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))  
  
 [Instrukcje: Wykonaj zapytanie zwracające obiekty typu anonimowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))  
  
 [Instrukcje: Wykonaj zapytanie, które zwraca kolekcję typów pierwotnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))  
  
 [Instrukcje: Zapytanie dotyczące obiektów pokrewnych w obiekcie EntityCollection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))  
  
 [Instrukcje: Zamów Unię dwóch zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
 [Instrukcje: Strona za poorednictwem wyników zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie jednostki SQL](entity-sql-overview.md)  
  
 [Odwołanie do jednostki SQL](entity-sql-reference.md)  
  
## <a name="see-also"></a>Zobacz także

- [Program Entity Framework na platformie ADO.NET](../index.md)
- [Dokumentacja języka](index.md)
