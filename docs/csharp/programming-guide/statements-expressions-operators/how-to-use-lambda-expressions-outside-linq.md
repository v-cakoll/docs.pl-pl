---
title: 'Instrukcje: Użycie wyrażeń Lambda poza LINQ — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: c66dea393ad2351402f54b2391d424701208eba2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61678802"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="3f664-102">Instrukcje: Użycie wyrażeń Lambda poza LINQ (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="3f664-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="3f664-103">Wyrażenia lambda nie są ograniczone do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="3f664-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="3f664-104">Możesz użyć ich wszędzie tam, gdzie delegata jest oczekiwana wartość, czyli wszędzie tam, gdzie można metodę anonimową.</span><span class="sxs-lookup"><span data-stu-id="3f664-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="3f664-105">Poniższy przykład przedstawia sposób użycia wyrażenia lambda w obsłudze zdarzeń Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3f664-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="3f664-106">Należy zauważyć, że typy danych wejściowych (<xref:System.Object> i <xref:System.Windows.Forms.MouseEventArgs>) są wnioskowane przez kompilator i nie mają jawnie podana w danych wejściowych parametrów wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="3f664-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f664-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f664-107">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f664-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f664-108">See also</span></span>

- [<span data-ttu-id="3f664-109">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="3f664-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="3f664-110">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="3f664-110">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
- [<span data-ttu-id="3f664-111">Zapytanie o języku zintegrowanym (LINQ))</span><span class="sxs-lookup"><span data-stu-id="3f664-111">Language Integrated Query (LINQ))</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
