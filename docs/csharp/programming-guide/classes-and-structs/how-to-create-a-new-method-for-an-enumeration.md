---
title: 'Instrukcje: Utworzenie nowej metody wyliczania - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 2ca388d19c0e4e1b098076caa5baa0a83cc0dd4c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585886"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Instrukcje: Utworzenie nowej metody wyliczania (C# Programming Guide)
Metody rozszerzające umożliwia dodawanie funkcji charakterystycznej do typu określonego typu wyliczeniowego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `Grades` wyliczenie reprezentuje możliwe litery ocen, które student może pojawić się w klasie. Metody rozszerzenia o nazwie `Passing` jest dodawany do `Grades` wpisz, aby każde wystąpienie tego typu teraz "wie" czy reprezentuje klasy przekazywanie, czy nie.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 Należy pamiętać, że `Extensions` klasa zawiera także zmienną statyczną, która jest aktualizowana dynamicznie i że wartość zwracana przez metoda rozszerzenia odzwierciedla bieżącą wartość tej zmiennej. Oznacza to, że w tle metody rozszerzenia są wywoływane bezpośrednio na klasy statycznej, w której są zdefiniowane.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Metody rozszerzeń](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
