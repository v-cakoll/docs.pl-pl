---
title: Używanie struktur — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: d2e89c842ae83a5be65c7500e47beb7f302e23be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427191"
---
# <a name="using-structs-c-programming-guide"></a>Używanie struktur (Przewodnik programowania w języku C#)
`struct` Typu nadaje się do reprezentowania lekkie obiekty, takie jak `Point`, `Rectangle`, i `Color`. Mimo że jest to po prostu jako wygodne reprezentuje punkt jako [klasy](../../../csharp/language-reference/keywords/class.md) z [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), [struktury](../../../csharp/language-reference/keywords/struct.md) może być bardziej efektywne w niektórych scenariuszach. Na przykład, jeśli zadeklarować tablicę 1000 `Point` obiektów do odwoływania się do każdego obiektu; w tym przypadku przydzieli dodatkową pamięć, struktura będzie mniej kosztowne. Ponieważ [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zawiera obiekt o nazwie <xref:System.Drawing.Point>, struktury, w tym przykładzie ma nazwę "Coords" zamiast niego.  
  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 Jest to błąd, aby zdefiniować domyślnego (bezparametrowego) konstruktora struktury. Jest również błędu, aby zainicjować pola wystąpienia w treści struktury. Składowe struktury dostępną z zewnątrz można zainicjować tylko przy użyciu sparametryzowanego konstruktora, pośrednie, Konstruktor domyślny [inicjatora obiektu](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md), lub uzyskując dostęp do elementów członkowskich pojedynczo po zadeklarowana jest struktura. Wszystkie elementy członkowskie prywatne lub w inny sposób niedostępny korzystają z konstruktorów wyłącznie.
  
 Po utworzeniu obiektu struktury przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) operatora, powstaje i odpowiedniego konstruktora jest wywoływana, zgodnie z opisem w [sygnatury konstruktora firmy](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax). W przeciwieństwie do klasy, struktury mogą być utworzone bez użycia `new` operatora. W takim przypadku nie ma żadnych wywołanie konstruktora, co sprawia, że przydział jest bardziej wydajne. Jednak pola pozostaną nieprzypisane i nie można użyć obiektu, dopóki wszystkie pola są inicjowane. W tym z brakiem, aby pobrać lub ustawić wartości za pomocą właściwości.
 
 W przypadku tworzenia wystąpienia obiektu struktury, przy użyciu domyślnego, konstruktora bez parametrów, wszystkie elementy członkowskie są przypisywane zgodnie z opisem w ich [wartości domyślne](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md).
  
 Podczas pisania konstruktora z parametrami struktury, należy jawnie zainicjować wszystkich elementów członkowskich; w przeciwnym razie co najmniej jednego członka pozostają nieprzypisane i struktury nie można użyć, błąd kompilatora CS0171 produkcji.  
  
 Brak nie dziedziczenia dla struktury istnieje dla klasy. Struktura nie może dziedziczyć z innej struktury lub klasy, a nie może być podstawą klasy. Struktury, jednak dziedziczy z klasy bazowej <xref:System.Object>. Struktura może zaimplementować interfejsów, a tak, dokładnie tak jak klasy.  
  
 Nie można zadeklarować klasy za pomocą słowa kluczowego `struct`. W języku C# są semantycznie różne klasy i struktury. Struktura jest typem wartości, gdy klasa jest typem referencyjnym. Aby uzyskać więcej informacji, zobacz [typów wartości](../../../csharp/language-reference/keywords/value-types.md).  
  
 Chyba że potrzebujesz semantyki typ odwołania, mała klasa wydajniej zajmował się przez system, jeśli trzeba je zadeklarować jako struktury zamiast tego.  
  
## <a name="example-1"></a>Przykład 1  
  
### <a name="description"></a>Opis  
 W tym przykładzie przedstawiono `struct` inicjalizacja za pomocą domyślnych i konstruktory sparametryzowane.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]  
  
## <a name="example-2"></a>Przykład 2  
  
### <a name="description"></a>Opis  
 W tym przykładzie pokazano funkcję, która jest unikatowa dla struktury. Tworzy obiekt Coords bez użycia `new` operatora. Jeżeli wymienisz wyraz `struct` wyrazami `class`, program nie zostanie skompilowany.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)
