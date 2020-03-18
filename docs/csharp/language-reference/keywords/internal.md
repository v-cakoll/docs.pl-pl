---
title: wewnętrzny - C# Referencje
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: e5a5ca18828b689241abbb6d80c5adc51efb073c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173604"
---
# <a name="internal-c-reference"></a><span data-ttu-id="2d433-102">internal (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="2d433-102">internal (C# Reference)</span></span>
<span data-ttu-id="2d433-103">Słowo `internal` kluczowe jest [modyfikatorem dostępu](./access-modifiers.md) dla typów i elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="2d433-103">The `internal` keyword is an [access modifier](./access-modifiers.md) for types and type members.</span></span>
  
 > <span data-ttu-id="2d433-104">Ta strona `internal` obejmuje dostęp.</span><span class="sxs-lookup"><span data-stu-id="2d433-104">This page covers `internal` access.</span></span> <span data-ttu-id="2d433-105">Słowo `internal` kluczowe jest również [`protected internal`](./protected-internal.md) częścią modyfikatora dostępu.</span><span class="sxs-lookup"><span data-stu-id="2d433-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="2d433-106">Typy wewnętrzne lub elementy członkowskie są dostępne tylko w plikach w tym samym zestawie, jak w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2d433-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="2d433-107">Aby porównać `internal` z innymi modyfikatorami dostępu, zobacz [Poziomy ułatwień dostępu](./accessibility-levels.md) i [modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="2d433-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](./accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="2d433-108">Aby uzyskać więcej informacji na temat zestawów, zobacz [Zestawy w .NET](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="2d433-108">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="2d433-109">Typowe użycie dostępu wewnętrznego jest w rozwoju opartym na składnikach, ponieważ umożliwia grupie składników współpracę w sposób prywatny bez narażenia na resztę kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2d433-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="2d433-110">Na przykład struktura do tworzenia graficznych interfejsów użytkownika może zapewnić `Control` i `Form` klas, które współpracują przy użyciu elementów członkowskich z dostępem wewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="2d433-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="2d433-111">Ponieważ te elementy członkowskie są wewnętrzne, nie są one udostępniane do kodu, który używa struktury.</span><span class="sxs-lookup"><span data-stu-id="2d433-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="2d433-112">Jest to błąd, aby odwołać się do typu lub elementu członkowskiego z dostępem wewnętrznym poza zestawem, w którym został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="2d433-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d433-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d433-113">Example</span></span>  
 <span data-ttu-id="2d433-114">W tym przykładzie `Assembly1.cs` znajdują `Assembly1_a.cs`się dwa pliki i .</span><span class="sxs-lookup"><span data-stu-id="2d433-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="2d433-115">Pierwszy plik zawiera wewnętrzną `BaseClass`klasę podstawową.</span><span class="sxs-lookup"><span data-stu-id="2d433-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="2d433-116">W drugim pliku próba wystąpienia spowoduje `BaseClass` wywołanie błędu.</span><span class="sxs-lookup"><span data-stu-id="2d433-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="2d433-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d433-117">Example</span></span>  
 <span data-ttu-id="2d433-118">W tym przykładzie użyj tych samych plików, które zostały `BaseClass` użyte `public`w przykładzie 1 i zmień poziom ułatwień dostępu na .</span><span class="sxs-lookup"><span data-stu-id="2d433-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="2d433-119">Zmień również poziom dostępności `intM` elementu `internal`członkowskiego na .</span><span class="sxs-lookup"><span data-stu-id="2d433-119">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="2d433-120">W takim przypadku można utworzyć wystąpienia klasy, ale nie można uzyskać dostępu do elementu członkowskiego wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="2d433-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="2d433-121">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2d433-121">C# Language Specification</span></span>  

<span data-ttu-id="2d433-122">Aby uzyskać więcej informacji, zobacz [Zadeklarowana dostępność](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="2d433-122">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="2d433-123">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="2d433-123">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2d433-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d433-124">See also</span></span>

- [<span data-ttu-id="2d433-125">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="2d433-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2d433-126">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="2d433-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2d433-127">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="2d433-127">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="2d433-128">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="2d433-128">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="2d433-129">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="2d433-129">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="2d433-130">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="2d433-130">Modifiers</span></span>](index.md)
- [<span data-ttu-id="2d433-131">Publicznego</span><span class="sxs-lookup"><span data-stu-id="2d433-131">public</span></span>](./public.md)
- [<span data-ttu-id="2d433-132">Prywatny</span><span class="sxs-lookup"><span data-stu-id="2d433-132">private</span></span>](./private.md)
- [<span data-ttu-id="2d433-133">protected</span><span class="sxs-lookup"><span data-stu-id="2d433-133">protected</span></span>](./protected.md)
