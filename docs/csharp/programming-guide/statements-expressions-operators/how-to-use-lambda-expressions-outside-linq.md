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
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="c9869-102">Porady: użycie wyrażeń lambda poza LINQ (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c9869-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="c9869-103">Wyrażenia lambda nie są ograniczone do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="c9869-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="c9869-104">Można je tam, gdzie wartość delegata oczekuje, oznacza to, wszędzie tam, gdzie można metody anonimowej.</span><span class="sxs-lookup"><span data-stu-id="c9869-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="c9869-105">Poniższy przykład przedstawia użycie wyrażenia lambda w obsłudze zdarzeń formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c9869-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="c9869-106">Zwróć uwagę, że typy danych wejściowych (<xref:System.Object> i <xref:System.Windows.Forms.MouseEventArgs>) są wykryta przez kompilator i nie muszą być określone jawnie w parametrach wejściowych lambda.</span><span class="sxs-lookup"><span data-stu-id="c9869-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9869-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9869-107">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c9869-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9869-108">See Also</span></span>  
 [<span data-ttu-id="c9869-109">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="c9869-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="c9869-110">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="c9869-110">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="c9869-111">LINQ (zapytania o języku zintegrowanym)</span><span class="sxs-lookup"><span data-stu-id="c9869-111">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
