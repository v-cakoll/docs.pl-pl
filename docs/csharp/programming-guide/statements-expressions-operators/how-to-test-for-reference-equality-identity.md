---
title: Jak przetestować równość referencyjną (Tożsamość) - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 77ce2ef0ccf47d619134c120101ba2aa04f485e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75699057"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="ad50e-102">Jak przetestować równość referencyjną (Tożsamość) (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="ad50e-102">How to test for reference equality (Identity) (C# Programming Guide)</span></span>
<span data-ttu-id="ad50e-103">Nie trzeba implementować żadnej logiki niestandardowej do obsługi porównań równości odwołań w typach.</span><span class="sxs-lookup"><span data-stu-id="ad50e-103">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="ad50e-104">Ta funkcja jest dostępna dla wszystkich <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> typów za pomocą metody statycznej.</span><span class="sxs-lookup"><span data-stu-id="ad50e-104">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="ad50e-105">W poniższym przykładzie pokazano, jak ustalić, czy dwie zmienne mają *równość odwołania*, co oznacza, że odnoszą się do tego samego obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad50e-105">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="ad50e-106">W przykładzie pokazano również, dlaczego <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> zawsze zwraca `false` <xref:System.Object.ReferenceEquals%2A> dla typów wartości i dlaczego nie należy używać do określania równości ciągów.</span><span class="sxs-lookup"><span data-stu-id="ad50e-106">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad50e-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad50e-107">Example</span></span>  
 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 <span data-ttu-id="ad50e-108">Implementacja `Equals` w <xref:System.Object?displayProperty=nameWithType> uniwersalnej klasie podstawowej wykonuje również sprawdzanie równości odwołania, ale najlepiej nie używać tego, ponieważ jeśli klasa dzieje się zastąpić metodę, wyniki mogą nie być to, czego oczekujesz.</span><span class="sxs-lookup"><span data-stu-id="ad50e-108">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="ad50e-109">To samo dotyczy `==` operatorów `!=` i operatorów.</span><span class="sxs-lookup"><span data-stu-id="ad50e-109">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="ad50e-110">Gdy działają na typy odwołań, domyślne `==` `!=` zachowanie i jest do wykonywania kontroli równości odwołania.</span><span class="sxs-lookup"><span data-stu-id="ad50e-110">When they are operating on reference types, the default behavior of `==` and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="ad50e-111">Jednak klasy pochodne można przeciążać operatora, aby wykonać sprawdzanie równości wartości.</span><span class="sxs-lookup"><span data-stu-id="ad50e-111">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="ad50e-112">Aby zminimalizować ryzyko wystąpienia błędu, najlepiej <xref:System.Object.ReferenceEquals%2A> jest zawsze używać, gdy trzeba określić, czy dwa obiekty mają równość odwołania.</span><span class="sxs-lookup"><span data-stu-id="ad50e-112">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="ad50e-113">Ciągi stałe w tym samym zestawie są zawsze internowane przez czas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ad50e-113">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="ad50e-114">Oznacza to, że jest zachowywany tylko jedno wystąpienie każdego unikatowego ciągu literału.</span><span class="sxs-lookup"><span data-stu-id="ad50e-114">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="ad50e-115">Jednak czas wykonywania nie gwarantuje, że ciągi utworzone w czasie wykonywania są internowane, ani nie gwarantuje, że dwa równe ciągi stałej w różnych zestawach są internowane.</span><span class="sxs-lookup"><span data-stu-id="ad50e-115">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad50e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad50e-116">See also</span></span>

- [<span data-ttu-id="ad50e-117">Porównania równości</span><span class="sxs-lookup"><span data-stu-id="ad50e-117">Equality Comparisons</span></span>](./equality-comparisons.md)
