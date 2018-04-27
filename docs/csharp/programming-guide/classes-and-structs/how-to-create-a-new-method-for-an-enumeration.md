---
title: 'Porady: utworzenie nowej metody wyliczania (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
caps.latest.revision: 7
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b05d9f910e8c268fded8cdcc462392a1e80efdb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Porady: utworzenie nowej metody wyliczania (Przewodnik programowania w języku C#)
Metody rozszerzenia służy do dodawania funkcji charakterystycznej do wyliczenia określonego typu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `Grades` wyliczenie reprezentuje klas możliwych list, które student może pojawić się w klasie. Metody rozszerzenia o nazwie `Passing` jest dodawany do `Grades` wpisz, aby każde wystąpienie tego typu teraz "wie" czy reprezentuje klasy przekazywanie, czy nie.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 Należy pamiętać, że `Extensions` klasa zawiera także zmienną statyczną, która jest aktualizowana dynamicznie, i że zwracana wartość metody rozszerzenia odzwierciedla bieżącą wartość tej zmiennej. Oznacza to, że w tle metody rozszerzenia są wywoływane bezpośrednio w przypadku klasy statycznej, w którym są zdefiniowane.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten kod, skopiuj i wklej go do języka Visual C# projektu aplikacji konsolowej utworzony w programie Visual Studio. Domyślnie ten projekt jest przeznaczony dla wersji 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], i zawiera odwołania do System.Core.dll i `using` dyrektywy dla System.Linq. Jeśli co najmniej jeden z tych wymagań brakuje z projektu, należy je dodać ręcznie.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Metody rozszerzeń](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
