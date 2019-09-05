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
# <a name="how-to-execute-a-polymorphic-query"></a><span data-ttu-id="1bc50-102">Instrukcje: Wykonywanie zapytania polimorficznego</span><span class="sxs-lookup"><span data-stu-id="1bc50-102">How to: Execute a Polymorphic Query</span></span>

<span data-ttu-id="1bc50-103">W tym temacie pokazano, jak wykonać zapytanie [!INCLUDE[esql](../../../../../includes/esql-md.md)] polimorficzne przy użyciu operatora [OFTYPE](./language-reference/oftype-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="1bc50-103">This topic shows how to execute a polymorphic [!INCLUDE[esql](../../../../../includes/esql-md.md)] query using the [OFTYPE](./language-reference/oftype-entity-sql.md) operator.</span></span>

### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="1bc50-104">Aby uruchomić kod w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="1bc50-104">To run the code in this example</span></span>

1. <span data-ttu-id="1bc50-105">Dodaj [model szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) do projektu i skonfiguruj projekt tak, aby korzystał z Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="1bc50-105">Add the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="1bc50-106">Aby uzyskać więcej informacji, zobacz [jak: Użyj kreatora](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="1bc50-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

2. <span data-ttu-id="1bc50-107">Na stronie kodowej aplikacji Dodaj następujące `using` instrukcje (`Imports` w Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="1bc50-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. <span data-ttu-id="1bc50-108">Zmodyfikuj model koncepcyjny w taki sposób, aby miał dziedziczenie hierarchii tabeli, wykonując czynności opisane w [przewodniku: Dziedziczenie mapowania — tabela na hierarchię](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1bc50-108">Modify the conceptual model to have a table-per-hierarchy inheritance by following the steps in [Walkthrough: Mapping Inheritance - Table-per-Hierarchy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="1bc50-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="1bc50-109">Example</span></span>

<span data-ttu-id="1bc50-110">Poniższy przykład używa operatora OFTYPE do pobierania i wyświetlania kolekcji tylko `OnsiteCourses` z `Courses`kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1bc50-110">The following example uses an OFTYPE operator to get and display a collection of only `OnsiteCourses` from a collection of `Courses`.</span></span>

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a><span data-ttu-id="1bc50-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1bc50-111">See also</span></span>

- [<span data-ttu-id="1bc50-112">Dostawca EntityClient dla programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="1bc50-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="1bc50-113">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="1bc50-113">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
