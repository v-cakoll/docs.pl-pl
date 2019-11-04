---
title: C# odwołanie wewnętrzne
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: f72866cafbf291310d88fc6f18a5a15dc77c621d
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422729"
---
# <a name="internal-c-reference"></a><span data-ttu-id="9b103-102">internal (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9b103-102">internal (C# Reference)</span></span>
<span data-ttu-id="9b103-103">Słowo kluczowe `internal` jest [modyfikatorem dostępu](./access-modifiers.md) dla typów i elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="9b103-103">The `internal` keyword is an [access modifier](./access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="9b103-104">Ta strona obejmuje `internal` dostępu.</span><span class="sxs-lookup"><span data-stu-id="9b103-104">This page covers `internal` access.</span></span> <span data-ttu-id="9b103-105">Słowo kluczowe `internal` jest również częścią modyfikatora dostępu [`protected internal`](./protected-internal.md) .</span><span class="sxs-lookup"><span data-stu-id="9b103-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="9b103-106">Typy wewnętrzne lub składowe są dostępne tylko w plikach w tym samym zestawie, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9b103-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="9b103-107">Aby uzyskać porównanie `internal` z innymi modyfikatorami dostępu, zobacz [poziomy ułatwień](./accessibility-levels.md) dostępu i [Modyfikatory dostęp](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="9b103-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](./accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="9b103-108">Aby uzyskać więcej informacji o zestawach, zobacz [zestawy w programie .NET](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="9b103-108">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="9b103-109">Typowym zastosowaniem dostępu wewnętrznego jest w programowaniu opartym na składnikach, ponieważ umożliwia ono grupom współdziałanie w sposób prywatny bez ujawniania pozostałej części kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b103-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="9b103-110">Na przykład struktura do tworzenia graficznych interfejsów użytkownika może zapewnić `Control` i `Form` klas, które współpracują z użytkownikami z dostępem wewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="9b103-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="9b103-111">Ponieważ te składowe są wewnętrzne, nie są one widoczne dla kodu, który używa struktury.</span><span class="sxs-lookup"><span data-stu-id="9b103-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="9b103-112">Wystąpił błąd podczas odwoływania się do typu lub elementu członkowskiego z dostępem wewnętrznym poza zestawem, w ramach którego został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="9b103-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b103-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="9b103-113">Example</span></span>  
 <span data-ttu-id="9b103-114">Ten przykład zawiera dwa pliki, `Assembly1.cs` i `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="9b103-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="9b103-115">Pierwszy plik zawiera wewnętrzną klasę bazową `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="9b103-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="9b103-116">W drugim pliku próba wystąpienia `BaseClass` spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="9b103-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
      var myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="9b103-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="9b103-117">Example</span></span>  
 <span data-ttu-id="9b103-118">W tym przykładzie należy użyć tych samych plików, które zostały użyte w przykładzie 1, i zmienić poziom dostępności `BaseClass` na `public`.</span><span class="sxs-lookup"><span data-stu-id="9b103-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="9b103-119">Zmień również poziom dostępności `intM` Członkowskich, aby `internal`.</span><span class="sxs-lookup"><span data-stu-id="9b103-119">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="9b103-120">W takim przypadku można utworzyć wystąpienie klasy, ale nie można uzyskać dostępu do wewnętrznego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9b103-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
      var myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="9b103-121">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9b103-121">C# Language Specification</span></span>  

<span data-ttu-id="9b103-122">Aby uzyskać więcej informacji, zobacz [zadeklarowane ułatwienia dostępu](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="9b103-122">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="9b103-123">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="9b103-123">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9b103-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b103-124">See also</span></span>

- [<span data-ttu-id="9b103-125">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="9b103-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9b103-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9b103-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9b103-127">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9b103-127">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="9b103-128">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="9b103-128">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="9b103-129">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="9b103-129">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="9b103-130">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="9b103-130">Modifiers</span></span>](index.md)
- [<span data-ttu-id="9b103-131">public</span><span class="sxs-lookup"><span data-stu-id="9b103-131">public</span></span>](./public.md)
- [<span data-ttu-id="9b103-132">private</span><span class="sxs-lookup"><span data-stu-id="9b103-132">private</span></span>](./private.md)
- [<span data-ttu-id="9b103-133">protected</span><span class="sxs-lookup"><span data-stu-id="9b103-133">protected</span></span>](./protected.md)
