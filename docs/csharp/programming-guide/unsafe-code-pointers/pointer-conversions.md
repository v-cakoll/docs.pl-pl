---
title: Konwersje wskaźników - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 91be48aa2ca64b152af3dc3f33c713bf4adac0c7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968390"
---
# <a name="pointer-conversions-c-programming-guide"></a>Konwersje wskaźników (Przewodnik programowania w języku C#)
W poniższej tabeli przedstawiono konwersje wskaźnika niejawne wstępnie zdefiniowane. Niejawne konwersje mogą wystąpić w wielu sytuacjach, w tym metody wywoływania i przypisania poufności informacji.  
  
## <a name="implicit-pointer-conversions"></a>Konwersje niejawne wskaźników  
  
|Z|Zadanie|  
|----------|--------|  
|Dowolny typ wskaźnika|void *|  
|wartość null|Dowolny typ wskaźnika|  
  
 Konwersja jawna wskaźnika jest używany do wykonywania konwersji, dla których istnieje niejawna konwersja, za pomocą wyrażenia rzutowania. W poniższej tabeli przedstawiono takiej konwersji.  
  
## <a name="explicit-pointer-conversions"></a>Konwersje jawne wskaźników  
  
|Z|Zadanie|  
|----------|--------|  
|Dowolny typ wskaźnika|Dowolny typ wskaźnika|  
|sbyte, bajt, short, ushort, int, uint, long lub ulong|Dowolny typ wskaźnika|  
|Dowolny typ wskaźnika|sbyte, bajt, short, ushort, int, uint, long lub ulong|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie, wskaźnik do `int` jest konwertowana na wskaźnik do `byte`. Należy zauważyć, że wskaźnik wskazuje najniższą zaadresowane bajt zmiennej. Gdy kolejno inkrementacji wyniku przy rozmiarze `int` (4 bajtów), można wyświetlić pozostałe bajty zmiennej.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
