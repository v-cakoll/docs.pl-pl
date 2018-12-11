---
title: Konstruktory statyczne - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: fabcbb084a74334a7a1bcddb9a04cc6705caeb29
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53234932"
---
# <a name="static-constructors-c-programming-guide"></a>Konstruktory statyczne (Przewodnik programowania w języku C#)
Statyczny Konstruktor jest wykorzystywany do inicjacji dowolne [statyczne](../../../csharp/language-reference/keywords/static.md) danych, lub do wykonania określonej akcji, która musi zostać wykonana tylko raz. Jest wywoływana automatycznie przed pierwsze wystąpienie jest tworzone lub żadnych statycznych składowych są wywoływane.  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 Konstruktory statyczne mają następujące właściwości:  
  
-   Statyczny Konstruktor zająć modyfikatory dostępu lub nie mieć parametrów.  
  
-   Statyczny Konstruktor jest wywoływana automatycznie zainicjować [klasy](../../../csharp/language-reference/keywords/class.md) przed pierwsze wystąpienie jest tworzone lub żadnych statycznych składowych są wywoływane.  
  
-   Konstruktor statyczny nie może wywołać bezpośrednio.  
  
-   Użytkownik nie ma kontroli na gdy Konstruktor statyczny jest wykonywane w programie.  
  
-   Typowym zastosowaniem konstruktorów statycznych jest, gdy klasa korzysta z pliku dziennika i konstruktora jest używany do zapisywania wpisów w tym pliku.  
  
-   Konstruktory statyczne są także przydatne przy tworzeniu klas otoki dla niezarządzanego kodu podczas można wywołać konstruktora `LoadLibrary` metody.  
  
-   Jeśli statyczny Konstruktor zgłasza wyjątek, środowisko wykonawcze nie wywoła go drugi raz, a typ pozostanie niezainicjowanej okres istnienia domeny aplikacji, w którym jest uruchomiony program.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa `Bus` ma Konstruktor statyczny. Po pierwsze wystąpienie `Bus` zostanie utworzony (`bus1`), statyczny Konstruktor jest wywoływane w celu zainicjowania klasy. Przykładowe dane wyjściowe weryfikuje, że Konstruktor statyczny działa tylko jeden raz, nawet jeśli dwa wystąpienia `Bus` są tworzone, to jest uruchamiane przed uruchomieniem konstruktora wystąpienia.  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Klasy statyczne i statyczne elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)
