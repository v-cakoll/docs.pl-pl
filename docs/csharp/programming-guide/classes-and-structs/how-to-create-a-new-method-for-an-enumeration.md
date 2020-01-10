---
title: Jak utworzyć nową metodę dla przewodnika C# programowania
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 0d8e562342239c8ac3c53e05086ede9c234d0b63
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705655"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Jak utworzyć nową metodę dla wyliczenia (C# Przewodnik programowania)
Można użyć metod rozszerzających, aby dodać funkcje specyficzne dla określonego typu wyliczeniowego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie Wyliczenie `Grades` reprezentuje możliwe klasy liter, które student może otrzymać w klasie. Metoda rozszerzająca o nazwie `Passing` jest dodawana do typu `Grades`, tak aby każde wystąpienie tego typu było teraz "znane", niezależnie od tego, czy reprezentuje ona przewagę, czy nie.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 Należy zauważyć, że Klasa `Extensions` również zawiera zmienną statyczną, która jest aktualizowana dynamicznie i że wartość zwracana metody rozszerzenia odzwierciedla bieżącą wartość tej zmiennej. Pokazuje to, że w tle metody rozszerzające są wywoływane bezpośrednio w klasie statycznej, w której są zdefiniowane.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Metody rozszerzeń](./extension-methods.md)
