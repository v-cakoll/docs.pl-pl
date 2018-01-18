---
title: "Jednostki języka SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1618ff37ffd2b25140196a42d49d5a01f7e9da90
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="entity-sql-language"></a>Jednostki języka SQL
Jednostka SQL jest język kwerendy niezależne od magazynu, która jest podobna do bazy danych SQL. Jednostki SQL umożliwia zapytania danych jednostki, jako obiekty lub w formie tabelarycznej. Należy rozważyć użycie SQL jednostki w następujących przypadkach:  
  
-   Jeśli zapytanie musi być dynamicznie skonstruowany w czasie wykonywania. W takim przypadku należy również rozważyć za pomocą metody konstruktora zapytań <xref:System.Data.Objects.ObjectQuery%601> zamiast tworzenia SQL jednostki ciągu w czasie wykonywania zapytania.  
  
-   Jeśli chcesz zdefiniować zapytania jako część definicji modelu. Tylko jednostki SQL jest obsługiwana w modelu danych. Aby uzyskać więcej informacji, zobacz [Element QueryView (MSL)](http://msdn.microsoft.com/en-us/f0426b34-45cb-4fd7-9777-e0570c5e0e80)  
  
-   W przypadku używania EntityClient do zwracanych danych tylko do odczytu jednostki jako za pomocą zestawów wierszy <xref:System.Data.EntityClient.EntityDataReader>. Aby uzyskać więcej informacji, zobacz [dostawcy EntityClient Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
-   Jeśli masz już eksperta w językach SQL na podstawie kwerendy, jednostki SQL może wydawać się najbardziej fizyczne do Ciebie.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Przy użyciu programu SQL jednostki z dostawcą EntityClient  
 Jeśli chcesz korzystać z SQL jednostki z dostawcą EntityClient, zobacz następujące tematy, aby uzyskać więcej informacji:  
  
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
  
## <a name="using-entity-sql-with-object-queries"></a>Przy użyciu programu SQL jednostka z obiektu zapytań  
 Jeśli chcesz użyć SQL jednostek z obiektu zapytań, zobacz następujące tematy, aby uzyskać więcej informacji:  
  
 [Porady: kwerenda zwraca obiekty typu jednostki](http://msdn.microsoft.com/en-us/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [Porady: wykonanie zapytania parametrycznego](http://msdn.microsoft.com/en-us/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [Porady: nawigowanie po relacjach za pomocą właściwości nawigacji](http://msdn.microsoft.com/en-us/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [Porady: wywoływanie funkcji zdefiniowanej przez użytkownika](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [Porady: filtrowanie danych](http://msdn.microsoft.com/en-us/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [Porady: sortowanie danych](http://msdn.microsoft.com/en-us/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [Porady: grupowanie danych](http://msdn.microsoft.com/en-us/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [Porady: agregowanie danych](http://msdn.microsoft.com/en-us/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [Porady: kwerenda zwraca obiekty typu anonimowego](http://msdn.microsoft.com/en-us/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [Porady: kwerenda zwraca kolekcję typów pierwotnych](http://msdn.microsoft.com/en-us/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [Porady: zapytanie powiązane obiekty w obiekcie EntityCollection](http://msdn.microsoft.com/en-us/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [Porady: kolejność złożenie dwóch zapytań](http://msdn.microsoft.com/en-us/853c583a-eaba-4400-830d-be974e735313)  
  
 [Porady: powoduje strony za pomocą kwerendy](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Program Entity Framework na platformie ADO.NET](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [Dokumentacja języka](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
