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
ms.openlocfilehash: 4e5be295a52edc1a7f0a0a3aa98f55335ae3e31b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77453003"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>Wyrażenia Lambda w PLINQ i TPL

Biblioteka równoległa zadania (TPL) zawiera wiele <xref:System.Func%601?displayProperty=nameWithType> metod, które biorą jeden z lub <xref:System.Action?displayProperty=nameWithType> rodziny delegatów jako parametry wejściowe. Ci pełnomocnicy są używane do przekazywania w niestandardowej logiki programu do pętli równoległej, zadania lub kwerendy. Przykłady kodu dla TPL, a także PLINQ używać wyrażeń lambda do tworzenia wystąpień tych delegatów jako bloki kodu liniowego. W tym temacie przedstawiono krótkie wprowadzenie do Func i Action i pokazano, jak używać wyrażeń lambda w bibliotece równoległej zadania i PLINQ.

> [!NOTE]
> Aby uzyskać więcej informacji na temat delegatów w ogóle, zobacz [delegatów](../../csharp/programming-guide/delegates/index.md) i [delegatów](../../visual-basic/programming-guide/language-features/delegates/index.md). Aby uzyskać więcej informacji na temat wyrażeń lambda w językach C# i Visual Basic, zobacz [Wyrażenia Lambda](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) i [wyrażenia Lambda](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="func-delegate"></a>Delegat Func

Pełnomocnik `Func` hermetyzuje metodę, która zwraca wartość. W `Func` podpisie ostatni lub prawy parametr typu zawsze określa typ zwracany. Jedną z typowych przyczyn błędów kompilatora jest <xref:System.Func%602?displayProperty=nameWithType>próba przekazania w dwóch parametrów wejściowych do ; w rzeczywistości ten typ przyjmuje tylko jeden parametr wejściowy. .NET definiuje 17 `Func`wersji <xref:System.Func%601?displayProperty=nameWithType> <xref:System.Func%602?displayProperty=nameWithType>: <xref:System.Func%603?displayProperty=nameWithType>, , i <xref:System.Func%6017?displayProperty=nameWithType>tak dalej przez .

## <a name="action-delegate"></a>Pełnomocnik akcji

Delegat <xref:System.Action?displayProperty=nameWithType> hermetyzuje metodę (Sub w języku Visual Basic), która nie zwraca wartości. W `Action` podpisie typu parametry typu reprezentują tylko parametry wejściowe. Podobnie `Func`jak . . `Action`

## <a name="example"></a>Przykład

Poniższy przykład dla <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> metody pokazuje, jak wyrazić zarówno Func i Action delegatów przy użyciu wyrażeń lambda.

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a>Zobacz też

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
