---
title: "Klasy (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: "40"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37e810fc5a5397a6b9240346ac28505b11b1e817
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="classes-c-programming-guide"></a>Klasy (Przewodnik programowania w języku C#)
A *klasy* jest konstrukcję, która umożliwia tworzenie własnych niestandardowych typów grupując zmienne innych typów, metod i zdarzeń. Klasa jest podobny do planu. Definiuje danych i zachowania typu. Jeśli klasa nie jest zadeklarowane jako statyczne, kod klienta może być używany przez utworzenie *obiektów* lub *wystąpień* przypisane do zmiennej. Zmienna pozostaje w pamięci, dopóki wszystkie odwołania do niego się znaleźć poza zakresem. W tym czasie CLR oznacza je jako kwalifikujący się do wyrzucanie elementów bezużytecznych. Jeśli klasa jest zadeklarowany jako [statycznych](../../../csharp/language-reference/keywords/static.md), następnie istnieje tylko jedna kopia w pamięci i kod klienta można do niego dostęp tylko za pośrednictwem klasy, nie *zmienna wystąpienia*. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statycznych elementów członkowskich klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 W przeciwieństwie do struktury, klasy pomocy technicznej *dziedziczenia*, podstawowych cech programowanie zorientowane obiektowo. Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## <a name="declaring-classes"></a>Deklarowanie klas  
 Klasy są zadeklarowane za pomocą [klasy](../../../csharp/language-reference/keywords/class.md) — słowo kluczowe, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]  
  
 `class` — Słowo kluczowe jest poprzedzony poziom dostępu. Ponieważ [publicznego](../../../csharp/language-reference/keywords/public.md) jest używany w takim przypadku każdy użytkownik utworzyć obiekty z tej klasy. Następuje nazwa klasy `class` — słowo kluczowe. W pozostałej części definicji jest treści klasy, gdzie są zdefiniowane danych i zachowania. Pola, właściwości, metod i zdarzeń w klasie są nazywane zbiorczo *elementy członkowskie klasy*.  
  
## <a name="creating-objects"></a>Tworzenie obiektów  
 Mimo że czasami używane zamiennie, klasy i obiektu są różne. Klasa określa typ obiektu, ale nie jest obiektem samej siebie. Obiekt jest podmiotem konkretnych oparty na klasie i jest czasami określana jako wystąpienie klasy.  
  
 Obiekty mogą być tworzone przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) — słowo kluczowe następuje nazwa klasy, która obiektu zależy, podobnie do następującej:  
  
 [!code-csharp[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]  
  
 Podczas tworzenia wystąpienia klasy odwołania do obiektu jest przekazywane z powrotem do programowania. W poprzednim przykładzie `object1` jest odwołaniem do obiektu, który jest oparty na `Customer`. To odwołanie odwołuje się do nowego obiektu, ale nie zawiera dane obiektu. W rzeczywistości można utworzyć odwołanie do obiektu bez tworzenia obiektu w ogóle:  
  
 [!code-csharp[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]  
  
 Nie zaleca się tworzenia odwołań do obiektów takich jak ta, które nie odwołują się do obiektu, ponieważ próby dostępu do obiektu za pomocą odniesienie zakończy się niepowodzeniem w czasie wykonywania. Jednak odniesienie możliwe do odwoływania się do obiektu, tworząc nowy obiekt lub przypisywania go do istniejącego obiektu, takich jak ta:  
  
 [!code-csharp[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]  
  
 Ten kod tworzy dwa odwołania do obiektów odnoszą się do tego samego obiektu. W związku z tym wszystkie zmiany wprowadzane za pośrednictwem obiektu `object3` zostaną odzwierciedlone w kolejnych zastosowań `object4`. Ponieważ obiekty, które są oparte na klas są określane przez odwołanie, klas są określane jako typy referencyjne.  
  
## <a name="class-inheritance"></a>Dziedziczenie oparte na klasach  
 Dziedziczenie odbywa się przy użyciu *pochodnym*, która oznacza, że klasa jest zadeklarowany za pomocą *klasa podstawowa* po którym dziedziczy danych i zachowania. Klasa podstawowa jest określony przez dołączenie dwukropek i nazwę klasy podstawowej po nazwie klasy pochodnej, jak to:  
  
 [!code-csharp[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]  
  
 Klasa deklaruje klasy podstawowej, dziedziczy wszystkie elementy członkowskie klasy podstawowej, z wyjątkiem konstruktorów.  
  
 W przeciwieństwie do języka C++ klasy w języku C# może dziedziczyć tylko bezpośrednio z jedną klasę podstawową. Jednak ponieważ samej klasy podstawowej może dziedziczyć z innej klasy, klasy mogą pośrednio dziedziczyć wiele klas podstawowych. Ponadto klasa bezpośrednio można zaimplementować więcej niż jeden interfejs. Aby uzyskać więcej informacji, zobacz [interfejsów](../../../csharp/programming-guide/interfaces/index.md).  
  
 Klasy mogą być deklarowane [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md). Klasa abstrakcyjna zawiera metody abstrakcyjne mających definicji podpisu, ale żadnej implementacji. Nie można utworzyć wystąpienia klasy abstrakcyjnej. Tylko użyciem za pośrednictwem klas pochodnych, w których zaimplementowano metody abstrakcyjne. Z kolei [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md) klasy nie zezwala na innych klas pochodzić od niego. Aby uzyskać więcej informacji, zobacz [abstrakcyjne i zapieczętowane klasy oraz członkowie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Definicje klas może zostać podzielony między plikami z innego źródła. Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="description"></a>Opis  
 W poniższym przykładzie zdefiniowano publicznego klasę, która zawiera jedno pole, metoda i specjalne metody o nazwie konstruktora. Aby uzyskać więcej informacji, zobacz [konstruktorów](../../../csharp/programming-guide/classes-and-structs/constructors.md). Następnie utworzyć wystąpienia klasy z `new` — słowo kluczowe.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]  
  
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
