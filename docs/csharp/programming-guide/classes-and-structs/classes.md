---
title: Klasy (Przewodnik programowania w języku C#)
description: Dowiedz się więcej o typach klasy i jak je utworzyć
ms.date: 04/05/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 688736aa8556719789b02d7db25858f442b4309e
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245724"
---
# <a name="classes-c-programming-guide"></a>Klasy (Przewodnik programowania w języku C#)
A *klasy* to konstrukcja, która pozwala na tworzenie własnych typach niestandardowych przez grupowanie zmienne innych typów, metod i zdarzeń. Klasa jest podobna do planu. Definiuje dane i zachowania tego typu. Jeśli klasa nie jest zadeklarowana jako statyczna, kod klienta może utworzyć *wystąpień* go. Te wystąpienia są *obiektów* przypisane do zmiennej. Wystąpienie klasy pozostaje w pamięci, dopóki wszystkie odwołania do niego wykraczają poza zakres. W tym czasie CLR oznacza je jako kwalifikuje się do wyrzucania elementów bezużytecznych. Jeśli klasa jest zadeklarowana jako [statyczne](../../../csharp/language-reference/keywords/static.md), nie można utworzyć wystąpień i kod klienta tylko do niego dostęp za pośrednictwem samej klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  

## <a name="reference-types"></a>Typy odwołań  
Typ, który jest zdefiniowany jako [klasy](../../../csharp/language-reference/keywords/class.md) jest *odwołania do typu*. W czasie wykonywania, kiedy Deklarujesz zmienną typu odwołania, zmienna zawiera wartość [null](../../../csharp/language-reference/keywords/null.md) aż jawnie tworzone jest wystąpienie klasy za pomocą [nowe](../../../csharp/language-reference/keywords/new.md) operatora lub obiektu, została utworzona w innych miejscach, jak pokazano w poniższym przykładzie:

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

Po utworzeniu obiektu pamięć jest alokowane na zarządzanym stosie, a zmienna zawiera tylko odwołanie do lokalizacji obiektu. Typy na zarządzanym stosie wymagają narzutu zarówno kiedy są alokowane oraz kiedy są odbierane przez funkcjonalność zarządzania pamięcią automatyczną CLR, który jest znany jako *wyrzucania elementów bezużytecznych*. Jednak wyrzucanie elementów bezużytecznych jest również bardzo dobrze zoptymalizowane i w większości scenariuszy nie powoduje problemów z wydajnością. Aby uzyskać więcej informacji dotyczących wyrzucania elementów bezużytecznych, zobacz [pamięcią automatyczną zarządzania i wyrzucania elementów kolekcji](../../../standard/garbage-collection/gc.md).  
  
## <a name="declaring-classes"></a>Deklarowanie klas  
 Klasy są deklarowane przy użyciu [klasy](../../../csharp/language-reference/keywords/class.md) — słowo kluczowe, jak pokazano w poniższym przykładzie:

 ```csharp
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 `class` — Słowo kluczowe jest poprzedzony przez poziom dostępu. Ponieważ [publicznych](../../../csharp/language-reference/keywords/public.md) jest używany w tym przypadku każdy może utworzyć wystąpienia tej klasy. Następuje nazwa klasy `class` — słowo kluczowe. W pozostałej części definicji jest treści klasy, gdzie są zdefiniowane zachowanie i dane. Pola, właściwości, metody i zdarzenia dla klasy, są nazywane zbiorczo *elementy członkowskie klasy*.  
  
## <a name="creating-objects"></a>Tworzenie obiektów  
 Chociaż czasami są używane zamiennie, klasy i obiektu są różne. Klasa określa typ obiektu, ale nie jest sam obiekt. Obiekt jest jednostką konkretnych na podstawie klasy i jest czasami określane jako wystąpienia klasy.  
  
 Obiekty mogą być tworzone za pomocą [nowe](../../../csharp/language-reference/keywords/new.md) — słowo kluczowe następuje nazwa klasy, która obiekt będzie zależeć od, podobnie do następującego:  

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
  
## <a name="class-inheritance"></a>Dziedziczenie oparte na klasach  

 Klasy w pełni obsługiwać *dziedziczenia*, podstawowe charakterystyka programowanie zorientowane obiektowo. Kiedy tworzysz klasę, możesz dziedziczyć od innego interfejsu lub klasy, która nie jest zdefiniowana jako [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md), a inne klasy mogą dziedziczyć od Twojej klasy i zastępują metody wirtualne klasy.

 Dziedziczenie odbywa się za pomocą *pochodnym*, która oznacza, że klasa jest zadeklarowana za pomocą *klasy bazowej* z którego dziedziczy dane i zachowania. Klasa podstawowa jest określona przez dołączenie dwukropek i nazwę klasy bazowej, po nazwie klasy pochodnej, takich jak to:  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```
  
 Klasa deklaruje klasę bazową, dziedziczy wszystkich członków klasy podstawowej, z wyjątkiem konstruktorów. Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).
  
 W przeciwieństwie do języka C++ klasy w języku C# tylko bezpośrednio może dziedziczyć z jednej klasy bazowej. Jednak ponieważ sam podstawowej klasy mogą dziedziczyć z innej klasy, klasy mogą pośrednio dziedziczyć wielu klas bazowych. Ponadto klasy można bezpośrednio zaimplementować więcej niż jednego interfejsu. Więcej informacji znajdziesz w artykule [Interfejsy](../../../csharp/programming-guide/interfaces/index.md).  
  
 Klasy mogą być deklarowane [abstrakcyjne](../../../csharp/language-reference/keywords/abstract.md). Abstrakcyjna klasa zawiera metody abstrakcyjne, które mają definicji podpisu, ale nie implementacji. Nie można utworzyć wystąpienia klasy abstrakcyjnej. One należy używać tylko przez klasy pochodne, które implementują metody abstrakcyjne. Z drugiej strony [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md) klasy nie zezwala na innych klas dziedziczyć po nim. Aby uzyskać więcej informacji, zobacz [abstrakcyjnych i zapieczętowanych klas i składowych klasy](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Definicje klas może zostać podzielony między plikami z innego źródła. Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano Klasa publiczna, która zawiera [automatycznie implementowana właściwość](auto-implemented-properties.md), metody i specjalnych metodę o nazwie konstruktora. Aby uzyskać więcej informacji, zobacz [właściwości](properties.md), [metody](methods.md), i [konstruktory](constructors.md) tematów. Wystąpienia klasy następnie są tworzone za pomocą `new` — słowo kluczowe.  
  
 [!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Programowanie zorientowane obiektowo](../concepts/object-oriented-programming.md)  
 [Polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [Elementy członkowskie](../../../csharp/programming-guide/classes-and-structs/members.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [Obiekty](../../../csharp/programming-guide/classes-and-structs/objects.md)
