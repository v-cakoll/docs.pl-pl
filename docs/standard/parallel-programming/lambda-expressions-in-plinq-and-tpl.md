---
title: Wyrażenia Lambda w PLINQ i TPL
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36a003c96e81996e304fc4347ed05bf7a255c224
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189454"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>Wyrażenia Lambda w PLINQ i TPL
Biblioteka zadań równoległych (TPL) zawiera wiele metod, które Przystąp do jednego z <xref:System.Func%601?displayProperty=nameWithType> lub <xref:System.Action?displayProperty=nameWithType> rodziny delegatów jako parametry wejściowe. Użyjesz tych delegatów do przekazania w logice program niestandardowy do pętli równoległej, zadania lub kwerendę. Przykłady kodu dla TPL, a także PLINQ używać wyrażeń lambda do tworzenia wystąpień tych delegatów jako bloków kodu w tekście. Ten temat zawiera krótkie wprowadzenie do Func i Action i pokazano, jak używać wyrażeń lambda w bibliotece równoległych zadań i PLINQ.  
  
 **Uwaga** Aby uzyskać więcej informacji na temat delegatów ogólnie rzecz biorąc, zobacz [delegatów](../../csharp/programming-guide/delegates/index.md) i [delegatów](../../visual-basic/programming-guide/language-features/delegates/index.md). Aby uzyskać więcej informacji na temat wyrażeń lambda w języku C# i Visual Basic, zobacz [wyrażeń Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) i [wyrażeń Lambda](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="func-delegate"></a>FUNC — delegowanie  
 A `Func` delegata hermetyzuje metody, która nie zwraca wartości. W podpisie Func parametru typu z prawej strony zawsze określa typ zwracany. Częstą przyczyną błędów kompilatora jest próba przekazania w dwóch parametrów wejściowych do <xref:System.Func%602?displayProperty=nameWithType>; w rzeczywistości tego typu zajmuje tylko jeden parametr wejściowy. Biblioteka klas Framework definiuje 17 wersje `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, i tak dalej, nawet za pośrednictwem <xref:System.Func%6017?displayProperty=nameWithType>.  
  
## <a name="action-delegate"></a>Delegat akcji  
 A <xref:System.Action?displayProperty=nameWithType> delegata hermetyzuje metody (Sub w języku Visual Basic), która nie zwraca wartości, lub zwraca [void](~/docs/csharp/language-reference/keywords/void.md). W podpisie typ akcji parametrów typu reprezentują tylko parametry wejściowe. Jak Func biblioteki klas Framework definiuje 17 wersje działania, wersji, która nie ma parametrów typu przy użyciu wersji zawierającej 16 parametrów typu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> metoda pokazuje, jak express delegatów Func i akcji za pomocą wyrażenia lambda.  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
