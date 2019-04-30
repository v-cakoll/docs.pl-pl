---
title: Konstruktory statyczne - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 6a990dbf26ac1a6bdc642442b9f4b75c05ee9635
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703039"
---
# <a name="static-constructors-c-programming-guide"></a>Konstruktory statyczne (Przewodnik programowania w języku C#)
Statyczny Konstruktor jest wykorzystywany do inicjacji dowolne [statyczne](../../../csharp/language-reference/keywords/static.md) danych, lub do wykonania określonej akcji, która musi zostać wykonana tylko raz. Jest wywoływana automatycznie przed pierwsze wystąpienie jest tworzone lub żadnych statycznych składowych są wywoływane.  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
  
 Konstruktory statyczne mają następujące właściwości:  
  
- Statyczny Konstruktor zająć modyfikatory dostępu lub nie mieć parametrów.  
  
- Statyczny Konstruktor jest wywoływana automatycznie zainicjować [klasy](../../../csharp/language-reference/keywords/class.md) przed pierwsze wystąpienie jest tworzone lub żadnych statycznych składowych są wywoływane.  
  
- Konstruktor statyczny nie może wywołać bezpośrednio.  
  
- Użytkownik nie ma kontroli na gdy Konstruktor statyczny jest wykonywane w programie.  
  
- Typowym zastosowaniem konstruktorów statycznych jest, gdy klasa korzysta z pliku dziennika i konstruktora jest używany do zapisywania wpisów w tym pliku.  
  
- Konstruktory statyczne są także przydatne przy tworzeniu klas otoki dla niezarządzanego kodu podczas można wywołać konstruktora `LoadLibrary` metody.  
  
- Jeśli statyczny Konstruktor zgłasza wyjątek, środowisko wykonawcze nie wywoła go drugi raz, a typ pozostanie niezainicjowanej okres istnienia domeny aplikacji, w którym jest uruchomiony program.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa `Bus` ma Konstruktor statyczny. Po pierwsze wystąpienie `Bus` zostanie utworzony (`bus1`), statyczny Konstruktor jest wywoływane w celu zainicjowania klasy. Przykładowe dane wyjściowe weryfikuje, że Konstruktor statyczny działa tylko jeden raz, nawet jeśli dwa wystąpienia `Bus` są tworzone, to jest uruchamiane przed uruchomieniem konstruktora wystąpienia.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Klasy statyczne i statyczne elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)
