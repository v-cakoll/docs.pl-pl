---
title: "Klasy — przewodnik C#"
description: "Dowiedz się więcej o typach klasy i sposób ich tworzenia"
keywords: .NET, .NET core, C#
author: BillWagner
ms.author: wiwagn
ms.date: 10/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: 13cbd3a5b53ea9b0f1acb22684b6a28639d00751
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="classes"></a>Klasy
A *klasy* jest konstrukcję, która umożliwia tworzenie własnych niestandardowych typów grupując zmienne innych typów, metod i zdarzeń. Klasa jest podobny do planu. Definiuje danych i zachowania typu. Jeśli klasa nie jest zadeklarowane jako statyczne, kod klienta może być używany przez utworzenie *obiektów* lub *wystąpień* przypisane do zmiennej. Zmienna pozostaje w pamięci, dopóki wszystkie odwołania do niego się znaleźć poza zakresem. W tym czasie CLR oznacza je jako kwalifikujący się do wyrzucanie elementów bezużytecznych. Jeśli klasa jest zadeklarowany jako [statycznych](language-reference/keywords/static.md), następnie istnieje tylko jedna kopia w pamięci i kod klienta można do niego dostęp tylko za pośrednictwem klasy, nie *zmienna wystąpienia*. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczni członkowie klas](programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  

## <a name="reference-types"></a>Typy odwołań  
Typ, który jest zdefiniowany jako [klasy](language-reference/keywords/class.md) jest *zawierają odwołania do typu*. W czasie wykonywania, gdy można zadeklarować zmiennej typu referencyjnego, zmienna zawiera wartość [null](language-reference/keywords/null.md) do momentu jawnego tworzenia wystąpienia obiektu przy użyciu [nowe](language-reference/keywords/new.md) operatora, lub Przypisz do niego obiekt który został utworzony w innym miejscu przy użyciu [nowe](language-reference/keywords/new.md), jak pokazano w poniższym przykładzie:  

[!code-csharp[Reference Types](../../samples/snippets/csharp/concepts/classes/reference-type.cs)]
  
Po utworzeniu obiektu na stercie zarządzanej jest przydzielana pamięć, a zmienna zawiera tylko odwołanie do lokalizacji obiektu. Typy w stercie zarządzanej wymaga obciążenie zarówno podczas są przydzielone i podczas odzyskane przez funkcje zarządzania automatyczne pamięci środowiska CLR, znany jako *wyrzucanie elementów bezużytecznych*. Jednak również stopniu zoptymalizowany wyrzucanie elementów bezużytecznych i w większości przypadków nie jest tworzony problem z wydajnością. Aby uzyskać więcej informacji o pamięci, zobacz [pamięci automatycznego zarządzania i odzyskiwanie pamięci](../standard/garbage-collection/gc.md).  
  
Typy odwołań w pełni obsługuje *dziedziczenia*, podstawowych cech programowanie zorientowane obiektowo. Podczas tworzenia klasy mogą dziedziczyć z innych interfejs lub klasa, która nie jest zdefiniowany jako [zapieczętowanego](language-reference/keywords/sealed.md), i inne klasy mogą dziedziczyć po klasie i zastąpienie metody wirtualnej. Aby uzyskać więcej informacji, zobacz [dziedziczenia](programming-guide/classes-and-structs/inheritance.md).

## <a name="declaring-classes"></a>Deklarowanie klas  
Klasy są zadeklarowane za pomocą [klasy](language-reference/keywords/class.md) — słowo kluczowe, jak pokazano w poniższym przykładzie:  
  
[!code-csharp[Declaring Classes](../../samples/snippets/csharp/concepts/classes/declaring-classes.cs)]  
  
**Klasy** — słowo kluczowe jest poprzedzony modyfikator dostępu. Ponieważ [publicznego](language-reference/keywords/public.md) jest używany w takim przypadku każdy użytkownik utworzyć obiekty z tej klasy. Następuje nazwa klasy **klasy** — słowo kluczowe. W pozostałej części definicji jest treści klasy, gdzie są zdefiniowane danych i zachowania. Pola, właściwości, metod i zdarzeń w klasie są nazywane zbiorczo *elementy członkowskie klasy*.  
  
## <a name="creating-objects"></a>Tworzenie obiektów  
Klasa określa typ obiektu, ale nie jest obiektem samej siebie. Obiekt jest podmiotem konkretnych oparty na klasie i jest czasami określana jako wystąpienie klasy.  
  
Obiekty mogą być tworzone przy użyciu [nowe](language-reference/keywords/new.md) — słowo kluczowe następuje nazwa klasy, która obiektu zależy, podobnie do następującej:  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects.cs)]   
  
