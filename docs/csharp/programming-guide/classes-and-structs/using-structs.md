---
title: Korzystanie z struktur — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 5577a5042ba77e133e3c6ee7760f7c3a4cce0537
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796582"
---
# <a name="using-structs-c-programming-guide"></a>Używanie struktur (Przewodnik programowania w języku C#)
Typ jest odpowiedni do reprezentowania obiektów lekkich, takich `Point`jak `Rectangle`,, `Color`i. `struct` Chociaż nie jest to wygodne do reprezentowania punktu jako [klasy](../../../csharp/language-reference/keywords/class.md) z właściwościami, [](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)które są implementowane, [Struktura](../../../csharp/language-reference/keywords/struct.md) może być bardziej wydajna w niektórych scenariuszach. Na przykład, Jeśli deklarujesz tablicę z 1000 `Point` obiektów, przydzielasz dodatkową pamięć do odwoływania się do każdego obiektu. w tym przypadku struktura byłaby mniej kosztowna. Ponieważ .NET Framework zawiera obiekt o nazwie <xref:System.Drawing.Point>, struktura w tym przykładzie nosi nazwę "coords".  
  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 Wystąpił błąd podczas definiowania domyślnego konstruktora (bez parametrów) dla struktury. Jest również błędem inicjowania pola wystąpienia w treści struktury. Możliwe jest zainicjowanie zewnętrznie dostępnych elementów członkowskich struktury tylko przy użyciu konstruktora sparametryzowanego, niejawnego konstruktora bez parametrów, [inicjatora obiektów](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)lub przez uzyskanie dostępu do elementów członkowskich pojedynczo po zadeklarowaniu struktury. Wszelkie prywatne lub w inny sposób niedostępni członkowie wymagają użycia wyłącznie konstruktorów.
  
 Podczas tworzenia obiektu struktury przy użyciu operatora [New](../../../csharp/language-reference/operators/new-operator.md) , zostanie on utworzony, a odpowiedni Konstruktor jest wywoływany zgodnie z [podpisem konstruktora](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax). W przeciwieństwie do klas, struktury mogą być tworzone bez użycia `new` operatora. W takim przypadku nie istnieje wywołanie konstruktora, które zwiększa efektywność przydziału. Jednak pola pozostaną nieprzypisane i nie będzie można użyć obiektu, dopóki nie zostaną zainicjowane wszystkie pola. Obejmuje to brak możliwości pobrania lub ustawienia wartości za pomocą właściwości.

 W przypadku wystąpienia obiektu struktury przy użyciu domyślnego konstruktora bez parametrów wszystkie elementy członkowskie są przypisywane zgodnie z ich [wartościami domyślnymi](../../../csharp/language-reference/keywords/default-values-table.md).
  
 Podczas pisania konstruktora z parametrami struktury należy jawnie zainicjować wszystkie elementy członkowskie; w przeciwnym razie co najmniej jeden element członkowski pozostaje nieprzypisany i nie można użyć struktury, generując błąd kompilatora CS0171.  
  
 Nie ma dziedziczenia struktur, ponieważ istnieją klasy. Struktura nie może dziedziczyć z innej struktury lub klasy i nie może być podstawą klasy. Struktury są jednak dziedziczone z klasy <xref:System.Object>bazowej. Struktura może implementować interfejsy i robi dokładnie jako klasy.  
  
 Nie można zadeklarować klasy za pomocą słowa `struct`kluczowego. W C#, klasy i struktury są semantycznie różne. Struktura jest typem wartości, podczas gdy Klasa jest typem referencyjnym. Aby uzyskać więcej informacji, zobacz [typy wartości](../../../csharp/language-reference/keywords/value-types.md).  
  
 O ile nie jest wymagana semantyka typu odwołania, niewielka Klasa może być bardziej wydajnie obsługiwana przez system, Jeśli zadeklarujesz ją jako strukturę.  
  
## <a name="example-1"></a>Przykład 1  
  
### <a name="description"></a>Opis  
 Ten przykład ilustruje `struct` inicjalizację przy użyciu domyślnych i sparametryzowanych konstruktorów.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]  
  
## <a name="example-2"></a>Przykład 2  
  
### <a name="description"></a>Opis  
 Ten przykład ilustruje funkcję, która jest unikatowa dla struktur. Tworzy obiekt coords bez użycia `new` operatora. Jeśli wyraz `struct` zostanie zastąpiony słowem `class`, program nie zostanie skompilowany.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)
