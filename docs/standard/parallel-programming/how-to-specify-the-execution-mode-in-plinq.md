---
title: 'Instrukcje: Określanie trybu wykonywania w PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: 39ccde003b60ac9cbcff7ab824103a9cf37cc453
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288098"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Instrukcje: Określanie trybu wykonywania w PLINQ

Ten przykład pokazuje, jak wymusić PLINQ, aby pominąć domyślne heurystyke i zrównoleglanie zapytanie niezależnie od kształtu zapytania.  
  
> [!NOTE]
> Ten przykład jest przeznaczony do zademonstrowania użycia i może nie działać szybciej niż równoważne LINQ to Objects sekwencyjne zapytanie. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [Opis przyspieszenie w PLINQ](understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ zaprojektowano w celu wykorzystania możliwości programu przetwarzanie równoległe. Jednak nie wszystkie zapytania korzystają z wykonywania równoległego. Na przykład, gdy zapytanie zawiera pojedynczego delegata użytkownika, który wykonuje małą ilość pracy, zapytanie będzie zazwyczaj wykonywane szybciej sekwencyjnie. Wykonywanie sekwencyjne jest szybsze, ponieważ obciążenie związane z włączaniem wykonywania przekształcają jest droższe niż uzyskany przyspieszenie. W związku z tym PLINQ nie jest automatycznie zrównoleglanie wszystkich zapytań. Najpierw analizuje kształt zapytania i różne operatory, które go tworzą. Na podstawie tej analizy PLINQ w domyślnym trybie wykonywania może zdecydować się na wykonanie niektórych lub wszystkich zapytań sekwencyjnie. Jednak w niektórych przypadkach można dowiedzieć się więcej o zapytaniu niż PLINQ jest w stanie określić na podstawie jego analizy. Na przykład może być wiadomo, że delegat jest kosztowny i że zapytanie będzie ostatecznie korzystać z przetwarzanie równoległe. W takich przypadkach można użyć <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metody i określić <xref:System.Linq.ParallelExecutionMode.ForceParallelism> wartość, aby polecić PLINQ, aby zawsze uruchamiała zapytanie jako Parallel.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wytnij i wklej ten kod do [przykładu danych PLINQ](plinq-data-sample.md) i Wywołaj metodę z `Main` .  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [Równoległe LINQ (PLINQ)](introduction-to-plinq.md)
