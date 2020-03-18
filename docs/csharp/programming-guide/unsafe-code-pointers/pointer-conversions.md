---
title: Konwersje wskaźnika — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 517166331d2bcf73132269ce2adcf68d5f60b4fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76745364"
---
# <a name="pointer-conversions-c-programming-guide"></a>Konwersje wskaźników (Przewodnik programowania w języku C#)
W poniższej tabeli przedstawiono wstępnie zdefiniowane niejawne konwersje wskaźnika. Konwersje niejawne mogą wystąpić w wielu sytuacjach, w tym wywoływania metody i instrukcji przypisania.  
  
## <a name="implicit-pointer-conversions"></a>Niejawne konwersje wskaźnika  
  
|Z|Do|  
|----------|--------|  
|Dowolny typ wskaźnika|nieważne*|  
|null|Dowolny typ wskaźnika|  
  
 Jawna konwersja wskaźnika służy do wykonywania konwersji, dla których nie ma konwersji niejawnych, przy użyciu wyrażenia rzutowania. W poniższej tabeli przedstawiono te konwersje.  
  
## <a name="explicit-pointer-conversions"></a>Jawne konwersje wskaźnika  
  
|Z|Do|  
|----------|--------|  
|Dowolny typ wskaźnika|Każdy inny typ wskaźnika|  
|sbajt, bajt, krótki, ushort, int, uint, długi lub ulong|Dowolny typ wskaźnika|  
|Dowolny typ wskaźnika|sbajt, bajt, krótki, ushort, int, uint, długi lub ulong|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie wskaźnik `int` do jest konwertowany `byte`na wskaźnik do . Należy zauważyć, że wskaźnik wskazuje najniższy bajt adresowany zmiennej. Podczas sukcesywnego zwiększania wyniku, do rozmiaru `int` (4 bajty), można wyświetlić pozostałe bajty zmiennej.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Typy wskaźnika](pointer-types.md)
- [Typy odwołań](../../language-reference/keywords/reference-types.md)
- [Typy wartości](../../language-reference/builtin-types/value-types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
- [fixed, instrukcja](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/operators/stackalloc.md)
