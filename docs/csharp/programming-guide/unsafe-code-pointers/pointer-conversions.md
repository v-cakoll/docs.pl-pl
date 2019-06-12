---
title: Konwersje wskaźników - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 3cef2f2d2af2d285504daea14aa57c55b9e9a21b
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833457"
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
- [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/operators/stackalloc.md)
