---
title: 'Instrukcje: Testowanie równości odwołań (tożsamości) - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 6aa3aebdc03fc54233ac1cc027241fcb36cc8535
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237054"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="672d4-102">Instrukcje: Testowanie równości odwołań (tożsamości) (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="672d4-102">How to: Test for Reference Equality (Identity) (C# Programming Guide)</span></span>
<span data-ttu-id="672d4-103">Nie masz implementuje żadnej logiki niestandardowej obsługuje porównania równości odwołań w typy.</span><span class="sxs-lookup"><span data-stu-id="672d4-103">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="672d4-104">Ta funkcjonalność jest dostarczana dla wszystkich typów przez statyczną <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="672d4-104">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="672d4-105">Poniższy przykład pokazuje, jak ustalić, czy dwie zmienne mają *równości odwołań*, co oznacza, że odnoszą się do tego samego obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="672d4-105">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="672d4-106">W przykładzie pokazano też, dlaczego <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> zawsze zwraca `false` dla typów wartości i dlaczego nie należy używać <xref:System.Object.ReferenceEquals%2A> Aby określić ciąg znaków równości.</span><span class="sxs-lookup"><span data-stu-id="672d4-106">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="672d4-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="672d4-107">Example</span></span>  
 [!code-csharp[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-test-for-reference-equality-identity_1.cs)]  
  
 <span data-ttu-id="672d4-108">Implementacja `Equals` w <xref:System.Object?displayProperty=nameWithType> universal klasa bazowa wykonuje sprawdzanie równości odwołań, ale zaleca się nie należy używać tego, ponieważ jeśli Klasa docelowa przesłonić metodę, wyniki mogą być czego oczekiwać.</span><span class="sxs-lookup"><span data-stu-id="672d4-108">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="672d4-109">Dotyczy to także `==` i `!=` operatorów.</span><span class="sxs-lookup"><span data-stu-id="672d4-109">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="672d4-110">Gdy działają w odwołaniu do typów, domyślne zachowanie `==` i `!=` jest sprawdzania równości odwołań.</span><span class="sxs-lookup"><span data-stu-id="672d4-110">When they are operating on reference types, the default behavior of `==` and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="672d4-111">Jednak klasy pochodne doprowadzić do przeciążenia operatora sprawdzania równości wartości.</span><span class="sxs-lookup"><span data-stu-id="672d4-111">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="672d4-112">Aby zminimalizować ryzyko błędów, najlepiej zawsze używaj <xref:System.Object.ReferenceEquals%2A> w przypadku określenia, czy dwa obiekty mają odniesienie równości.</span><span class="sxs-lookup"><span data-stu-id="672d4-112">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="672d4-113">Stałe ciągów w ramach tego samego zestawu są zawsze interned w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="672d4-113">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="672d4-114">Oznacza to obsługiwane jest tylko jedno wystąpienie każdego unikatowy ciąg literału.</span><span class="sxs-lookup"><span data-stu-id="672d4-114">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="672d4-115">Jednak środowisko uruchomieniowe nie gwarantuje, że są interned ciągi tworzony w czasie wykonywania, ponieważ gwarantuje to, że są interned równa dwa ciągi stałej w różnych zestawach.</span><span class="sxs-lookup"><span data-stu-id="672d4-115">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="672d4-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="672d4-116">See Also</span></span>

- [<span data-ttu-id="672d4-117">Porównywanie równości</span><span class="sxs-lookup"><span data-stu-id="672d4-117">Equality Comparisons</span></span>](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)
