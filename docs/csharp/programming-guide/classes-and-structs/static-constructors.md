---
title: Konstruktory statyczne — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 744bcacbc38299c0ef7d16e814c415ec5caf95dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170120"
---
# <a name="static-constructors-c-programming-guide"></a>Konstruktory statyczne (Przewodnik programowania w języku C#)
Konstruktor statyczny służy do inicjowania wszelkich danych [statycznych](../../language-reference/keywords/static.md) lub do wykonania określonej akcji, która musi być wykonana tylko raz. Jest wywoływana automatycznie przed utworzeniem pierwszego wystąpienia lub odwołania się do żadnych elementów statycznych.  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  

## <a name="remarks"></a>Uwagi
Konstruktory statyczne mają następujące właściwości:  
  
- Konstruktor statyczny nie ma modyfikatorów dostępu ani parametrów.  

- Klasa lub struktura może mieć tylko jeden konstruktor statyczny.

- Konstruktorów statycznych nie można dziedziczyć ani przeciążenia.

- Konstruktora statycznego nie można wywołać bezpośrednio i jest przeznaczony tylko do wywoływania przez program runtime języka wspólnego (CLR). Jest wywoływana automatycznie.

- Użytkownik nie ma kontroli, gdy konstruktor statyczny jest wykonywany w programie.
  
- Konstruktor statyczny jest wywoływana automatycznie do inicjowania [klasy](../../language-reference/keywords/class.md) przed pierwszym wystąpieniem jest tworzony lub żadnych elementów statycznych są przywoływani. Konstruktor statyczny zostanie uruchomiony przed konstruktorem wystąpienia. Konstruktora statycznego typu jest wywoływana, gdy metoda statyczna przypisana do zdarzenia lub delegata jest wywoływana, a nie, gdy jest przypisany. Jeśli statyczne inicjatory zmiennej pola są obecne w klasie konstruktora statycznego, będą one wykonywane w kolejności tekstowej, w której pojawiają się w deklaracji klasy bezpośrednio przed wykonaniem konstruktora statycznego.

- Jeśli konstruktor statyczny nie zostanie zainicjowany przez konstruktora statycznego, wszystkie pola statyczne zostaną zainicjowane do wartości domyślnej wymienionej w [wartościach domyślnych typów C#.](../../language-reference/builtin-types/default-values.md)
  
- Jeśli konstruktor statyczny zgłasza wyjątek, czas wykonywania nie wywoła go po raz drugi, a typ pozostanie niezainicjowany przez okres istnienia domeny aplikacji, w którym program jest uruchomiony. Najczęściej <xref:System.TypeInitializationException> wyjątek jest generowany, gdy konstruktor statyczny nie może utworzyć wystąpienia typu lub dla nieobsługiwanego wyjątku występującego w konstruktorze statycznym. W przypadku niejawnych konstruktorów statycznych, które nie są jawnie zdefiniowane w kodzie źródłowym, rozwiązywanie problemów może wymagać inspekcji kodu języka pośredniego (IL).

- Obecność konstruktora statycznego uniemożliwia dodanie <xref:System.Reflection.TypeAttributes.BeforeFieldInit> atrybutu typu. Ogranicza to optymalizację czasu wykonywania.

- Pole zadeklarowane `static readonly` jako może być przypisane tylko jako część jego deklaracji lub w konstruktorze statycznym. Gdy jawny konstruktor statyczny nie jest wymagany, zainicjować pola statyczne w deklaracji, a nie za pośrednictwem konstruktora statycznego dla lepszej optymalizacji czasu wykonywania.

> [!Note]
> Chociaż nie jest bezpośrednio dostępny, obecność jawnego konstruktora statycznego powinny być udokumentowane, aby pomóc w rozwiązywaniu problemów z wyjątkami inicjowania.

### <a name="usage"></a>Sposób użycia

- Typowe użycie konstruktorów statycznych jest, gdy klasa używa pliku dziennika i konstruktora jest używany do zapisu wpisów do tego pliku.  
- Konstruktory statyczne są również przydatne podczas tworzenia klas otoki dla `LoadLibrary` kodu niezarządzanego, gdy konstruktor może wywołać metodę.  

- Konstruktory statyczne są również wygodnym miejscem do wymuszania kontroli w czasie wykonywania parametru typu, który nie może być sprawdzany w czasie kompilacji za pomocą ograniczeń (Ograniczenia parametru Type).

## <a name="example"></a>Przykład
 W tym przykładzie `Bus` klasa ma konstruktora statycznego. Po utworzeniu `Bus` pierwszego wystąpienia`bus1`( ), konstruktor statyczny jest wywoływany w celu zainicjowania klasy. Przykładowe dane wyjściowe sprawdza, czy konstruktor statyczny `Bus` działa tylko jeden raz, mimo że dwa wystąpienia są tworzone i że jest uruchamiany przed wystąpieniem konstruktora uruchamia.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]

## <a name="c-language-specification"></a>specyfikacja języka C#
Aby uzyskać więcej informacji, zobacz [static konstruktorów](~/_csharplang/spec/classes.md#static-constructors) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Klasy statyczne i statyczni członkowie klas](./static-classes-and-static-class-members.md)
- [Finalizatory](./destructors.md)
- [Wytyczne dotyczące projektowania konstruktora](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [Ostrzeżenie o zabezpieczeniach — CA2121: Konstruktory statyczne powinny być prywatne](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
