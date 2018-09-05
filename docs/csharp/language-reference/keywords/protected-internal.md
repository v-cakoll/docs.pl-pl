---
title: chronionych wewnętrznych (odwołanie w C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 1a305cb84989f12350e2e7cc28dd18f9d0c7ae5e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536414"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="8acee-102">chronionych wewnętrznych (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8acee-102">protected internal (C# Reference)</span></span>

<span data-ttu-id="8acee-103">`protected internal` Kombinacja słów kluczowych jest modyfikator dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="8acee-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="8acee-104">Chronionych wewnętrznych składowych jest możliwy z bieżącego zestawu lub typy pochodzące z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="8acee-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="8acee-105">Porównanie `protected internal` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8acee-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="8acee-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="8acee-106">Example</span></span>

<span data-ttu-id="8acee-107">Chronionych wewnętrznych elementu członkowskiego klasy bazowej jest dostępna z dowolnego typu w ramach własnego zestawu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="8acee-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="8acee-108">Jest również dostępna w klasie pochodnej znajduje się w innym zestawie, tylko wtedy, gdy dostęp odbywa się za pośrednictwem zmiennej o typie klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="8acee-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="8acee-109">Na przykład rozważmy następujący segment kodu:</span><span class="sxs-lookup"><span data-stu-id="8acee-109">For example, consider the following code segment:</span></span>

```csharp
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
   protected internal int myValue = 0;
}

class TestAccess
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```
<span data-ttu-id="8acee-110">Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="8acee-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="8acee-111">Pierwszy plik zawiera klasę bazową publicznych `BaseClass`oraz inną klasę `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="8acee-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="8acee-112">`BaseClass` jest właścicielem wewnętrzny elementu członkowskiego chronionego `myValue`, który jest dostępny po `TestAccess` typu.</span><span class="sxs-lookup"><span data-stu-id="8acee-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="8acee-113">W drugim pliku, próba uzyskania dostępu do `myValue` za pośrednictwem wystąpienia `BaseClass` wystąpi błąd, podczas dostępu do tego elementu członkowskiego przez wystąpienie klasy pochodnej, `DerivedClass` zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8acee-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="8acee-114">Składowe struktury nie mogą być `protected internal` ponieważ struktura nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="8acee-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8acee-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8acee-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8acee-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8acee-116">See also</span></span>

- [<span data-ttu-id="8acee-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8acee-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8acee-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8acee-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8acee-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="8acee-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8acee-120">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="8acee-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="8acee-121">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="8acee-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="8acee-122">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="8acee-122">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="8acee-123">public</span><span class="sxs-lookup"><span data-stu-id="8acee-123">public</span></span>](public.md)
- [<span data-ttu-id="8acee-124">private</span><span class="sxs-lookup"><span data-stu-id="8acee-124">private</span></span>](private.md)
- [<span data-ttu-id="8acee-125">internal</span><span class="sxs-lookup"><span data-stu-id="8acee-125">internal</span></span>](internal.md)
- <span data-ttu-id="8acee-126">[Kwestie bezpieczeństwa wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8acee-126">[Security concerns for internal virtual keywords](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>