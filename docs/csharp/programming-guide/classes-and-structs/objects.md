---
title: Obiekty - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
ms.openlocfilehash: de44f0c416de798fb42fba93e30ec6aa6ed0208d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585984"
---
# <a name="objects-c-programming-guide"></a>Obiekty (Przewodnik programowania w języku C#)
Definicja klasy lub struktury jest podobna do planu, który określa, co zrobić, typ. Obiekt jest zasadniczo bloku pamięci, która została przydzielona i skonfigurowane zgodnie z planu. Program może tworzyć wiele obiektów w tej samej klasy. Obiekty są również nazywane wystąpieniami i mogą być przechowywane w nazwanej zmiennej lub w tablicy lub kolekcji. Kod klienta jest kodem, który używa tych zmiennych w celu wywołania metod i uzyskiwać dostęp do właściwości publiczne obiektu. W języku zorientowane obiektowo takich jak C# typowego programu składa się z wielu obiektów interakcji dynamicznie.  
  
> [!NOTE]
>  Typy statyczne będą działały inaczej niż opisane tutaj. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="struct-instances-vs-class-instances"></a>Struktura wystąpień programu vs. Wystąpienia klasy  
 Ponieważ klasy są typami odwołań, zmienna obiektu klasy zawiera odwołanie do adresu obiektu w zarządzanym stosie. Jeśli drugi obiekt tego samego typu, jest przypisany do pierwszego obiektu, obie zmienne odnoszą się do obiektu pod tym adresem. Ten punkt jest omówiona bardziej szczegółowo w dalszej części tego tematu.  
  
 Wystąpienia klas są tworzone za pomocą [operatora new](../../../csharp/language-reference/keywords/new-operator.md). W poniższym przykładzie `Person` jest typem i `person1` i `person 2` wystąpienia lub obiektów tego typu.  
  
 [!code-csharp[csProgGuideStatements#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#30)]  
  
 Ponieważ struktury są typami wartości, zmienna obiektu struktura zawiera kopię całego obiektu. Można również tworzyć wystąpienia struktury za pomocą `new` operatora, ale nie jest wymagane, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#31)]  
  
 Pamięć dla obu `p1` i `p2` jest przydzielony na stosie wątku. Że pamięć jest odzyskana wraz z typu lub metody, w którym jest zdeklarowana. To jest jednym z powodów dlaczego struktury są kopiowane w przydziale. Z drugiej strony pamięci przydzielonej do wystąpienia klasy jest automatycznie odzyskiwanego (bezużyteczne) przez środowisko uruchomieniowe języka wspólnego, gdy wszystkie odwołania do obiektu zniknie z zakresu. Nie jest możliwe w sposób deterministyczny zniszczenie obiektu klasy, jak w przypadku języka C++. Aby uzyskać więcej informacji dotyczących wyrzucania elementów bezużytecznych w .NET Framework, zobacz [wyrzucania elementów bezużytecznych](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Alokacji i dezalokacji pamięci na stosie zarządzanym jest wysoce zoptymalizowane pod kątem w środowisko uruchomieniowe języka wspólnego. W większości przypadków nie ma znaczące różnic w koszt wydajności związany z przydzielaniem wystąpienie klasy na stosie i przydzielanie wystąpienia struktury, na stosie.  
  
## <a name="object-identity-vs-value-equality"></a>Vs tożsamości obiektu. Równość wartości  
 Podczas porównywania dwóch obiektów pod kątem równości, należy najpierw odróżnić czy chcesz wiedzieć, czy dwie zmienne reprezentują tego samego obiektu w pamięci, lub czy są równoważne wartości co najmniej jednego pola. Jeśli mają zamiar porównać wartości, należy rozważyć, czy obiekty są wystąpień typów wartości (struktury) lub typów referencyjnych (klas, obiektów delegowanych, tablice).  
  
- Aby ustalić, czy dwa wystąpienia klasy odnoszą się do tej samej lokalizacji w pamięci (co oznacza, że mają tę samą *tożsamości*), używa się statycznej <xref:System.Object.Equals%2A> metody. (<xref:System.Object?displayProperty=nameWithType> jest niejawne klasą bazową dla wszystkich typów wartości i typy odwołania, w tym klasy i struktury zdefiniowany przez użytkownika.)  
  
- Aby określić, czy pola wystąpienia w dwa wystąpienia struktury mają te same wartości, należy użyć <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> metody. Ponieważ wszystkie struktury niejawnie dziedziczą z <xref:System.ValueType?displayProperty=nameWithType>, wywołać metodę bezpośrednio na obiekcie, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#32)]  
  
 <xref:System.ValueType?displayProperty=nameWithType> Implementacji `Equals` używa odbicia, ponieważ muszą być możliwe ustalenie, jakie pola znajdują się w dowolnej struktury. Podczas tworzenia własnych struktur, Zastąp `Equals` metodę, aby zapewnić efektywne równości algorytm, który jest specyficzne dla danego typu.  
  
- Aby ustalić, czy wartości pól w dwóch wystąpień klasy są takie same, można używać <xref:System.Object.Equals%2A> metody lub [== — operator](../../../csharp/language-reference/operators/equality-operators.md#equality-operator-). Jednak je stosować wyłącznie wtedy jeśli klasa ma przesłonięcia lub przeciążone je do dostarczania niestandardowych definicji jakie "równości" oznacza dla obiektów tego typu. Klasa może być także implementować <xref:System.IEquatable%601> interfejsu lub <xref:System.Collections.Generic.IEqualityComparer%601> interfejsu. Oba interfejsy zawierają metody, które mogą służyć do testowania równość wartości. Podczas projektowania własnych klas zastąpienie `Equals`, upewnij się, że zgodnie z wytycznymi dotyczącymi określonych w [jak: Definiowanie równości wartości dla typu](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md) i <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Informacje dodatkowe:  
  
- [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
- [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [object](../../../csharp/language-reference/keywords/object.md)
- [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
- [class](../../../csharp/language-reference/keywords/class.md)
- [struct](../../../csharp/language-reference/keywords/struct.md)
- [new, operator](../../../csharp/language-reference/keywords/new-operator.md)
- [System typu wspólnego](../../../standard/base-types/common-type-system.md)
