---
title: Konstruktory prywatne - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 0bd15b29f5e86b802eb48d96fde5be4b387261eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703351"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="3d025-102">Konstruktory prywatne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3d025-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="3d025-103">Konstruktor prywatny jest konstruktorem wystąpienia specjalnego.</span><span class="sxs-lookup"><span data-stu-id="3d025-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="3d025-104">Zazwyczaj jest używany w klasach, które zawierają tylko statyczne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="3d025-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="3d025-105">Jeśli klasa ma co najmniej jeden prywatny konstruktorów i konstruktorów publicznych, inne klasy (z wyjątkiem klas zagnieżdżonych) nie można utworzyć wystąpienia tej klasy.</span><span class="sxs-lookup"><span data-stu-id="3d025-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="3d025-106">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="3d025-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="3d025-107">Deklaracja pustego konstruktora uniemożliwia automatyczne generowanie konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="3d025-107">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="3d025-108">Należy pamiętać, że jeśli nie używasz modyfikatora dostępu za pomocą konstruktora nadal będzie domyślnie prywatny.</span><span class="sxs-lookup"><span data-stu-id="3d025-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="3d025-109">Jednak [prywatnej](../../../csharp/language-reference/keywords/private.md) modyfikator jest zwykle używany w sposób jawny do ułatwiają Wyczyść, że nie można utworzyć wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="3d025-109">However, the [private](../../../csharp/language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="3d025-110">Konstruktory prywatne są używane, aby uniknąć tworzenia wystąpienia klasy, gdy nie ma żadnych pól wystąpień lub metod, takich jak <xref:System.Math> klasy, lub gdy metoda jest wywoływana w celu uzyskania wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="3d025-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="3d025-111">Jeśli wszystkie metody w klasie statycznej, należy wziąć pod uwagę pełną klasy jako możliwej statyczne.</span><span class="sxs-lookup"><span data-stu-id="3d025-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="3d025-112">Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="3d025-112">For more information see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d025-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d025-113">Example</span></span>  
 <span data-ttu-id="3d025-114">Oto przykład klasy przy użyciu prywatnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="3d025-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="3d025-115">Zwróć uwagę, że jeśli usuniesz komentarz Poniższa instrukcja z przykładu, zostanie wygenerowany błąd ponieważ Konstruktor jest niedostępny z powodu swojego poziomu ochrony:</span><span class="sxs-lookup"><span data-stu-id="3d025-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3d025-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3d025-116">C# Language Specification</span></span>  

<span data-ttu-id="3d025-117">Aby uzyskać więcej informacji, zobacz [konstruktory prywatne](~/_csharplang/spec/classes.md#private-constructors) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3d025-117">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="3d025-118">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="3d025-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3d025-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d025-119">See also</span></span>

- [<span data-ttu-id="3d025-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3d025-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3d025-121">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="3d025-121">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="3d025-122">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="3d025-122">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="3d025-123">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="3d025-123">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [<span data-ttu-id="3d025-124">private</span><span class="sxs-lookup"><span data-stu-id="3d025-124">private</span></span>](../../../csharp/language-reference/keywords/private.md)
- [<span data-ttu-id="3d025-125">public</span><span class="sxs-lookup"><span data-stu-id="3d025-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)
