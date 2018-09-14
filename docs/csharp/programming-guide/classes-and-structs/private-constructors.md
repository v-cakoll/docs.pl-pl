---
title: Konstruktory prywatne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 1338a6efbe03522093899009178b6f31e558d8dd
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45520104"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="c2ab3-102">Konstruktory prywatne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c2ab3-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="c2ab3-103">Konstruktor prywatny jest konstruktorem wystąpienia specjalnego.</span><span class="sxs-lookup"><span data-stu-id="c2ab3-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="c2ab3-104">Zazwyczaj jest używany w klasach, które zawierają tylko statyczne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="c2ab3-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="c2ab3-105">Jeśli klasa ma co najmniej jeden prywatny konstruktorów i konstruktorów publicznych, inne klasy (z wyjątkiem klas zagnieżdżonych) nie można utworzyć wystąpienia tej klasy.</span><span class="sxs-lookup"><span data-stu-id="c2ab3-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="c2ab3-106">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c2ab3-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]  
  
 <span data-ttu-id="c2ab3-107">Deklaracja pustego konstruktora uniemożliwia automatyczne generowanie konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="c2ab3-107">The declaration of the empty constructor prevents the automatic generation of a default constructor.</span></span> <span data-ttu-id="c2ab3-108">Należy pamiętać, że jeśli nie używasz modyfikatora dostępu za pomocą konstruktora nadal będzie domyślnie prywatny.</span><span class="sxs-lookup"><span data-stu-id="c2ab3-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="c2ab3-109">Jednak [prywatnej](../../../csharp/language-reference/keywords/private.md) modyfikator jest zwykle używany w sposób jawny do ułatwiają Wyczyść, że nie można utworzyć wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="c2ab3-109">However, the [private](../../../csharp/language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="c2ab3-110">Konstruktory prywatne są używane, aby uniknąć tworzenia wystąpienia klasy, gdy nie ma żadnych pól wystąpień lub metod, takich jak <xref:System.Math> klasy, lub gdy metoda jest wywoływana w celu uzyskania wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="c2ab3-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="c2ab3-111">Jeśli wszystkie metody w klasie statycznej, należy wziąć pod uwagę pełną klasy jako możliwej statyczne.</span><span class="sxs-lookup"><span data-stu-id="c2ab3-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="c2ab3-112">Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="c2ab3-112">For more information see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2ab3-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="c2ab3-113">Example</span></span>  
 <span data-ttu-id="c2ab3-114">Oto przykład klasy przy użyciu prywatnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c2ab3-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]  
  
 <span data-ttu-id="c2ab3-115">Zwróć uwagę, że jeśli usuniesz komentarz Poniższa instrukcja z przykładu, zostanie wygenerowany błąd ponieważ Konstruktor jest niedostępny z powodu swojego poziomu ochrony:</span><span class="sxs-lookup"><span data-stu-id="c2ab3-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c2ab3-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c2ab3-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c2ab3-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2ab3-117">See Also</span></span>

- [<span data-ttu-id="c2ab3-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c2ab3-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c2ab3-119">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="c2ab3-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="c2ab3-120">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="c2ab3-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [<span data-ttu-id="c2ab3-121">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="c2ab3-121">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
- [<span data-ttu-id="c2ab3-122">private</span><span class="sxs-lookup"><span data-stu-id="c2ab3-122">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
- [<span data-ttu-id="c2ab3-123">public</span><span class="sxs-lookup"><span data-stu-id="c2ab3-123">public</span></span>](../../../csharp/language-reference/keywords/public.md)
