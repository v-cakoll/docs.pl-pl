---
title: Klasy — Przewodnik programowania w języku C#
description: Dowiedz się więcej o typach klas i sposobach ich tworzenia
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
Typ, który jest zdefiniowany jako [Klasa](../../language-reference/keywords/class.md) , jest *typem referencyjnym*. W czasie wykonywania, gdy deklarujesz zmienną typu referencyjnego, zmienna zawiera wartość [null](../../language-reference/keywords/null.md) , dopóki nie utworzysz jawnie instancji klasy przy użyciu operatora [New](../../language-reference/operators/new-operator.md) , lub przypiszesz do niego obiekt zgodnego typu, który mógł zostać utworzony w innym miejscu, jak pokazano w następującym przykładzie:

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

Gdy obiekt zostanie utworzony, wystarczająca ilość pamięci jest przydzielana na zarządzanym stosie dla tego konkretnego obiektu, a zmienna zawiera tylko odwołanie do lokalizacji wymienionego obiektu. Typy na stercie zarządzanej wymagają narzutu podczas przydzielania i kiedy są odzyskiwane przez funkcję automatycznego zarządzania pamięcią środowiska CLR, która jest znana jako *wyrzucanie elementów bezużytecznych*. Jednak wyrzucanie elementów bezużytecznych jest również wysoce zoptymalizowane i w większości scenariuszy nie tworzy problemu z wydajnością. Aby uzyskać więcej informacji dotyczących wyrzucania elementów bezużytecznych, zobacz [Automatyczne zarządzanie pamięcią i odzyskiwanie elementów bezużytecznych](../../../standard/garbage-collection/fundamentals.md)  
  
## <a name="declaring-classes"></a>Deklarowanie klas

 Klasy są deklarowane za pomocą słowa kluczowego [Class](../../language-reference/keywords/class.md) , po którym następuje unikatowy identyfikator, jak pokazano w następującym przykładzie:

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 `class`Słowo kluczowe jest poprzedzone poziomem dostępu. Ponieważ w tym przypadku jest używany [publiczny](../../language-reference/keywords/public.md) , każdy może utworzyć wystąpienia tej klasy. Nazwa klasy jest zgodna ze `class` słowem kluczowym. Nazwa klasy musi być prawidłową [nazwą identyfikatora](../inside-a-program/identifier-names.md)języka C#. Pozostała część definicji jest treścią klasy, w której zdefiniowane jest zachowanie i dane. Pola, właściwości, metody i zdarzenia w klasie są zbiorczo nazywane *elementami członkowskimi klas*.  
  
## <a name="creating-objects"></a>Tworzenie obiektów

Chociaż są czasami używane zamiennie, Klasa i obiekt są różne. Klasa definiuje typ obiektu, ale nie jest on samym obiektem. Obiekt jest konkretną jednostką opartą na klasie i jest czasami określany jako wystąpienie klasy.  
  
 Obiekty mogą być tworzone za pomocą [nowego](../../language-reference/operators/new-operator.md) słowa kluczowego, po którym następuje nazwa klasy, na której będzie oparty obiekt, na przykład:  

 ```csharp
 Customer object1 = new Customer();
 ```

 Po utworzeniu wystąpienia klasy odwołanie do obiektu jest przesyłane z powrotem do programisty. W poprzednim przykładzie, `object1` jest odwołaniem do obiektu, który jest oparty na `Customer` . To odwołanie odnosi się do nowego obiektu, ale nie zawiera samych danych obiektu. W rzeczywistości można utworzyć odwołanie do obiektu bez tworzenia obiektu w ogóle:  

```csharp
 Customer object2;
```

 Nie zalecamy tworzenia odwołań do obiektów, takich jak te, które nie odwołują się do obiektu, ponieważ próba uzyskania dostępu do obiektu za pomocą takiego odwołania zakończy się niepowodzeniem w czasie wykonywania. Takie odwołanie można jednak wykonać, aby odwołać się do obiektu, tworząc nowy obiekt lub przez przypisanie go do istniejącego obiektu, takiego jak:  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 Ten kod tworzy dwa odwołania do obiektów, które odwołują się do tego samego obiektu. W związku z tym wszelkie zmiany wprowadzone w obiekcie `object3` zostaną odzwierciedlone w kolejnych zastosowaniach `object4` . Ponieważ obiekty, które są oparte na klasach są określane przez odwołanie, klasy są znane jako typy referencyjne.  
  
## <a name="class-inheritance"></a>Dziedziczenie klas  

Klasy w pełni obsługują *dziedziczenie*, podstawową cechą programowania zorientowanego obiektowo. Podczas tworzenia klasy można dziedziczyć z dowolnego innego interfejsu lub klasy, która nie jest zdefiniowana jako [Sealed](../../language-reference/keywords/sealed.md), a inne klasy mogą dziedziczyć z klasy i zastępować metody wirtualne klas.

Dziedziczenie jest realizowane przy użyciu wartości *pochodnych*, co oznacza, że Klasa jest zadeklarowana przy użyciu *klasy bazowej* , z której dziedziczy dane i zachowanie. Klasa bazowa jest określana przez dołączenie dwukropka i nazwy klasy bazowej następującej po nazwie klasy pochodnej, w następujący sposób:  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

Gdy Klasa deklaruje klasę bazową, dziedziczy wszystkich elementów członkowskich klasy podstawowej, z wyjątkiem konstruktorów. Aby uzyskać więcej informacji, zobacz [dziedziczenie](inheritance.md).
  
W przeciwieństwie do języka C++, Klasa w języku C# może dziedziczyć bezpośrednio z jednej klasy bazowej. Jednak ponieważ klasa bazowa może sama dziedziczyć z innej klasy, Klasa może pośrednio dziedziczyć wiele klas bazowych. Ponadto Klasa może bezpośrednio zaimplementować więcej niż jeden interfejs. Aby uzyskać więcej informacji, zobacz [interfejsy](../interfaces/index.md).  
  
Klasa może być zadeklarowana jako [abstract](../../language-reference/keywords/abstract.md). Klasa abstrakcyjna zawiera metody abstrakcyjne z definicją podpisu, ale bez implementacji. Nie można utworzyć wystąpienia klas abstrakcyjnych. Mogą one być używane tylko przez klasy pochodne, które implementują metody abstrakcyjne. Z kolei Klasa [zapieczętowana](../../language-reference/keywords/sealed.md) nie zezwala innym klasom na ich wyprowadzanie. Aby uzyskać więcej informacji, zobacz [klasy abstrakcyjne i zapieczętowane oraz składowe klas](abstract-and-sealed-classes-and-class-members.md).  
  
Definicje klas można podzielić między różne pliki źródłowe. Aby uzyskać więcej informacji, zobacz [częściowe klasy i metody](partial-classes-and-methods.md).  
  
## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano klasę publiczną, która zawiera [Właściwość](auto-implemented-properties.md), czyli metodę i specjalną metodę o nazwie Konstruktor. Aby uzyskać więcej informacji, zobacz temat [Właściwości](properties.md), [metody](methods.md)i [konstruktory](constructors.md) . Wystąpienia klasy są następnie tworzone za pomocą `new` słowa kluczowego.  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)]
  
## <a name="c-language-specification"></a>Specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Programowanie zorientowane obiektowo](../concepts/object-oriented-programming.md)
- [Polimorfizm](polymorphism.md)
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
- [Elementy członkowskie](members.md)
- [Metody](methods.md)
- [Konstruktory](constructors.md)
- [Finalizatory](destructors.md)
- [Obiekty](objects.md)
