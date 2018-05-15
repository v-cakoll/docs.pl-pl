---
title: Konstruktory prywatne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: e8f1f097a62f022d305987800e89353b038f42ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="14878-102">Konstruktory prywatne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="14878-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="14878-103">Konstruktor prywatny jest konstruktor wystąpienia specjalnego.</span><span class="sxs-lookup"><span data-stu-id="14878-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="14878-104">Jest zwykle używany w klasach, które zawierają tylko statyczne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="14878-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="14878-105">Jeśli klasa ma co najmniej jeden konstruktory prywatne i nie konstruktorów publicznych, innych klas (z wyjątkiem klasy zagnieżdżone) nie można utworzyć wystąpienia tej klasy.</span><span class="sxs-lookup"><span data-stu-id="14878-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="14878-106">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="14878-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]  
  
 <span data-ttu-id="14878-107">Deklaracja pustego konstruktora uniemożliwia automatyczne generowanie konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="14878-107">The declaration of the empty constructor prevents the automatic generation of a default constructor.</span></span> <span data-ttu-id="14878-108">Należy pamiętać, że jeśli nie używasz modyfikatora dostępu z konstruktora nadal będzie domyślnie prywatne.</span><span class="sxs-lookup"><span data-stu-id="14878-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="14878-109">Jednak [prywatnej](../../../csharp/language-reference/keywords/private.md) modyfikator zwykle używane jest jawnie go wyczyścić, że nie można utworzyć wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="14878-109">However, the [private](../../../csharp/language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="14878-110">Konstruktory prywatne są używane, aby uniknąć tworzenia wystąpień klasy, gdy nie ma żadnych pól wystąpień lub metod, takich jak <xref:System.Math> klas, lub gdy jest wywoływana metoda uzyskać wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="14878-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="14878-111">Jeśli wszystkie metody w klasie statycznej, należy rozważyć zmianę pełnej klasy statycznej.</span><span class="sxs-lookup"><span data-stu-id="14878-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="14878-112">Aby uzyskać więcej informacji, zobacz [klasy statyczne i statycznych elementów członkowskich klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="14878-112">For more information see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="14878-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="14878-113">Example</span></span>  
 <span data-ttu-id="14878-114">Oto przykład klasy przy użyciu konstruktora prywatnego.</span><span class="sxs-lookup"><span data-stu-id="14878-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]  
  
 <span data-ttu-id="14878-115">Zwróć uwagę, że jeśli usuń znaczniki komentarza z przykładu następującą instrukcję, go spowodują wygenerowanie błędu, ponieważ Konstruktor jest niedostępny z powodu swojego poziomu ochrony:</span><span class="sxs-lookup"><span data-stu-id="14878-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="14878-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="14878-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="14878-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14878-117">See Also</span></span>  
 [<span data-ttu-id="14878-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="14878-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="14878-119">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="14878-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="14878-120">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="14878-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="14878-121">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="14878-121">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [<span data-ttu-id="14878-122">private</span><span class="sxs-lookup"><span data-stu-id="14878-122">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="14878-123">public</span><span class="sxs-lookup"><span data-stu-id="14878-123">public</span></span>](../../../csharp/language-reference/keywords/public.md)
