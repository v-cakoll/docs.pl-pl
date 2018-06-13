---
title: Klasy (Przewodnik programowania w języku C#)
description: Dowiedz się więcej o typach klasy i sposób ich tworzenia
ms.date: 04/05/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 688736aa8556719789b02d7db25858f442b4309e
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2018
ms.locfileid: "34312095"
---
# <a name="classes-c-programming-guide"></a>Klasy (Przewodnik programowania w języku C#)
A *klasy* jest konstrukcję, która umożliwia tworzenie własnych niestandardowych typów grupując zmienne innych typów, metod i zdarzeń. Klasa jest podobny do planu. Definiuje danych i zachowania typu. Jeśli klasa nie jest zadeklarowane jako statyczne, można utworzyć kod klienta *wystąpień* go. Te wystąpienia są *obiektów* przypisane do zmiennej. Wystąpienie klasy pozostaje w pamięci, dopóki wszystkie odwołania do niego się znaleźć poza zakresem. W tym czasie CLR oznacza je jako kwalifikujący się do wyrzucanie elementów bezużytecznych. Jeśli klasa jest zadeklarowany jako [statycznych](../../../csharp/language-reference/keywords/static.md), nie można utworzyć wystąpień i kod klienta można do niego dostęp tylko za pośrednictwem samej klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statycznych elementów członkowskich klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  

## <a name="reference-types"></a>Typy odwołań  
Typ, który jest zdefiniowany jako [klasy](../../../csharp/language-reference/keywords/class.md) jest *zawierają odwołania do typu*. W czasie wykonywania, gdy można zadeklarować zmiennej typu referencyjnego, zmienna zawiera wartość [null](../../../csharp/language-reference/keywords/null.md) dopóki jawnie utworzyć wystąpienia klasy przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) operatora, lub Przypisz do niego obiekt który została utworzona w innych miejscach, jak pokazano w poniższym przykładzie:

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

Po utworzeniu obiektu na stercie zarządzanej jest przydzielana pamięć, a zmienna zawiera tylko odwołanie do lokalizacji obiektu. Typy w stercie zarządzanej wymaga obciążenie zarówno podczas są przydzielone i podczas odzyskane przez funkcje zarządzania automatyczne pamięci środowiska CLR, znany jako *wyrzucanie elementów bezużytecznych*. Jednak również stopniu zoptymalizowany wyrzucanie elementów bezużytecznych i w większości przypadków nie jest tworzony problem z wydajnością. Aby uzyskać więcej informacji o pamięci, zobacz [pamięci automatycznego zarządzania i odzyskiwanie pamięci](../../../standard/garbage-collection/gc.md).  
  
## <a name="declaring-classes"></a>Deklarowanie klas  
 Klasy są zadeklarowane za pomocą [klasy](../../../csharp/language-reference/keywords/class.md) — słowo kluczowe, jak pokazano w poniższym przykładzie:

 ```csharp
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 `class` — Słowo kluczowe jest poprzedzony poziom dostępu. Ponieważ [publicznego](../../../csharp/language-reference/keywords/public.md) jest używany w takim przypadku każdy użytkownik można utworzyć wystąpienia tej klasy. Następuje nazwa klasy `class` — słowo kluczowe. W pozostałej części definicji jest treści klasy, gdzie są zdefiniowane danych i zachowania. Pola, właściwości, metod i zdarzeń w klasie są nazywane zbiorczo *elementy członkowskie klasy*.  
  
## <a name="creating-objects"></a>Tworzenie obiektów  
 Mimo że czasami używane zamiennie, klasy i obiektu są różne. Klasa określa typ obiektu, ale nie jest obiektem samej siebie. Obiekt jest podmiotem konkretnych oparty na klasie i jest czasami określana jako wystąpienie klasy.  
  
 Obiekty mogą być tworzone przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) — słowo kluczowe następuje nazwa klasy, która obiektu zależy, podobnie do następującej:  

 ```csharp
 Customer object1 = new Customer();
 ```
  
 Podczas tworzenia wystąpienia klasy odwołania do obiektu jest przekazywane z powrotem do programowania. W poprzednim przykładzie `object1` jest odwołaniem do obiektu, który jest oparty na `Customer`. To odwołanie odwołuje się do nowego obiektu, ale nie zawiera dane obiektu. W rzeczywistości można utworzyć odwołanie do obiektu bez tworzenia obiektu w ogóle:  
  
  ```csharp
  Customer object2;
  ```
  
 Nie zaleca się tworzenia odwołań do obiektów takich jak ta, które nie odwołują się do obiektu, ponieważ próby dostępu do obiektu za pomocą odniesienie zakończy się niepowodzeniem w czasie wykonywania. Jednak odniesienie możliwe do odwoływania się do obiektu, tworząc nowy obiekt lub przypisywania go do istniejącego obiektu, takich jak ta:  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
 ```
  
 Ten kod tworzy dwa odwołania do obiektów odnoszą się do tego samego obiektu. W związku z tym wszystkie zmiany wprowadzane za pośrednictwem obiektu `object3` są uwzględniane w kolejnych zastosowań `object4`. Ponieważ obiekty, które są oparte na klas są określane przez odwołanie, klas są określane jako typy referencyjne.  
  
## <a name="class-inheritance"></a>Dziedziczenie oparte na klasach  

 W pełni obsługuje klasy *dziedziczenia*, podstawowych cech programowanie zorientowane obiektowo. Podczas tworzenia klasy mogą dziedziczyć z innych interfejs lub klasa, która nie jest zdefiniowany jako [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md), i inne klasy mogą dziedziczyć po klasie i zastąpić metody wirtualnej klasy.

 Dziedziczenie odbywa się przy użyciu *pochodnym*, która oznacza, że klasa jest zadeklarowany za pomocą *klasa podstawowa* po którym dziedziczy danych i zachowania. Klasa podstawowa jest określony przez dołączenie dwukropek i nazwę klasy podstawowej po nazwie klasy pochodnej, jak to:  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```
  
 Klasa deklaruje klasy podstawowej, dziedziczy wszystkie elementy członkowskie klasy podstawowej, z wyjątkiem konstruktorów. Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).
  
 W przeciwieństwie do języka C++ klasy w języku C# może dziedziczyć tylko bezpośrednio z jedną klasę podstawową. Jednak ponieważ samej klasy podstawowej może dziedziczyć z innej klasy, klasy mogą pośrednio dziedziczyć wiele klas podstawowych. Ponadto klasa bezpośrednio można zaimplementować więcej niż jeden interfejs. Aby uzyskać więcej informacji, zobacz [interfejsów](../../../csharp/programming-guide/interfaces/index.md).  
  
 Klasy mogą być deklarowane [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md). Klasa abstrakcyjna zawiera metody abstrakcyjne mających definicji podpisu, ale żadnej implementacji. Nie można utworzyć wystąpienia klasy abstrakcyjnej. Tylko użyciem za pośrednictwem klas pochodnych, w których zaimplementowano metody abstrakcyjne. Z kolei [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md) klasy nie zezwala na innych klas pochodzić od niego. Aby uzyskać więcej informacji, zobacz [abstrakcyjne i zapieczętowane klasy oraz członkowie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Definicje klas może zostać podzielony między plikami z innego źródła. Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano klasę publicznej, która zawiera [automatycznie implementowanej właściwości](auto-implemented-properties.md), metody i specjalne metody o nazwie konstruktora. Aby uzyskać więcej informacji, zobacz [właściwości](properties.md), [metody](methods.md), i [konstruktorów](constructors.md) tematów. Wystąpienia klasy są następnie utworzono wystąpienie `new` — słowo kluczowe.  
  
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
