---
title: Konstruktory prywatne — przewodnik programowania c#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 2f8b93fbeb7c2996f3e2683fe86f159fbfa61a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705447"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="75268-102">Konstruktory prywatne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="75268-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="75268-103">Konstruktora prywatnego jest konstruktorem instancji specjalne.</span><span class="sxs-lookup"><span data-stu-id="75268-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="75268-104">Zazwyczaj jest używany w klasach, które zawierają tylko elementy członkowskie statyczne.</span><span class="sxs-lookup"><span data-stu-id="75268-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="75268-105">Jeśli klasa ma jeden lub więcej prywatnych konstruktorów i nie konstruktorów publicznych, inne klasy (z wyjątkiem klas zagnieżdżonych) nie można utworzyć wystąpienia tej klasy.</span><span class="sxs-lookup"><span data-stu-id="75268-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="75268-106">Przykład:</span><span class="sxs-lookup"><span data-stu-id="75268-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="75268-107">Deklaracja pustego konstruktora uniemożliwia automatyczne generowanie konstruktora bezparametrowego.</span><span class="sxs-lookup"><span data-stu-id="75268-107">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="75268-108">Należy zauważyć, że jeśli nie używasz modyfikatordostępu z konstruktorem nadal będzie prywatny domyślnie.</span><span class="sxs-lookup"><span data-stu-id="75268-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="75268-109">Jednak [prywatny](../../language-reference/keywords/private.md) modyfikator jest zwykle używany jawnie, aby wyjaśnić, że klasa nie może być tworzone.</span><span class="sxs-lookup"><span data-stu-id="75268-109">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="75268-110">Konstruktory prywatne są używane do zapobiegania tworzeniu wystąpień klasy, gdy nie <xref:System.Math> ma pól lub metod wystąpienia, takich jak klasa lub gdy metoda jest wywoływana w celu uzyskania wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="75268-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="75268-111">Jeśli wszystkie metody w klasie są statyczne, należy rozważyć uczynienie pełnej klasy statyczne.</span><span class="sxs-lookup"><span data-stu-id="75268-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="75268-112">Aby uzyskać więcej informacji, zobacz [Klasy statyczne i Elementy członkowskie klasy statycznej](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="75268-112">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="75268-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="75268-113">Example</span></span>  
 <span data-ttu-id="75268-114">Poniżej przedstawiono przykład klasy przy użyciu konstruktora prywatnego.</span><span class="sxs-lookup"><span data-stu-id="75268-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="75268-115">Należy zauważyć, że jeśli odkomentować następującą instrukcję z przykładu, wygeneruje błąd, ponieważ konstruktor jest niedostępny ze względu na jego poziom ochrony:</span><span class="sxs-lookup"><span data-stu-id="75268-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="75268-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="75268-116">C# Language Specification</span></span>  

<span data-ttu-id="75268-117">Aby uzyskać więcej informacji, zobacz [Konstruktory prywatne](~/_csharplang/spec/classes.md#private-constructors) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="75268-117">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="75268-118">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="75268-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="75268-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75268-119">See also</span></span>

- [<span data-ttu-id="75268-120">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="75268-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="75268-121">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="75268-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="75268-122">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="75268-122">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="75268-123">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="75268-123">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="75268-124">Prywatny</span><span class="sxs-lookup"><span data-stu-id="75268-124">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="75268-125">Publicznego</span><span class="sxs-lookup"><span data-stu-id="75268-125">public</span></span>](../../language-reference/keywords/public.md)
