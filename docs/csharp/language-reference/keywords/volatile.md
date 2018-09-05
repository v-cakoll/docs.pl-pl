---
title: volatile (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: be7e081b18702710c00b5b86a9bc152800f0cf3d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526222"
---
# <a name="volatile-c-reference"></a>volatile (odwołanie w C#)
`volatile` — Słowo kluczowe wskazuje, że pola mogą zostać zmodyfikowane przez wiele wątków, które są wykonywane w tym samym czasie. Pola, które są zadeklarowane `volatile` nie są objęte optymalizacje kompilatora, które zakładają dostępu przez jednego wątku. Te ograniczenia upewnij się, że wszystkie wątki będzie przestrzegać volatile zapisów wykonywane przez inny wątek, w kolejności, w którym zostały wykonane. Nie ma żadnej gwarancji, pojedynczy całkowita kolejności volatile zapisów wyświetlanego ze wszystkich wątków wykonania.  
  
 `volatile` Modyfikator jest zwykle używany dla pola, która jest dostępna w wielu wątkach, bez użycia [blokady](../../../csharp/language-reference/keywords/lock-statement.md) instrukcję, aby serializować dostępu.  
  
 `volatile` — Słowo kluczowe mogą być stosowane do pól z następujących typów:  
  
-   Typy odwołań.  
  
-   Typy wskaźników (w niebezpiecznym kontekście). Należy pamiętać, że chociaż wskaźnika, sama może być nietrwałe, obiekt, który wskazuje nie może. Innymi słowy nie można zadeklarować "wskaźnik volatile."  
  
-   Typy takie jak sbyte, byte, short, ushort, int, uint, char, float i bool.  
  
-   Typ wyliczeniowy z jednym z następujących typów podstawowych: byte, sbyte, short, ushort, int lub uint.  
  
-   Parametry typu ogólnego, znane jako typy odwołań.  
  
-   <xref:System.IntPtr> i <xref:System.UIntPtr>.  
  
 Volatile — słowo kluczowe będzie stosowany tylko do pól klasy lub struktury. Nie można zadeklarować zmienne lokalne `volatile`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób deklarowania zmiennej pole publiczne `volatile`.  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wątek wiadomości pomocniczych lub procesu roboczego można tworzyć i używany do wykonywania przetwarzania równolegle z wątku głównego. Aby uzyskać ogólne informacje o wielowątkowości, zobacz [zarządzana wątkowość](../../../standard/threading/index.md) i [wątki (C#)](../../programming-guide/concepts/threading/index.md).  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)
