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
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="d179c-102">Instrukcje: Użycie wyrażeń lambda poza LINQ (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="d179c-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="d179c-103">Wyrażenia lambda nie są ograniczone do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań.</span><span class="sxs-lookup"><span data-stu-id="d179c-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="d179c-104">Można ich używać wszędzie tam, gdzie jest oczekiwana wartość delegata, to jest, wszędzie tam, gdzie można użyć anonimowej metody.</span><span class="sxs-lookup"><span data-stu-id="d179c-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="d179c-105">Poniższy przykład pokazuje, jak używać wyrażenia lambda w obsłudze zdarzeń Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d179c-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="d179c-106">Należy zauważyć, że typy danych wejściowych (<xref:System.Object> i <xref:System.Windows.Forms.MouseEventArgs>) są wywnioskowane przez kompilator i nie muszą być jawnie określone w parametrach wejściowych lambda.</span><span class="sxs-lookup"><span data-stu-id="d179c-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d179c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d179c-107">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d179c-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d179c-108">See also</span></span>

- [<span data-ttu-id="d179c-109">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="d179c-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="d179c-110">Query Integrated Language (LINQ))</span><span class="sxs-lookup"><span data-stu-id="d179c-110">Language Integrated Query (LINQ))</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
