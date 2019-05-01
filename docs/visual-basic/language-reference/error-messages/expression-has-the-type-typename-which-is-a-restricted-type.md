---
title: Wyrażenie zawiera typ „<typename>”, który jest typem ograniczonym i nie można go używać do uzyskiwania dostępu do członków dziedziczonych po elemencie „Object” lub „ValueType”.
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 017a2458562068727674bd3fd9cda8c33d989e8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803171"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a><span data-ttu-id="6ff54-102">Wyrażenie zawiera typ "\<typename >" który jest typem ograniczonym i nie może być używane do dostępu członków dziedziczonych po elemencie "Object" lub "ValueType"</span><span class="sxs-lookup"><span data-stu-id="6ff54-102">Expression has the type '\<typename>' which is a restricted type and cannot be used to access members inherited from 'Object' or 'ValueType'</span></span>
<span data-ttu-id="6ff54-103">Wyrażenie obliczane do typu, który nie może zostać opakowany przez środowisko uruchomieniowe języka wspólnego (CLR), ale uzyskuje dostęp do składowej, która wymaga opakowania.</span><span class="sxs-lookup"><span data-stu-id="6ff54-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="6ff54-104">*Konwersja boxing* odnosi się do przetwarzania niezbędne w celu konwersji typu do `Object` lub, czasami <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="6ff54-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="6ff54-105">Środowisko uruchomieniowe języka wspólnego nie polu na przykład niektóre typy struktury <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, i <xref:System.TypedReference>.</span><span class="sxs-lookup"><span data-stu-id="6ff54-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="6ff54-106">To wyrażenie podejmują próbę użycia w typie ograniczonym do wywołania metody dziedziczone z <xref:System.Object> lub <xref:System.ValueType>, takich jak <xref:System.Object.GetHashCode%2A> lub <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="6ff54-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="6ff54-107">Aby uzyskać dostęp do tej metody, Visual Basic została podjęta próba konwersji niejawnej konwersji boxing, która powoduje występowanie tego błędu.</span><span class="sxs-lookup"><span data-stu-id="6ff54-107">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="6ff54-108">**Identyfikator błędu:** BC31393</span><span class="sxs-lookup"><span data-stu-id="6ff54-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6ff54-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6ff54-109">To correct this error</span></span>  
  
1. <span data-ttu-id="6ff54-110">Znajdź wyrażenie obliczane do typu wspominane.</span><span class="sxs-lookup"><span data-stu-id="6ff54-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2. <span data-ttu-id="6ff54-111">Znajdź część instrukcji, który próbuje wywołać metodę odziedziczone <xref:System.Object> lub <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="6ff54-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3. <span data-ttu-id="6ff54-112">Napisz ponownie instrukcję, aby uniknąć wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="6ff54-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ff54-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ff54-113">See also</span></span>

- [<span data-ttu-id="6ff54-114">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="6ff54-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
