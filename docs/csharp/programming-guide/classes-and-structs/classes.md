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
# <a name="classes-c-programming-guide"></a>Klasy (Przewodnik programowania w języku C#)

## <a name="reference-types"></a>Typy odwołań  
Typ zdefiniowany jako [klasa](../../language-reference/keywords/class.md) jest *typem odwołania*. W czasie wykonywania podczas deklarowania zmiennej typu odwołania zmienna zawiera wartość [null,](../../language-reference/keywords/null.md) dopóki jawnie nie utworzysz wystąpienia klasy przy użyciu [nowego](../../language-reference/operators/new-operator.md) operatora lub nie przypiszesz jej obiektu zgodnego typu, który mógł zostać utworzony w innym miejscu, jak pokazano w poniższym przykładzie:

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

Po utworzeniu obiektu wystarczająca ilość pamięci jest przydzielana na zarządzanym stosie dla tego określonego obiektu, a zmienna zawiera tylko odwołanie do lokalizacji wspomnianego obiektu. Typy na zarządzanym stosie wymagają narzutów zarówno podczas ich przydzielania, jak i odzyskiwania przez funkcję automatycznego zarządzania pamięcią programu CLR, która jest nazywana *wyrzucaniem elementów bezużytecznych.* Jednak wyrzucanie elementów bezużytecznych jest również wysoce zoptymalizowane i w większości scenariuszy nie tworzy problemu z wydajnością. Aby uzyskać więcej informacji na temat wyrzucania elementów [bezużytecznych, zobacz Automatyczne zarządzanie pamięcią i wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/fundamentals.md).  
  
## <a name="declaring-classes"></a>Deklarowanie klas

 Klasy są deklarowane przy użyciu słowa kluczowego [klasy,](../../language-reference/keywords/class.md) po którym następuje unikatowy identyfikator, jak pokazano w poniższym przykładzie:

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 Słowo `class` kluczowe jest poprzedzone poziomem dostępu. Ponieważ [public](../../language-reference/keywords/public.md) jest używany w tym przypadku, każdy może utworzyć wystąpienia tej klasy. Nazwa klasy następuje `class` słowa kluczowego. Nazwa klasy musi być prawidłową [nazwą identyfikatora](../inside-a-program/identifier-names.md)Języka C#. Pozostała część definicji jest treścią klasy, w której zdefiniowano zachowanie i dane. Pola, właściwości, metody i zdarzenia w klasie są zbiorczo określane jako *elementy członkowskie klasy*.  
  
## <a name="creating-objects"></a>Tworzenie obiektów

Chociaż są one czasami używane zamiennie, klasa i obiekt są różne rzeczy. Klasa definiuje typ obiektu, ale nie jest obiektem. Obiekt jest konkretną jednostką opartą na klasie i jest czasami określany jako wystąpienie klasy.  
  
 Obiekty można tworzyć przy użyciu [nowego](../../language-reference/operators/new-operator.md) słowa kluczowego, po którym następuje nazwa klasy, na której będzie oparty obiekt, w ten sposób:  

 ```csharp
 Customer object1 = new Customer();
 ```

 Po utworzeniu wystąpienia klasy odwołanie do obiektu jest przekazywane z powrotem do programisty. W poprzednim przykładzie jest odwołaniem do obiektu, `object1` który jest oparty na `Customer`. To odwołanie odwołuje się do nowego obiektu, ale nie zawiera samych danych obiektu. W rzeczywistości można utworzyć odwołanie do obiektu bez tworzenia obiektu w ogóle:  

