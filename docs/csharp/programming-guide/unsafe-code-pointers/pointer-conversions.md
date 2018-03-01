---
title: "Konwersje wskaźników (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36589d139c91e04d9e3d8b31281a91c26b85a5d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-conversions-c-programming-guide"></a>Konwersje wskaźników (Przewodnik programowania w języku C#)
W poniższej tabeli przedstawiono wstępnie zdefiniowane wskaźnika niejawne konwersje. Niejawne konwersje może wystąpić w wielu sytuacjach, w tym instrukcje metody wywoływania i przypisanie.  
  
## <a name="implicit-pointer-conversions"></a>Wskaźnik niejawne konwersje  
  
|Z|Do|  
|----------|--------|  
|Dowolny typ wskaźnika|void *|  
|null|Dowolny typ wskaźnika|  
  
 Konwersja jawna wskaźnika jest używany do wykonywania konwersji, dla których nie jest niejawna konwersja, używając wyrażenia rzutowania. W poniższej tabeli przedstawiono te konwersji.  
  
## <a name="explicit-pointer-conversions"></a>Konwersje jawne wskaźników  
  
|Z|Do|  
|----------|--------|  
|Dowolny typ wskaźnika|Innego typu wskaźnika|  
|sbyte, byte, short, ushort, int, uint, long lub ulong|Dowolny typ wskaźnika|  
|Dowolny typ wskaźnika|sbyte, byte, short, ushort, int, uint, long lub ulong|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie wskaźnik do `int` jest konwertowana na wskaźnik do `byte`. Zwróć uwagę, że wskaźnik wskazuje najniższa bajtów zaadresowane zmiennej. Gdy kolejno inkrementacji wyniku do rozmiaru `int` (4 bajty), można wyświetlić Pozostała liczba bajtów zmiennej.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy wskaźnika](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [Fixed — instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
