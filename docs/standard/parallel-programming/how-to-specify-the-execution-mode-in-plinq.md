---
title: 'Porady: określanie trybu wykonywania w PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebea62f33c5df252dd73a0708f31612cd2998728
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580942"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Porady: określanie trybu wykonywania w PLINQ
W tym przykładzie pokazano, jak wymusić PLINQ do obejścia jego domyślny algorytm heurystyczny i parallelize zapytania niezależnie od tego zapytania kształtu.  
  
> [!WARNING]
>  W tym przykładzie jest jedynie do zademonstrowania użycia i mogą nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytania. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ zaprojektowano możliwości paralelizacja. Jednak nie wszystkie zapytania korzyści przetwarzania równoległego. Na przykład jeśli zapytanie zawiera delegata pojedynczego użytkownika, który jest bardzo małego wysiłku, zapytanie zwykle uruchomi szybciej sekwencyjnie. Jest to spowodowane koszty związane z włączaniem parallelizing wykonywania jest droższe niż przyspieszenie, uzyskany. W związku z tym PLINQ automatycznie nie parallelize każdego zapytania. To najpierw sprawdza, czy kształt zapytania i różne operatory wchodzących w jej skład. Oparte na tej analizy, PLINQ w domyślnym trybie wykonanie może zadecydować o wykonać niektóre lub wszystkie zapytania po kolei. Jednak w niektórych przypadkach użytkownik może dowiedzieć się więcej o kwerendy niż PLINQ ma możliwość określenia z jego analizy. Na przykład wiadomo, że delegata jest bardzo kosztowna i czy zapytanie ostatecznie będą korzystać z paralelizacja. W takich przypadkach można użyć <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> — metoda i określ <xref:System.Linq.ParallelExecutionMode.ForceParallelism> wartość nakazać programowi PLINQ zawsze uruchomić kwerendę jako równoległe.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wycinanie i wklejanie go w [próbka danych PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) i wywołaj metodę z `Main`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
