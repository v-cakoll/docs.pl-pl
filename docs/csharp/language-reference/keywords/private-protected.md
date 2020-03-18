---
title: chronione prywatne — odwołanie do języka C#
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: a73d61712075cf24d2b94c505104df1fade629e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713212"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="9a5b4-102">chronione prywatne (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="9a5b4-102">private protected (C# Reference)</span></span>

<span data-ttu-id="9a5b4-103">Kombinacja `private protected` słów kluczowych jest modyfikatorem dostępu do elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="9a5b4-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="9a5b4-104">Prywatny chroniony element członkowski jest dostępny przez typy pochodzące z klasy zawierającej, ale tylko w jego zestawie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="9a5b4-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="9a5b4-105">Aby porównać `private protected` inne modyfikatory dostępu, zobacz [Poziomy ułatwień dostępu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9a5b4-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9a5b4-106">Modyfikator `private protected` dostępu jest prawidłowy w wersji C# 7.2 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="9a5b4-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="9a5b4-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a5b4-107">Example</span></span>

<span data-ttu-id="9a5b4-108">Prywatny chroniony element członkowski klasy podstawowej jest dostępny z typów pochodnych w jego zestawie zawierającym tylko wtedy, gdy typ statyczny zmiennej jest typem klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="9a5b4-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="9a5b4-109">Rozważmy na przykład następujący segment kodu:</span><span class="sxs-lookup"><span data-stu-id="9a5b4-109">For example, consider the following code segment:</span></span>  

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

<span data-ttu-id="9a5b4-110">W tym przykładzie `Assembly1.cs` znajdują `Assembly2.cs`się dwa pliki i .</span><span class="sxs-lookup"><span data-stu-id="9a5b4-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="9a5b4-111">Pierwszy plik zawiera publiczną `BaseClass`klasę podstawową i typ `DerivedClass1`pochodzący z niej.</span><span class="sxs-lookup"><span data-stu-id="9a5b4-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="9a5b4-112">`BaseClass`jest właścicielem prywatnego `myValue`chronionego `DerivedClass1` elementu członkowskiego, który próbuje uzyskać dostęp na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="9a5b4-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="9a5b4-113">Pierwsza próba dostępu `myValue` za pośrednictwem wystąpienia `BaseClass` spowoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="9a5b4-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="9a5b4-114">Jednak próba użycia go jako dziedziczonego `DerivedClass1` elementu członkowskiego w zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9a5b4-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="9a5b4-115">W drugim pliku próba dostępu `myValue` jako dziedziczony element członkowski `DerivedClass2` spowoduje błąd, ponieważ jest dostępny tylko przez typy pochodne w Assembly1.</span><span class="sxs-lookup"><span data-stu-id="9a5b4-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="9a5b4-116">Elementy członkowskie struktury `private protected` nie mogą być, ponieważ struktura nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="9a5b4-116">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="9a5b4-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9a5b4-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="9a5b4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a5b4-118">See also</span></span>

- [<span data-ttu-id="9a5b4-119">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="9a5b4-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9a5b4-120">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="9a5b4-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9a5b4-121">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9a5b4-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9a5b4-122">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="9a5b4-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="9a5b4-123">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="9a5b4-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="9a5b4-124">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="9a5b4-124">Modifiers</span></span>](index.md)
- [<span data-ttu-id="9a5b4-125">Publicznego</span><span class="sxs-lookup"><span data-stu-id="9a5b4-125">public</span></span>](public.md)
- [<span data-ttu-id="9a5b4-126">Prywatny</span><span class="sxs-lookup"><span data-stu-id="9a5b4-126">private</span></span>](private.md)
- [<span data-ttu-id="9a5b4-127">Wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="9a5b4-127">internal</span></span>](internal.md)
- <span data-ttu-id="9a5b4-128">[Obawy dotyczące zabezpieczeń wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9a5b4-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
