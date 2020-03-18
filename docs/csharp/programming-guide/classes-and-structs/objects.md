---
title: Obiekty — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
ms.openlocfilehash: 09b290713f3bc2a7a7824bb19c98138943ad5b2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673384"
---
# <a name="objects-c-programming-guide"></a>Obiekty (Przewodnik programowania w języku C#)
Klasa lub struktura definicji jest jak plan, który określa, co typ może zrobić. Obiekt jest w zasadzie blok pamięci, który został przydzielony i skonfigurowany zgodnie z planem. Program może utworzyć wiele obiektów tej samej klasy. Obiekty są również nazywane wystąpieniami i mogą być przechowywane w nazwanej zmiennej lub w tablicy lub kolekcji. Kod klienta jest kod, który używa tych zmiennych do wywoływania metod i dostęp do właściwości publicznych obiektu. W języku obiektowym, takim jak C#, typowy program składa się z wielu obiektów współdziałających dynamicznie.  
  
> [!NOTE]
> Typy statyczne zachowują się inaczej niż opisane w tym miejscu. Aby uzyskać więcej informacji, zobacz [Klasy statyczne i elementy członkowskie klasy statycznej](./static-classes-and-static-class-members.md).
  
## <a name="struct-instances-vs-class-instances"></a>Wystąpienia struktury a wystąpienia klasy  
 Ponieważ klasy są typami odwołań, zmienna obiektu klasy zawiera odwołanie do adresu obiektu na zarządzanym stosie. Jeśli drugi obiekt tego samego typu jest przypisany do pierwszego obiektu, obie zmienne odnoszą się do obiektu pod tym adresem. Ten punkt został omówiony bardziej szczegółowo w dalszej części tego tematu.  
  
 Wystąpienia klas są tworzone przy użyciu [nowego operatora](../../language-reference/operators/new-operator.md). W poniższym `Person` przykładzie jest `person1` type `person 2` m.in.  
  
 [!code-csharp[csProgGuideStatements#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#30)]  
  
 Ponieważ struktury są typami wartości, zmienna obiektu struct zawiera kopię całego obiektu. Wystąpienia struktur można również utworzyć przy użyciu `new` operatora, ale nie jest to wymagane, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#31)]  
  
 Pamięć dla `p1` obu `p2` i jest przydzielana na stosie wątków. Ta pamięć jest odzyskiwana wraz z typem lub metodą, w której jest zadeklarowana. Jest to jeden z powodów, dla których struktury są kopiowane na przypisanie. Natomiast pamięć, która jest przydzielona dla wystąpienia klasy jest automatycznie odzyskiwany (śmieci zbierane) przez wspólny język wykonywania, gdy wszystkie odwołania do obiektu zniknęły z zakresu. Nie jest możliwe deterministycznie zniszczyć obiekt klasy, jak można w języku C++. Aby uzyskać więcej informacji na temat wyrzucania elementów bezużytecznych w platformie .NET Framework, zobacz [Wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
> Alokacja i alokacja pamięci na zarządzanym stercie jest wysoce zoptymalizowana w czasie wykonywania języka wspólnego. W większości przypadków nie ma znaczącej różnicy w kosztach wydajności przydzielania wystąpienia klasy na stercie w porównaniu z przydzielaniem wystąpienia struktury na stosie.
  
## <a name="object-identity-vs-value-equality"></a>Tożsamość obiektu a równość wartości  
 Podczas porównywania dwóch obiektów dla równości, należy najpierw odróżnić, czy chcesz wiedzieć, czy dwie zmienne reprezentują ten sam obiekt w pamięci, czy też wartości jednego lub więcej ich pól są równoważne. Jeśli zamierzasz porównać wartości, należy wziąć pod uwagę, czy obiekty są wystąpieniami typów wartości (struktury) lub typów odwołań (klasy, delegaty, tablice).  
  
- Aby ustalić, czy dwa wystąpienia klasy odnoszą się do tej samej lokalizacji w <xref:System.Object.Equals%2A> pamięci (co oznacza, że mają taką samą *tożsamość),* należy użyć metody statycznej. (<xref:System.Object?displayProperty=nameWithType> jest niejawną klasą podstawową dla wszystkich typów wartości i typów odwołań, w tym struktur i klas zdefiniowanych przez użytkownika).  
  
- Aby ustalić, czy pola wystąpienia w dwóch wystąpieniach struktury <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> mają te same wartości, należy użyć tej metody. Ponieważ wszystkie struktury niejawnie <xref:System.ValueType?displayProperty=nameWithType>dziedziczą z , wywołać metodę bezpośrednio na obiekcie, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#32)]  
  
 Implementacja <xref:System.ValueType?displayProperty=nameWithType> `Equals` używa odbicia, ponieważ musi być w stanie określić, jakie pola znajdują się w dowolnej strukturze. Podczas tworzenia własnych struktur, zastąpić `Equals` metodę, aby zapewnić algorytm równości efektywnej, który jest specyficzny dla danego typu.  
  
- Aby ustalić, czy wartości pól w dwóch wystąpieniach klas są równe, można użyć <xref:System.Object.Equals%2A> metody lub operatora [==.](../../language-reference/operators/equality-operators.md#equality-operator-) Jednak należy ich używać tylko wtedy, gdy klasa ma zastąpić lub przeciążone je, aby zapewnić niestandardową definicję, co "równości" oznacza dla obiektów tego typu. Klasa może również <xref:System.IEquatable%601> zaimplementować <xref:System.Collections.Generic.IEqualityComparer%601> interfejs lub interfejs. Oba interfejsy zapewniają metody, które mogą służyć do testowania równości wartości. Podczas projektowania własnych klas, `Equals`które zastępują, należy postępować zgodnie z wytycznymi podanymi w [jak zdefiniować równość wartości dla typu](../statements-expressions-operators/how-to-define-value-equality-for-a-type.md) i <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>.
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Więcej informacji:  
  
- [Klasy](./classes.md)  
  
- [Konstruktory](./constructors.md)  
  
- [Finalizatory](./destructors.md)  
  
- [Zdarzenia](../events/index.md)  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [obiekt](../../language-reference/builtin-types/reference-types.md)
- [Dziedziczenie](./inheritance.md)
- [Klasa](../../language-reference/keywords/class.md)
- [Typy konstrukcji](../../language-reference/builtin-types/struct.md)
- [new, operator](../../language-reference/operators/new-operator.md)
- [System typu wspólnego](../../../standard/base-types/common-type-system.md)
