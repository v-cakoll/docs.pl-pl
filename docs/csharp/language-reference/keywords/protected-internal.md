---
title: chronione wewnętrzne - C# Odwołanie
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 877df74b51fb859043171619f5687ecddb8409d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713199"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="7b998-102">chroniony wewnętrzny (odwołanie do Języka C#)</span><span class="sxs-lookup"><span data-stu-id="7b998-102">protected internal (C# Reference)</span></span>

<span data-ttu-id="7b998-103">Kombinacja `protected internal` słów kluczowych jest modyfikatorem dostępu do elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="7b998-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="7b998-104">Chroniony wewnętrzny element członkowski jest dostępny z bieżącego zestawu lub z typów, które są uzyskiwane z klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="7b998-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="7b998-105">Aby porównać `protected internal` inne modyfikatory dostępu, zobacz [Poziomy ułatwień dostępu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7b998-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="7b998-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b998-106">Example</span></span>

<span data-ttu-id="7b998-107">Chroniony wewnętrzny element członkowski klasy podstawowej jest dostępny z dowolnego typu w jego zestawie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="7b998-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="7b998-108">Jest również dostępny w klasie pochodnej znajduje się w innym zestawie tylko wtedy, gdy dostęp występuje za pośrednictwem zmiennej typu klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7b998-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="7b998-109">Rozważmy na przykład następujący segment kodu:</span><span class="sxs-lookup"><span data-stu-id="7b998-109">For example, consider the following code segment:</span></span>

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

<span data-ttu-id="7b998-110">W tym przykładzie `Assembly1.cs` znajdują `Assembly2.cs`się dwa pliki i .</span><span class="sxs-lookup"><span data-stu-id="7b998-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="7b998-111">Pierwszy plik zawiera publiczną `BaseClass`klasę podstawową, `TestAccess`a inna klasa .</span><span class="sxs-lookup"><span data-stu-id="7b998-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="7b998-112">`BaseClass`jest właścicielem chronionego `myValue`elementu wewnętrznego, `TestAccess` który jest dostępny przez typ.</span><span class="sxs-lookup"><span data-stu-id="7b998-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="7b998-113">W drugim pliku próba dostępu `myValue` za pośrednictwem wystąpienia `BaseClass` spowoduje błąd, podczas gdy dostęp do tego elementu `DerivedClass` członkowskiego za pośrednictwem wystąpienia klasy pochodnej, zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7b998-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="7b998-114">Elementy członkowskie struktury `protected internal` nie mogą być, ponieważ struktura nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="7b998-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7b998-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7b998-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7b998-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b998-116">See also</span></span>

- [<span data-ttu-id="7b998-117">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="7b998-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7b998-118">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="7b998-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7b998-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="7b998-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7b998-120">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="7b998-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="7b998-121">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="7b998-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="7b998-122">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="7b998-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="7b998-123">Publicznego</span><span class="sxs-lookup"><span data-stu-id="7b998-123">public</span></span>](public.md)
- [<span data-ttu-id="7b998-124">Prywatny</span><span class="sxs-lookup"><span data-stu-id="7b998-124">private</span></span>](private.md)
- [<span data-ttu-id="7b998-125">Wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="7b998-125">internal</span></span>](internal.md)
- <span data-ttu-id="7b998-126">[Obawy dotyczące zabezpieczeń wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7b998-126">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
