---
title: "sealed (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords: sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8248b451f0431286fdaba3583fc2031eb6cdbcd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sealed-c-reference"></a><span data-ttu-id="6aa86-102">sealed (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6aa86-102">sealed (C# Reference)</span></span>
<span data-ttu-id="6aa86-103">Po zastosowaniu do klasy, `sealed` modyfikator uniemożliwia innym klasom dziedziczenie z tego.</span><span class="sxs-lookup"><span data-stu-id="6aa86-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="6aa86-104">W poniższym przykładzie klasa `B` dziedziczy z klasy `A`, ale klasa nie może dziedziczyć po klasie `B`.</span><span class="sxs-lookup"><span data-stu-id="6aa86-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>  
  
```  
class A {}      
sealed class B : A {}  
```  
  
 <span data-ttu-id="6aa86-105">Można również użyć `sealed` modyfikator metoda lub właściwość, która zastępuje metody wirtualnej lub w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="6aa86-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="6aa86-106">Dzięki temu można zezwolić klas pochodzi od klasy i uniemożliwić przesłanianie określonej wirtualnej metody lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="6aa86-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6aa86-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="6aa86-107">Example</span></span>  
 <span data-ttu-id="6aa86-108">W poniższym przykładzie `Z` dziedziczy `Y` , ale `Z` nie może przesłonić funkcji wirtualnej `F` zadeklarowanego w `X` i zapieczętowany w `Y`.</span><span class="sxs-lookup"><span data-stu-id="6aa86-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]  
  
 <span data-ttu-id="6aa86-109">Podczas definiowania nowej metody lub właściwości w klasie, można zapobiec klas pochodnych zastąpieniem przez nie deklarowanie je jako [wirtualnego](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="6aa86-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
 <span data-ttu-id="6aa86-110">Jest błędem [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md) modyfikator z klasy zapieczętowanej, ponieważ klasa abstrakcyjna muszą być dziedziczone przez klasy, która udostępnia implementację metody abstrakcyjne lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="6aa86-110">It is an error to use the [abstract](../../../csharp/language-reference/keywords/abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>  
  
 <span data-ttu-id="6aa86-111">Po zastosowaniu do metody lub właściwości, `sealed` modyfikator zawsze musi być używany z [zastąpienia](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="6aa86-111">When applied to a method or property, the `sealed` modifier must always be used with [override](../../../csharp/language-reference/keywords/override.md).</span></span>  
  
 <span data-ttu-id="6aa86-112">Ponieważ niejawnie są zapieczętowane struktury, nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="6aa86-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>  
  
 <span data-ttu-id="6aa86-113">Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="6aa86-113">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="6aa86-114">Aby uzyskać więcej przykładów, zobacz [abstrakcyjne i zapieczętowane klasy oraz członkowie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="6aa86-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6aa86-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="6aa86-115">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]  
  
 <span data-ttu-id="6aa86-116">W poprzednim przykładzie możesz spróbować dziedziczona z klasy zapieczętowanej przy użyciu następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="6aa86-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 <span data-ttu-id="6aa86-117">Wynik jest komunikat o błędzie:</span><span class="sxs-lookup"><span data-stu-id="6aa86-117">The result is an error message:</span></span>  
  
 `'MyDerivedC' cannot inherit from sealed class 'SealedClass'.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="6aa86-118">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6aa86-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="remarks"></a><span data-ttu-id="6aa86-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6aa86-119">Remarks</span></span>  
 <span data-ttu-id="6aa86-120">Aby ustalić, czy zapieczętować klasy, metody lub właściwości, zazwyczaj należy rozważyć następujące dwa punkty:</span><span class="sxs-lookup"><span data-stu-id="6aa86-120">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>  
  
-   <span data-ttu-id="6aa86-121">Potencjalnych korzyści, że wyprowadzanie klas może uzyskać za pośrednictwem możliwość dostosowania swojej klasy.</span><span class="sxs-lookup"><span data-stu-id="6aa86-121">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>  
  
-   <span data-ttu-id="6aa86-122">Ryzyko, że wyprowadzanie klas może zmodyfikować klas w taki sposób, że będzie już działać poprawnie lub oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="6aa86-122">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aa86-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6aa86-123">See Also</span></span>  
 [<span data-ttu-id="6aa86-124">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="6aa86-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6aa86-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6aa86-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6aa86-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6aa86-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6aa86-127">Klasy statyczne i statyczni członkowie klas</span><span class="sxs-lookup"><span data-stu-id="6aa86-127">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [<span data-ttu-id="6aa86-128">Klasy abstrakcyjne i zapieczętowane oraz członkowie klas</span><span class="sxs-lookup"><span data-stu-id="6aa86-128">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [<span data-ttu-id="6aa86-129">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="6aa86-129">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="6aa86-130">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="6aa86-130">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="6aa86-131">zastąpienie</span><span class="sxs-lookup"><span data-stu-id="6aa86-131">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="6aa86-132">wirtualny</span><span class="sxs-lookup"><span data-stu-id="6aa86-132">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)
