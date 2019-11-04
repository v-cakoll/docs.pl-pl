---
title: Obiekty — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
ms.openlocfilehash: 1b3ceb2671a4c21f1df89599c9b8c0bc107a7435
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419269"
---
# <a name="objects-c-programming-guide"></a>Obiekty (Przewodnik programowania w języku C#)
Definicja klasy lub struktury jest taka sama jak w przypadku planu, który określa, jaki typ może być wykonywany. Obiekt jest w zasadzie blok pamięci, który został przydzielony i skonfigurowany zgodnie z planem. Program może utworzyć wiele obiektów tej samej klasy. Obiekty są również nazywane wystąpieniami i mogą być przechowywane w zmiennej nazwanej lub w tablicy lub kolekcji. Kod klienta to kod, który używa tych zmiennych do wywoływania metod i uzyskiwania dostępu do właściwości publicznych obiektu. W języku zorientowanym obiektowo, takim jak C#, typowy program składa się z wielu obiektów, które współpracują dynamicznie.  
  
> [!NOTE]
> Typy statyczne zachowują się inaczej niż opisane w tym miejscu. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klas](./static-classes-and-static-class-members.md).
  
## <a name="struct-instances-vs-class-instances"></a>Wystąpienia struktury a wystąpienia klas  
 Ponieważ klasy są typami odwołań, zmienna obiektu klasy przechowuje odwołanie do adresu obiektu na zarządzanym stosie. Jeśli drugi obiekt tego samego typu jest przypisany do pierwszego obiektu, obie zmienne odwołują się do obiektu na tym adresie. Ten punkt jest omówiona bardziej szczegółowo w dalszej części tego tematu.  
  
 Wystąpienia klas są tworzone przy użyciu [operatora new](../../language-reference/operators/new-operator.md). W poniższym przykładzie `Person` jest typem i `person1` i `person 2` są wystąpieniami lub obiektami tego typu.  
  
 [!code-csharp[csProgGuideStatements#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#30)]  
  
 Ponieważ struktury są typami wartości, zmienna obiektu struktury przechowuje kopię całego obiektu. Wystąpienia struktur można również utworzyć za pomocą operatora `new`, ale nie jest to wymagane, jak pokazano w następującym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#31)]  
  
 Pamięć dla obu `p1` i `p2` jest przypisana na stosie wątków. Ta pamięć jest odzyskiwana wraz z typem lub metodą, w której jest zadeklarowana. Jest to jedną z przyczyn, dlaczego struktury są kopiowane podczas przypisywania. Z kolei, pamięć przydzieloną dla wystąpienia klasy jest automatycznie odzyskiwana (nieelementy bezużyteczne) przez środowisko uruchomieniowe języka wspólnego, gdy wszystkie odwołania do obiektu zostały utracone poza zakresem. Nie można deterministycznie zniszczyć obiektu klasy, takiego jak można w C++. Aby uzyskać więcej informacji dotyczących wyrzucania elementów bezużytecznych w .NET Framework, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
> Alokacja i cofanie alokacji pamięci na stercie zarządzanej jest wysoce zoptymalizowana w środowisku uruchomieniowym języka wspólnego. W większości przypadków nie ma znaczącej różnicy kosztu wydajności alokacji wystąpienia klasy na stercie i przydzielania wystąpienia struktury na stosie.
  
## <a name="object-identity-vs-value-equality"></a>Tożsamość obiektu a równość wartości  
 Porównując dwa obiekty pod kątem równości, należy najpierw rozróżnić, czy chcesz wiedzieć, czy dwie zmienne reprezentują ten sam obiekt w pamięci, czy też wartości co najmniej jednego z tych pól są równoważne. Jeśli zamierzasz porównywać wartości, należy wziąć pod uwagę, czy obiekty są wystąpieniami typów wartości (struktur) czy typy odwołań (klasy, delegatów, tablice).  
  
- Aby określić, czy dwa wystąpienia klasy odwołują się do tej samej lokalizacji w pamięci (co oznacza, że mają tę samą *tożsamość*), użyj statycznej metody <xref:System.Object.Equals%2A>. (<xref:System.Object?displayProperty=nameWithType> jest niejawną klasą bazową dla wszystkich typów wartości i typów referencyjnych, łącznie z strukturami i klasami zdefiniowanymi przez użytkownika).  
  
- Aby określić, czy pola wystąpienia w dwóch wystąpieniach struktury mają te same wartości, użyj metody <xref:System.ValueType.Equals%2A?displayProperty=nameWithType>. Ponieważ wszystkie struktury niejawnie dziedziczą z <xref:System.ValueType?displayProperty=nameWithType>, wywoływana jest metoda bezpośrednio w obiekcie, jak pokazano w następującym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#32)]  
  
 <xref:System.ValueType?displayProperty=nameWithType> implementacja `Equals` używa odbicia, ponieważ musi być w stanie określić, jakie pola znajdują się w dowolnej strukturze. Podczas tworzenia własnych struktur Zastąp metodę `Equals`, aby zapewnić wydajny algorytm równości, który jest specyficzny dla danego typu.  
  
- Aby określić, czy wartości pól w dwóch wystąpieniach klasy są równe, może być możliwe użycie metody <xref:System.Object.Equals%2A> lub [operatora = =](../../language-reference/operators/equality-operators.md#equality-operator-). Jednak należy ich używać tylko wtedy, gdy klasa została zastąpiona lub przeciążona, aby zapewnić niestandardową definicję "Równość" dla obiektów tego typu. Klasa może również zaimplementować interfejs <xref:System.IEquatable%601> lub interfejs <xref:System.Collections.Generic.IEqualityComparer%601>. Oba interfejsy zapewniają metody, których można użyć do testowania równości wartości. Podczas projektowania własnych klas, które zastępują `Equals`, należy postępować zgodnie z wytycznymi opisanymi w temacie [How to: define Value równość dla typu](../statements-expressions-operators/how-to-define-value-equality-for-a-type.md) i <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Informacje dodatkowe:  
  
- [Klasy](./classes.md)  
  
- [Struktury](./structs.md)  
  
- [Konstruktory](./constructors.md)  
  
- [Finalizatory](./destructors.md)  
  
- [Zdarzenia](../events/index.md)  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [object](../../language-reference/builtin-types/reference-types.md)
- [Dziedziczenie](./inheritance.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/keywords/struct.md)
- [Operator new](../../language-reference/operators/new-operator.md)
- [System typu wspólnego](../../../standard/base-types/common-type-system.md)
