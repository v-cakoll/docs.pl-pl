---
title: Klasy — C# przewodnik programowania
ms.custom: seodec18
description: Dowiedz się więcej o typach klasy i jak je utworzyć
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: ad19099242a3bedbb7283219dfd7733db13231ec
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398589"
---
# <a name="classes-c-programming-guide"></a>Klasy (Przewodnik programowania w języku C#)

## <a name="reference-types"></a>Typy odwołań  
Typ, który jest zdefiniowany jako [klasy](../../../csharp/language-reference/keywords/class.md) jest *odwołania do typu*. W czasie wykonywania, kiedy Deklarujesz zmienną typu odwołania, zmienna zawiera wartość [null](../../../csharp/language-reference/keywords/null.md) aż jawnie tworzone jest wystąpienie klasy za pomocą [nowe](../../../csharp/language-reference/operators/new-operator.md) operatora, lub obiekt niezgodny typ, który mógł zostać utworzony w innych miejscach, jak pokazano w poniższym przykładzie:

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

Po utworzeniu obiektu wystarczającej ilości pamięć jest alokowane na zarządzanym stosie dla tego określonego obiektu, a zmienna zawiera tylko odwołanie do lokalizacji obiektu wymienionych. Typy na zarządzanym stosie wymagają narzutu zarówno kiedy są alokowane oraz kiedy są odbierane przez funkcjonalność zarządzania pamięcią automatyczną CLR, który jest znany jako *wyrzucania elementów bezużytecznych*. Jednak wyrzucanie elementów bezużytecznych jest również bardzo dobrze zoptymalizowane i w większości scenariuszy nie powoduje problemów z wydajnością. Aby uzyskać więcej informacji dotyczących wyrzucania elementów bezużytecznych, zobacz [pamięcią automatyczną zarządzania i wyrzucania elementów kolekcji](../../../standard/garbage-collection/gc.md).  
  
## <a name="declaring-classes"></a>Deklarowanie klas

 Klasy są deklarowane przy użyciu [klasy](../../../csharp/language-reference/keywords/class.md) — słowo kluczowe, a następnie za pomocą unikatowego identyfikatora, jak pokazano w poniższym przykładzie:

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 `class` — Słowo kluczowe jest poprzedzony przez poziom dostępu. Ponieważ [publicznych](../../language-reference/keywords/public.md) jest używany w tym przypadku każdy może utworzyć wystąpienia tej klasy. Następuje nazwa klasy `class` — słowo kluczowe. Nazwa klasy musi być prawidłową C# [nazwa identyfikatora](../inside-a-program/identifier-names.md). W pozostałej części definicji jest treści klasy, gdzie są zdefiniowane zachowanie i dane. Pola, właściwości, metody i zdarzenia dla klasy, są nazywane zbiorczo *elementy członkowskie klasy*.  
  
## <a name="creating-objects"></a>Tworzenie obiektów

Chociaż czasami są używane zamiennie, klasy i obiektu są różne. Klasa określa typ obiektu, ale nie jest sam obiekt. Obiekt jest jednostką konkretnych na podstawie klasy i jest czasami określane jako wystąpienia klasy.  
  
 Obiekty mogą być tworzone za pomocą [nowe](../../language-reference/operators/new-operator.md) — słowo kluczowe następuje nazwa klasy, która obiekt będzie zależeć od, podobnie do następującego:  

 ```csharp
 Customer object1 = new Customer();
 ```

 Po utworzeniu wystąpienia klasy odwołania do obiektu jest przekazywany do programisty należy. W poprzednim przykładzie `object1` jest odwołaniem do obiektu, który jest oparty na `Customer`. Ta dokumentacja odnosi się do nowego obiektu, ale nie zawiera danych obiektu. W rzeczywistości można utworzyć odwołanie do obiektu, bez tworzenia obiektu w ogóle:  
 
