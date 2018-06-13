---
title: 'Porady: przesłanianie metody ToString (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 86394f5fed55f57df8928648548fcfca117b00d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330710"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="fa795-102">Porady: przesłanianie metody ToString (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="fa795-102">How to: Override the ToString Method (C# Programming Guide)</span></span>
<span data-ttu-id="fa795-103">Każdej klasie lub strukturze w języku C# niejawnie dziedziczy <xref:System.Object> klasy.</span><span class="sxs-lookup"><span data-stu-id="fa795-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="fa795-104">W związku z tym każdy obiekt w języku C# pobiera <xref:System.Object.ToString%2A> metodę, która zwraca reprezentację ciągu tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="fa795-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="fa795-105">Na przykład wszystkie zmienne typu `int` ma `ToString` metodę, która pozwala na zwrócenie ich zawartość jako ciąg:</span><span class="sxs-lookup"><span data-stu-id="fa795-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 <span data-ttu-id="fa795-106">Podczas tworzenia niestandardowej klasy lub struktury, należy zastąpić <xref:System.Object.ToString%2A> metody w celu podania informacji o typie, aby kod klienta.</span><span class="sxs-lookup"><span data-stu-id="fa795-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="fa795-107">Aby uzyskać informacje o sposobie używania ciągów formatu i inne typy formatowania niestandardowych z `ToString` metody, zobacz [typy formatowania](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="fa795-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fa795-108">W przypadku podjęcia decyzji informacjach zapewnienie za pomocą tej metody, należy rozważyć, czy Twojej klasie lub strukturze będzie nigdy używana w kodzie niezaufanym.</span><span class="sxs-lookup"><span data-stu-id="fa795-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="fa795-109">Należy zachować ostrożność upewnić się, że nie udostępniają wszystkie informacje, które mogą być wykorzystywane przez złośliwy kod.</span><span class="sxs-lookup"><span data-stu-id="fa795-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a><span data-ttu-id="fa795-110">Aby przesłonić metodę ToString w Twojej klasie lub strukturze</span><span class="sxs-lookup"><span data-stu-id="fa795-110">To override the ToString method in your class or struct</span></span>  
  
1.  <span data-ttu-id="fa795-111">Deklarowanie `ToString` metody za pomocą następujących modyfikatorów i typ zwracany:</span><span class="sxs-lookup"><span data-stu-id="fa795-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  <span data-ttu-id="fa795-112">Zaimplementuj metodę, tak aby zwracało ciąg.</span><span class="sxs-lookup"><span data-stu-id="fa795-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="fa795-113">Poniższy przykład zwraca nazwę klasy oprócz danych określonej do konkretnego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="fa795-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     <span data-ttu-id="fa795-114">Możesz przetestować `ToString` metody, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fa795-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="fa795-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa795-115">See Also</span></span>  
 <xref:System.IFormattable>  
 [<span data-ttu-id="fa795-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fa795-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fa795-117">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="fa795-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="fa795-118">Ciągi</span><span class="sxs-lookup"><span data-stu-id="fa795-118">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="fa795-119">string</span><span class="sxs-lookup"><span data-stu-id="fa795-119">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
 [<span data-ttu-id="fa795-120">new</span><span class="sxs-lookup"><span data-stu-id="fa795-120">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="fa795-121">override</span><span class="sxs-lookup"><span data-stu-id="fa795-121">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="fa795-122">virtual</span><span class="sxs-lookup"><span data-stu-id="fa795-122">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="fa795-123">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="fa795-123">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
