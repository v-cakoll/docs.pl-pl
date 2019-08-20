---
title: 'Instrukcje: Test pod kątem równości odwołań (tożsamość) C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 2b4b7b7bdd03077a78aa2a6375764fa86a885ef5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588641"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="571ef-102">Instrukcje: Testowanie równości odwołań (tożsamość) (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="571ef-102">How to: Test for Reference Equality (Identity) (C# Programming Guide)</span></span>
<span data-ttu-id="571ef-103">Nie trzeba implementować żadnej logiki niestandardowej w celu obsługi porównania równości odwołań w typach.</span><span class="sxs-lookup"><span data-stu-id="571ef-103">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="571ef-104">Ta funkcja jest dostępna dla wszystkich typów przez metodę statyczną <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="571ef-104">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="571ef-105">Poniższy przykład pokazuje, jak określić, czy dwie zmienne mają *równość odwołania*, co oznacza, że odwołują się do tego samego obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="571ef-105">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="571ef-106">W przykładzie pokazano również, <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> dlaczego zawsze `false` są zwracane dla typów wartości i dlaczego nie należy <xref:System.Object.ReferenceEquals%2A> używać do określania równości ciągów.</span><span class="sxs-lookup"><span data-stu-id="571ef-106">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="571ef-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="571ef-107">Example</span></span>  
 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 <span data-ttu-id="571ef-108">`Equals` Implementacja<xref:System.Object?displayProperty=nameWithType> w uniwersalnej klasie bazowej również wykonuje kontrolę równości odwołań, ale nie jest to zalecane, ponieważ jeśli klasa ma przesłonić metodę, wyniki mogą nie być oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="571ef-108">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="571ef-109">Ta sama wartość `==` dotyczy operatorów i `!=` .</span><span class="sxs-lookup"><span data-stu-id="571ef-109">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="571ef-110">Gdy są one wykonywane na typach referencyjnych, domyślne zachowanie `==` i `!=` ma na celu wykonywanie kontroli równości odwołań.</span><span class="sxs-lookup"><span data-stu-id="571ef-110">When they are operating on reference types, the default behavior of `==` and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="571ef-111">Jednak klasy pochodne mogą przeciążać operator, aby wykonać kontrolę równości wartości.</span><span class="sxs-lookup"><span data-stu-id="571ef-111">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="571ef-112">Aby zminimalizować prawdopodobieństwo wystąpienia błędu, najlepiej jest zawsze używać <xref:System.Object.ReferenceEquals%2A> , gdy trzeba określić, czy dwa obiekty mają równość odwołania.</span><span class="sxs-lookup"><span data-stu-id="571ef-112">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="571ef-113">Stałe ciągi w tym samym zestawie są zawsze Interni przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="571ef-113">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="571ef-114">Oznacza to, że jest obsługiwane tylko jedno wystąpienie każdego unikatowego ciągu literału.</span><span class="sxs-lookup"><span data-stu-id="571ef-114">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="571ef-115">Jednak środowisko uruchomieniowe nie gwarantuje, że ciągi utworzone w czasie wykonywania są InterNIC, ani nie gwarantujemy, że dwie równe ciągi stałe w różnych zestawach są InterNIC.</span><span class="sxs-lookup"><span data-stu-id="571ef-115">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="571ef-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="571ef-116">See also</span></span>

- [<span data-ttu-id="571ef-117">Porównywanie równości</span><span class="sxs-lookup"><span data-stu-id="571ef-117">Equality Comparisons</span></span>](./equality-comparisons.md)
