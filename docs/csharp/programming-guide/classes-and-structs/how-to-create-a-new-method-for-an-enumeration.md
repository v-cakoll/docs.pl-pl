---
title: 'Instrukcje: Utwórz nową metodę dla przewodnika C# programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 99a2005e1a64fa214776145a903341fb162f0633
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597047"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Instrukcje: Tworzenie nowej metody dla wyliczenia (C# Przewodnik programowania)
Można użyć metod rozszerzających, aby dodać funkcje specyficzne dla określonego typu wyliczeniowego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `Grades` Wyliczenie reprezentuje możliwe klasy liter, które student może odebrać w klasie. Metoda rozszerzenia o nazwie `Passing` jest dodawana `Grades` do typu, tak aby każde wystąpienie tego typu było teraz "znane", niezależnie od tego, czy reprezentuje ona przewagę, czy nie.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 Należy zauważyć, `Extensions` że Klasa zawiera również zmienną statyczną, która jest aktualizowana dynamicznie i że wartość zwracana metody rozszerzenia odzwierciedla bieżącą wartość tej zmiennej. Pokazuje to, że w tle metody rozszerzające są wywoływane bezpośrednio w klasie statycznej, w której są zdefiniowane.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Metody rozszerzeń](./extension-methods.md)
