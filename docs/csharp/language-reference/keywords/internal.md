---
title: internal (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 54ec003683953b53dedf8885a41350daf5338f83
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523364"
---
# <a name="internal-c-reference"></a><span data-ttu-id="88ee8-102">internal (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="88ee8-102">internal (C# Reference)</span></span>
<span data-ttu-id="88ee8-103">`internal` Słowo kluczowe jest [modyfikator dostępu](../../../csharp/language-reference/keywords/access-modifiers.md) dla typów i elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="88ee8-103">The `internal` keyword is an [access modifier](../../../csharp/language-reference/keywords/access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="88ee8-104">Ta strona obejmuje `internal` dostępu.</span><span class="sxs-lookup"><span data-stu-id="88ee8-104">This page covers `internal` access.</span></span> <span data-ttu-id="88ee8-105">`internal` — Słowo kluczowe jest również częścią [ `protected internal` ](./protected-internal.md) modyfikator dostępu.</span><span class="sxs-lookup"><span data-stu-id="88ee8-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="88ee8-106">Typy wewnętrzne lub elementy członkowskie są dostępne tylko z poziomu plików w tym samym zestawie, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="88ee8-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 <span data-ttu-id="88ee8-107">Porównanie `internal` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md) i [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="88ee8-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="88ee8-108">Aby uzyskać więcej informacji na temat zestawów, zobacz [zestawy i Globalna pamięć podręczna zestawów](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span><span class="sxs-lookup"><span data-stu-id="88ee8-108">For more information about assemblies, see [Assemblies and the Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
 <span data-ttu-id="88ee8-109">Typowym zastosowaniem dostępu wewnętrznego jest opracowywany oparty na komponentach, ponieważ umożliwia grupy składników do współpracy w sposób prywatne bez ujawniania w pozostałej części kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="88ee8-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="88ee8-110">Na przykład można dostarczyć umożliwiająca tworzenie graficznych interfejsów użytkownika `Control` i `Form` klas, które współpracują przy użyciu elementów członkowskich z dostępem do wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="88ee8-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="88ee8-111">Ponieważ te elementy członkowskie są wewnętrzne, nie są one widoczne do kodu, który używa programu framework.</span><span class="sxs-lookup"><span data-stu-id="88ee8-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="88ee8-112">Jest to błąd, aby odwoływać się do typu lub elementu członkowskiego z wewnętrznego dostępem spoza zestawu, w którym został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="88ee8-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88ee8-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="88ee8-113">Example</span></span>  
 <span data-ttu-id="88ee8-114">Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="88ee8-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="88ee8-115">Pierwszy plik zawiera wewnętrzny klasy bazowej `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="88ee8-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="88ee8-116">W drugim pliku, próba utworzenia wystąpienia `BaseClass` powoduje wygenerowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="88ee8-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="88ee8-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="88ee8-117">Example</span></span>  
 <span data-ttu-id="88ee8-118">W tym przykładzie należy użyć tych samych plików, które są używane w przykładzie 1 i zmienić poziom dostępności `BaseClass` do `public`.</span><span class="sxs-lookup"><span data-stu-id="88ee8-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="88ee8-119">Również zmienić poziom dostępności elementu członkowskiego `IntM` do `internal`.</span><span class="sxs-lookup"><span data-stu-id="88ee8-119">Also change the accessibility level of the member `IntM` to `internal`.</span></span> <span data-ttu-id="88ee8-120">W takim przypadku można utworzyć wystąpienia klasy, ale nie masz dostępu do wewnętrznego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="88ee8-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
// Compile with: /reference:Assembly2.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="88ee8-121">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="88ee8-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="88ee8-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88ee8-122">See Also</span></span>

- [<span data-ttu-id="88ee8-123">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="88ee8-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="88ee8-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="88ee8-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="88ee8-125">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="88ee8-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="88ee8-126">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="88ee8-126">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [<span data-ttu-id="88ee8-127">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="88ee8-127">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [<span data-ttu-id="88ee8-128">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="88ee8-128">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="88ee8-129">public</span><span class="sxs-lookup"><span data-stu-id="88ee8-129">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
- [<span data-ttu-id="88ee8-130">private</span><span class="sxs-lookup"><span data-stu-id="88ee8-130">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
- [<span data-ttu-id="88ee8-131">protected</span><span class="sxs-lookup"><span data-stu-id="88ee8-131">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
