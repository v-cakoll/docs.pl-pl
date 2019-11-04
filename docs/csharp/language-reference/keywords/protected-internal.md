---
title: chronione C# odwołanie wewnętrzne
ms.custom: seodec18
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 6e5a4c6e63c2c05df54df6bed542eab3f43f9272
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422583"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="2e3c1-102">chroniona wewnętrznieC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="2e3c1-102">protected internal (C# Reference)</span></span>

<span data-ttu-id="2e3c1-103">Kombinacja słowa kluczowego `protected internal` jest modyfikatorem dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="2e3c1-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="2e3c1-104">Chroniony wewnętrzny element członkowski jest dostępny z bieżącego zestawu lub z typów, które pochodzą od klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="2e3c1-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="2e3c1-105">Aby uzyskać porównanie `protected internal` z innymi modyfikatorami dostępu, zobacz [poziomy dostępności](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2e3c1-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="2e3c1-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="2e3c1-106">Example</span></span>

<span data-ttu-id="2e3c1-107">Chroniona wewnętrzna składowa klasy bazowej jest dostępna z dowolnego typu w obrębie zawierającego go zestawu.</span><span class="sxs-lookup"><span data-stu-id="2e3c1-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="2e3c1-108">Jest ona również dostępna w klasie pochodnej znajdującej się w innym zestawie tylko wtedy, gdy dostęp odbywa się za pomocą zmiennej typu klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="2e3c1-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="2e3c1-109">Rozważmy na przykład następujący segment kodu:</span><span class="sxs-lookup"><span data-stu-id="2e3c1-109">For example, consider the following code segment:</span></span>

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
        var baseObject = new BaseClass();
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
        var baseObject = new BaseClass();
        var derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

<span data-ttu-id="2e3c1-110">Ten przykład zawiera dwa pliki, `Assembly1.cs` i `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="2e3c1-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="2e3c1-111">Pierwszy plik zawiera publiczną klasę bazową, `BaseClass`i inną klasę, `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="2e3c1-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="2e3c1-112">`BaseClass` jest właścicielem chronionego wewnętrznego elementu członkowskiego, `myValue`, do którego jest uzyskiwany dostęp za pomocą typu `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="2e3c1-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="2e3c1-113">W drugim pliku próba uzyskania dostępu do `myValue` za pomocą wystąpienia `BaseClass` spowoduje wystąpienie błędu, podczas gdy dostęp do tego elementu członkowskiego odbywa się za pomocą wystąpienia klasy pochodnej, `DerivedClass` powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="2e3c1-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="2e3c1-114">Elementy członkowskie struktury nie mogą być `protected internal`, ponieważ struktura nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="2e3c1-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2e3c1-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2e3c1-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2e3c1-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e3c1-116">See also</span></span>

- [<span data-ttu-id="2e3c1-117">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="2e3c1-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2e3c1-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2e3c1-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2e3c1-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="2e3c1-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2e3c1-120">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="2e3c1-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="2e3c1-121">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="2e3c1-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="2e3c1-122">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="2e3c1-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="2e3c1-123">public</span><span class="sxs-lookup"><span data-stu-id="2e3c1-123">public</span></span>](public.md)
- [<span data-ttu-id="2e3c1-124">private</span><span class="sxs-lookup"><span data-stu-id="2e3c1-124">private</span></span>](private.md)
- [<span data-ttu-id="2e3c1-125">internal</span><span class="sxs-lookup"><span data-stu-id="2e3c1-125">internal</span></span>](internal.md)
- <span data-ttu-id="2e3c1-126">[Zagadnienia dotyczące zabezpieczeń wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2e3c1-126">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
