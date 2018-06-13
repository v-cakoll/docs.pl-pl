---
title: Obiekty (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
ms.openlocfilehash: 553b0a5e75364bc5c294867852265575fb9271b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324678"
---
# <a name="objects-c-programming-guide"></a>Obiekty (Przewodnik programowania w języku C#)
Definicja klasy lub struktury jest podobny do planu, określający, co można zrobić typu. Obiekt jest zasadniczo blok pamięci przydzielony i skonfigurowany zgodnie z planu. Program może tworzyć wiele obiektów o tej samej klasy. Obiekty są również nazywane wystąpień i mogą być przechowywane w nazwanej zmiennej lub tablicą lub kolekcją. Kod klienta jest kodem, który używa tych zmiennych do wywołania metody i uzyskać dostęp do publicznej właściwości obiektu. W języku zorientowane obiektowo takich jak C# typowego programu składa się z wielu obiektów interakcji dynamicznie.  
  
> [!NOTE]
>  Statyczne typy zachowywać się inaczej niż opisany w tym miejscu. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statycznych elementów członkowskich klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="struct-instances-vs-class-instances"></a>Vs wystąpienia struktury. Wystąpienia klas  
 Ponieważ klas typów referencyjnych, zmienna obiektu klasy zawiera odwołanie do adresu obiektu na stercie zarządzanej. Drugi obiekt tego samego typu przypisane do pierwszego obiektu obie zmienne odwoływać się do obiektu pod tym adresem. Ten punkt jest omówiona bardziej szczegółowo w dalszej części tego tematu.  
  
 Wystąpienia klas są tworzone za pomocą [operatora new](../../../csharp/language-reference/keywords/new-operator.md). W poniższym przykładzie `Person` jest typem i `person1` i `person 2` wystąpienia ani obiektów tego typu.  
  
 [!code-csharp[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]  
  
 Ponieważ struktury są typy wartości, zmienna obiektu struktury przechowuje kopię całego obiektu. Można również tworzyć wystąpień struktur za pomocą `new` operatora, ale nie jest wymagane, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]  
  
 Pamięć dla obu `p1` i `p2` został przydzielony na stosie wątku. Wraz z typu lub metody, w którym jest zadeklarowany jest odzyskać tej pamięci. Jest jednym z powodów dlaczego struktury są kopiowane na przypisanie. Z kolei pamięci przydzielonej do wystąpienia klasy jest automatycznie regeneracji (bezużytecznych) przez środowisko uruchomieniowe języka wspólnego, gdy wszystkie odwołania do obiektu przeszły poza zakresem. Nie jest możliwe w sposób niejednoznaczny zniszczenie obiektu klasy, jak w języku C++. Aby uzyskać więcej informacji na temat wyrzucanie elementów bezużytecznych w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], zobacz [wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Alokacja i cofania alokacji pamięci sterty zarządzanej stopniu zoptymalizowany w środowisko uruchomieniowe języka wspólnego. W większości przypadków nie ma żadnych znaczące różnice dotyczące alokacji w stercie i przydzielanie wystąpieniem struktury na stosie wystąpienia klasy koszt wydajności.  
  
## <a name="object-identity-vs-value-equality"></a>Vs tożsamości obiektu. Równość wartości  
 Podczas porównywania dwa obiekty pod kątem równości, należy najpierw odróżnić czy chcesz wiedzieć, czy dwie zmienne reprezentują tego samego obiektu w pamięci, lub czy wartości co najmniej jednego swoich pól są równoważne. Jeśli mają zamiar porównać wartości, należy rozważyć, czy obiekty są wystąpień typów wartości (struktury) lub typy odwołań (klas, obiektów delegowanych, tablice).  
  
-   Aby ustalić, czy dwa wystąpienia klasy odwoływać się do tej samej lokalizacji w pamięci (co oznacza, że mają takie same *tożsamości*), użyj statycznych <xref:System.Object.Equals%2A> metody. (<xref:System.Object?displayProperty=nameWithType> jest niejawna klasę podstawową dla wszystkich typów wartości i typy referencyjne, łącznie z klasy i struktury zdefiniowane przez użytkownika.)  
  
-   Aby określić, czy pola wystąpienia w dwa wystąpienia struktury mają takie same wartości, użyj <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> metody. Ponieważ dziedziczy niejawnie strukturami <xref:System.ValueType?displayProperty=nameWithType>, wywołaj metodę bezpośrednio na obiekt, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]  
  
 <xref:System.ValueType?displayProperty=nameWithType> Implementacja `Equals` używa odbicia, ponieważ musi być możliwe ustalenie, jakie pola znajdują się w dowolnej struktury. Podczas tworzenia własnych struktur, Zastąp `Equals` metodę w celu zapewnienia algorytm wydajne równości, specyficzne dla danego typu.  
  
-   Aby ustalić, czy wartości pól w dwóch wystąpień klas są takie same, można używać <xref:System.Object.Equals%2A> metody lub [== — operator](../../../csharp/language-reference/operators/equality-comparison-operator.md). Jednak tylko użycia ich czy klasa ma przesłonięcia przeciążony je, aby zapewnić niestandardowej definicji jakie "równości" oznacza, że w przypadku obiektów tego typu. Klasa może również implementuje <xref:System.IEquatable%601> interfejsu lub <xref:System.Collections.Generic.IEqualityComparer%601> interfejsu. Oba interfejsy Podaj metod, które mogą służyć do testowania równości wartości. Podczas projektowania własnych klas zastąpienie tego `Equals`, upewnij się trzymać się wskazówek, o których wspomniano w [porady: Definiowanie równości wartości dla typu](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md) i <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Informacje dodatkowe:  
  
-   [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [object](../../../csharp/language-reference/keywords/object.md)  
 [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [new, operator](../../../csharp/language-reference/keywords/new-operator.md)  
 [System typu wspólnego](../../../standard/base-types/common-type-system.md)
