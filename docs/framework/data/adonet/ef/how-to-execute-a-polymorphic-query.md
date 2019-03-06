---
title: 'Instrukcje: Wykonywanie zapytania Polimorficznego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 08ae5722267ef781ed6bee59c7895269f63a75e5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355554"
---
# <a name="how-to-execute-a-polymorphic-query"></a><span data-ttu-id="ab650-102">Instrukcje: Wykonywanie zapytania Polimorficznego</span><span class="sxs-lookup"><span data-stu-id="ab650-102">How to: Execute a Polymorphic Query</span></span>

<span data-ttu-id="ab650-103">W tym temacie przedstawiono sposób wykonywania polimorficznych [!INCLUDE[esql](../../../../../includes/esql-md.md)] wykonywać zapytania za pomocą [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="ab650-103">This topic shows how to execute a polymorphic [!INCLUDE[esql](../../../../../includes/esql-md.md)] query using the [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator.</span></span>

### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="ab650-104">Aby uruchomić kod w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="ab650-104">To run the code in this example</span></span>

1. <span data-ttu-id="ab650-105">Dodaj [modelu School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) do projektu i skonfiguruj projekt, aby używać programu Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ab650-105">Add the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="ab650-106">Aby uzyskać więcej informacji, zobacz [jak: Użyj Kreatora modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ab650-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

2. <span data-ttu-id="ab650-107">Na stronie kodowej dla aplikacji, Dodaj następujący kod `using` instrukcji (`Imports` w języku Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="ab650-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. <span data-ttu-id="ab650-108">Modyfikowanie modelu koncepcyjnego mieć dziedziczenia tabela wg hierarchii, wykonując kroki opisane w [instruktażu: Mapowanie dziedziczenia — tabela wg hierarchii](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ab650-108">Modify the conceptual model to have a table-per-hierarchy inheritance by following the steps in [Walkthrough: Mapping Inheritance - Table-per-Hierarchy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="ab650-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab650-109">Example</span></span>

<span data-ttu-id="ab650-110">W poniższym przykładzie użyto operatora OFTYPE, aby pobrać i wyświetlić kolekcję tylko `OnsiteCourses` z kolekcji `Courses`.</span><span class="sxs-lookup"><span data-stu-id="ab650-110">The following example uses an OFTYPE operator to get and display a collection of only `OnsiteCourses` from a collection of `Courses`.</span></span>

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a><span data-ttu-id="ab650-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab650-111">See also</span></span>

- [<span data-ttu-id="ab650-112">Dostawca EntityClient dla programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ab650-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="ab650-113">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="ab650-113">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