```csharp
 Customer object2;
```

 Nie zaleca się tworzenia odwołań do obiektów, takich jak ten, który nie odwołuje się do obiektu, ponieważ próba uzyskania dostępu do obiektu za pośrednictwem takiego odwołania zakończy się niepowodzeniem w czasie wykonywania. Jednak takie odwołanie można dokonać w celu odwoływania się do obiektu, tworząc nowy obiekt lub przypisując go do istniejącego obiektu, takiego jak ten:  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 Ten kod tworzy dwa odwołania do obiektów, które odwołują się do tego samego obiektu. W związku z tym wszelkie `object3` zmiany w obiekcie wprowadzone `object4`za pośrednictwem są odzwierciedlane w kolejnych zastosowaniach . Ponieważ obiekty, które są oparte na klasach są określane przez odwołanie, klasy są znane jako typy odwołań.  
  
## <a name="class-inheritance"></a>Dziedziczenie klas  

Klasy w pełni obsługują *dziedziczenie*, podstawową cechę programowania obiektowego. Podczas tworzenia klasy, można dziedziczyć z dowolnego innego interfejsu lub klasy, która nie jest zdefiniowana jako [zapieczętowane](../../language-reference/keywords/sealed.md), a inne klasy mogą dziedziczyć z klasy i zastąpić klasy metod wirtualnych.

Dziedziczenie odbywa się przy użyciu *wyprowadzania*, co oznacza, że klasa jest zadeklarowana przy użyciu *klasy podstawowej,* z której dziedziczy dane i zachowanie. Klasa podstawowa jest określona przez dołączenie dwukropka i nazwy klasy podstawowej po nazwie klasy pochodnej, w następujący sposób:  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

Gdy klasa deklaruje klasę podstawową, dziedziczy wszystkie elementy członkowskie klasy podstawowej z wyjątkiem konstruktorów. Aby uzyskać więcej informacji, zobacz [Dziedziczenie](inheritance.md).
  
W przeciwieństwie do języka C++, klasa w języku C# może dziedziczyć tylko bezpośrednio z jednej klasy podstawowej. Jednak ponieważ klasa podstawowa może sama dziedziczyć z innej klasy, klasa może pośrednio dziedziczyć wiele klas podstawowych. Ponadto klasa może bezpośrednio zaimplementować więcej niż jeden interfejs. Aby uzyskać więcej informacji, zobacz [Interfejsy](../interfaces/index.md).  
  
Klasę można zadeklarować [jako abstrakcyjną](../../language-reference/keywords/abstract.md). Klasa abstrakcyjna zawiera metody abstrakcyjne, które mają definicję podpisu, ale nie implementacji. Nie można utworzyć wystąpienia klas abstrakcyjnych. Mogą być używane tylko za pośrednictwem klas pochodnych, które implementują metody abstrakcyjne. Z drugiej [strony, zapieczętowana](../../language-reference/keywords/sealed.md) klasa nie zezwala na inne klasy, aby pochodzić od niego. Aby uzyskać więcej informacji, zobacz [Abstrakcyjne i zapieczętowane klasy i członkowie klasy](abstract-and-sealed-classes-and-class-members.md).  
  
Definicje klas można podzielić między różne pliki źródłowe. Aby uzyskać więcej informacji, zobacz [częściowe klasy i metody](partial-classes-and-methods.md).  
  
## <a name="example"></a>Przykład

Poniższy przykład definiuje klasę publiczną, która zawiera [właściwości zaimplementowane automatycznie,](auto-implemented-properties.md)metodę i metodę specjalną o nazwie konstruktora. Aby uzyskać więcej informacji, zobacz [właściwości](properties.md), [Metody](methods.md)i [Konstruktory](constructors.md) tematy. Wystąpienia klasy są następnie tworzone za pomocą `new` słowa kluczowego.  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)]
  
## <a name="c-language-specification"></a>Specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [C# Przewodnik programowania](../index.md)
- [Programowanie zorientowane obiektowo](../concepts/object-oriented-programming.md)
- [Polimorfizm](polymorphism.md)
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
- [Elementy członkowskie](members.md)
- [Metody](methods.md)
- [Konstruktorów](constructors.md)
- [Finalizatory](destructors.md)
- [Obiekty](objects.md)
