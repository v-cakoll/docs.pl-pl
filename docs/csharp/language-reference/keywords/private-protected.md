---
title: prywatny chroniony - C# odwołania
ms.custom: seodec18
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: c739dd0b5a5457a66c11962ed86bcd2ffbf811ab
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661676"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="fc915-102">prywatny chroniony (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="fc915-102">private protected (C# Reference)</span></span>

<span data-ttu-id="fc915-103">`private protected` Kombinacja słów kluczowych jest modyfikator dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="fc915-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="fc915-104">Prywatny chroniony element członkowski jest dostępna przez typy pochodne z zawierającego klasy, ale tylko w ramach własnego zestawu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="fc915-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="fc915-105">Porównanie `private protected` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="fc915-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="fc915-106">`private protected` Modyfikator dostępu jest nieprawidłowy w języku C# w wersji 7.2 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="fc915-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="fc915-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc915-107">Example</span></span>

<span data-ttu-id="fc915-108">Prywatne chronione elementy członkowskie klasy bazowej jest dostępna z typów pochodnych w jego zawierające zestaw, tylko wtedy, gdy typ klasy pochodnej zmiennej typu statycznego.</span><span class="sxs-lookup"><span data-stu-id="fc915-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="fc915-109">Na przykład rozważmy następujący segment kodu:</span><span class="sxs-lookup"><span data-stu-id="fc915-109">For example, consider the following code segment:</span></span>  

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

<span data-ttu-id="fc915-110">Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="fc915-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="fc915-111">Pierwszy plik zawiera klasę bazową publicznych `BaseClass`oraz typu pochodnego w `DerivedClass1`.</span><span class="sxs-lookup"><span data-stu-id="fc915-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="fc915-112">`BaseClass` jest właścicielem prywatnego elementu członkowskiego chronionego `myValue`, który `DerivedClass1` próbuje uzyskać dostęp na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="fc915-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="fc915-113">Pierwsza próba dostępu do `myValue` za pośrednictwem wystąpienia `BaseClass` powoduje wygenerowanie błędu.</span><span class="sxs-lookup"><span data-stu-id="fc915-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="fc915-114">Jednak można go użyć jako dziedziczonego członka w `DerivedClass1` zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="fc915-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="fc915-115">W drugim pliku, próba uzyskania dostępu do `myValue` jako dziedziczonego członka `DerivedClass2` generuje błąd, ponieważ nie jest tylko dostępny przez typy pochodne w Assembly1.</span><span class="sxs-lookup"><span data-stu-id="fc915-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="fc915-116">Składowe struktury nie mogą być `private protected` ponieważ struktura nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="fc915-116">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="fc915-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fc915-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="fc915-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc915-118">See also</span></span>

- [<span data-ttu-id="fc915-119">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fc915-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fc915-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fc915-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fc915-121">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="fc915-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fc915-122">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="fc915-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="fc915-123">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="fc915-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="fc915-124">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="fc915-124">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="fc915-125">public</span><span class="sxs-lookup"><span data-stu-id="fc915-125">public</span></span>](public.md)
- [<span data-ttu-id="fc915-126">private</span><span class="sxs-lookup"><span data-stu-id="fc915-126">private</span></span>](private.md)
- [<span data-ttu-id="fc915-127">internal</span><span class="sxs-lookup"><span data-stu-id="fc915-127">internal</span></span>](internal.md)
- <span data-ttu-id="fc915-128">[Kwestie bezpieczeństwa wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fc915-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
