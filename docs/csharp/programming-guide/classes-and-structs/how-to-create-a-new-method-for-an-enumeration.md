---
title: 'Instrukcje: Utworzenie nowej metody wyliczania - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: f8495cd747cf895c4da34c216ba9285182890af1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238732"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Instrukcje: Utworzenie nowej metody wyliczania (C# Programming Guide)
Metody rozszerzające umożliwia dodawanie funkcji charakterystycznej do typu określonego typu wyliczeniowego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `Grades` wyliczenie reprezentuje możliwe litery ocen, które student może pojawić się w klasie. Metody rozszerzenia o nazwie `Passing` jest dodawany do `Grades` wpisz, aby każde wystąpienie tego typu teraz "wie" czy reprezentuje klasy przekazywanie, czy nie.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 Należy pamiętać, że `Extensions` klasa zawiera także zmienną statyczną, która jest aktualizowana dynamicznie i że wartość zwracana przez metoda rozszerzenia odzwierciedla bieżącą wartość tej zmiennej. Oznacza to, że w tle metody rozszerzenia są wywoływane bezpośrednio na klasy statycznej, w której są zdefiniowane.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten kod, skopiuj i wklej go do programu Visual C# projekt aplikacji konsoli, która została utworzona w programie Visual Studio. Domyślnie ten projekt jest przeznaczony dla wersji 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], i ma odwołania do System.Core.dll i `using` dyrektywy dla System.Linq. Jeśli co najmniej jeden z tych wymagań brakuje z projektu, możesz je dodać ręcznie.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Metody rozszerzeń](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
