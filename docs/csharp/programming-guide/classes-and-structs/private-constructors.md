---
title: Konstruktory prywatne C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 2f8b93fbeb7c2996f3e2683fe86f159fbfa61a92
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705447"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="93537-102">Konstruktory prywatne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="93537-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="93537-103">Konstruktor prywatny jest specjalnym konstruktorem wystąpień.</span><span class="sxs-lookup"><span data-stu-id="93537-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="93537-104">Jest on zazwyczaj używany w klasach, które zawierają tylko statyczne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="93537-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="93537-105">Jeśli klasa ma jeden lub więcej konstruktorów prywatnych i nie ma konstruktorów publicznych, inne klasy (poza klasami zagnieżdżonymi) nie mogą tworzyć wystąpień tej klasy.</span><span class="sxs-lookup"><span data-stu-id="93537-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="93537-106">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="93537-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="93537-107">Deklaracja pustego konstruktora uniemożliwia automatyczne generowanie konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="93537-107">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="93537-108">Należy pamiętać, że jeśli nie używasz modyfikatora dostępu z konstruktorem, będzie on nadal domyślnie prywatny.</span><span class="sxs-lookup"><span data-stu-id="93537-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="93537-109">Jednak modyfikator [prywatny](../../language-reference/keywords/private.md) jest zwykle używany jawnie, aby wyczyścił, że nie można utworzyć wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="93537-109">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="93537-110">Konstruktory prywatne są używane do zapobiegania tworzeniu wystąpień klasy w przypadku braku pól lub metod wystąpienia, takich jak Klasa <xref:System.Math> lub gdy wywoływana jest metoda w celu uzyskania wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="93537-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="93537-111">Jeśli wszystkie metody w klasie są statyczne, należy rozważyć uczynienie kompletnej klasy statycznej.</span><span class="sxs-lookup"><span data-stu-id="93537-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="93537-112">Aby uzyskać więcej informacji [, zobacz klasy statyczne i statyczne elementy członkowskie klas](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="93537-112">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="93537-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="93537-113">Example</span></span>  
 <span data-ttu-id="93537-114">Poniżej znajduje się przykład klasy korzystającej z konstruktora prywatnego.</span><span class="sxs-lookup"><span data-stu-id="93537-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="93537-115">Zwróć uwagę, że jeśli dodasz komentarz z następującej instrukcji z przykładu, zostanie wygenerowany błąd, ponieważ Konstruktor jest niedostępny z powodu swojego poziomu ochrony:</span><span class="sxs-lookup"><span data-stu-id="93537-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="93537-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="93537-116">C# Language Specification</span></span>  

<span data-ttu-id="93537-117">Aby uzyskać więcej informacji, zobacz [prywatne konstruktory](~/_csharplang/spec/classes.md#private-constructors) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="93537-117">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="93537-118">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="93537-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="93537-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93537-119">See also</span></span>

- [<span data-ttu-id="93537-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="93537-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="93537-121">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="93537-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="93537-122">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="93537-122">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="93537-123">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="93537-123">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="93537-124">private</span><span class="sxs-lookup"><span data-stu-id="93537-124">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="93537-125">public</span><span class="sxs-lookup"><span data-stu-id="93537-125">public</span></span>](../../language-reference/keywords/public.md)