Podczas tworzenia wystąpienia klasy odwołania do obiektu jest przekazywane z powrotem do programowania. W poprzednim przykładzie `object1` jest odwołaniem do obiektu, który jest oparty na `Customer`. To odwołanie odwołuje się do nowego obiektu, ale nie zawiera dane obiektu. W rzeczywistości można utworzyć odwołanie do obiektu bez tworzenia obiektu w ogóle:  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects2.cs)]  
  
Nie zaleca się tworzenia odwołań do obiektów, takich jak ta jedną, która nie odwołuje się do obiektu, ponieważ próby dostępu do obiektu za pomocą odniesienie zakończy się niepowodzeniem w czasie wykonywania. Jednak odniesienie możliwe do odwoływania się do obiektu, tworząc nowy obiekt lub przypisywania go do istniejącego obiektu, takich jak ta:  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects3.cs)]  
  
Ten kod tworzy dwa odwołania do obiektów odnoszą się do tego samego obiektu. W związku z tym wszystkie zmiany wprowadzane za pośrednictwem obiektu `object3` zostaną odzwierciedlone w kolejnych zastosowań `object4`. Ponieważ obiekty, które są oparte na klas są określane przez odwołanie, klas są określane jako typy referencyjne.  
  
## <a name="class-inheritance"></a>Dziedziczenie klas  
Dziedziczenie odbywa się przy użyciu *pochodnym*, która oznacza, że klasa jest zadeklarowany za pomocą *klasa podstawowa* po którym dziedziczy danych i zachowania. Klasa podstawowa jest określony przez dołączenie dwukropek i nazwę klasy podstawowej po nazwie klasy pochodnej, jak to:  
  
[!code-csharp[Inheritance](../../samples/snippets/csharp/concepts/classes/inheritance.cs)]  
  
Klasa deklaruje klasy podstawowej, dziedziczy wszystkie elementy członkowskie klasy podstawowej, z wyjątkiem konstruktorów.  
  
W przeciwieństwie do języka C++ klasy w języku C# może dziedziczyć tylko bezpośrednio z jedną klasę podstawową. Jednak ponieważ samej klasy podstawowej może dziedziczyć z innej klasy, klasy mogą pośrednio dziedziczyć wiele klas podstawowych. Ponadto klasa bezpośrednio można zaimplementować więcej niż jeden interfejs. Aby uzyskać więcej informacji, zobacz [interfejsów](programming-guide/interfaces/index.md).  
  
Klasy mogą być deklarowane [abstrakcyjny](language-reference/keywords/abstract.md). Klasa abstrakcyjna zawiera metody abstrakcyjne mających definicji podpisu, ale żadnej implementacji. Nie można utworzyć wystąpienia klasy abstrakcyjnej. Tylko użyciem za pośrednictwem klas pochodnych, w których zaimplementowano metody abstrakcyjne. Z kolei [zapieczętowanego](language-reference/keywords/sealed.md) klasy nie zezwala na innych klas pochodzić od niego. Aby uzyskać więcej informacji, zobacz [abstrakcyjne i zapieczętowane klasy i elementów członkowskich klasy](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
Definicje klas może zostać podzielony między plikami z innego źródła. Aby uzyskać więcej informacji, zobacz [definicje klas częściowych](programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
 
## <a name="example"></a>Przykład
W poniższym przykładzie zdefiniowano publicznego klasę, która zawiera jedno pole, metoda i specjalne metody o nazwie konstruktora. Aby uzyskać więcej informacji, zobacz [konstruktorów](programming-guide/classes-and-structs/constructors.md). Następnie utworzyć wystąpienia klasy z **nowe** — słowo kluczowe.

[!code-csharp[Class Example](../../samples/snippets/csharp/concepts/classes/class-example.cs)]  
  
## <a name="c-language-specification"></a>specyfikacja języka C#  
Aby uzyskać więcej informacji, zobacz [specyfikacji języka C#](language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także  
[Podręcznik programowania C#](programming-guide/index.md)   
[Polimorfizm](programming-guide/classes-and-structs/polymorphism.md)   
[Elementy członkowskie klasy i struktury](programming-guide/classes-and-structs/members.md)   
[Metody klasy i struktury](programming-guide/classes-and-structs/methods.md)   
[Konstruktory](programming-guide/classes-and-structs/constructors.md)   
[Finalizatory](programming-guide/classes-and-structs/destructors.md)   
[Obiekty](programming-guide/classes-and-structs/objects.md)

