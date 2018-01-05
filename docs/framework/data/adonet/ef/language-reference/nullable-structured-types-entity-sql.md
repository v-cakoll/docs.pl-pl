---
title: "Typy dopuszczające wartości zerowe strukturalne (jednostki SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3f294088e92951e964c3daa2a105b767bca1d288
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="deb50-102">Typy dopuszczające wartości zerowe strukturalne (jednostki SQL)</span><span class="sxs-lookup"><span data-stu-id="deb50-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="deb50-103">A `null` wystąpienia typu strukturalnego to wystąpienie nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="deb50-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="deb50-104">To różni się od istniejącego wystąpienia, w którym ma wszystkie właściwości `null` wartości.</span><span class="sxs-lookup"><span data-stu-id="deb50-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="deb50-105">W tym temacie opisano typy dopuszczające wartości zerowe strukturalnych, w tym typy, które dopuszczają wartości null i które kodu wzorce produktu `null` wystąpień strukturalnych typy dopuszczające wartości zerowe.</span><span class="sxs-lookup"><span data-stu-id="deb50-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="deb50-106">Typy strukturalne typy dopuszczające wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="deb50-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="deb50-107">Istnieją trzy rodzaje typy dopuszczające wartości zerowe struktury:</span><span class="sxs-lookup"><span data-stu-id="deb50-107">There are three kinds of nullable structure types:</span></span>  
  
-   <span data-ttu-id="deb50-108">Typy wierszy.</span><span class="sxs-lookup"><span data-stu-id="deb50-108">Row types.</span></span>  
  
-   <span data-ttu-id="deb50-109">Typy złożone.</span><span class="sxs-lookup"><span data-stu-id="deb50-109">Complex types.</span></span>  
  
-   <span data-ttu-id="deb50-110">Typy jednostek.</span><span class="sxs-lookup"><span data-stu-id="deb50-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="deb50-111">Wzorce kodu, które powodują powstanie Null wystąpień typów strukturalnych</span><span class="sxs-lookup"><span data-stu-id="deb50-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="deb50-112">Następujące scenariusze tworzenia `null` wystąpień:</span><span class="sxs-lookup"><span data-stu-id="deb50-112">The following scenarios produce `null` instances:</span></span>  
  
-   <span data-ttu-id="deb50-113">Kształtowania `null` jako typ strukturalny:</span><span class="sxs-lookup"><span data-stu-id="deb50-113">Shaping `null` as a structured type:</span></span>  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   <span data-ttu-id="deb50-114">Rzutowanie w górę do typem pochodnym typu podstawowego:</span><span class="sxs-lookup"><span data-stu-id="deb50-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   <span data-ttu-id="deb50-115">Sprzężenie zewnętrzne na fałszywego warunku:</span><span class="sxs-lookup"><span data-stu-id="deb50-115">Outer join on false condition:</span></span>  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="deb50-116">--lub</span><span class="sxs-lookup"><span data-stu-id="deb50-116">--or</span></span>  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="deb50-117">--lub</span><span class="sxs-lookup"><span data-stu-id="deb50-117">--or</span></span>  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   <span data-ttu-id="deb50-118">Dereferencji `null` odwołania:</span><span class="sxs-lookup"><span data-stu-id="deb50-118">Dereferencing a `null` reference:</span></span>  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   <span data-ttu-id="deb50-119">Uzyskiwanie ANYELEMENT z pustej kolekcji:</span><span class="sxs-lookup"><span data-stu-id="deb50-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   <span data-ttu-id="deb50-120">Sprawdzanie `null` wystąpień typów strukturalnych:</span><span class="sxs-lookup"><span data-stu-id="deb50-120">Checking for `null` instances of structured types:</span></span>  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="deb50-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="deb50-121">See Also</span></span>  
 [<span data-ttu-id="deb50-122">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="deb50-122">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
