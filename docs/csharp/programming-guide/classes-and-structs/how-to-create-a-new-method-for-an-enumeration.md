---
title: Jak utworzyć nową metodę wyliczenia - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 0d8e562342239c8ac3c53e05086ede9c234d0b63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705655"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Jak utworzyć nową metodę wyliczenia (Przewodnik programowania C#)
Metody rozszerzenia służy do dodawania funkcji specyficznych dla określonego typu wyliczenia.  
  
## <a name="example"></a>Przykład  
 W poniższym `Grades` przykładzie wyliczenie reprezentuje możliwe oceny liter, które uczeń może otrzymać w klasie. Metoda rozszerzenia `Passing` o nazwie `Grades` jest dodawany do typu, tak aby każde wystąpienie tego typu teraz "wie", czy reprezentuje ocenę przekazywania, czy nie.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 Należy zauważyć, że `Extensions` klasa zawiera również zmienną statyczną, która jest aktualizowana dynamicznie i że zwracana wartość metody rozszerzenia odzwierciedla bieżącą wartość tej zmiennej. Pokazuje to, że w tle metody rozszerzenia są wywoływane bezpośrednio na klasy statycznej, w której są zdefiniowane.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Metody rozszerzeń](./extension-methods.md)
