---
title: "Konstruktory statyczne (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee5448095cf06c2473c94bae542c02557918271a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="static-constructors-c-programming-guide"></a>Konstruktory statyczne (Przewodnik programowania w języku C#)
Statyczny Konstruktor używany do inicjowania żadnego [statycznych](../../../csharp/language-reference/keywords/static.md) danych, lub wykonania określonej akcji, która musi zostać wykonana tylko raz. Jest ona wywoływana automatycznie przed utworzeniu pierwszego wystąpienia lub odwołuje się żadnych statycznych elementów członkowskich.  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 Konstruktory statyczne mieć następujące właściwości:  
  
-   Konstruktor statyczny zająć modyfikatory dostępu lub nie ma parametrów.  
  
-   Konstruktor statyczny jest wywoływana automatycznie zainicjować [klasy](../../../csharp/language-reference/keywords/class.md) przed utworzeniu pierwszego wystąpienia lub odwołuje się żadnych statycznych elementów członkowskich.  
  
-   Konstruktor statyczny nie może wywołać bezpośrednio.  
  
-   Użytkownik nie ma kontroli na kiedy Konstruktor statyczny jest wykonywane w programie.  
  
-   Typowym zastosowaniem konstruktorów statycznych jest po klasie jest używany plik dziennika i Konstruktor jest używany do zapisywania wpisów do tego pliku.  
  
-   Konstruktory statyczne są także przydatne podczas tworzenia klasy otoki dla niezarządzanego kodu, gdy można wywołać konstruktora `LoadLibrary` metody.  
  
-   Jeśli w konstruktorze statycznym zgłasza wyjątek, środowisko uruchomieniowe nie wywoła go po raz drugi, a typ pozostanie niezainicjowanej przez czas ich istnienia domeny aplikacji, w którym jest uruchomiony program.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa `Bus` ma Konstruktor statyczny. Po pierwsze wystąpienie `Bus` utworzeniu (`bus1`), Konstruktor statyczny jest wywoływane w celu zainicjowania klasy. Przykładowe dane wyjściowe sprawdza, czy Konstruktor statyczny uruchamiane tylko jeden raz, nawet jeśli dwa wystąpienia `Bus` są tworzone i że będzie ono przeprowadzane przed uruchomieniem konstruktora wystąpienia.  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Klasy statyczne i statyczni członkowie klas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)
