---
title: 'Porady: użycie wyrażeń lambda poza LINQ (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: a7b7d25adab7ce1fc777b3bdbe581666ab952413
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328958"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="8d0fe-102">Porady: użycie wyrażeń lambda poza LINQ (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="8d0fe-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="8d0fe-103">Wyrażenia lambda nie są ograniczone do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="8d0fe-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="8d0fe-104">Można je tam, gdzie wartość delegata oczekuje, oznacza to, wszędzie tam, gdzie można metody anonimowej.</span><span class="sxs-lookup"><span data-stu-id="8d0fe-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="8d0fe-105">Poniższy przykład przedstawia użycie wyrażenia lambda w obsłudze zdarzeń formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8d0fe-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="8d0fe-106">Zwróć uwagę, że typy danych wejściowych (<xref:System.Object> i <xref:System.Windows.Forms.MouseEventArgs>) są wykryta przez kompilator i nie muszą być określone jawnie w parametrach wejściowych lambda.</span><span class="sxs-lookup"><span data-stu-id="8d0fe-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d0fe-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d0fe-107">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d0fe-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d0fe-108">See Also</span></span>  
 [<span data-ttu-id="8d0fe-109">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="8d0fe-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="8d0fe-110">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="8d0fe-110">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="8d0fe-111">LINQ (zapytania o języku zintegrowanym)</span><span class="sxs-lookup"><span data-stu-id="8d0fe-111">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
