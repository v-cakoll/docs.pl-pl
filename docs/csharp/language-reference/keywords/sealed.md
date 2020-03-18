---
title: modyfikator zapieczętowany - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 686afd5d9d0394bb1a802551b65083732599f384
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713108"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="45257-102">sealed (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="45257-102">sealed (C# Reference)</span></span>

<span data-ttu-id="45257-103">Po zastosowaniu do klasy `sealed` modyfikator uniemożliwia innym klasom dziedziczenie z niego.</span><span class="sxs-lookup"><span data-stu-id="45257-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="45257-104">W poniższym przykładzie `B` klasa dziedziczy z klasy `A`, `B`ale żadna klasa nie może dziedziczyć z klasy .</span><span class="sxs-lookup"><span data-stu-id="45257-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>

```csharp
class A {}
sealed class B : A {}
```

<span data-ttu-id="45257-105">Można również użyć `sealed` modyfikatora na metodę lub właściwość, która zastępuje metodę wirtualną lub właściwość w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="45257-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="45257-106">Dzięki temu można zezwolić klas pochodzić z klasy i uniemożliwić im zastępowanie określonych metod wirtualnych lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="45257-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>

## <a name="example"></a><span data-ttu-id="45257-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="45257-107">Example</span></span>

<span data-ttu-id="45257-108">W poniższym `Z` przykładzie dziedziczy `Y` z, ale `F` `X` `Y` `Z` nie można zastąpić funkcji wirtualnej, która jest zadeklarowana i zapieczętowane w .</span><span class="sxs-lookup"><span data-stu-id="45257-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

<span data-ttu-id="45257-109">Podczas definiowania nowych metod lub właściwości w klasie, można zapobiec klas pochodnych z zastępowania ich, nie deklarując je jako [wirtualne](virtual.md).</span><span class="sxs-lookup"><span data-stu-id="45257-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](virtual.md).</span></span>

<span data-ttu-id="45257-110">Jest to błąd, aby użyć [modyfikatora abstrakcyjnego](abstract.md) z zapieczętowaną klasą, ponieważ klasa abstrakcyjna musi być dziedziczona przez klasę, która zapewnia implementację metod abstrakcyjnych lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="45257-110">It is an error to use the [abstract](abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>

<span data-ttu-id="45257-111">Po zastosowaniu do metody lub `sealed` właściwości, modyfikator musi być zawsze używany z [override](override.md).</span><span class="sxs-lookup"><span data-stu-id="45257-111">When applied to a method or property, the `sealed` modifier must always be used with [override](override.md).</span></span>

<span data-ttu-id="45257-112">Ponieważ struktury są niejawnie zapieczętowane, nie mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="45257-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>

<span data-ttu-id="45257-113">Aby uzyskać więcej informacji, zobacz [Dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="45257-113">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="45257-114">Aby uzyskać więcej przykładów, zobacz [klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klasy](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="45257-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="45257-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="45257-115">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

<span data-ttu-id="45257-116">W poprzednim przykładzie można spróbować dziedziczyć z zapieczętowanej klasy przy użyciu następującej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="45257-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>

`class MyDerivedC: SealedClass {}   // Error`

<span data-ttu-id="45257-117">Rezultatem jest komunikat o błędzie:</span><span class="sxs-lookup"><span data-stu-id="45257-117">The result is an error message:</span></span>

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a><span data-ttu-id="45257-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45257-118">Remarks</span></span>

<span data-ttu-id="45257-119">Aby ustalić, czy należy uszczelnić klasę, metodę lub właściwość, należy ogólnie rozważyć następujące dwa punkty:</span><span class="sxs-lookup"><span data-stu-id="45257-119">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>

- <span data-ttu-id="45257-120">Potencjalne korzyści, które klasy pochodne mogą uzyskać poprzez możliwość dostosowania klasy.</span><span class="sxs-lookup"><span data-stu-id="45257-120">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>

- <span data-ttu-id="45257-121">Potencjał, że klasy pochodne może modyfikować klas w taki sposób, że nie będą już działać poprawnie lub zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="45257-121">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="45257-122">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="45257-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="45257-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45257-123">See also</span></span>

- [<span data-ttu-id="45257-124">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="45257-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="45257-125">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="45257-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="45257-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="45257-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="45257-127">Klasy statyczne i statyczni członkowie klas</span><span class="sxs-lookup"><span data-stu-id="45257-127">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="45257-128">Klasy abstrakcyjne i zapieczętowane oraz członkowie klas</span><span class="sxs-lookup"><span data-stu-id="45257-128">Abstract and Sealed Classes and Class Members</span></span>](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="45257-129">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="45257-129">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="45257-130">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="45257-130">Modifiers</span></span>](index.md)
- [<span data-ttu-id="45257-131">override</span><span class="sxs-lookup"><span data-stu-id="45257-131">override</span></span>](override.md)
- [<span data-ttu-id="45257-132">virtual</span><span class="sxs-lookup"><span data-stu-id="45257-132">virtual</span></span>](virtual.md)