```csharp
 Customer object2;
```
 
 Nie zaleca się utworzenie odwołania do obiektu taką jak ta, które nie odwołują się do obiektu, ponieważ próbuje uzyskać dostęp do obiektu poprzez odniesienie zakończy się niepowodzeniem w czasie wykonywania. Jednak takie odwołanie może się do odwoływania się do obiektu, albo przez utworzenie nowego obiektu, albo, przypisując go do istniejącego obiektu, takie jak to:  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 Ten kod tworzy dwa odwołania do obiektu odnoszą się do tego samego obiektu. W związku z tym, zmiany wprowadzone w obiekcie za pośrednictwem `object3` są odzwierciedlane w kolejnych zastosowań `object4`. Ponieważ obiekty, które są oparte na klasach są określane przez odwołanie, klas są określane jako typy odwołań.  
  
## <a name="class-inheritance"></a>Dziedziczenie klas  

Klasy w pełni obsługiwać *dziedziczenia*, podstawowe charakterystyka programowanie zorientowane obiektowo. Kiedy tworzysz klasę, możesz dziedziczyć od innego interfejsu lub klasy, która nie jest zdefiniowana jako [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md), a inne klasy mogą dziedziczyć od Twojej klasy i zastępują metody wirtualne klasy.

Dziedziczenie odbywa się za pomocą *pochodnym*, która oznacza, że klasa jest zadeklarowana za pomocą *klasy bazowej* z którego dziedziczy dane i zachowania. Klasa podstawowa jest określona przez dołączenie dwukropek i nazwę klasy bazowej, po nazwie klasy pochodnej, takich jak to:  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

Klasa deklaruje klasę bazową, dziedziczy wszystkich członków klasy podstawowej, z wyjątkiem konstruktorów. Aby uzyskać więcej informacji, zobacz [dziedziczenia](inheritance.md).
  
W przeciwieństwie do języka C++ klasy w języku C# tylko bezpośrednio może dziedziczyć z jednej klasy bazowej. Jednak ponieważ sam podstawowej klasy mogą dziedziczyć z innej klasy, klasy mogą pośrednio dziedziczyć wielu klas bazowych. Ponadto klasy można bezpośrednio zaimplementować więcej niż jednego interfejsu. Więcej informacji znajdziesz w artykule [Interfejsy](../interfaces/index.md).  
  
Klasy mogą być deklarowane [abstrakcyjne](../../language-reference/keywords/abstract.md). Abstrakcyjna klasa zawiera metody abstrakcyjne, które mają definicji podpisu, ale nie implementacji. Nie można utworzyć wystąpienia klasy abstrakcyjnej. One należy używać tylko przez klasy pochodne, które implementują metody abstrakcyjne. Z drugiej strony [zapieczętowanego](../../language-reference/keywords/sealed.md) klasy nie zezwala na innych klas dziedziczyć po nim. Aby uzyskać więcej informacji, zobacz [abstrakcyjnych i zapieczętowanych klas i składowych klasy](abstract-and-sealed-classes-and-class-members.md).  
  
Definicje klas może zostać podzielony między plikami z innego źródła. Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](partial-classes-and-methods.md).  
  
## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano Klasa publiczna, która zawiera [automatycznie implementowana właściwość](auto-implemented-properties.md), metody i specjalnych metodę o nazwie konstruktora. Aby uzyskać więcej informacji, zobacz [właściwości](properties.md), [metody](methods.md), i [konstruktory](constructors.md) tematów. Wystąpienia klasy następnie są tworzone za pomocą `new` — słowo kluczowe.  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a>Specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Programowanie zorientowane obiektowo](../concepts/object-oriented-programming.md)
- [Polimorfizm](polymorphism.md)
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
- [Elementy członkowskie](members.md)
- [Metody](methods.md)
- [Konstruktory](constructors.md)
- [Finalizatory](destructors.md)
- [Obiekty](objects.md)
