---
title: volatile (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: 29
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4f63c4b7b2d32afac9b0d086ecd64cd2b29366f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="volatile-c-reference"></a>volatile (odwołanie w C#)
`volatile` — Słowo kluczowe wskazuje, czy pole może zostać zmodyfikowany przez wiele wątków, które są wykonywane w tym samym czasie. Pola, które są zadeklarowane `volatile` nie są objęte optymalizacje kompilatora, które przyjmuje dostępu przez jednego wątku. Dzięki temu, czy aktualną wartość znajduje się w polu przez cały czas.  
  
 `volatile` Modyfikator jest zwykle używany dla pola, który jest dostępny przez wiele wątków bez użycia [blokady](../../../csharp/language-reference/keywords/lock-statement.md) instrukcji do serializacji dostępu.  
  
 `volatile` — Słowo kluczowe może odnosić się do pól z następujących typów:  
  
-   Typy referencyjne.  
  
-   Typy wskaźnika (w niebezpiecznym kontekście). Należy pamiętać, że chociaż sama wskaźnik może być nietrwałe, obiekt, który wskazuje nie. Innymi słowy nie można zadeklarować "wskaźnik do volatile."  
  
-   Typy, takie jak sbyte, byte, short, ushort, int, uint, char, float i bool.  
  
-   Typ wyliczeniowy z jednym z następujących typów podstawowych: byte, sbyte, short, ushort, int lub uint.  
  
-   Parametry typu ogólnego, znane jako typy referencyjne.  
  
-   <xref:System.IntPtr> i <xref:System.UIntPtr>.  
  
 Volatile — słowo kluczowe można zastosować tylko do pól klasy lub struktury. Nie można deklarować zmiennych lokalnych `volatile`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zadeklarować zmiennej pole publiczne jako `volatile`.  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak wątek pomocniczy lub procesu roboczego można tworzyć i używane do przetwarzania równolegle z podstawowym wątku. Aby uzyskać ogólne informacje o wielowątkowości, zobacz [wątki (C#)](../../../standard/threading/index.md) i [zarządzanych wątków](../../programming-guide/concepts/threading/index.md).  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)
