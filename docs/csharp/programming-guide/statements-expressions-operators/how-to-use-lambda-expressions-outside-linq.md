---
title: "Porady: użycie wyrażeń lambda poza LINQ (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c99f6bc7c9db1f0e2341c31ec5bf60217723d4e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>Porady: użycie wyrażeń lambda poza LINQ (Przewodnik programowania w języku C#)
Wyrażenia lambda nie są ograniczone do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Można je tam, gdzie wartość delegata oczekuje, oznacza to, wszędzie tam, gdzie można metody anonimowej. Poniższy przykład przedstawia użycie wyrażenia lambda w obsłudze zdarzeń formularzy systemu Windows. Zwróć uwagę, że typy danych wejściowych (<xref:System.Object> i <xref:System.Windows.Forms.MouseEventArgs>) są wykryta przez kompilator i nie muszą być określone jawnie w parametrach wejściowych lambda.  
  
## <a name="example"></a>Przykład  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Metody anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [LINQ (zapytania o języku zintegrowanym)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
