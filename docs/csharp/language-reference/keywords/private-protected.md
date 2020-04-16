---
title: private protected - C# Reference
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 03fa90582d096919f2e6546fae2fde28e486fe41
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463053"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="b60dd-102">private protected (c# Reference)</span><span class="sxs-lookup"><span data-stu-id="b60dd-102">private protected (C# Reference)</span></span>

<span data-ttu-id="b60dd-103">Kombinacja `private protected` słów kluczowych jest modyfikatorem dostępu do członków.</span><span class="sxs-lookup"><span data-stu-id="b60dd-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="b60dd-104">Prywatny chroniony element członkowski jest dostępny dla typów pochodzących z klasy zawierającej, ale tylko w ramach jego zestawu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="b60dd-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="b60dd-105">Aby zapoznać `private protected` się z innymi modyfikatorami dostępu, zobacz [Poziomy ułatwień dostępu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b60dd-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b60dd-106">Modyfikator `private protected` dostępu jest prawidłowy w języku C# w wersji 7.2 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="b60dd-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="b60dd-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="b60dd-107">Example</span></span>

<span data-ttu-id="b60dd-108">Prywatny chroniony element członkowski klasy podstawowej jest dostępny z typów pochodnych w zestawie zawierającym tylko wtedy, gdy typ statyczny zmiennej jest typem klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b60dd-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="b60dd-109">Rozważmy na przykład następujący segment kodu:</span><span class="sxs-lookup"><span data-stu-id="b60dd-109">For example, consider the following code segment:</span></span>

```csharp
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

<span data-ttu-id="b60dd-110">W tym przykładzie `Assembly1.cs` `Assembly2.cs`znajdują się dwa pliki i .</span><span class="sxs-lookup"><span data-stu-id="b60dd-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="b60dd-111">Pierwszy plik zawiera publiczną `BaseClass`klasę podstawową i typ `DerivedClass1`pochodną.</span><span class="sxs-lookup"><span data-stu-id="b60dd-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="b60dd-112">`BaseClass`jest właścicielem prywatnego chronionego `myValue` `DerivedClass1` członka, który próbuje uzyskać dostęp na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="b60dd-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="b60dd-113">Pierwsza próba uzyskania `myValue` dostępu za `BaseClass` pośrednictwem wystąpienia spowoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="b60dd-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="b60dd-114">Jednak próba użycia go jako dziedziczonego `DerivedClass1` elementu członkowskiego w zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b60dd-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>

<span data-ttu-id="b60dd-115">W drugim pliku próba dostępu `myValue` jako dziedziczony `DerivedClass2` element członkowski spowoduje błąd, ponieważ jest dostępny tylko dla typów pochodnych w Assembly1.</span><span class="sxs-lookup"><span data-stu-id="b60dd-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="b60dd-116">Jeśli `Assembly1.cs` zawiera <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> tę `Assembly2`nazwy, klasa `DerivedClass1` pochodna `private protected` będzie miała `BaseClass`dostęp do elementów członkowskich zadeklarowanych w programie .</span><span class="sxs-lookup"><span data-stu-id="b60dd-116">If `Assembly1.cs` contains an <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> that names `Assembly2`, the derived class `DerivedClass1` will have access to `private protected` members declared in `BaseClass`.</span></span> <span data-ttu-id="b60dd-117">`InternalsVisibleTo`sprawia, że `private protected` elementy członkowskie są widoczne dla klas pochodnych w innych zestawach.</span><span class="sxs-lookup"><span data-stu-id="b60dd-117">`InternalsVisibleTo` makes `private protected` members visible to derived classes in other assemblies.</span></span>

<span data-ttu-id="b60dd-118">Struct elementów `private protected` członkowskich nie może być, ponieważ struktura nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="b60dd-118">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b60dd-119">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b60dd-119">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b60dd-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b60dd-120">See also</span></span>

- [<span data-ttu-id="b60dd-121">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="b60dd-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b60dd-122">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="b60dd-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b60dd-123">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b60dd-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b60dd-124">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="b60dd-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="b60dd-125">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="b60dd-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="b60dd-126">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="b60dd-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="b60dd-127">public</span><span class="sxs-lookup"><span data-stu-id="b60dd-127">public</span></span>](public.md)
- [<span data-ttu-id="b60dd-128">private</span><span class="sxs-lookup"><span data-stu-id="b60dd-128">private</span></span>](private.md)
- [<span data-ttu-id="b60dd-129">internal</span><span class="sxs-lookup"><span data-stu-id="b60dd-129">internal</span></span>](internal.md)
- <span data-ttu-id="b60dd-130">[Kwestie bezpieczeństwa wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b60dd-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
