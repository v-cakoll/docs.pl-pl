---
title: Konwersje wskaźników — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 81b2110e6a571e174693fd272d1c6b4bf44dbae3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588219"
---
# <a name="pointer-conversions-c-programming-guide"></a>Konwersje wskaźników (Przewodnik programowania w języku C#)
W poniższej tabeli przedstawiono wstępnie zdefiniowane konwersje niejawnych wskaźników. Konwersje niejawne mogą wystąpić w wielu sytuacjach, w tym wywoływanie metod i instrukcje przypisania.  
  
## <a name="implicit-pointer-conversions"></a>Niejawne konwersje wskaźników  
  
|Z|Zadanie|  
|----------|--------|  
|Dowolny typ wskaźnika|pozycję|  
|wartość null|Dowolny typ wskaźnika|  
  
 Jawna konwersja wskaźnika jest używana do przeprowadzania konwersji, dla których nie istnieje niejawna konwersja za pomocą wyrażenia Cast. W poniższej tabeli przedstawiono te konwersje.  
  
## <a name="explicit-pointer-conversions"></a>Jawne konwersje wskaźników  
  
|Z|Zadanie|  
|----------|--------|  
|Dowolny typ wskaźnika|Dowolny inny typ wskaźnika|  
|bajty, Byte, Short, UShort, int, uint, Long lub ULONG|Dowolny typ wskaźnika|  
|Dowolny typ wskaźnika|bajty, Byte, Short, UShort, int, uint, Long lub ULONG|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie wskaźnik do `int` jest konwertowany na wskaźnik do. `byte` Zauważ, że wskaźnik wskazuje najniższy przyjmowany bajt zmiennej. Po kolejnym zwiększeniu wyniku do rozmiaru `int` (4 bajty) można wyświetlić pozostałe bajty zmiennej.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Typy wskaźników](./pointer-types.md)
- [Typy](../../language-reference/keywords/types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
- [fixed, instrukcja](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/operators/stackalloc.md)
