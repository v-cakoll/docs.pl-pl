---
title: Wywoływanie funkcji w składniku LINQ do zapytań jednostki
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 8cb861c72f33a7dff3d6bef94719ae590a13706d
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828153"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>Wywoływanie funkcji w składniku LINQ do zapytań jednostki
Tematy w tej sekcji opisano sposób wywołania funkcji w składniku LINQ do zapytań jednostki.  
  
 <xref:System.Data.Objects.EntityFunctions> i <xref:System.Data.Objects.SqlClient.SqlFunctions> klasy zapewniają dostęp do canonical i funkcje bazy danych jako część programu Entity Framework. Aby uzyskać więcej informacji, zobacz [jak: Wywoływanie funkcji kanonicznych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) i [jak: Wywoływanie funkcji bazy danych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).  
  
 Proces wywoływania funkcji niestandardowej wymaga trzy podstawowe kroki:  
  
1.  Zdefiniuj funkcję w model koncepcyjny lub deklarowania funkcji w modelu magazynu.  
  
2.  Dodaj metodę do swojej aplikacji i Mapuj na funkcję w modelu z <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3.  Wywołanie funkcji w zapytaniu składnika LINQ to Entities.  
  
 Aby uzyskać więcej informacji zobacz Tematy w tej sekcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Wywoływanie funkcji kanonicznych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [Instrukcje: Wywoływanie funkcji bazy danych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [Instrukcje: Wywoływanie niestandardowych funkcji bazy danych](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [Instrukcje: Wywoływanie funkcji definiowanych przez Model w zapytaniach](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [Instrukcje: Wywoływanie funkcji definiowanych przez Model jako metod obiektu](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Zobacz także
- [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [Funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
- [Omówienie pliku edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Instrukcje: Definiowanie funkcji niestandardowych w modelu koncepcyjnym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
