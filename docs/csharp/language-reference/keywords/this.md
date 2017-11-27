---
title: "this (odwołanie w C#)"
description: "to słowo kluczowe (odwołanie w C#)"
keywords: "Ta (C#), to słowo kluczowe (C#), to słowo kluczowe (odwołanie w C#), to słowo kluczowe (język odwołanie w C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords: this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f159967707061481a34e72a97ec8cc8316d982ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="this-c-reference"></a>this (odwołanie w C#)
`this` — Słowo kluczowe odwołuje się do bieżącego wystąpienia klasy, a także jest używane jako modyfikator pierwszy parametr metody rozszerzenia.  
  
> [!NOTE]
>  W tym artykule omówiono używanie `this` z wystąpień klasy. Aby uzyskać więcej informacji dotyczących używania jej w metody rozszerzenia, zobacz [metody rozszerzenia](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
 Poniżej przedstawiono typowe zastosowania `this`:  
  
-   Aby zakwalifikować członków ukryty przez podobne nazwy, na przykład:  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   Aby przekazać obiektu jako parametr do innych metod, na przykład:  
  
    ```  
    CalcTax(this);  
    ```  
  
-   Aby zadeklarować indeksatorów, na przykład:  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 Statyczne funkcje Członkowskie, ponieważ istnieją one na poziomie klasy, a nie jako część obiektu nie jest dostępna `this` wskaźnika. Błąd w odwołaniu do `this` w metodzie statycznej.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `this` są używane do kwalifikowania `Employee` klasy elementów członkowskich, `name` i `alias`, które zostały ukryte za podobne nazwy. On również używany do przekazywania obiektu do metody `CalcTax`, która należy do innej klasy.  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Podstawa](../../../csharp/language-reference/keywords/base.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
