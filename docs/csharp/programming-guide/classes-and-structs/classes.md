---
title: Klasy — C# przewodnik programowania
ms.custom: seodec18
description: Dowiedz się więcej o typach klasy i jak je utworzyć
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 614b70562954fee99c6de3e66b54bbdd1134f553
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242295"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="c7690-103">Klasy (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c7690-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="c7690-104">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="c7690-104">Reference types</span></span>  
<span data-ttu-id="c7690-105">Typ, który jest zdefiniowany jako [klasy](../../../csharp/language-reference/keywords/class.md) jest *odwołania do typu*.</span><span class="sxs-lookup"><span data-stu-id="c7690-105">A type that is defined as a [class](../../../csharp/language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="c7690-106">W czasie wykonywania, kiedy Deklarujesz zmienną typu odwołania, zmienna zawiera wartość [null](../../../csharp/language-reference/keywords/null.md) aż jawnie tworzone jest wystąpienie klasy za pomocą [nowe](../../../csharp/language-reference/keywords/new.md) operatora, lub obiekt niezgodny typ, który mógł zostać utworzony w innych miejscach, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c7690-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../../csharp/language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../../csharp/language-reference/keywords/new.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="c7690-107">Po utworzeniu obiektu wystarczającej ilości pamięć jest alokowane na zarządzanym stosie dla tego określonego obiektu, a zmienna zawiera tylko odwołanie do lokalizacji obiektu wymienionych.</span><span class="sxs-lookup"><span data-stu-id="c7690-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="c7690-108">Typy na zarządzanym stosie wymagają narzutu zarówno kiedy są alokowane oraz kiedy są odbierane przez funkcjonalność zarządzania pamięcią automatyczną CLR, który jest znany jako *wyrzucania elementów bezużytecznych*.</span><span class="sxs-lookup"><span data-stu-id="c7690-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="c7690-109">Jednak wyrzucanie elementów bezużytecznych jest również bardzo dobrze zoptymalizowane i w większości scenariuszy nie powoduje problemów z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="c7690-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="c7690-110">Aby uzyskać więcej informacji dotyczących wyrzucania elementów bezużytecznych, zobacz [pamięcią automatyczną zarządzania i wyrzucania elementów kolekcji](../../../standard/garbage-collection/gc.md).</span><span class="sxs-lookup"><span data-stu-id="c7690-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/gc.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="c7690-111">Deklarowanie klas</span><span class="sxs-lookup"><span data-stu-id="c7690-111">Declaring Classes</span></span>

 <span data-ttu-id="c7690-112">Klasy są deklarowane przy użyciu [klasy](../../../csharp/language-reference/keywords/class.md) — słowo kluczowe, a następnie za pomocą unikatowego identyfikatora, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c7690-112">Classes are declared by using the [class](../../../csharp/language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="c7690-113">`class` — Słowo kluczowe jest poprzedzony przez poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="c7690-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="c7690-114">Ponieważ [publicznych](../../language-reference/keywords/public.md) jest używany w tym przypadku każdy może utworzyć wystąpienia tej klasy.</span><span class="sxs-lookup"><span data-stu-id="c7690-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="c7690-115">Następuje nazwa klasy `class` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="c7690-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="c7690-116">Nazwa klasy musi być prawidłową C# [nazwa identyfikatora](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="c7690-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="c7690-117">W pozostałej części definicji jest treści klasy, gdzie są zdefiniowane zachowanie i dane.</span><span class="sxs-lookup"><span data-stu-id="c7690-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="c7690-118">Pola, właściwości, metody i zdarzenia dla klasy, są nazywane zbiorczo *elementy członkowskie klasy*.</span><span class="sxs-lookup"><span data-stu-id="c7690-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="c7690-119">Tworzenie obiektów</span><span class="sxs-lookup"><span data-stu-id="c7690-119">Creating objects</span></span>

<span data-ttu-id="c7690-120">Chociaż czasami są używane zamiennie, klasy i obiektu są różne.</span><span class="sxs-lookup"><span data-stu-id="c7690-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="c7690-121">Klasa określa typ obiektu, ale nie jest sam obiekt.</span><span class="sxs-lookup"><span data-stu-id="c7690-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="c7690-122">Obiekt jest jednostką konkretnych na podstawie klasy i jest czasami określane jako wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="c7690-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="c7690-123">Obiekty mogą być tworzone za pomocą [nowe](../../language-reference/keywords/new.md) — słowo kluczowe następuje nazwa klasy, która obiekt będzie zależeć od, podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="c7690-123">Objects can be created by using the [new](../../language-reference/keywords/new.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="c7690-124">Po utworzeniu wystąpienia klasy odwołania do obiektu jest przekazywany do programisty należy.</span><span class="sxs-lookup"><span data-stu-id="c7690-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="c7690-125">W poprzednim przykładzie `object1` jest odwołaniem do obiektu, który jest oparty na `Customer`.</span><span class="sxs-lookup"><span data-stu-id="c7690-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="c7690-126">Ta dokumentacja odnosi się do nowego obiektu, ale nie zawiera danych obiektu.</span><span class="sxs-lookup"><span data-stu-id="c7690-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="c7690-127">W rzeczywistości można utworzyć odwołanie do obiektu, bez tworzenia obiektu w ogóle:</span><span class="sxs-lookup"><span data-stu-id="c7690-127">In fact, you can create an object reference without creating an object at all:</span></span>  
 
```csharp
 Customer object2;
```
 
 <span data-ttu-id="c7690-128">Nie zaleca się utworzenie odwołania do obiektu taką jak ta, które nie odwołują się do obiektu, ponieważ próbuje uzyskać dostęp do obiektu poprzez odniesienie zakończy się niepowodzeniem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c7690-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="c7690-129">Jednak takie odwołanie może się do odwoływania się do obiektu, albo przez utworzenie nowego obiektu, albo, przypisując go do istniejącego obiektu, takie jak to:</span><span class="sxs-lookup"><span data-stu-id="c7690-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="c7690-130">Ten kod tworzy dwa odwołania do obiektu odnoszą się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c7690-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="c7690-131">W związku z tym, zmiany wprowadzone w obiekcie za pośrednictwem `object3` są odzwierciedlane w kolejnych zastosowań `object4`.</span><span class="sxs-lookup"><span data-stu-id="c7690-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="c7690-132">Ponieważ obiekty, które są oparte na klasach są określane przez odwołanie, klas są określane jako typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="c7690-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="c7690-133">Dziedziczenie klas</span><span class="sxs-lookup"><span data-stu-id="c7690-133">Class inheritance</span></span>  

<span data-ttu-id="c7690-134">Klasy w pełni obsługiwać *dziedziczenia*, podstawowe charakterystyka programowanie zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="c7690-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="c7690-135">Kiedy tworzysz klasę, możesz dziedziczyć od innego interfejsu lub klasy, która nie jest zdefiniowana jako [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md), a inne klasy mogą dziedziczyć od Twojej klasy i zastępują metody wirtualne klasy.</span><span class="sxs-lookup"><span data-stu-id="c7690-135">When you create a class, you can inherit from any other interface or class that is not defined as [sealed](../../../csharp/language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span>

<span data-ttu-id="c7690-136">Dziedziczenie odbywa się za pomocą *pochodnym*, która oznacza, że klasa jest zadeklarowana za pomocą *klasy bazowej* z którego dziedziczy dane i zachowania.</span><span class="sxs-lookup"><span data-stu-id="c7690-136">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="c7690-137">Klasa podstawowa jest określona przez dołączenie dwukropek i nazwę klasy bazowej, po nazwie klasy pochodnej, takich jak to:</span><span class="sxs-lookup"><span data-stu-id="c7690-137">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="c7690-138">Klasa deklaruje klasę bazową, dziedziczy wszystkich członków klasy podstawowej, z wyjątkiem konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="c7690-138">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="c7690-139">Aby uzyskać więcej informacji, zobacz [dziedziczenia](inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="c7690-139">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="c7690-140">W przeciwieństwie do języka C++ klasy w języku C# tylko bezpośrednio może dziedziczyć z jednej klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c7690-140">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="c7690-141">Jednak ponieważ sam podstawowej klasy mogą dziedziczyć z innej klasy, klasy mogą pośrednio dziedziczyć wielu klas bazowych.</span><span class="sxs-lookup"><span data-stu-id="c7690-141">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="c7690-142">Ponadto klasy można bezpośrednio zaimplementować więcej niż jednego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c7690-142">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="c7690-143">Więcej informacji znajdziesz w artykule [Interfejsy](../interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="c7690-143">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="c7690-144">Klasy mogą być deklarowane [abstrakcyjne](../../language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="c7690-144">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="c7690-145">Abstrakcyjna klasa zawiera metody abstrakcyjne, które mają definicji podpisu, ale nie implementacji.</span><span class="sxs-lookup"><span data-stu-id="c7690-145">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="c7690-146">Nie można utworzyć wystąpienia klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="c7690-146">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="c7690-147">One należy używać tylko przez klasy pochodne, które implementują metody abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="c7690-147">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="c7690-148">Z drugiej strony [zapieczętowanego](../../language-reference/keywords/sealed.md) klasy nie zezwala na innych klas dziedziczyć po nim.</span><span class="sxs-lookup"><span data-stu-id="c7690-148">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="c7690-149">Aby uzyskać więcej informacji, zobacz [abstrakcyjnych i zapieczętowanych klas i składowych klasy](abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="c7690-149">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="c7690-150">Definicje klas może zostać podzielony między plikami z innego źródła.</span><span class="sxs-lookup"><span data-stu-id="c7690-150">Class definitions can be split between different source files.</span></span> <span data-ttu-id="c7690-151">Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="c7690-151">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7690-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="c7690-152">Example</span></span>

<span data-ttu-id="c7690-153">W poniższym przykładzie zdefiniowano Klasa publiczna, która zawiera [automatycznie implementowana właściwość](auto-implemented-properties.md), metody i specjalnych metodę o nazwie konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c7690-153">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="c7690-154">Aby uzyskać więcej informacji, zobacz [właściwości](properties.md), [metody](methods.md), i [konstruktory](constructors.md) tematów.</span><span class="sxs-lookup"><span data-stu-id="c7690-154">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="c7690-155">Wystąpienia klasy następnie są tworzone za pomocą `new` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="c7690-155">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a><span data-ttu-id="c7690-156">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c7690-156">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c7690-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7690-157">See Also</span></span>

- [<span data-ttu-id="c7690-158">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c7690-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c7690-159">Programowanie zorientowane obiektowo</span><span class="sxs-lookup"><span data-stu-id="c7690-159">Object-Oriented Programming</span></span>](../concepts/object-oriented-programming.md)
- [<span data-ttu-id="c7690-160">Polimorfizm</span><span class="sxs-lookup"><span data-stu-id="c7690-160">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="c7690-161">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="c7690-161">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="c7690-162">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c7690-162">Members</span></span>](members.md)
- [<span data-ttu-id="c7690-163">Metody</span><span class="sxs-lookup"><span data-stu-id="c7690-163">Methods</span></span>](methods.md)
- [<span data-ttu-id="c7690-164">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="c7690-164">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="c7690-165">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="c7690-165">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="c7690-166">Obiekty</span><span class="sxs-lookup"><span data-stu-id="c7690-166">Objects</span></span>](objects.md)
