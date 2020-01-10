---
title: zapieczętowany modyfikator- C# odwołanie
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 686afd5d9d0394bb1a802551b65083732599f384
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713108"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="31d8e-102">sealed (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="31d8e-102">sealed (C# Reference)</span></span>

<span data-ttu-id="31d8e-103">W przypadku zastosowania do klasy modyfikator `sealed` uniemożliwia innym klasom dziedziczenie z tego typu.</span><span class="sxs-lookup"><span data-stu-id="31d8e-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="31d8e-104">W poniższym przykładzie Klasa `B` dziedziczy po klasie `A`, ale żadna Klasa nie może dziedziczyć z klasy `B`.</span><span class="sxs-lookup"><span data-stu-id="31d8e-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>

```csharp
class A {}
sealed class B : A {}
```

<span data-ttu-id="31d8e-105">Można również użyć modyfikatora `sealed` dla metody lub właściwości, która zastępuje wirtualną metodę lub właściwość w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="31d8e-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="31d8e-106">Dzięki temu można zezwolić klasom na pochodną klasy i uniemożliwić im zastępowanie określonych metod lub właściwości wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="31d8e-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>

## <a name="example"></a><span data-ttu-id="31d8e-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="31d8e-107">Example</span></span>

<span data-ttu-id="31d8e-108">W poniższym przykładzie `Z` dziedziczy po `Y`, ale `Z` nie może przesłonić funkcji wirtualnej `F` zadeklarowanej w `X` i zapieczętowanej w `Y`.</span><span class="sxs-lookup"><span data-stu-id="31d8e-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

<span data-ttu-id="31d8e-109">Podczas definiowania nowych metod lub właściwości w klasie można zapobiegać występowaniu klas przez wyprowadzanie ich przez niezadeklarowanie ich jako [wirtualne](virtual.md).</span><span class="sxs-lookup"><span data-stu-id="31d8e-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](virtual.md).</span></span>

<span data-ttu-id="31d8e-110">Wystąpił błąd podczas używania modyfikatora [abstract](abstract.md) z klasą zapieczętowana, ponieważ Klasa abstrakcyjna musi być dziedziczona przez klasę, która dostarcza implementację metod abstrakcyjnych lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="31d8e-110">It is an error to use the [abstract](abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>

<span data-ttu-id="31d8e-111">W przypadku zastosowania do metody lub właściwości modyfikator `sealed` musi być zawsze używany z [zastępowaniem](override.md).</span><span class="sxs-lookup"><span data-stu-id="31d8e-111">When applied to a method or property, the `sealed` modifier must always be used with [override](override.md).</span></span>

<span data-ttu-id="31d8e-112">Ponieważ struktury są niejawnie zapieczętowane, nie można ich dziedziczyć.</span><span class="sxs-lookup"><span data-stu-id="31d8e-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>

<span data-ttu-id="31d8e-113">Aby uzyskać więcej informacji, zobacz [dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="31d8e-113">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="31d8e-114">Aby uzyskać więcej przykładów, zobacz [klasy abstrakcyjne i zapieczętowane oraz składowe klas](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="31d8e-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="31d8e-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="31d8e-115">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

<span data-ttu-id="31d8e-116">W poprzednim przykładzie można spróbować dziedziczyć z klasy zapieczętowanej przy użyciu następującej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="31d8e-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>

`class MyDerivedC: SealedClass {}   // Error`

<span data-ttu-id="31d8e-117">Wynik jest komunikatem o błędzie:</span><span class="sxs-lookup"><span data-stu-id="31d8e-117">The result is an error message:</span></span>

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a><span data-ttu-id="31d8e-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31d8e-118">Remarks</span></span>

<span data-ttu-id="31d8e-119">Aby określić, czy należy zapieczętować klasę, metodę lub właściwość, należy ogólnie wziąć pod uwagę następujące dwa punkty:</span><span class="sxs-lookup"><span data-stu-id="31d8e-119">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>

- <span data-ttu-id="31d8e-120">Potencjalne korzyści wynikające z używania klas mogą uzyskać możliwość dostosowania klasy.</span><span class="sxs-lookup"><span data-stu-id="31d8e-120">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>

- <span data-ttu-id="31d8e-121">Potencjalna Klasa może modyfikować klasy w taki sposób, że nie będą działać prawidłowo lub zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="31d8e-121">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="31d8e-122">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="31d8e-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="31d8e-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31d8e-123">See also</span></span>

- [<span data-ttu-id="31d8e-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="31d8e-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="31d8e-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="31d8e-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="31d8e-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="31d8e-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="31d8e-127">Klasy statyczne i statyczne elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="31d8e-127">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="31d8e-128">Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="31d8e-128">Abstract and Sealed Classes and Class Members</span></span>](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="31d8e-129">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="31d8e-129">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="31d8e-130">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="31d8e-130">Modifiers</span></span>](index.md)
- [<span data-ttu-id="31d8e-131">override</span><span class="sxs-lookup"><span data-stu-id="31d8e-131">override</span></span>](override.md)
- [<span data-ttu-id="31d8e-132">virtual</span><span class="sxs-lookup"><span data-stu-id="31d8e-132">virtual</span></span>](virtual.md)
