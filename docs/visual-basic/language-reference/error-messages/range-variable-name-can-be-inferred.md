---
title: Nazwę zmiennej zakresu można wywnioskować tylko na podstawie prostej lub kwalifikowanej nazwy bez argumentów
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: d6b155de0bb62f667ca76ec9454dec1466976a9b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400412"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="d70fc-102">Nazwę zmiennej zakresu można wywnioskować tylko na podstawie prostej lub kwalifikowanej nazwy bez argumentów</span><span class="sxs-lookup"><span data-stu-id="d70fc-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>

<span data-ttu-id="d70fc-103">Element programistyczny, który ma co najmniej jeden argument jest dołączony do zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="d70fc-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="d70fc-104">Kompilator nie może wywnioskować zmiennej zakresu z tego elementu programowania.</span><span class="sxs-lookup"><span data-stu-id="d70fc-104">The compiler is unable to infer a range variable from that programming element.</span></span>

<span data-ttu-id="d70fc-105">**Identyfikator błędu:** BC36599</span><span class="sxs-lookup"><span data-stu-id="d70fc-105">**Error ID:** BC36599</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d70fc-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d70fc-106">To correct this error</span></span>

<span data-ttu-id="d70fc-107">Podaj jawną nazwę zmiennej dla elementu programistycznego, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="d70fc-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a><span data-ttu-id="d70fc-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d70fc-108">See also</span></span>

- [<span data-ttu-id="d70fc-109">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d70fc-109">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d70fc-110">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="d70fc-110">Select Clause</span></span>](../queries/select-clause.md)
