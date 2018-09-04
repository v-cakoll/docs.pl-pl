---
title: 'Porady: wykonywanie zapytania Polimorficznego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: ae491d0eeda7f8703dca174bdf4c5c847f78e675
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519085"
---
# <a name="how-to-execute-a-polymorphic-query"></a>Porady: wykonywanie zapytania Polimorficznego
W tym temacie przedstawiono sposób wykonywania polimorficznych [!INCLUDE[esql](../../../../../includes/esql-md.md)] wykonywać zapytania za pomocą [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operatora.  
  
### <a name="to-run-the-code-in-this-example"></a>Aby uruchomić kod w tym przykładzie  
  
1.  Dodaj [modelu School](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) do projektu i skonfiguruj projekt, aby używać programu Entity Framework. Aby uzyskać więcej informacji, zobacz [porady: Użyj Kreator modelu Entity Data Model](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Na stronie kodowej dla aplikacji, Dodaj następujący kod `using` instrukcji (`Imports` w języku Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  Modyfikowanie modelu koncepcyjnego mieć dziedziczenia tabeli na hierrachy, wykonując kroki opisane w [wskazówki: mapowanie dziedziczenia — tabela wg hierarchii](https://msdn.microsoft.com/library/49b685cf-9db8-4d6d-b885-8837ed238f55).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto operatora OFTYPE, aby pobrać i wyświetlić kolekcję tylko `OnsiteCourses` z kolekcji `Courses`.  
  
 [!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
 [!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dostawca EntityClient dla programu Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
 [Jednostki języka SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
