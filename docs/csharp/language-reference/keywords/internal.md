---
title: wewnętrzne — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: aefb806b452452d4837b29b6ab11ce158ea412bc
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745424"
---
# <a name="internal-c-reference"></a><span data-ttu-id="0aa21-102">internal (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0aa21-102">internal (C# Reference)</span></span>
<span data-ttu-id="0aa21-103">`internal` Słowo kluczowe jest [modyfikator dostępu](../../../csharp/language-reference/keywords/access-modifiers.md) dla typów i elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="0aa21-103">The `internal` keyword is an [access modifier](../../../csharp/language-reference/keywords/access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="0aa21-104">Ta strona obejmuje `internal` dostępu.</span><span class="sxs-lookup"><span data-stu-id="0aa21-104">This page covers `internal` access.</span></span> <span data-ttu-id="0aa21-105">`internal` — Słowo kluczowe jest również częścią [ `protected internal` ](./protected-internal.md) modyfikator dostępu.</span><span class="sxs-lookup"><span data-stu-id="0aa21-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="0aa21-106">Typy wewnętrzne lub elementy członkowskie są dostępne tylko z poziomu plików w tym samym zestawie, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0aa21-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 <span data-ttu-id="0aa21-107">Porównanie `internal` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md) i [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="0aa21-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="0aa21-108">Aby uzyskać więcej informacji na temat zestawów, zobacz [zestawy na platformie .NET](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="0aa21-108">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="0aa21-109">Typowym zastosowaniem dostępu wewnętrznego jest opracowywany oparty na komponentach, ponieważ umożliwia grupy składników do współpracy w sposób prywatne bez ujawniania w pozostałej części kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0aa21-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="0aa21-110">Na przykład można dostarczyć umożliwiająca tworzenie graficznych interfejsów użytkownika `Control` i `Form` klas, które współpracują przy użyciu elementów członkowskich z dostępem do wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="0aa21-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="0aa21-111">Ponieważ te elementy członkowskie są wewnętrzne, nie są one widoczne do kodu, który używa programu framework.</span><span class="sxs-lookup"><span data-stu-id="0aa21-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="0aa21-112">Jest to błąd, aby odwoływać się do typu lub elementu członkowskiego z wewnętrznego dostępem spoza zestawu, w którym został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="0aa21-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0aa21-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="0aa21-113">Example</span></span>  
 <span data-ttu-id="0aa21-114">Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="0aa21-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="0aa21-115">Pierwszy plik zawiera wewnętrzny klasy bazowej `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="0aa21-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="0aa21-116">W drugim pliku, próba utworzenia wystąpienia `BaseClass` powoduje wygenerowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="0aa21-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="0aa21-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="0aa21-117">Example</span></span>  
 <span data-ttu-id="0aa21-118">W tym przykładzie należy użyć tych samych plików, które są używane w przykładzie 1 i zmienić poziom dostępności `BaseClass` do `public`.</span><span class="sxs-lookup"><span data-stu-id="0aa21-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="0aa21-119">Również zmienić poziom dostępności elementu członkowskiego `IntM` do `internal`.</span><span class="sxs-lookup"><span data-stu-id="0aa21-119">Also change the accessibility level of the member `IntM` to `internal`.</span></span> <span data-ttu-id="0aa21-120">W takim przypadku można utworzyć wystąpienia klasy, ale nie masz dostępu do wewnętrznego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0aa21-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="0aa21-121">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0aa21-121">C# Language Specification</span></span>  

<span data-ttu-id="0aa21-122">Aby uzyskać więcej informacji, zobacz [zadeklarowana dostępność](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0aa21-122">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="0aa21-123">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="0aa21-123">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0aa21-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0aa21-124">See also</span></span>

- [<span data-ttu-id="0aa21-125">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0aa21-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="0aa21-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0aa21-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0aa21-127">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0aa21-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="0aa21-128">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="0aa21-128">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="0aa21-129">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="0aa21-129">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)
- [<span data-ttu-id="0aa21-130">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="0aa21-130">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
- [<span data-ttu-id="0aa21-131">public</span><span class="sxs-lookup"><span data-stu-id="0aa21-131">public</span></span>](../../../csharp/language-reference/keywords/public.md)
- [<span data-ttu-id="0aa21-132">private</span><span class="sxs-lookup"><span data-stu-id="0aa21-132">private</span></span>](../../../csharp/language-reference/keywords/private.md)
- [<span data-ttu-id="0aa21-133">protected</span><span class="sxs-lookup"><span data-stu-id="0aa21-133">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
