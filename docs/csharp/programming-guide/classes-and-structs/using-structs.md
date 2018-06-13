---
title: Używanie struktur (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 553a6d1d2e922d1683cb5dbe2fa0b525c9b1e37a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326423"
---
# <a name="using-structs-c-programming-guide"></a>Używanie struktur (Przewodnik programowania w języku C#)
`struct` Typu jest odpowiedni dla reprezentujący lekkie obiekty, takie jak `Point`, `Rectangle`, i `Color`. Chociaż jest to po prostu wygodny jako reprezentuje punkt jako [klasy](../../../csharp/language-reference/keywords/class.md) z [właściwości Auto-Implemented](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), [struktury](../../../csharp/language-reference/keywords/struct.md) może być skuteczniejsza w niektórych scenariuszach. Na przykład, jeśli zadeklarować tablicę 1000 `Point` obiekty odwołujące się do każdego obiektu; w takim przypadku przyzna dodatkowej pamięci, struktury, będą mniej kosztowne. Ponieważ [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zawiera obiekt o nazwie <xref:System.Drawing.Point>, struktury, w tym przykładzie ma nazwę "CoOrds" zamiast niego.  
  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 Jest błąd, aby zdefiniować domyślnego (bezparametrowego) konstruktora struktury. Istnieje również wystąpił błąd inicjowania pole wystąpienia w treści struktury. Elementy członkowskie struktury dostępne z zewnątrz można zainicjować tylko przy użyciu sparametryzowanym konstruktorze, pośrednie, domyślny konstruktor [obiekt inicjatora](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md), lub dostęp do elementów członkowskich pojedynczo po zadeklarowana jest struktura. Żadnych członków prywatnych lub jest niedostępny w przeciwnym razie wyłącznie wymagają użycia konstruktorów.
  
 Podczas tworzenia obiektu struktury przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) operatora, pobiera ona utworzona i odpowiedni konstruktor jest nazywany zgodnie z [podpisu konstruktora](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax). W przeciwieństwie do klasy, struktury można wdrożyć bez użycia `new` operatora. W takim przypadku nie ma żadnych wywołania konstruktora, co sprawia, że przydział jest bardziej wydajne. Jednak pola pozostanie nieprzypisane i nie można użyć obiektu, dopóki wszystkie pola są zainicjowane. Dotyczy to również w której nie można pobrać lub ustawić wartości za pośrednictwem właściwości zaimplementowane automatycznie.
 
 Jeśli wystąpienia obiektu struktury przy użyciu domyślnego, konstruktora bez parametrów, wszystkie elementy członkowskie są przypisane zgodnie z ich [wartości domyślne](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md).
  
 Podczas zapisywania konstruktora z parametrami struktury, należy jawnie zainicjować wszystkich elementów członkowskich; w przeciwnym razie co najmniej jednego członka pozostają nieprzypisane i struktury nie można użyć, który wygenerował błąd kompilatora CS0171.  
  
 Brak nie dziedziczenia struktur istnieje dla klasy. Struktury nie może dziedziczyć z innego struktury lub klasy, a nie może być podstawą klasy. Struktury, jednak dziedziczy z klasy podstawowej <xref:System.Object>. Struktury mogą implementować interfejsów i który tak dokładnie, jak klasy.  
  
 Nie można zadeklarować klasy za pomocą słowa kluczowego `struct`. W języku C# klasy i struktury są różnymi semantycznie. Struktury jest typem wartości, gdy klasa jest typem referencyjnym. Aby uzyskać więcej informacji, zobacz [typów wartości](../../../csharp/language-reference/keywords/value-types.md).  
  
 Jeśli nie potrzebujesz semantyki Typ referencyjny, małych klasy mogą wydajniej obsługi przez system przy deklarowaniu go jako struktura zamiast tego.  
  
## <a name="example-1"></a>Przykład 1  
  
### <a name="description"></a>Opis  
 W tym przykładzie przedstawiono `struct` inicjowania przy użyciu domyślnych i konstruktory sparametryzowane.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]  
  
## <a name="example-2"></a>Przykład 2  
  
### <a name="description"></a>Opis  
 W tym przykładzie pokazano, funkcja, która jest unikatowa dla struktury. Tworzy obiekt CoOrds bez użycia `new` operatora. Jeśli zamienić słowo `struct` słowem `class`, program nie zostanie skompilowany.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)
