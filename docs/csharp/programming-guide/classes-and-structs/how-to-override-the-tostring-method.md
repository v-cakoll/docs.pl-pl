---
title: Jak zastąpić metodę ToString — Przewodnik programowania w języku C#
description: Dowiedz się, jak zastąpić metodę ToString w języku C#. Każda klasa lub struktura dziedziczy obiekt i pobiera ToString, który zwraca ciąg reprezentujący ten obiekt.
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 65b34b485d4b90173a4c956dd0ebaaa590a0c7c9
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865011"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="be965-104">Jak zastąpić metodę ToString (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="be965-104">How to override the ToString method (C# Programming Guide)</span></span>

<span data-ttu-id="be965-105">Każda klasa lub struktura w języku C# niejawnie dziedziczy <xref:System.Object> klasę.</span><span class="sxs-lookup"><span data-stu-id="be965-105">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="be965-106">W związku z tym każdy obiekt w C# pobiera <xref:System.Object.ToString%2A> metodę, która zwraca ciąg reprezentujący ten obiekt.</span><span class="sxs-lookup"><span data-stu-id="be965-106">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="be965-107">Na przykład wszystkie zmienne typu `int` mają `ToString` metodę, która umożliwia im zwracanie ich zawartości jako ciągu:</span><span class="sxs-lookup"><span data-stu-id="be965-107">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="be965-108">Podczas tworzenia niestandardowej klasy lub struktury należy zastąpić <xref:System.Object.ToString%2A> metodę, aby podać informacje o typie kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="be965-108">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="be965-109">Aby uzyskać informacje o sposobach używania ciągów formatowania i innych typów formatowania niestandardowego z `ToString` metodą, zobacz [Typy formatowania](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="be965-109">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="be965-110">W przypadku podjęcia decyzji o tym, jakie informacje mają być zawarte w tej metodzie, należy rozważyć, czy dana klasa lub struktura będzie kiedykolwiek używana przez kod niezaufany.</span><span class="sxs-lookup"><span data-stu-id="be965-110">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="be965-111">Należy zachować ostrożność, aby upewnić się, że nie podano żadnych informacji, które mogą być wykorzystywane przez złośliwy kod.</span><span class="sxs-lookup"><span data-stu-id="be965-111">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="be965-112">Aby zastąpić `ToString` metodę w klasie lub strukturze:</span><span class="sxs-lookup"><span data-stu-id="be965-112">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="be965-113">Zadeklaruj `ToString` metodę z następującymi modyfikatorami i zwracanym typem:</span><span class="sxs-lookup"><span data-stu-id="be965-113">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="be965-114">Zaimplementuj metodę, tak aby zwracała ciąg.</span><span class="sxs-lookup"><span data-stu-id="be965-114">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="be965-115">Poniższy przykład zwraca nazwę klasy oprócz danych specyficznych dla określonego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="be965-115">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="be965-116">Możesz przetestować `ToString` metodę, jak pokazano w poniższym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="be965-116">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="be965-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be965-117">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="be965-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="be965-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="be965-119">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="be965-119">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="be965-120">Ciągi</span><span class="sxs-lookup"><span data-stu-id="be965-120">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="be965-121">parametry</span><span class="sxs-lookup"><span data-stu-id="be965-121">string</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="be965-122">override</span><span class="sxs-lookup"><span data-stu-id="be965-122">override</span></span>](../../language-reference/keywords/override.md)
- [<span data-ttu-id="be965-123">wirtualnej</span><span class="sxs-lookup"><span data-stu-id="be965-123">virtual</span></span>](../../language-reference/keywords/virtual.md)
- [<span data-ttu-id="be965-124">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="be965-124">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
