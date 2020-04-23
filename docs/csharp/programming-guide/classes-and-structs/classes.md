---
title: Klasy - Przewodnik programowania C#
description: Dowiedz się więcej o typach klas i o tym, jak je tworzyć
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: d726ab3a882d2e6913fa69c7b82f1d6db78dd47d
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102050"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="8074b-103">Klasy (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="8074b-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="8074b-104">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="8074b-104">Reference types</span></span>  
<span data-ttu-id="8074b-105">Typ zdefiniowany jako [klasa](../../language-reference/keywords/class.md) jest *typem odwołania*.</span><span class="sxs-lookup"><span data-stu-id="8074b-105">A type that is defined as a [class](../../language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="8074b-106">W czasie wykonywania podczas deklarowania zmiennej typu odwołania zmienna zawiera wartość [null,](../../language-reference/keywords/null.md) dopóki jawnie nie utworzysz wystąpienia klasy przy użyciu [nowego](../../language-reference/operators/new-operator.md) operatora lub nie przypiszesz jej obiektu zgodnego typu, który mógł zostać utworzony w innym miejscu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8074b-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../language-reference/operators/new-operator.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="8074b-107">Po utworzeniu obiektu wystarczająca ilość pamięci jest przydzielana na zarządzanym stosie dla tego określonego obiektu, a zmienna zawiera tylko odwołanie do lokalizacji wspomnianego obiektu.</span><span class="sxs-lookup"><span data-stu-id="8074b-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="8074b-108">Typy na zarządzanym stosie wymagają narzutów zarówno podczas ich przydzielania, jak i odzyskiwania przez funkcję automatycznego zarządzania pamięcią programu CLR, która jest nazywana *wyrzucaniem elementów bezużytecznych.*</span><span class="sxs-lookup"><span data-stu-id="8074b-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="8074b-109">Jednak wyrzucanie elementów bezużytecznych jest również wysoce zoptymalizowane i w większości scenariuszy nie tworzy problemu z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="8074b-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="8074b-110">Aby uzyskać więcej informacji na temat wyrzucania elementów [bezużytecznych, zobacz Automatyczne zarządzanie pamięcią i wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/fundamentals.md).</span><span class="sxs-lookup"><span data-stu-id="8074b-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/fundamentals.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="8074b-111">Deklarowanie klas</span><span class="sxs-lookup"><span data-stu-id="8074b-111">Declaring Classes</span></span>

 <span data-ttu-id="8074b-112">Klasy są deklarowane przy użyciu słowa kluczowego [klasy,](../../language-reference/keywords/class.md) po którym następuje unikatowy identyfikator, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8074b-112">Classes are declared by using the [class](../../language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="8074b-113">Słowo `class` kluczowe jest poprzedzone poziomem dostępu.</span><span class="sxs-lookup"><span data-stu-id="8074b-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="8074b-114">Ponieważ [public](../../language-reference/keywords/public.md) jest używany w tym przypadku, każdy może utworzyć wystąpienia tej klasy.</span><span class="sxs-lookup"><span data-stu-id="8074b-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="8074b-115">Nazwa klasy następuje `class` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="8074b-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="8074b-116">Nazwa klasy musi być prawidłową [nazwą identyfikatora](../inside-a-program/identifier-names.md)Języka C#.</span><span class="sxs-lookup"><span data-stu-id="8074b-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="8074b-117">Pozostała część definicji jest treścią klasy, w której zdefiniowano zachowanie i dane.</span><span class="sxs-lookup"><span data-stu-id="8074b-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="8074b-118">Pola, właściwości, metody i zdarzenia w klasie są zbiorczo określane jako *elementy członkowskie klasy*.</span><span class="sxs-lookup"><span data-stu-id="8074b-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="8074b-119">Tworzenie obiektów</span><span class="sxs-lookup"><span data-stu-id="8074b-119">Creating objects</span></span>

<span data-ttu-id="8074b-120">Chociaż są one czasami używane zamiennie, klasa i obiekt są różne rzeczy.</span><span class="sxs-lookup"><span data-stu-id="8074b-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="8074b-121">Klasa definiuje typ obiektu, ale nie jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="8074b-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="8074b-122">Obiekt jest konkretną jednostką opartą na klasie i jest czasami określany jako wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="8074b-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="8074b-123">Obiekty można tworzyć przy użyciu [nowego](../../language-reference/operators/new-operator.md) słowa kluczowego, po którym następuje nazwa klasy, na której będzie oparty obiekt, w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="8074b-123">Objects can be created by using the [new](../../language-reference/operators/new-operator.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="8074b-124">Po utworzeniu wystąpienia klasy odwołanie do obiektu jest przekazywane z powrotem do programisty.</span><span class="sxs-lookup"><span data-stu-id="8074b-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="8074b-125">W poprzednim przykładzie jest odwołaniem do obiektu, `object1` który jest oparty na `Customer`.</span><span class="sxs-lookup"><span data-stu-id="8074b-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="8074b-126">To odwołanie odwołuje się do nowego obiektu, ale nie zawiera samych danych obiektu.</span><span class="sxs-lookup"><span data-stu-id="8074b-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="8074b-127">W rzeczywistości można utworzyć odwołanie do obiektu bez tworzenia obiektu w ogóle:</span><span class="sxs-lookup"><span data-stu-id="8074b-127">In fact, you can create an object reference without creating an object at all:</span></span>  

```csharp
 Customer object2;
```

 <span data-ttu-id="8074b-128">Nie zaleca się tworzenia odwołań do obiektów, takich jak ten, który nie odwołuje się do obiektu, ponieważ próba uzyskania dostępu do obiektu za pośrednictwem takiego odwołania zakończy się niepowodzeniem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8074b-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="8074b-129">Jednak takie odwołanie można dokonać w celu odwoływania się do obiektu, tworząc nowy obiekt lub przypisując go do istniejącego obiektu, takiego jak ten:</span><span class="sxs-lookup"><span data-stu-id="8074b-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="8074b-130">Ten kod tworzy dwa odwołania do obiektów, które odwołują się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="8074b-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="8074b-131">W związku z tym wszelkie `object3` zmiany w obiekcie wprowadzone `object4`za pośrednictwem są odzwierciedlane w kolejnych zastosowaniach .</span><span class="sxs-lookup"><span data-stu-id="8074b-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="8074b-132">Ponieważ obiekty, które są oparte na klasach są określane przez odwołanie, klasy są znane jako typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="8074b-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="8074b-133">Dziedziczenie klas</span><span class="sxs-lookup"><span data-stu-id="8074b-133">Class inheritance</span></span>  

<span data-ttu-id="8074b-134">Klasy w pełni obsługują *dziedziczenie*, podstawową cechę programowania obiektowego.</span><span class="sxs-lookup"><span data-stu-id="8074b-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="8074b-135">Podczas tworzenia klasy, można dziedziczyć z dowolnego innego interfejsu lub klasy, która nie jest zdefiniowana jako [zapieczętowane](../../language-reference/keywords/sealed.md), a inne klasy mogą dziedziczyć z klasy i zastąpić klasy metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="8074b-135">When you create a class, you can inherit from any other interface or class that is not defined as [sealed](../../language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span>

<span data-ttu-id="8074b-136">Dziedziczenie odbywa się przy użyciu *wyprowadzania*, co oznacza, że klasa jest zadeklarowana przy użyciu *klasy podstawowej,* z której dziedziczy dane i zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8074b-136">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="8074b-137">Klasa podstawowa jest określona przez dołączenie dwukropka i nazwy klasy podstawowej po nazwie klasy pochodnej, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8074b-137">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="8074b-138">Gdy klasa deklaruje klasę podstawową, dziedziczy wszystkie elementy członkowskie klasy podstawowej z wyjątkiem konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="8074b-138">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="8074b-139">Aby uzyskać więcej informacji, zobacz [Dziedziczenie](inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="8074b-139">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="8074b-140">W przeciwieństwie do języka C++, klasa w języku C# może dziedziczyć tylko bezpośrednio z jednej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="8074b-140">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="8074b-141">Jednak ponieważ klasa podstawowa może sama dziedziczyć z innej klasy, klasa może pośrednio dziedziczyć wiele klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="8074b-141">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="8074b-142">Ponadto klasa może bezpośrednio zaimplementować więcej niż jeden interfejs.</span><span class="sxs-lookup"><span data-stu-id="8074b-142">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="8074b-143">Aby uzyskać więcej informacji, zobacz [Interfejsy](../interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="8074b-143">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="8074b-144">Klasę można zadeklarować [jako abstrakcyjną](../../language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="8074b-144">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="8074b-145">Klasa abstrakcyjna zawiera metody abstrakcyjne, które mają definicję podpisu, ale nie implementacji.</span><span class="sxs-lookup"><span data-stu-id="8074b-145">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="8074b-146">Nie można utworzyć wystąpienia klas abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="8074b-146">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="8074b-147">Mogą być używane tylko za pośrednictwem klas pochodnych, które implementują metody abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="8074b-147">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="8074b-148">Z drugiej [strony, zapieczętowana](../../language-reference/keywords/sealed.md) klasa nie zezwala na inne klasy, aby pochodzić od niego.</span><span class="sxs-lookup"><span data-stu-id="8074b-148">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="8074b-149">Aby uzyskać więcej informacji, zobacz [Abstrakcyjne i zapieczętowane klasy i członkowie klasy](abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="8074b-149">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="8074b-150">Definicje klas można podzielić między różne pliki źródłowe.</span><span class="sxs-lookup"><span data-stu-id="8074b-150">Class definitions can be split between different source files.</span></span> <span data-ttu-id="8074b-151">Aby uzyskać więcej informacji, zobacz [częściowe klasy i metody](partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="8074b-151">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8074b-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="8074b-152">Example</span></span>

<span data-ttu-id="8074b-153">Poniższy przykład definiuje klasę publiczną, która zawiera [właściwości zaimplementowane automatycznie,](auto-implemented-properties.md)metodę i metodę specjalną o nazwie konstruktora.</span><span class="sxs-lookup"><span data-stu-id="8074b-153">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="8074b-154">Aby uzyskać więcej informacji, zobacz [właściwości](properties.md), [Metody](methods.md)i [Konstruktory](constructors.md) tematy.</span><span class="sxs-lookup"><span data-stu-id="8074b-154">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="8074b-155">Wystąpienia klasy są następnie tworzone za pomocą `new` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="8074b-155">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="8074b-156">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8074b-156">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8074b-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8074b-157">See also</span></span>

- [<span data-ttu-id="8074b-158">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="8074b-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8074b-159">Programowanie zorientowane obiektowo</span><span class="sxs-lookup"><span data-stu-id="8074b-159">Object-Oriented Programming</span></span>](../concepts/object-oriented-programming.md)
- [<span data-ttu-id="8074b-160">Polimorfizm</span><span class="sxs-lookup"><span data-stu-id="8074b-160">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="8074b-161">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="8074b-161">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="8074b-162">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8074b-162">Members</span></span>](members.md)
- [<span data-ttu-id="8074b-163">Metody</span><span class="sxs-lookup"><span data-stu-id="8074b-163">Methods</span></span>](methods.md)
- [<span data-ttu-id="8074b-164">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="8074b-164">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="8074b-165">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="8074b-165">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="8074b-166">Obiekty</span><span class="sxs-lookup"><span data-stu-id="8074b-166">Objects</span></span>](objects.md)
