---
title: Operand 'IsNot' typu „typename” można porównać tylko z elementem „Nothing”, ponieważ typ „typename” jest typem zerowalnym
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: fb61b04021bd844fade94413b4f3b28b82f6411b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402801"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="2893b-102">Operand 'IsNot' typu „typename” można porównać tylko z elementem „Nothing”, ponieważ typ „typename” jest typem zerowalnym</span><span class="sxs-lookup"><span data-stu-id="2893b-102">'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>

<span data-ttu-id="2893b-103">Zmienna zadeklarowana jako typ wartości null została porównana z wyrażeniem innym niż `Nothing` użycie `IsNot` operatora.</span><span class="sxs-lookup"><span data-stu-id="2893b-103">A variable declared as a nullable value type has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>

<span data-ttu-id="2893b-104">**Identyfikator błędu:** BC32128</span><span class="sxs-lookup"><span data-stu-id="2893b-104">**Error ID:** BC32128</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2893b-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="2893b-105">To correct this error</span></span>

<span data-ttu-id="2893b-106">Aby porównać typ dopuszczający wartość null z wyrażeniem innym niż `Nothing` przy użyciu `IsNot` operatora, należy wywołać `GetType` metodę na typie dopuszczającym wartość null i porównać wynik z wyrażeniem, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2893b-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a><span data-ttu-id="2893b-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2893b-107">See also</span></span>

- [<span data-ttu-id="2893b-108">Typy wartości null</span><span class="sxs-lookup"><span data-stu-id="2893b-108">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="2893b-109">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="2893b-109">IsNot Operator</span></span>](../operators/isnot-operator.md)
