---
title: zapieczętowane modyfikator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: babad3b07c5faea1381e6af13d3c713122de2332
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235179"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="d5ce5-102">sealed (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d5ce5-102">sealed (C# Reference)</span></span>

<span data-ttu-id="d5ce5-103">Po zastosowaniu do klasy, `sealed` modyfikator uniemożliwia innych klas z niego dziedziczącego.</span><span class="sxs-lookup"><span data-stu-id="d5ce5-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="d5ce5-104">W poniższym przykładzie klasa `B` dziedziczy z klasy `A`, ale klasa nie może dziedziczyć z klasy `B`.</span><span class="sxs-lookup"><span data-stu-id="d5ce5-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>

```csharp
class A {}
sealed class B : A {}
```

<span data-ttu-id="d5ce5-105">Można również użyć `sealed` modyfikator metoda lub właściwość, która zastępuje metodę wirtualną lub właściwości w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="d5ce5-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="d5ce5-106">Dzięki temu można umożliwić klasy pochodzi od klasy i uniemożliwić zastępowanie konkretnych metod wirtualnych lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5ce5-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>

## <a name="example"></a><span data-ttu-id="d5ce5-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5ce5-107">Example</span></span>

<span data-ttu-id="d5ce5-108">W poniższym przykładzie `Z` dziedziczy `Y` , ale `Z` nie może przesłonić funkcji wirtualnej `F` zadeklarowanego w `X` i zamkniętych w `Y`.</span><span class="sxs-lookup"><span data-stu-id="d5ce5-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

<span data-ttu-id="d5ce5-109">Definiując nowe metody lub właściwości w klasie, można zapobiec klas pochodnych zastępowania ich nie deklarując je jako [wirtualnego](virtual.md).</span><span class="sxs-lookup"><span data-stu-id="d5ce5-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](virtual.md).</span></span>

<span data-ttu-id="d5ce5-110">Jest to błąd, aby użyć [abstrakcyjne](abstract.md) modyfikator za pomocą klasy zapieczętowanej ponieważ klasy abstrakcyjnej muszą być dziedziczone przez klasę, która dostarcza implementację metody abstrakcyjne lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5ce5-110">It is an error to use the [abstract](abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>

<span data-ttu-id="d5ce5-111">Po zastosowaniu do metody lub właściwości, `sealed` modyfikator zawsze musi być używany z [zastąpienia](override.md).</span><span class="sxs-lookup"><span data-stu-id="d5ce5-111">When applied to a method or property, the `sealed` modifier must always be used with [override](override.md).</span></span>

<span data-ttu-id="d5ce5-112">Ponieważ struktury niejawnie są zamknięte, nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="d5ce5-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>

<span data-ttu-id="d5ce5-113">Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="d5ce5-113">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="d5ce5-114">Aby uzyskać więcej przykładów, zobacz [abstrakcyjnych i zapieczętowanych klas i składowych klasy](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="d5ce5-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="d5ce5-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5ce5-115">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

<span data-ttu-id="d5ce5-116">W poprzednim przykładzie możesz spróbować dziedziczą z klasy zapieczętowanej przy użyciu następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="d5ce5-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>

`class MyDerivedC: SealedClass {}   // Error`

<span data-ttu-id="d5ce5-117">Wynik jest komunikat o błędzie:</span><span class="sxs-lookup"><span data-stu-id="d5ce5-117">The result is an error message:</span></span>

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="c-language-specification"></a><span data-ttu-id="d5ce5-118">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d5ce5-118">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="remarks"></a><span data-ttu-id="d5ce5-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5ce5-119">Remarks</span></span>

<span data-ttu-id="d5ce5-120">Aby ustalić, czy ma być Zapieczętuj klasę, metodę lub właściwość, zazwyczaj należy rozważyć następujące dwa punkty:</span><span class="sxs-lookup"><span data-stu-id="d5ce5-120">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>

- <span data-ttu-id="d5ce5-121">Potencjalnych korzyści, że wyprowadzanie klas mogą uzyskać za pośrednictwem możliwość dostosowania swojej klasy.</span><span class="sxs-lookup"><span data-stu-id="d5ce5-121">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>

- <span data-ttu-id="d5ce5-122">Ryzyko, że wyprowadzanie klas można zmodyfikować klas w taki sposób, że będzie już działać poprawnie lub oczekuje.</span><span class="sxs-lookup"><span data-stu-id="d5ce5-122">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5ce5-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5ce5-123">See also</span></span>

- [<span data-ttu-id="d5ce5-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d5ce5-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d5ce5-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d5ce5-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d5ce5-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="d5ce5-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d5ce5-127">Klasy statyczne i statyczne elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="d5ce5-127">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="d5ce5-128">Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="d5ce5-128">Abstract and Sealed Classes and Class Members</span></span>](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="d5ce5-129">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="d5ce5-129">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="d5ce5-130">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="d5ce5-130">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="d5ce5-131">override</span><span class="sxs-lookup"><span data-stu-id="d5ce5-131">override</span></span>](override.md)
- [<span data-ttu-id="d5ce5-132">virtual</span><span class="sxs-lookup"><span data-stu-id="d5ce5-132">virtual</span></span>](virtual.md)