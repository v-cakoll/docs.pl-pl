---
title: Konstruktory statyczne C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 27a7cbb1490f42811c79778382063980f3828395
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964091"
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
  
- Statyczny Konstruktor jest automatycznie wywoływany w celu zainicjowania [klasy](../../language-reference/keywords/class.md) przed utworzeniem pierwszego wystąpienia lub odwołania do jakichkolwiek statycznych elementów członkowskich. Statyczny Konstruktor zostanie uruchomiony przed konstruktorem wystąpienia. Należy zauważyć, że statyczny Konstruktor typu jest wywoływany, gdy metoda statyczna przypisana do zdarzenia lub delegata jest wywoływana, a nie w momencie przypisania. Jeśli inicjatory zmiennych pól statycznych są obecne w klasie konstruktora statycznego, zostaną one wykonane w kolejności tekstowej, w której pojawiają się w deklaracji klasy bezpośrednio przed wykonaniem konstruktora statycznego.

- Jeśli nie postanowisz statycznego konstruktora do zainicjowania pól statycznych, wszystkie pola statyczne są inicjowane do ich wartości domyślnej, jak wymieniono w [domyślnych wartości C# typów](../../language-reference/builtin-types/default-values.md).
  
- Jeśli Konstruktor statyczny zgłosi wyjątek, środowisko uruchomieniowe nie wywołaje go po raz drugi, a typ pozostanie niezainicjowany przez okres istnienia domeny aplikacji, w której uruchomiono program. Najczęściej wyjątek <xref:System.TypeInitializationException> jest zgłaszany, gdy Konstruktor statyczny nie może utworzyć wystąpienia typu lub dla nieobsłużonego wyjątku w konstruktorze statycznym. W przypadku niejawnych konstruktorów statycznych, które nie są jawnie zdefiniowane w kodzie źródłowym, rozwiązywanie problemów może wymagać inspekcji kodu języka pośredniego (IL).

- Obecność konstruktora statycznego uniemożliwia dodanie atrybutu typu <xref:System.Reflection.TypeAttributes.BeforeFieldInit>. To ogranicza optymalizację środowiska uruchomieniowego.

- Pole zadeklarowane jako `static readonly` mogą być przypisywane tylko jako część swojej deklaracji lub w konstruktorze statycznym. Gdy jawny Konstruktor statyczny nie jest wymagany, zainicjuj pola statyczne w deklaracji, a nie za pomocą konstruktora statycznego w celu zapewnienia lepszej optymalizacji środowiska uruchomieniowego.

> [!Note]
> Chociaż nie jest to bezpośrednio dostępne, obecność jawnego konstruktora statycznego powinna zostać udokumentowana w celu ułatwienia rozwiązywania problemów z wyjątkami inicjalizacji.

### <a name="usage"></a>Pomiar

- Typowym zastosowaniem konstruktorów statycznych jest użycie pliku dziennika przez klasę, a Konstruktor jest używany do zapisu wpisów do tego pliku.  
- Konstruktory statyczne są również przydatne podczas tworzenia klas otoki dla niezarządzanego kodu, gdy Konstruktor może wywołać metodę `LoadLibrary`.  

- Konstruktory statyczne są również wygodnym miejscem do wymuszania sprawdzania w czasie wykonywania na parametrze typu, który nie może być sprawdzany w czasie kompilacji za pomocą ograniczeń (ograniczenia parametru typu).

## <a name="example"></a>Przykład
 W tym przykładzie Klasa `Bus` ma statyczny Konstruktor. Po utworzeniu pierwszego wystąpienia `Bus` (`bus1`), Konstruktor statyczny jest wywoływany w celu zainicjowania klasy. Przykładowe dane wyjściowe sprawdzają, czy statyczny Konstruktor działa tylko raz, nawet jeśli dwa wystąpienia `Bus` są tworzone i są uruchamiane przed uruchomieniem konstruktora wystąpień.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]
 
## <a name="c-language-specification"></a>specyfikacja języka C#
Aby uzyskać więcej informacji, zobacz sekcję " [konstruktory statyczne](~/_csharplang/spec/classes.md#static-constructors) " [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Klasy statyczne i statyczne elementy członkowskie klas](./static-classes-and-static-class-members.md)
- [Finalizatory](./destructors.md)
- [Wytyczne dotyczące projektowania konstruktora](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [Ostrzeżenie o zabezpieczeniach — CA2121: konstruktory statyczne powinny być prywatne](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
