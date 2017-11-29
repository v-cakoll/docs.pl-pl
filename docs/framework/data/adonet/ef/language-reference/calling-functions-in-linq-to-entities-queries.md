---
title: "Wywoływanie funkcji w składniku LINQ to Entities zapytań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6e50147d356ad9e389a87868205bb9b8b6b3e7b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>Wywoływanie funkcji w składniku LINQ to Entities zapytań
Tematy w tej sekcji opisano sposób wywołania funkcji w składniku LINQ do jednostek zapytań.  
  
 <xref:System.Data.Objects.EntityFunctions> i <xref:System.Data.Objects.SqlClient.SqlFunctions> klasy zapewniają dostęp do kanonicznej i funkcje bazy danych jako część programu Entity Framework. Aby uzyskać więcej informacji, zobacz [jak: wywołanie funkcji kanonicznej](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) i [jak: Wywołaj funkcje bazy danych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).  
  
 Proces wywoływania funkcji niestandardowej wymaga trzy podstawowe czynności:  
  
1.  Zdefiniuj funkcję w modelu koncepcyjnym lub zadeklarowania funkcji w modelu magazynu.  
  
2.  Dodawanie metody do aplikacji i mapowanie go do funkcji w modelu o <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3.  Wywołanie funkcji w zapytaniu składnika LINQ to Entities.  
  
 Aby uzyskać więcej informacji zobacz Tematy w tej sekcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: wywoływać funkcje kanoniczny](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [Porady: Wywołaj funkcje bazy danych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [Porady: wywoływać funkcje w niestandardowej bazie danych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [Porady: Wywołaj funkcje zdefiniowane przez Model w zapytaniach](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [Porady: Wywołaj funkcje zdefiniowane przez Model, jako metody obiektów](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Canonical funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [Omówienie plików edmx](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Porady: Definiowanie funkcji niestandardowych w modelu koncepcyjnym](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)
