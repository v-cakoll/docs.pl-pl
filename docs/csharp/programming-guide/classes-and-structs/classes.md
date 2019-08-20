---
title: Klasy — C# Przewodnik programowania
ms.custom: seodec18
description: Dowiedz się więcej o typach klas i sposobach ich tworzenia
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 193446ff98edce3b7c078c6eeba07cf9acdadaf0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597176"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="585d2-103">Klasy (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="585d2-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="585d2-104">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="585d2-104">Reference types</span></span>  
<span data-ttu-id="585d2-105">Typ, który jest zdefiniowany jako [Klasa](../../language-reference/keywords/class.md) , jest *typem referencyjnym*.</span><span class="sxs-lookup"><span data-stu-id="585d2-105">A type that is defined as a [class](../../language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="585d2-106">W czasie wykonywania, gdy deklarujesz zmienną typu referencyjnego, zmienna zawiera wartość [null](../../language-reference/keywords/null.md) , dopóki nie utworzysz jawnie instancji klasy przy użyciu operatora [New](../../language-reference/operators/new-operator.md) , lub przypiszesz jej obiekt typu zgodnego, który mógł zostać utworzony w innym miejscu, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="585d2-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../language-reference/operators/new-operator.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="585d2-107">Gdy obiekt zostanie utworzony, wystarczająca ilość pamięci jest przydzielana na zarządzanym stosie dla tego konkretnego obiektu, a zmienna zawiera tylko odwołanie do lokalizacji wymienionego obiektu.</span><span class="sxs-lookup"><span data-stu-id="585d2-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="585d2-108">Typy na stercie zarządzanej wymagają narzutu podczas przydzielania i kiedy są odzyskiwane przez funkcję automatycznego zarządzania pamięcią środowiska CLR, która jest znana jako wyrzucanie *elementów*bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="585d2-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="585d2-109">Jednak wyrzucanie elementów bezużytecznych jest również wysoce zoptymalizowane i w większości scenariuszy nie tworzy problemu z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="585d2-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="585d2-110">Aby uzyskać więcej informacji dotyczących wyrzucania elementów bezużytecznych, zobacz [Automatyczne zarządzanie pamięcią i odzyskiwanie elementów](../../../standard/garbage-collection/gc.md)bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="585d2-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/gc.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="585d2-111">Deklarowanie klas</span><span class="sxs-lookup"><span data-stu-id="585d2-111">Declaring Classes</span></span>

 <span data-ttu-id="585d2-112">Klasy są deklarowane za pomocą słowa kluczowego [Class](../../language-reference/keywords/class.md) , po którym następuje unikatowy identyfikator, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="585d2-112">Classes are declared by using the [class](../../language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="585d2-113">`class` Słowo kluczowe jest poprzedzone poziomem dostępu.</span><span class="sxs-lookup"><span data-stu-id="585d2-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="585d2-114">Ponieważ w tym przypadku jest używany [publiczny](../../language-reference/keywords/public.md) , każdy może utworzyć wystąpienia tej klasy.</span><span class="sxs-lookup"><span data-stu-id="585d2-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="585d2-115">Nazwa klasy jest zgodna ze `class` słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="585d2-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="585d2-116">Nazwa klasy musi być prawidłową C# [nazwą identyfikatora](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="585d2-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="585d2-117">Pozostała część definicji jest treścią klasy, w której zdefiniowane jest zachowanie i dane.</span><span class="sxs-lookup"><span data-stu-id="585d2-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="585d2-118">Pola, właściwości, metody i zdarzenia w klasie są zbiorczo nazywane *elementami członkowskimi klas*.</span><span class="sxs-lookup"><span data-stu-id="585d2-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="585d2-119">Tworzenie obiektów</span><span class="sxs-lookup"><span data-stu-id="585d2-119">Creating objects</span></span>

<span data-ttu-id="585d2-120">Chociaż są czasami używane zamiennie, Klasa i obiekt są różne.</span><span class="sxs-lookup"><span data-stu-id="585d2-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="585d2-121">Klasa definiuje typ obiektu, ale nie jest on samym obiektem.</span><span class="sxs-lookup"><span data-stu-id="585d2-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="585d2-122">Obiekt jest konkretną jednostką opartą na klasie i jest czasami określany jako wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="585d2-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="585d2-123">Obiekty mogą być tworzone za pomocą [nowego](../../language-reference/operators/new-operator.md) słowa kluczowego, po którym następuje nazwa klasy, na której będzie oparty obiekt, na przykład:</span><span class="sxs-lookup"><span data-stu-id="585d2-123">Objects can be created by using the [new](../../language-reference/operators/new-operator.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="585d2-124">Po utworzeniu wystąpienia klasy odwołanie do obiektu jest przesyłane z powrotem do programisty.</span><span class="sxs-lookup"><span data-stu-id="585d2-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="585d2-125">W poprzednim przykładzie, `object1` jest odwołaniem do obiektu, który jest oparty na. `Customer`</span><span class="sxs-lookup"><span data-stu-id="585d2-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="585d2-126">To odwołanie odnosi się do nowego obiektu, ale nie zawiera samych danych obiektu.</span><span class="sxs-lookup"><span data-stu-id="585d2-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="585d2-127">W rzeczywistości można utworzyć odwołanie do obiektu bez tworzenia obiektu w ogóle:</span><span class="sxs-lookup"><span data-stu-id="585d2-127">In fact, you can create an object reference without creating an object at all:</span></span>  
 
```csharp
 Customer object2;
```
 
 <span data-ttu-id="585d2-128">Nie zalecamy tworzenia odwołań do obiektów, takich jak te, które nie odwołują się do obiektu, ponieważ próba uzyskania dostępu do obiektu za pomocą takiego odwołania zakończy się niepowodzeniem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="585d2-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="585d2-129">Takie odwołanie można jednak wykonać, aby odwołać się do obiektu, tworząc nowy obiekt lub przez przypisanie go do istniejącego obiektu, takiego jak:</span><span class="sxs-lookup"><span data-stu-id="585d2-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="585d2-130">Ten kod tworzy dwa odwołania do obiektów, które odwołują się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="585d2-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="585d2-131">W związku z `object3` `object4`tym wszelkie zmiany wprowadzone w obiekcie zostaną odzwierciedlone w kolejnych zastosowaniach.</span><span class="sxs-lookup"><span data-stu-id="585d2-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="585d2-132">Ponieważ obiekty, które są oparte na klasach są określane przez odwołanie, klasy są znane jako typy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="585d2-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="585d2-133">Dziedziczenie klas</span><span class="sxs-lookup"><span data-stu-id="585d2-133">Class inheritance</span></span>  

<span data-ttu-id="585d2-134">Klasy w pełniobsługują dziedziczenie, podstawową cechą programowania zorientowanego obiektowo.</span><span class="sxs-lookup"><span data-stu-id="585d2-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="585d2-135">Podczas tworzenia klasy można dziedziczyć z dowolnego innego interfejsu lub klasy, która nie jest zdefiniowana jako Sealed [](../../language-reference/keywords/sealed.md), a inne klasy mogą dziedziczyć z klasy i zastępować metody wirtualne klas.</span><span class="sxs-lookup"><span data-stu-id="585d2-135">When you create a class, you can inherit from any other interface or class that is not defined as [sealed](../../language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span>

<span data-ttu-id="585d2-136">Dziedziczenie jest realizowane przy użyciu wartości *pochodnych*, co oznacza, że Klasa jest zadeklarowana przy użyciu *klasy bazowej* , z której dziedziczy dane i zachowanie.</span><span class="sxs-lookup"><span data-stu-id="585d2-136">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="585d2-137">Klasa bazowa jest określana przez dołączenie dwukropka i nazwy klasy bazowej następującej po nazwie klasy pochodnej, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="585d2-137">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="585d2-138">Gdy Klasa deklaruje klasę bazową, dziedziczy wszystkich elementów członkowskich klasy podstawowej, z wyjątkiem konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="585d2-138">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="585d2-139">Aby uzyskać więcej informacji, [](inheritance.md)Zobacz dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="585d2-139">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="585d2-140">W przeciwieństwie C++do, Klasa C# w może dziedziczyć bezpośrednio z jednej klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="585d2-140">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="585d2-141">Jednak ponieważ klasa bazowa może sama dziedziczyć z innej klasy, Klasa może pośrednio dziedziczyć wiele klas bazowych.</span><span class="sxs-lookup"><span data-stu-id="585d2-141">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="585d2-142">Ponadto Klasa może bezpośrednio zaimplementować więcej niż jeden interfejs.</span><span class="sxs-lookup"><span data-stu-id="585d2-142">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="585d2-143">Więcej informacji znajdziesz w artykule [Interfejsy](../interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="585d2-143">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="585d2-144">Klasa może być zadeklarowana jako [abstract](../../language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="585d2-144">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="585d2-145">Klasa abstrakcyjna zawiera metody abstrakcyjne z definicją podpisu, ale bez implementacji.</span><span class="sxs-lookup"><span data-stu-id="585d2-145">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="585d2-146">Nie można utworzyć wystąpienia klas abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="585d2-146">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="585d2-147">Mogą one być używane tylko przez klasy pochodne, które implementują metody abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="585d2-147">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="585d2-148">Z kolei Klasa [zapieczętowana](../../language-reference/keywords/sealed.md) nie zezwala innym klasom na ich wyprowadzanie.</span><span class="sxs-lookup"><span data-stu-id="585d2-148">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="585d2-149">Aby uzyskać więcej informacji, zobacz [klasy abstrakcyjne i zapieczętowane oraz składowe klas](abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="585d2-149">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="585d2-150">Definicje klas można podzielić między różne pliki źródłowe.</span><span class="sxs-lookup"><span data-stu-id="585d2-150">Class definitions can be split between different source files.</span></span> <span data-ttu-id="585d2-151">Aby uzyskać więcej informacji, zobacz [częściowe klasy i metody](partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="585d2-151">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="585d2-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="585d2-152">Example</span></span>

<span data-ttu-id="585d2-153">W poniższym przykładzie zdefiniowano klasę publiczną, która zawiera [Właściwość](auto-implemented-properties.md), czyli metodę i specjalną metodę o nazwie Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="585d2-153">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="585d2-154">Aby uzyskać więcej informacji, zobacz temat [Właściwości](properties.md), [metody](methods.md)i [konstruktory](constructors.md) .</span><span class="sxs-lookup"><span data-stu-id="585d2-154">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="585d2-155">Wystąpienia klasy są następnie tworzone za pomocą `new` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="585d2-155">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a><span data-ttu-id="585d2-156">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="585d2-156">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="585d2-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="585d2-157">See also</span></span>

- [<span data-ttu-id="585d2-158">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="585d2-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="585d2-159">Programowanie zorientowane obiektowo</span><span class="sxs-lookup"><span data-stu-id="585d2-159">Object-Oriented Programming</span></span>](../concepts/object-oriented-programming.md)
- [<span data-ttu-id="585d2-160">Polimorfizm</span><span class="sxs-lookup"><span data-stu-id="585d2-160">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="585d2-161">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="585d2-161">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="585d2-162">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="585d2-162">Members</span></span>](members.md)
- [<span data-ttu-id="585d2-163">Metody</span><span class="sxs-lookup"><span data-stu-id="585d2-163">Methods</span></span>](methods.md)
- [<span data-ttu-id="585d2-164">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="585d2-164">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="585d2-165">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="585d2-165">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="585d2-166">Obiekty</span><span class="sxs-lookup"><span data-stu-id="585d2-166">Objects</span></span>](objects.md)
