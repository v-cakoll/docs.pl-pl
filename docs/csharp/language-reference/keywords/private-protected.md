---
title: Private Protected C# — odwołanie
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: a73d61712075cf24d2b94c505104df1fade629e9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713212"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="c3cdc-102">prywatna chroniona (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="c3cdc-102">private protected (C# Reference)</span></span>

<span data-ttu-id="c3cdc-103">Kombinacja słowa kluczowego `private protected` jest modyfikatorem dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="c3cdc-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="c3cdc-104">Prywatna chroniona składowa jest dostępna dla typów pochodzących od klasy zawierającej, ale tylko w obrębie zawartego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c3cdc-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="c3cdc-105">Aby uzyskać porównanie `private protected` z innymi modyfikatorami dostępu, zobacz [poziomy dostępności](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c3cdc-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c3cdc-106">Modyfikator dostępu `private protected` jest prawidłowy w C# wersji 7,2 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="c3cdc-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="c3cdc-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3cdc-107">Example</span></span>

<span data-ttu-id="c3cdc-108">Prywatna chroniona składowa klasy bazowej jest dostępna z typów pochodnych w jego zestawie zawierającym tylko wtedy, gdy typ statyczny zmiennej jest typem klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="c3cdc-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="c3cdc-109">Rozważmy na przykład następujący segment kodu:</span><span class="sxs-lookup"><span data-stu-id="c3cdc-109">For example, consider the following code segment:</span></span>  

```csharp
// Assembly1.cs  
// Compile with: /target:library  
public class BaseClass
{
    private protected int myValue = 0;
}

public class DerivedClass1 : BaseClass
{
    void Access()
    {
        var baseObject = new BaseClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 5;  

        // OK, accessed through the current derived class instance
        myValue = 5;
    }
}
```

```csharp
// Assembly2.cs  
// Compile with: /reference:Assembly1.dll  
class DerivedClass2 : BaseClass
{
    void Access()
    {
        // Error CS0122, because myValue can only be
        // accessed by types in Assembly1
        // myValue = 10;
    }
}
```

<span data-ttu-id="c3cdc-110">Ten przykład zawiera dwa pliki, `Assembly1.cs` i `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="c3cdc-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="c3cdc-111">Pierwszy plik zawiera publiczną klasę bazową, `BaseClass`i typ pochodny, `DerivedClass1`.</span><span class="sxs-lookup"><span data-stu-id="c3cdc-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="c3cdc-112">`BaseClass` jest właścicielem prywatnej chronionej składowej, `myValue`, która `DerivedClass1` próbuje uzyskać dostęp na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="c3cdc-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="c3cdc-113">Pierwsza próba dostępu do `myValue` za pomocą wystąpienia `BaseClass` spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="c3cdc-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="c3cdc-114">Jednak próba użycia jej jako dziedziczonego elementu członkowskiego w `DerivedClass1` powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="c3cdc-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="c3cdc-115">W drugim pliku próba uzyskania dostępu do `myValue` jako dziedziczonego elementu członkowskiego `DerivedClass2` spowoduje wystąpienie błędu, ponieważ jest on dostępny tylko dla typów pochodnych w assembly1.</span><span class="sxs-lookup"><span data-stu-id="c3cdc-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="c3cdc-116">Elementy członkowskie struktury nie mogą być `private protected`, ponieważ struktura nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="c3cdc-116">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="c3cdc-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c3cdc-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="c3cdc-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3cdc-118">See also</span></span>

- [<span data-ttu-id="c3cdc-119">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c3cdc-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c3cdc-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c3cdc-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c3cdc-121">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c3cdc-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c3cdc-122">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="c3cdc-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="c3cdc-123">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="c3cdc-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="c3cdc-124">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="c3cdc-124">Modifiers</span></span>](index.md)
- [<span data-ttu-id="c3cdc-125">public</span><span class="sxs-lookup"><span data-stu-id="c3cdc-125">public</span></span>](public.md)
- [<span data-ttu-id="c3cdc-126">private</span><span class="sxs-lookup"><span data-stu-id="c3cdc-126">private</span></span>](private.md)
- [<span data-ttu-id="c3cdc-127">internal</span><span class="sxs-lookup"><span data-stu-id="c3cdc-127">internal</span></span>](internal.md)
- <span data-ttu-id="c3cdc-128">[Zagadnienia dotyczące zabezpieczeń wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c3cdc-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
