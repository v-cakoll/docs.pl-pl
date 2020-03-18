---
title: Jak zastąpić ToString metody - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 7c7196df56821c134b31982d7956a75039e9f929
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705577"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="f03ca-102">Jak zastąpić ToString metody (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="f03ca-102">How to override the ToString method (C# Programming Guide)</span></span>

<span data-ttu-id="f03ca-103">Każda klasa lub struktura w języku <xref:System.Object> C# niejawnie dziedziczy klasę.</span><span class="sxs-lookup"><span data-stu-id="f03ca-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="f03ca-104">W związku z tym każdy <xref:System.Object.ToString%2A> obiekt w języku C# pobiera metodę, która zwraca reprezentację ciągu tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f03ca-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="f03ca-105">Na przykład wszystkie zmienne `int` typu `ToString` mają metodę, która umożliwia im zwracanie ich zawartości jako ciągu:</span><span class="sxs-lookup"><span data-stu-id="f03ca-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="f03ca-106">Podczas tworzenia klasy niestandardowej lub struktury, należy <xref:System.Object.ToString%2A> zastąpić metodę w celu dostarczenia informacji o typie do kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="f03ca-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="f03ca-107">Aby uzyskać informacje dotyczące używania ciągów formatu i innych `ToString` typów formatowania niestandardowego z tą metodą, zobacz [Typy formatowania](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="f03ca-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f03ca-108">Po podjęciu decyzji, jakie informacje należy podać za pomocą tej metody, należy wziąć pod uwagę, czy klasy lub struktury będą kiedykolwiek używane przez niezaufany kod.</span><span class="sxs-lookup"><span data-stu-id="f03ca-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="f03ca-109">Należy zachować ostrożność, aby upewnić się, że nie podasz żadnych informacji, które mogą być wykorzystane przez złośliwy kod.</span><span class="sxs-lookup"><span data-stu-id="f03ca-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="f03ca-110">Aby zastąpić `ToString` metodę w klasie lub strukturze:</span><span class="sxs-lookup"><span data-stu-id="f03ca-110">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="f03ca-111">Deklaruj `ToString` metodę za pomocą następujących modyfikatorów i typu zwracanego:</span><span class="sxs-lookup"><span data-stu-id="f03ca-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="f03ca-112">Zaimplementuj metodę tak, aby zwracaciąg.</span><span class="sxs-lookup"><span data-stu-id="f03ca-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="f03ca-113">Poniższy przykład zwraca nazwę klasy oprócz danych specyficznych dla określonego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="f03ca-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="f03ca-114">Można przetestować `ToString` metodę, jak pokazano w poniższym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="f03ca-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="f03ca-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f03ca-115">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="f03ca-116">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="f03ca-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f03ca-117">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="f03ca-117">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="f03ca-118">Ciągi</span><span class="sxs-lookup"><span data-stu-id="f03ca-118">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="f03ca-119">ciąg</span><span class="sxs-lookup"><span data-stu-id="f03ca-119">string</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="f03ca-120">override</span><span class="sxs-lookup"><span data-stu-id="f03ca-120">override</span></span>](../../language-reference/keywords/override.md)
- [<span data-ttu-id="f03ca-121">virtual</span><span class="sxs-lookup"><span data-stu-id="f03ca-121">virtual</span></span>](../../language-reference/keywords/virtual.md)
- [<span data-ttu-id="f03ca-122">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="f03ca-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
