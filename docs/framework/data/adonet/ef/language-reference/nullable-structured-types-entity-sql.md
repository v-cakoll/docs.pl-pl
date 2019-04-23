---
title: Typy strukturalne dopuszczające wartości zerowe (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 632b092e1d0d99a2a40cc3cd4b323e234de6232b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127858"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="07bdf-102">Typy strukturalne dopuszczające wartości zerowe (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="07bdf-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="07bdf-103">A `null` wystąpienia typu ze strukturą to wystąpienie, który nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="07bdf-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="07bdf-104">To różni się od istniejącego wystąpienia, w którym ma wszystkie właściwości `null` wartości.</span><span class="sxs-lookup"><span data-stu-id="07bdf-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="07bdf-105">W tym temacie opisano dopuszczający ze strukturą, w tym typy dopuszczają wartości null i wzorce, które kodu produktu `null` wystąpień typy strukturalne dopuszczające wartość null.</span><span class="sxs-lookup"><span data-stu-id="07bdf-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="07bdf-106">Rodzaje typy strukturalne dopuszczające wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="07bdf-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="07bdf-107">Istnieją trzy rodzaje typów nullable struktury:</span><span class="sxs-lookup"><span data-stu-id="07bdf-107">There are three kinds of nullable structure types:</span></span>  
  
-   <span data-ttu-id="07bdf-108">Typy wierszy.</span><span class="sxs-lookup"><span data-stu-id="07bdf-108">Row types.</span></span>  
  
-   <span data-ttu-id="07bdf-109">Typy złożone.</span><span class="sxs-lookup"><span data-stu-id="07bdf-109">Complex types.</span></span>  
  
-   <span data-ttu-id="07bdf-110">Typy jednostek.</span><span class="sxs-lookup"><span data-stu-id="07bdf-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="07bdf-111">Wzorce kodu, które tworzą Null wystąpień typów strukturalnych</span><span class="sxs-lookup"><span data-stu-id="07bdf-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="07bdf-112">Następujące scenariusze tworzenia `null` wystąpień:</span><span class="sxs-lookup"><span data-stu-id="07bdf-112">The following scenarios produce `null` instances:</span></span>  
  
-   <span data-ttu-id="07bdf-113">Kształtowanie `null` jako typ ze strukturą:</span><span class="sxs-lookup"><span data-stu-id="07bdf-113">Shaping `null` as a structured type:</span></span>  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   <span data-ttu-id="07bdf-114">Rzutowanie rozszerzające typu podstawowego na pochodny typ:</span><span class="sxs-lookup"><span data-stu-id="07bdf-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   <span data-ttu-id="07bdf-115">Sprzężenie zewnętrzne, pod warunkiem false:</span><span class="sxs-lookup"><span data-stu-id="07bdf-115">Outer join on false condition:</span></span>  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="07bdf-116">--or</span><span class="sxs-lookup"><span data-stu-id="07bdf-116">--or</span></span>  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="07bdf-117">--or</span><span class="sxs-lookup"><span data-stu-id="07bdf-117">--or</span></span>  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   <span data-ttu-id="07bdf-118">Wyłuskanie `null` odwołania:</span><span class="sxs-lookup"><span data-stu-id="07bdf-118">Dereferencing a `null` reference:</span></span>  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   <span data-ttu-id="07bdf-119">Uzyskiwanie ANYELEMENT z pustą kolekcję:</span><span class="sxs-lookup"><span data-stu-id="07bdf-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   <span data-ttu-id="07bdf-120">Sprawdzanie `null` wystąpień typów strukturalnych:</span><span class="sxs-lookup"><span data-stu-id="07bdf-120">Checking for `null` instances of structured types:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07bdf-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07bdf-121">See also</span></span>

- [<span data-ttu-id="07bdf-122">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="07bdf-122">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
