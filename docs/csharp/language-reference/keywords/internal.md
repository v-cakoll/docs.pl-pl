---
title: internal (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: d2fcc19bb7bc6de373412e7728f3025647c0435d
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172675"
---
# <a name="internal-c-reference"></a><span data-ttu-id="323a4-102">internal (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="323a4-102">internal (C# Reference)</span></span>
<span data-ttu-id="323a4-103">`internal` — Słowo kluczowe jest [modyfikator dostępu](../../../csharp/language-reference/keywords/access-modifiers.md) typy i elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="323a4-103">The `internal` keyword is an [access modifier](../../../csharp/language-reference/keywords/access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="323a4-104">Ta strona zawiera `internal` dostępu.</span><span class="sxs-lookup"><span data-stu-id="323a4-104">This page covers `internal` access.</span></span> <span data-ttu-id="323a4-105">`internal` — Słowo kluczowe jest również częścią [ `protected internal` ](./protected-internal.md) modyfikator dostępu.</span><span class="sxs-lookup"><span data-stu-id="323a4-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="323a4-106">Wewnętrzne typy i elementy członkowskie są dostępne tylko w plikach w tym samym zestawie, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="323a4-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 <span data-ttu-id="323a4-107">Porównanie `internal` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md) i [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="323a4-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="323a4-108">Aby uzyskać więcej informacji na temat zestawów, zobacz [zestawy i Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span><span class="sxs-lookup"><span data-stu-id="323a4-108">For more information about assemblies, see [Assemblies and the Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
 <span data-ttu-id="323a4-109">Zazwyczaj wewnętrznego dostępu jest używane w programowania opartego na składnik ponieważ dzięki grupy składników do współpracy w sposób prywatnej bez narażania z resztą kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="323a4-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="323a4-110">Na przykład można podać struktura umożliwiająca tworzenie graficznych interfejsów użytkownika `Control` i `Form` klasy, które współpracują przy użyciu elementów członkowskich z dostępem do wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="323a4-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="323a4-111">Ponieważ te elementy członkowskie są wewnętrzne, ich nie są widoczne dla kodu, który używa programu framework.</span><span class="sxs-lookup"><span data-stu-id="323a4-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="323a4-112">Jest błąd, aby odwoływać się do typu lub elementu członkowskiego o wewnętrznej dostęp spoza zestawu, w którym został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="323a4-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="323a4-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="323a4-113">Example</span></span>  
 <span data-ttu-id="323a4-114">Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="323a4-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="323a4-115">Wewnętrzna klasa podstawowa zawiera pierwszy plik `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="323a4-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="323a4-116">W drugim pliku, próba utworzenia wystąpienia `BaseClass` spowoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="323a4-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="323a4-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="323a4-117">Example</span></span>  
 <span data-ttu-id="323a4-118">W tym przykładzie należy używać tych samych plików, które są używane w przykładzie 1 i zmienić poziom dostępności `BaseClass` do `public`.</span><span class="sxs-lookup"><span data-stu-id="323a4-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="323a4-119">Również zmienić poziom dostępności elementu członkowskiego `IntM` do `internal`.</span><span class="sxs-lookup"><span data-stu-id="323a4-119">Also change the accessibility level of the member `IntM` to `internal`.</span></span> <span data-ttu-id="323a4-120">W takim przypadku można utworzyć wystąpienia klasy, ale nie masz dostępu do wewnętrznego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="323a4-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="323a4-121">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="323a4-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="323a4-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="323a4-122">See Also</span></span>  
 [<span data-ttu-id="323a4-123">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="323a4-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="323a4-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="323a4-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="323a4-125">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="323a4-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="323a4-126">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="323a4-126">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="323a4-127">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="323a4-127">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="323a4-128">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="323a4-128">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="323a4-129">public</span><span class="sxs-lookup"><span data-stu-id="323a4-129">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="323a4-130">private</span><span class="sxs-lookup"><span data-stu-id="323a4-130">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="323a4-131">protected</span><span class="sxs-lookup"><span data-stu-id="323a4-131">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
