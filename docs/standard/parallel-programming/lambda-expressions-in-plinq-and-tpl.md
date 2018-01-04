---
title: "Wyrażenia Lambda w PLINQ i TPL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 364d23db41aac4733226189f7c8ae85d281b9887
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>Wyrażenia Lambda w PLINQ i TPL
Zadania biblioteki równoległych (TPL) zawiera wiele metod, które wykonać jedną z <xref:System.Func%601?displayProperty=nameWithType> lub <xref:System.Action?displayProperty=nameWithType> rodziny delegatów jako parametry wejściowe. Te obiekty delegowane umożliwia Przekaż logiki program niestandardowy do pętli równoległej, zadania lub zapytania. Przykłady kodu dla TPL, a także PLINQ użycie wyrażeń lambda, można utworzyć wystąpień tych obiektów delegowanych jako bloki kodu wbudowanego. Ten temat zawiera krótkie wprowadzenie do Func i Action i przedstawiono sposób użycie wyrażeń lambda w bibliotece równoległych zadań i PLINQ.  
  
 **Uwaga** uzyskać więcej informacji na temat delegatów ogólnie rzecz biorąc, zobacz [delegatów](../../csharp/programming-guide/delegates/index.md) i [delegatów](../../visual-basic/programming-guide/language-features/delegates/index.md). Aby uzyskać więcej informacji na temat wyrażeń lambda w języku C# i [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], zobacz [wyrażenia Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) i [wyrażenia Lambda](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="func-delegate"></a>FUNC — delegowanie  
 A `Func` delegata hermetyzuje metody, która nie zwraca wartości. W podpisie Func parametru typu z prawej strony zawsze określa typ zwracany. Jedną z typowych przyczyn błędów kompilatora jest próba przekazania w dwóch parametrów wejściowych do <xref:System.Func%602?displayProperty=nameWithType>; w rzeczywistości tego typu przyjmuje tylko jeden parametr wejściowy. Biblioteka klas Framework definiuje 17 wersje `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, i tak dalej nawet za pośrednictwem <xref:System.Func%6017?displayProperty=nameWithType>.  
  
## <a name="action-delegate"></a>Delegat akcji  
 A <xref:System.Action?displayProperty=nameWithType> delegata hermetyzuje metody (Sub w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) może zwracać wartości i zwraca [void](~/docs/csharp/language-reference/keywords/void.md). W podpisie typu akcji parametrów typu reprezentują tylko parametry wejściowe. Podobnie jak Func biblioteki klas w ramach definiuje 17 wersji działania, z wersji, która nie ma typu parametrów przy użyciu wersji, który ma 16 parametrów typu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dla <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> metody pokazano, jak express zarówno Func i Action delegatów za pomocą wyrażenia lambda.  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
