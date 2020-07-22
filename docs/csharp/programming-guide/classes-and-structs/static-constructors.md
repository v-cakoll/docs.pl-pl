---
title: Konstruktory statyczne — Przewodnik programowania w języku C#
description: Statyczny Konstruktor w języku C# inicjuje dane statyczne lub wykonuje akcję wykonywaną tylko raz przed utworzeniem pierwszego wystąpienia lub odwołaniem do statycznych elementów członkowskich.
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: e324b2aa968ff5fdf9c268fa3891f67e8530ff87
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863985"
---
# <a name="static-constructors-c-programming-guide"></a>Konstruktory statyczne (Przewodnik programowania w języku C#)
Statyczny Konstruktor jest używany do inicjowania wszelkich danych [statycznych](../../language-reference/keywords/static.md) lub wykonywania określonej akcji, która musi zostać wykonana tylko raz. Jest wywoływana automatycznie przed utworzeniem pierwszego wystąpienia lub odwołaniem do jakiegokolwiek statycznego członka.  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  

## <a name="remarks"></a>Uwagi
Konstruktory statyczne mają następujące właściwości:  
  
- Konstruktor statyczny nie przyjmuje modyfikatorów dostępu ani nie ma parametrów.  

- Klasa lub struktura może mieć tylko jeden Konstruktor statyczny.

- Konstruktory statyczne nie mogą być dziedziczone ani przeciążone.

- Statyczny Konstruktor nie może być wywoływany bezpośrednio i jest przeznaczony tylko do wywoływania przez środowisko uruchomieniowe języka wspólnego (CLR). Jest wywoływana automatycznie.

- Użytkownik nie ma kontroli nad tym, kiedy Konstruktor statyczny jest wykonywany w programie.
  
- Statyczny Konstruktor jest automatycznie wywoływany w celu zainicjowania [klasy](../../language-reference/keywords/class.md) przed utworzeniem pierwszego wystąpienia lub odwołania do jakichkolwiek statycznych elementów członkowskich. Statyczny Konstruktor zostanie uruchomiony przed konstruktorem wystąpienia. Statyczny Konstruktor typu jest wywoływany, gdy metoda statyczna przypisana do zdarzenia lub delegata jest wywoływana, a nie podczas przypisywania. Jeśli inicjatory zmiennych pól statycznych są obecne w klasie konstruktora statycznego, zostaną one wykonane w kolejności tekstowej, w której pojawiają się w deklaracji klasy bezpośrednio przed wykonaniem konstruktora statycznego.

- Jeśli nie podano statycznego konstruktora do zainicjowania pól statycznych, wszystkie pola statyczne są inicjowane do wartości domyślnej, jak wymieniono w [domyślnych wartości typów języka C#](../../language-reference/builtin-types/default-values.md).
  
- Jeśli Konstruktor statyczny zgłosi wyjątek, środowisko uruchomieniowe nie wywołaje go po raz drugi, a typ pozostanie niezainicjowany przez okres istnienia domeny aplikacji, w której uruchomiono program. Najczęściej <xref:System.TypeInitializationException> wyjątek jest zgłaszany, gdy Konstruktor statyczny nie może utworzyć wystąpienia typu lub dla nieobsłużonego wyjątku w konstruktorze statycznym. W przypadku niejawnych konstruktorów statycznych, które nie są jawnie zdefiniowane w kodzie źródłowym, rozwiązywanie problemów może wymagać inspekcji kodu języka pośredniego (IL).

- Obecność konstruktora statycznego uniemożliwia dodanie <xref:System.Reflection.TypeAttributes.BeforeFieldInit> atrybutu typu. To ogranicza optymalizację środowiska uruchomieniowego.

- Pole zadeklarowane jako `static readonly` może być przypisane tylko jako część swojej deklaracji lub w konstruktorze statycznym. Gdy jawny Konstruktor statyczny nie jest wymagany, zainicjuj pola statyczne w deklaracji, a nie za pomocą konstruktora statycznego w celu zapewnienia lepszej optymalizacji środowiska uruchomieniowego.

> [!Note]
> Chociaż nie jest to bezpośrednio dostępne, obecność jawnego konstruktora statycznego powinna zostać udokumentowana w celu ułatwienia rozwiązywania problemów z wyjątkami inicjalizacji.

### <a name="usage"></a>Użycie

- Typowym zastosowaniem konstruktorów statycznych jest użycie pliku dziennika przez klasę, a Konstruktor jest używany do zapisu wpisów do tego pliku.  
- Konstruktory statyczne są również przydatne podczas tworzenia klas otoki dla niezarządzanego kodu, gdy Konstruktor może wywołać `LoadLibrary` metodę.  

- Konstruktory statyczne są również wygodnym miejscem do wymuszania sprawdzania w czasie wykonywania na parametrze typu, który nie może być sprawdzany w czasie kompilacji za pomocą ograniczeń (ograniczenia parametru typu).

## <a name="example"></a>Przykład
 W tym przykładzie Klasa `Bus` ma Konstruktor statyczny. Po utworzeniu pierwszego wystąpienia elementu `Bus` ( `bus1` ) statyczny Konstruktor jest wywoływany, aby zainicjować klasę. Przykładowe dane wyjściowe sprawdzają, czy Konstruktor statyczny działa tylko raz, nawet jeśli utworzono dwa wystąpienia `Bus` , i że jest on uruchamiany przed uruchomieniem konstruktora wystąpień.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]

## <a name="c-language-specification"></a>specyfikacja języka C#
Aby uzyskać więcej informacji, zobacz sekcję [konstruktory statyczne](~/_csharplang/spec/classes.md#static-constructors) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Klasy statyczne i statyczni członkowie klas](./static-classes-and-static-class-members.md)
- [Finalizatory](./destructors.md)
- [Wytyczne dotyczące projektowania konstruktora](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [Ostrzeżenie o zabezpieczeniach — CA2121: konstruktory statyczne powinny być prywatne](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
