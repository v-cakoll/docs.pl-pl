---
title: 'Porady: przesłanianie metody ToString (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: b047efb9215675b8c3dfb75438a6dbbc4e6f92d0
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084176"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="69da3-102">Porady: przesłanianie metody ToString (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="69da3-102">How to: Override the ToString Method (C# Programming Guide)</span></span>
<span data-ttu-id="69da3-103">Każdej klasy lub struktury w języku C# dziedziczy niejawnie <xref:System.Object> klasy.</span><span class="sxs-lookup"><span data-stu-id="69da3-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="69da3-104">W związku z tym, każdy obiekt w języku C# pobiera <xref:System.Object.ToString%2A> metody, która zwraca reprezentację ciągu tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="69da3-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="69da3-105">Na przykład, wszystkie zmienne typu `int` mają `ToString` metody, która pozwala na zwrócenie ich zawartość jako ciąg:</span><span class="sxs-lookup"><span data-stu-id="69da3-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 <span data-ttu-id="69da3-106">Podczas tworzenia niestandardowej klasy lub struktury, należy zastąpić <xref:System.Object.ToString%2A> metody w celu zapewnienia informacji na temat danego typu kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="69da3-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="69da3-107">Aby uzyskać informacje o sposobie używania ciągów formatu oraz inne rodzaje niestandardowe formatowanie przy użyciu `ToString` metody, zobacz [typy formatowania](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="69da3-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="69da3-108">Gdy zdecydujesz, jakie informacje, aby zapewnić za pośrednictwem tej metody, należy rozważyć, czy swojej klasy lub struktury nigdy nie będzie służyć przez niezaufany kod.</span><span class="sxs-lookup"><span data-stu-id="69da3-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="69da3-109">Uważaj upewnić się, nie podano żadnych informacji, które mogą zostać wykorzystane przez złośliwego kodu.</span><span class="sxs-lookup"><span data-stu-id="69da3-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a><span data-ttu-id="69da3-110">Aby przesłonięcie metody ToString w swojej klasie lub strukturze</span><span class="sxs-lookup"><span data-stu-id="69da3-110">To override the ToString method in your class or struct</span></span>  
  
1.  <span data-ttu-id="69da3-111">Zadeklaruj `ToString` następujące Modyfikatory oraz zwracany typ metody:</span><span class="sxs-lookup"><span data-stu-id="69da3-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  <span data-ttu-id="69da3-112">Implementowanie metoda zwraca ciąg.</span><span class="sxs-lookup"><span data-stu-id="69da3-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="69da3-113">Poniższy przykład zwraca nazwę klasy, oprócz danych określonej do konkretnego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="69da3-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     <span data-ttu-id="69da3-114">Możesz przetestować `ToString` metody, jak pokazano w poniższym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="69da3-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="69da3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69da3-115">See Also</span></span>

- <xref:System.IFormattable>  
- [<span data-ttu-id="69da3-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="69da3-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="69da3-117">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="69da3-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="69da3-118">Ciągi</span><span class="sxs-lookup"><span data-stu-id="69da3-118">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
- [<span data-ttu-id="69da3-119">string</span><span class="sxs-lookup"><span data-stu-id="69da3-119">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
- [<span data-ttu-id="69da3-120">new</span><span class="sxs-lookup"><span data-stu-id="69da3-120">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
- [<span data-ttu-id="69da3-121">override</span><span class="sxs-lookup"><span data-stu-id="69da3-121">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
- [<span data-ttu-id="69da3-122">virtual</span><span class="sxs-lookup"><span data-stu-id="69da3-122">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
- [<span data-ttu-id="69da3-123">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="69da3-123">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
