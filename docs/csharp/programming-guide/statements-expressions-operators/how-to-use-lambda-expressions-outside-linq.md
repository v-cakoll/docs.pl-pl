---
title: 'Porady: użycie wyrażeń lambda poza LINQ (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: a7b7d25adab7ce1fc777b3bdbe581666ab952413
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959724"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>Porady: użycie wyrażeń lambda poza LINQ (Przewodnik programowania w języku C#)
Wyrażenia lambda nie są ograniczone do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Możesz użyć ich wszędzie tam, gdzie delegata jest oczekiwana wartość, czyli wszędzie tam, gdzie można metodę anonimową. Poniższy przykład przedstawia sposób użycia wyrażenia lambda w obsłudze zdarzeń Windows Forms. Należy zauważyć, że typy danych wejściowych (<xref:System.Object> i <xref:System.Windows.Forms.MouseEventArgs>) są wnioskowane przez kompilator i nie mają jawnie podana w danych wejściowych parametrów wyrażenia lambda.  
  
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
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
