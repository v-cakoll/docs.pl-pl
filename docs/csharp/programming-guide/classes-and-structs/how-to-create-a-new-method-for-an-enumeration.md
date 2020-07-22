---
title: Jak utworzyć nową metodę dla Przewodnik programowania w języku C#
description: Dowiedz się, jak przy użyciu metod rozszerzania dodać funkcję do wyliczenia w języku C#. Ten przykład pokazuje metodę rozszerzenia o nazwie Pass dla wyliczenia o nazwie klasy.
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 6c01a73476e98e8344a7a8dc35a5fd80384fc7a2
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864491"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Jak utworzyć nową metodę dla wyliczenia (Przewodnik programowania w języku C#)
Można użyć metod rozszerzających, aby dodać funkcje specyficzne dla określonego typu wyliczeniowego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `Grades` Wyliczenie reprezentuje możliwe klasy liter, które student może odebrać w klasie. Metoda rozszerzenia o nazwie `Passing` jest dodawana do `Grades` typu, tak aby każde wystąpienie tego typu było teraz "znane", niezależnie od tego, czy reprezentuje ona przewagę, czy nie.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 Należy zauważyć, że `Extensions` Klasa zawiera również zmienną statyczną, która jest aktualizowana dynamicznie i że wartość zwracana metody rozszerzenia odzwierciedla bieżącą wartość tej zmiennej. Pokazuje to, że w tle metody rozszerzające są wywoływane bezpośrednio w klasie statycznej, w której są zdefiniowane.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Metody rozszerzające](./extension-methods.md)
