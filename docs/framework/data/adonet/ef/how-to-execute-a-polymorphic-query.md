---
title: 'Instrukcje: Wykonywanie zapytania polimorficznego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 49e0a6b44af0729959fabf6278cc6d8ecf37a16b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251510"
---
# <a name="how-to-execute-a-polymorphic-query"></a>Instrukcje: Wykonywanie zapytania polimorficznego

W tym temacie pokazano, jak wykonać zapytanie [!INCLUDE[esql](../../../../../includes/esql-md.md)] polimorficzne przy użyciu operatora [OFTYPE](./language-reference/oftype-entity-sql.md) .

### <a name="to-run-the-code-in-this-example"></a>Aby uruchomić kod w tym przykładzie

1. Dodaj [model szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) do projektu i skonfiguruj projekt tak, aby korzystał z Entity Framework. Aby uzyskać więcej informacji, zobacz [jak: Użyj kreatora](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.

2. Na stronie kodowej aplikacji Dodaj następujące `using` instrukcje (`Imports` w Visual Basic):

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. Zmodyfikuj model koncepcyjny w taki sposób, aby miał dziedziczenie hierarchii tabeli, wykonując czynności opisane w [przewodniku: Dziedziczenie mapowania — tabela na hierarchię](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).

## <a name="example"></a>Przykład

Poniższy przykład używa operatora OFTYPE do pobierania i wyświetlania kolekcji tylko `OnsiteCourses` z `Courses`kolekcji.

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a>Zobacz także

- [Dostawca EntityClient dla programu Entity Framework](entityclient-provider-for-the-entity-framework.md)
- [Jednostki języka SQL](./language-reference/entity-sql-language.md)
