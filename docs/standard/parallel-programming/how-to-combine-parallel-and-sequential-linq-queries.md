---
title: 'Porady: łączenie równoległych i sekwencyjnych zapytań LINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fd67d5f0cb5af33dc2b79f86148557a0dca6ec4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036323"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>Porady: łączenie równoległych i sekwencyjnych zapytań LINQ
W tym przykładzie pokazano, jak używać <xref:System.Linq.ParallelEnumerable.AsSequential%2A> metodę, aby nakazać PLINQ przetwarzają wszystkie kolejne operatory w zapytaniu sekwencyjnie. Mimo że zazwyczaj mniejsza niż równoległego przetwarzania sekwencyjnych czasami jest niezbędnych do wyprodukowania poprawne wyniki.  
  
> [!WARNING]
>  W tym przykładzie jest jedynie do zademonstrowania określonych użycia i może nie działać szybciej niż równoważna sekwencyjnego LINQ do kwerendy obiekty. Aby uzyskać więcej informacji na temat przyspieszenie zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano jeden scenariusz, w którym <xref:System.Linq.ParallelEnumerable.AsSequential%2A> jest wymagany, a mianowicie zachować kolejność, który został ustanowiony klauzuli poprzedniego zapytania.  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować i uruchomić ten kod, wklej go do [próbka danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) projektu, Dodaj wiersz w celu wywołania metody z `Main`, i naciśnij klawisz F5.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
