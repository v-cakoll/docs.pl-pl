---
title: 'Instrukcje: Użycie wyrażeń lambda poza Przewodnik C# programowania LINQ'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: 947f80fdaa90b6b5f8176aac01dd8e3cf40e38cc
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363773"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>Instrukcje: Użycie wyrażeń lambda poza LINQ (C# Przewodnik programowania)
Wyrażenia lambda nie są ograniczone do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań. Można ich używać wszędzie tam, gdzie jest oczekiwana wartość delegata, to jest, wszędzie tam, gdzie można użyć anonimowej metody. Poniższy przykład pokazuje, jak używać wyrażenia lambda w obsłudze zdarzeń Windows Forms. Należy zauważyć, że typy danych wejściowych (<xref:System.Object> i <xref:System.Windows.Forms.MouseEventArgs>) są wywnioskowane przez kompilator i nie muszą być jawnie określone w parametrach wejściowych lambda.  
  
## <a name="example"></a>Przykład  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
       this.Click += (s, e) => { MessageBox.Show(((MouseEventArgs)e).Location.ToString());};  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Query Integrated Language (LINQ))](../../../csharp/programming-guide/concepts/linq/index.md)
