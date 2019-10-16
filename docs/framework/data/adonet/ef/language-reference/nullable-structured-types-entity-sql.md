---
title: Typy strukturalne dopuszczające wartość null (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: b155c672d8c0bef8b01fb26fb49908f094add25a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319487"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="d7090-102">Typy strukturalne dopuszczające wartość null (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d7090-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="d7090-103">Wystąpienie `null` typu strukturalnego jest wystąpieniem, które nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="d7090-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="d7090-104">Różni się to od istniejącego wystąpienia, w którym wszystkie właściwości mają wartości `null`.</span><span class="sxs-lookup"><span data-stu-id="d7090-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="d7090-105">W tym temacie opisano typy strukturalne dopuszczające wartość null, w tym typy dopuszczające wartości null i które wzorce kodu tworzą wystąpienia `null` typów ze strukturą dopuszczającą wartość null.</span><span class="sxs-lookup"><span data-stu-id="d7090-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="d7090-106">Rodzaje typów strukturalnych dopuszczających wartość null</span><span class="sxs-lookup"><span data-stu-id="d7090-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="d7090-107">Istnieją trzy rodzaje typów struktur dopuszczających wartości null:</span><span class="sxs-lookup"><span data-stu-id="d7090-107">There are three kinds of nullable structure types:</span></span>  
  
- <span data-ttu-id="d7090-108">Typy wierszy.</span><span class="sxs-lookup"><span data-stu-id="d7090-108">Row types.</span></span>  
  
- <span data-ttu-id="d7090-109">Typy złożone.</span><span class="sxs-lookup"><span data-stu-id="d7090-109">Complex types.</span></span>  
  
- <span data-ttu-id="d7090-110">Typy jednostek.</span><span class="sxs-lookup"><span data-stu-id="d7090-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="d7090-111">Wzorce kodu generujące puste wystąpienia typów strukturalnych</span><span class="sxs-lookup"><span data-stu-id="d7090-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="d7090-112">Następujące scenariusze tworzą wystąpienia `null`:</span><span class="sxs-lookup"><span data-stu-id="d7090-112">The following scenarios produce `null` instances:</span></span>  
  
- <span data-ttu-id="d7090-113">Kształtowanie `null` jako typ strukturalny:</span><span class="sxs-lookup"><span data-stu-id="d7090-113">Shaping `null` as a structured type:</span></span>  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- <span data-ttu-id="d7090-114">Przerzutowanie typu podstawowego na typ pochodny:</span><span class="sxs-lookup"><span data-stu-id="d7090-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- <span data-ttu-id="d7090-115">Sprzężenie zewnętrzne w przypadku wartości false:</span><span class="sxs-lookup"><span data-stu-id="d7090-115">Outer join on false condition:</span></span>  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="d7090-116">--lub</span><span class="sxs-lookup"><span data-stu-id="d7090-116">--or</span></span>  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="d7090-117">--lub</span><span class="sxs-lookup"><span data-stu-id="d7090-117">--or</span></span>  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- <span data-ttu-id="d7090-118">Odwołujące się do `null` odwołania:</span><span class="sxs-lookup"><span data-stu-id="d7090-118">Dereferencing a `null` reference:</span></span>  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- <span data-ttu-id="d7090-119">Uzyskiwanie ANYELEMENT z pustej kolekcji:</span><span class="sxs-lookup"><span data-stu-id="d7090-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- <span data-ttu-id="d7090-120">Sprawdzanie wystąpień `null` typów strukturalnych:</span><span class="sxs-lookup"><span data-stu-id="d7090-120">Checking for `null` instances of structured types:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d7090-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7090-121">See also</span></span>

- [<span data-ttu-id="d7090-122">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="d7090-122">Entity SQL Overview</span></span>](entity-sql-overview.md)
