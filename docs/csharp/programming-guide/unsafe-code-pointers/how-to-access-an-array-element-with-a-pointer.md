---
title: 'Porady: uzyskiwanie dostępu do elementu tablicy za pomocą wskaźnika (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 92eb7a79c0e7522d1474537aeefbfdb083a11dc2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a>Porady: uzyskiwanie dostępu do elementu tablicy za pomocą wskaźnika (Przewodnik programowania w języku C#)
W niebezpiecznym kontekście uzyskujesz dostęp elementu w pamięci przy użyciu wskaźnika elementu dostępu, jak pokazano w poniższym przykładzie:  
  
```  
 char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 Wyrażenia w nawiasach kwadratowych musi istnieć możliwość niejawnego przekonwertowania do `int`, `uint`, `long`, lub `ulong`. Operacja p [e] jest odpowiednikiem *(p+e). Podobnie jak C i C++, dostęp do elementu wskaźnik nie sprawdza liczbach błędy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie 123 lokalizacji pamięci są przydzielone do tablicy znaków, `charPointer`. Tablica jest używana do wyświetlania listy małe i wielkie litery w dwóch [dla](../../../csharp/language-reference/keywords/for.md) pętli.  
  
 Zwróć uwagę, że wyrażenie `charPointer[i]` jest równoznaczne z wyrażeniem `*(charPointer + i)`, i można uzyskać ten sam rezultat przy użyciu jednej z dwóch wyrażeń.  
  
 [!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]  
  
 **Wielkie litery:**  
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**  
**Małe litery:**  
**abcdefghijklmnopqrstuvwxyz**   
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
