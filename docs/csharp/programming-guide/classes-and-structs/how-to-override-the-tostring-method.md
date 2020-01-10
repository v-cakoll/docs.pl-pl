---
title: Jak zastąpić metodę ToString — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 7c7196df56821c134b31982d7956a75039e9f929
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705577"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="0a330-102">Jak zastąpić metodę ToString (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="0a330-102">How to override the ToString method (C# Programming Guide)</span></span>

<span data-ttu-id="0a330-103">Każda klasa lub struktura w C# niejawnie dziedziczy klasy <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="0a330-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="0a330-104">W związku z tym każdy C# obiekt w pobiera metodę <xref:System.Object.ToString%2A>, która zwraca ciąg reprezentujący ten obiekt.</span><span class="sxs-lookup"><span data-stu-id="0a330-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="0a330-105">Na przykład wszystkie zmienne typu `int` mają metodę `ToString`, która umożliwia im zwracanie zawartości jako ciągu:</span><span class="sxs-lookup"><span data-stu-id="0a330-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="0a330-106">Podczas tworzenia niestandardowej klasy lub struktury należy zastąpić metodę <xref:System.Object.ToString%2A>, aby podać informacje o typie kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="0a330-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="0a330-107">Aby uzyskać informacje dotyczące sposobu używania ciągów formatowania i innych typów formatowania niestandardowego z metodą `ToString`, zobacz [Typy formatowania](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="0a330-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0a330-108">W przypadku podjęcia decyzji o tym, jakie informacje mają być zawarte w tej metodzie, należy rozważyć, czy dana klasa lub struktura będzie kiedykolwiek używana przez kod niezaufany.</span><span class="sxs-lookup"><span data-stu-id="0a330-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="0a330-109">Należy zachować ostrożność, aby upewnić się, że nie podano żadnych informacji, które mogą być wykorzystywane przez złośliwy kod.</span><span class="sxs-lookup"><span data-stu-id="0a330-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="0a330-110">Aby zastąpić metodę `ToString` w klasie lub strukturze:</span><span class="sxs-lookup"><span data-stu-id="0a330-110">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="0a330-111">Zadeklaruj metodę `ToString` z następującymi modyfikatorami i zwracanym typem:</span><span class="sxs-lookup"><span data-stu-id="0a330-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="0a330-112">Zaimplementuj metodę, tak aby zwracała ciąg.</span><span class="sxs-lookup"><span data-stu-id="0a330-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="0a330-113">Poniższy przykład zwraca nazwę klasy oprócz danych specyficznych dla określonego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="0a330-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="0a330-114">Możesz przetestować metodę `ToString`, jak pokazano w poniższym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="0a330-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="0a330-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a330-115">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="0a330-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0a330-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0a330-117">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="0a330-117">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="0a330-118">Ciągi</span><span class="sxs-lookup"><span data-stu-id="0a330-118">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="0a330-119">string</span><span class="sxs-lookup"><span data-stu-id="0a330-119">string</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="0a330-120">override</span><span class="sxs-lookup"><span data-stu-id="0a330-120">override</span></span>](../../language-reference/keywords/override.md)
- [<span data-ttu-id="0a330-121">virtual</span><span class="sxs-lookup"><span data-stu-id="0a330-121">virtual</span></span>](../../language-reference/keywords/virtual.md)
- [<span data-ttu-id="0a330-122">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="0a330-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
