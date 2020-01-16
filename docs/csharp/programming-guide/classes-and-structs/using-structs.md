---
title: Korzystanie z struktur — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 22d63465c534090a8918348ea5f050739c0cf01c
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964746"
---
# <a name="using-structs-c-programming-guide"></a>Używanie struktur (C# Przewodnik programowania)

Typ `struct` jest odpowiedni do reprezentowania obiektów lekkich, takich jak `Point`, `Rectangle`i `Color`. Chociaż nie jest to wygodne do reprezentowania punktu jako [klasy](../../language-reference/keywords/class.md) z właściwościami, które są [implementowane](./auto-implemented-properties.md), [Struktura](../../language-reference/keywords/struct.md) może być bardziej wydajna w niektórych scenariuszach. Na przykład, Jeśli deklarujesz tablicę z 1000 obiektów `Point`, przydzielasz dodatkową pamięć do odwoływania się do każdego obiektu; w takim przypadku struktura byłaby mniej kosztowna. Ponieważ .NET zawiera już obiekt o nazwie <xref:System.Drawing.Point>, struktura w tym przykładzie nosi nazwę `Coords`.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

Wystąpił błąd podczas definiowania konstruktora bez parametrów dla struktury. Jest również błędem inicjowania pola wystąpienia w treści struktury. Możliwe jest zainicjowanie zewnętrznie dostępnych elementów członkowskich struktury tylko przy użyciu konstruktora sparametryzowanego, niejawnego konstruktora bez parametrów, [inicjatora obiektów](object-and-collection-initializers.md)lub przez uzyskanie dostępu do elementów członkowskich pojedynczo po zadeklarowaniu struktury. Wszelkie prywatne lub w inny sposób niedostępni członkowie wymagają użycia wyłącznie konstruktorów.

Podczas tworzenia obiektu struktury przy użyciu operatora [New](../../language-reference/operators/new-operator.md) , zostanie on utworzony, a odpowiedni Konstruktor jest wywoływany zgodnie z [podpisem konstruktora](constructors.md#constructor-syntax). W przeciwieństwie do klas, struktury mogą być tworzone bez użycia operatora `new`. W takim przypadku nie istnieje wywołanie konstruktora, które zwiększa efektywność przydziału. Jednak pola pozostaną nieprzypisane i nie będzie można użyć obiektu, dopóki nie zostaną zainicjowane wszystkie pola. Obejmuje to brak możliwości pobrania lub ustawienia wartości za pomocą właściwości.

W przypadku wystąpienia obiektu struktury przy użyciu konstruktora bez parametrów wszystkie elementy członkowskie są przypisywane zgodnie z ich [wartościami domyślnymi](../../language-reference/builtin-types/default-values.md).

Podczas pisania konstruktora z parametrami struktury należy jawnie zainicjować wszystkie elementy członkowskie; w przeciwnym razie co najmniej jeden element członkowski pozostaje nieprzypisany i nie można użyć struktury, generując błąd kompilatora [CS0171](../../misc/cs0171.md).

Nie ma dziedziczenia struktur, ponieważ istnieją klasy. Struktura nie może dziedziczyć z innej struktury lub klasy i nie może być podstawą klasy. Struktury są jednak dziedziczone z klasy bazowej <xref:System.Object>. Struktura może implementować interfejsy i robi dokładnie jako klasy.

Nie można zadeklarować klasy przy użyciu słowa kluczowego `struct`. W C#, klasy i struktury są semantycznie różne. Struktura jest typem wartości, podczas gdy Klasa jest typem referencyjnym. Aby uzyskać więcej informacji, zobacz [typy wartości](../../language-reference/keywords/value-types.md) i [typy odwołań](../../language-reference/keywords/reference-types.md).

O ile nie jest wymagana semantyka typu odwołania, niewielka Klasa może być bardziej wydajnie obsługiwana przez system, Jeśli zadeklarujesz ją jako strukturę.

## <a name="example-1"></a>Przykład 1

Ten przykład ilustruje inicjalizację `struct` przy użyciu zarówno konstruktorów bez parametrów, jak i sparametryzowanych.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]

## <a name="example-2"></a>Przykład 2

Ten przykład ilustruje funkcję, która jest unikatowa dla struktur. Tworzy obiekt coords bez użycia operatora `new`. Jeśli zastąpisz słowo `struct` za pomocą słowa `class`, program nie zostanie skompilowany.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](index.md)
- [Struktury](structs.md)
