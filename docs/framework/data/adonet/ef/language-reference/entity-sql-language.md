---
title: Jednostki języka SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: f12a20f85a0449778614d3098f69d3da90902c95
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50048446"
---
# <a name="entity-sql-language"></a>Jednostki języka SQL
Jednostka SQL jest język zapytania niezależnie od magazynu, który jest podobny do bazy danych SQL. Jednostka SQL pozwala przesyłać zapytania dotyczące danych jednostki, jako obiekty lub w formie tabelarycznej. Należy rozważyć użycie jednostki SQL w następujących przypadkach:  
  
-   Gdy zapytania muszą być dynamicznie skonstruowane w czasie wykonywania. W takim przypadku warto także za pomocą metody konstruktora zapytań z <xref:System.Data.Objects.ObjectQuery%601> zamiast tworzenia SQL jednostki ciągu w czasie wykonywania zapytania.  
  
-   Jeśli chcesz zdefiniować zapytanie jako część definicji modelu. Tylko jednostki SQL jest obsługiwana w modelu danych. Aby uzyskać więcej informacji, zobacz [QueryView — Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)  
  
-   W przypadku używania EntityClient do zwracania danych tylko do odczytu jednostki jako za pomocą zestawów wierszy <xref:System.Data.EntityClient.EntityDataReader>. Aby uzyskać więcej informacji, zobacz [dostawca EntityClient dla programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
-   Jeśli jesteś już ekspertem w językach zapytań SQL, SQL jednostki może wydawać się najbardziej fizycznych dla Ciebie.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Z dostawcą EntityClient przy użyciu jednostki SQL  
 Jeśli chcesz użyć jednostki SQL z dostawcą EntityClient, zobacz następujące tematy, aby uzyskać więcej informacji:  
  
 [Dostawca EntityClient dla programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [Instrukcje: Tworzenie ciągu połączenia EntityConnection](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Instrukcje: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Instrukcje: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Instrukcje: Wykonywanie zapytania, które zwraca wyniki RefType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Instrukcje: Wykonywanie zapytania, które zwraca typy złożone](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Instrukcje: Wykonywanie zapytania, które zwraca kolekcje zagnieżdżone](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Instrukcje: Wykonywanie zapytania SQL do sparametryzowanej jednostki przy użyciu EntityCommand](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Instrukcje: Wykonywanie zapytania SQL do sparametryzowanej procedury składowanej przy użyciu EntityCommand](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Instrukcje: Wykonywanie zapytania polimorficznego](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Instrukcje: Nawigowanie po relacjach za pomocą operatora nawigowania](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Za pomocą obiektu zapytań przy użyciu jednostki SQL  
 Jeśli chcesz jednostki SQL za pomocą zapytań dotyczących obiektów, zobacz następujące tematy, aby uzyskać więcej informacji:  
  
 [Porady: wykonywanie zapytania, które zwraca obiekty typu jednostki](https://msdn.microsoft.com/library/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [Porady: wykonywanie zapytania parametrycznego](https://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [Porady: nawigowanie po relacjach za pomocą właściwości nawigacji](https://msdn.microsoft.com/library/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [Porady: wywoływanie funkcji zdefiniowanej przez użytkownika](https://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [Porady: filtrowanie danych](https://msdn.microsoft.com/library/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [Porady: sortowanie danych](https://msdn.microsoft.com/library/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [Porady: grupowanie danych](https://msdn.microsoft.com/library/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [Porady: agregować dane](https://msdn.microsoft.com/library/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [Porady: wykonywanie zapytania, które zwraca obiekty typu anonimowego](https://msdn.microsoft.com/library/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [Porady: wykonywanie zapytania, które zwraca kolekcję typów pierwotnych](https://msdn.microsoft.com/library/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [Porady: zapytanie powiązane obiekty w obiekt EntityCollection](https://msdn.microsoft.com/library/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [Porady: kolejność sumę dwóch zapytań](https://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313)  
  
 [Porady: wyniki strony za pomocą kwerendy](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Program Entity Framework na platformie ADO.NET](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [Dokumentacja języka](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
