---
title: Wyrażenie zawiera typ &#39; &lt;typename&gt; &#39; który jest typem ograniczonym i nie można uzyskać dostępu do członków dziedziczonych po elemencie &#39;obiektu&#39; lub &#39;ValueType&#39;
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 2ba2298da77ac31abc0b1b4ad84328be7bc6dbb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587576"
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a><span data-ttu-id="21891-102">Wyrażenie zawiera typ &#39; &lt;typename&gt; &#39; który jest typem ograniczonym i nie można uzyskać dostępu do członków dziedziczonych po elemencie &#39;obiektu&#39; lub &#39;ValueType&#39;</span><span class="sxs-lookup"><span data-stu-id="21891-102">Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39;</span></span>
<span data-ttu-id="21891-103">Wyrażenie obliczane do typu, który nie może zostać opakowany przez środowisko uruchomieniowe języka wspólnego (CLR), ale uzyskuje dostęp do elementu członkowskiego, który wymaga opakowania.</span><span class="sxs-lookup"><span data-stu-id="21891-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="21891-104">*Konwersja boxing* odwołuje się do przetwarzania, które są niezbędne do przekonwertowania typu na `Object` lub czasem do <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="21891-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="21891-105">Środowisko uruchomieniowe języka wspólnego nie polu na przykład niektóre typy struktur <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, i <xref:System.TypedReference>.</span><span class="sxs-lookup"><span data-stu-id="21891-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="21891-106">To wyrażenie odwołuje się do typie ograniczonym do wywołania metody dziedziczone z <xref:System.Object> lub <xref:System.ValueType>, takich jak <xref:System.Object.GetHashCode%2A> lub <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="21891-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="21891-107">Aby uzyskać dostęp do tej metody, Visual Basic próbował konwersji pakującej niejawne, która powoduje występowanie tego błędu.</span><span class="sxs-lookup"><span data-stu-id="21891-107">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="21891-108">**Identyfikator błędu:** BC31393</span><span class="sxs-lookup"><span data-stu-id="21891-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="21891-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="21891-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="21891-110">Znajdź wyrażenie cytowane typ zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="21891-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2.  <span data-ttu-id="21891-111">Znajdź część instrukcji, która podejmuje próbę wywołania metody odziedziczone <xref:System.Object> lub <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="21891-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3.  <span data-ttu-id="21891-112">Napisz ponownie instrukcję, aby uniknąć wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="21891-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21891-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21891-113">See Also</span></span>  
 [<span data-ttu-id="21891-114">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="21891-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
