---
title: 'Porady: użycie wyrażeń lambda poza LINQ (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: eb9fea64b8aeb96a880b7e177673c1316b7aa4c1
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44261539"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>Porady: użycie wyrażeń lambda poza LINQ (Przewodnik programowania w języku C#)
Wyrażenia lambda nie są ograniczone do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Możesz użyć ich wszędzie tam, gdzie delegata jest oczekiwana wartość, czyli wszędzie tam, gdzie można metodę anonimową. Poniższy przykład przedstawia sposób użycia wyrażenia lambda w obsłudze zdarzeń Windows Forms. Należy zauważyć, że typy danych wejściowych (<xref:System.Object> i <xref:System.Windows.Forms.MouseEventArgs>) są wnioskowane przez kompilator i nie mają jawnie podana w danych wejściowych parametrów wyrażenia lambda.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [Metody anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
- [Zapytanie o języku zintegrowanym (LINQ))](../../../csharp/programming-guide/concepts/linq/index.md)
