---
title: Konstruktory statyczne - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 9cf977be84a4d3098e009d5a58d0c12ad2000e92
ms.sourcegitcommit: ced0cccf15adfd492f8196cb739f01dde52c9252
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/14/2019
ms.locfileid: "67135647"
---
# <a name="static-constructors-c-programming-guide"></a>Konstruktory statyczne (Przewodnik programowania w języku C#)
Statyczny Konstruktor jest wykorzystywany do inicjacji dowolne [statyczne](../../../csharp/language-reference/keywords/static.md) danych, lub do wykonania określonej akcji, która musi zostać wykonana tylko raz. Jest wywoływana automatycznie przed pierwsze wystąpienie jest tworzone lub żadnych statycznych składowych są wywoływane.  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
 
## <a name="remarks"></a>Uwagi
Konstruktory statyczne mają następujące właściwości:  
  
- Statyczny Konstruktor zająć modyfikatory dostępu lub nie mieć parametrów.  

- Klasa lub struktura może mieć tylko jeden konstruktor statyczny.

- Konstruktory statyczne nie może być dziedziczona ani przeciążone.

- Konstruktor statyczny nie może być wywoływana bezpośrednio i jest przeznaczone wyłącznie do wywołania przez środowisko uruchomieniowe języka wspólnego (CLR). Jest wywoływane automatycznie.

- Użytkownik nie ma kontroli na gdy Konstruktor statyczny jest wykonywane w programie.
  
- Statyczny Konstruktor jest wywoływana automatycznie zainicjować [klasy](../../../csharp/language-reference/keywords/class.md) przed pierwsze wystąpienie jest tworzone lub żadnych statycznych składowych są wywoływane. Konstruktor statyczny będzie wykonywany przed konstruktora wystąpień. Należy pamiętać, że typ statyczny Konstruktor jest wywoływana po wywołaniu metody statycznej przypisanej do zdarzenia lub delegata, a nie w przypadku, gdy jest ona przypisana. Jeśli pole statyczne inicjatory zmiennych są obecne w klasie statyczny Konstruktor, zostaną one wykonane w kolejności tekstowych, w jakiej występują w deklaracji klasy, bezpośrednio przed wykonaniem Konstruktor statyczny.

- Jeśli nie podasz konstruktora statycznego zainicjować pola statyczne, wszystkie pola statyczne są inicjowane na ich wartości domyślne, zgodnie z zaleceniami z [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md). 
  
- Jeśli statyczny Konstruktor zgłasza wyjątek, środowisko wykonawcze nie wywoła go drugi raz, a typ pozostanie niezainicjowanej okres istnienia domeny aplikacji, w którym jest uruchomiony program. Najczęściej <xref:System.TypeInitializationException> wyjątek jest zgłaszany, gdy Konstruktor statyczny nie może utworzyć wystąpienia typu lub które zdarzyły się nieobsługiwany wyjątek w konstruktorze statycznym. Dla niejawnego konstruktorów statycznych, które nie są jawnie zdefiniowane w kodzie źródłowym rozwiązywania problemów może wymagać kontroli kodu języka pośredniego (IL).

- Obecność statyczny Konstruktor uniemożliwia dodanie <xref:System.Reflection.TypeAttributes.BeforeFieldInit> typu atrybutu. Ogranicza to optymalizacji środowiska wykonawczego.

- Pole jest zadeklarowane jako `static readonly` mogą być przypisywane tylko jako część swojej deklaracji lub w konstruktorze statycznym. Gdy jawny, statyczny Konstruktor nie jest wymagane, Inicjuj pola statyczne w deklaracji, a nie za pomocą Konstruktor statyczny w celu uzyskania lepszej optymalizacji środowiska uruchomieniowego.

> [!Note]
> Jednak bezpośrednio niedostępny, powinno być udokumentowane obecności jawny, statyczny Konstruktor, aby ułatwić rozwiązywanie problemów z wyjątkami inicjowania.

### <a name="usage"></a>Użycie

- Typowym zastosowaniem konstruktorów statycznych jest, gdy klasa korzysta z pliku dziennika i konstruktora jest używany do zapisywania wpisów w tym pliku.  
- Konstruktory statyczne są także przydatne przy tworzeniu klas otoki dla niezarządzanego kodu podczas można wywołać konstruktora `LoadLibrary` metody.  

- Konstruktory statyczne są również wygodne miejsce do wymuszają operacje sprawdzania czasu wykonywania na parametr typu, który nie można sprawdzić w czasie kompilacji za pomocą ograniczeń (ograniczenia parametru typu).

## <a name="example"></a>Przykład
 W tym przykładzie klasa `Bus` ma Konstruktor statyczny. Po pierwsze wystąpienie `Bus` zostanie utworzony (`bus1`), statyczny Konstruktor jest wywoływane w celu zainicjowania klasy. Przykładowe dane wyjściowe weryfikuje, że Konstruktor statyczny działa tylko jeden raz, nawet jeśli dwa wystąpienia `Bus` są tworzone, to jest uruchamiane przed uruchomieniem konstruktora wystąpienia.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]
 
## <a name="c-language-specification"></a>specyfikacja języka C#
Aby uzyskać więcej informacji, zobacz [konstruktorów statycznych](~/_csharplang/spec/classes.md#static-constructors) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Klasy statyczne i statyczne elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [Wytyczne dotyczące projektowania konstruktora](../../../docs/standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [Ostrzeżenie o zabezpieczeniach - CA2121: Konstruktory statyczne powinny być prywatne](https://docs.microsoft.com/en-us/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
