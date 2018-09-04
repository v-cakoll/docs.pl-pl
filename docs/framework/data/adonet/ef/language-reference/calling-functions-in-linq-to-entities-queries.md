---
title: Wywoływanie funkcji w składniku LINQ do zapytań jednostki
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 4aed9fd59cceb72baac9dc12a85c52787c4b3866
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506947"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>Wywoływanie funkcji w składniku LINQ do zapytań jednostki
Tematy w tej sekcji opisano sposób wywołania funkcji w składniku LINQ do zapytań jednostki.  
  
 <xref:System.Data.Objects.EntityFunctions> i <xref:System.Data.Objects.SqlClient.SqlFunctions> klasy zapewniają dostęp do canonical i funkcje bazy danych jako część programu Entity Framework. Aby uzyskać więcej informacji, zobacz [jak: wywoływać funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) i [porady: wywoływanie funkcji bazy danych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).  
  
 Proces wywoływania funkcji niestandardowej wymaga trzy podstawowe kroki:  
  
1.  Zdefiniuj funkcję w model koncepcyjny lub deklarowania funkcji w modelu magazynu.  
  
2.  Dodaj metodę do swojej aplikacji i Mapuj na funkcję w modelu z <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3.  Wywołanie funkcji w zapytaniu składnika LINQ to Entities.  
  
 Aby uzyskać więcej informacji zobacz Tematy w tej sekcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Wywoływanie funkcji kanonicznych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [Instrukcje: Wywoływanie funkcji bazy danych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [Instrukcje: Wywoływanie niestandardowych funkcji bazy danych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [Instrukcje: Wywoływanie funkcji definiowanych przez model w zapytaniach](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [Instrukcje: Wywoływanie funkcji definiowanych przez model jako metod obiektu](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [Omówienie pliku edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Porady: Definiowanie funkcji niestandardowych w modelu koncepcyjnym](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)
