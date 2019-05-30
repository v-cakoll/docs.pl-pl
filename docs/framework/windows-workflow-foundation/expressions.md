---
title: Expressions1
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 047f0f5d0214926fde2fe21efd9a24c4b645ed8e
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380169"
---
# <a name="expressions"></a>Wyrażenia
Wyrażenie Windows Workflow Foundation (WF) są wszystkie działania, które zwraca wynik. Wszystkie działania wyrażenie dziedziczyć pośrednio <xref:System.Activities.Activity%601>, który zawiera <xref:System.Activities.OutArgument> właściwość o nazwie <xref:System.Activities.Activity%601.Result%2A> jako wartość zwracaną przez działanie. [!INCLUDE[wf1](../../../includes/wf1-md.md)] jest dostarczany z szerokiej gamy wyrażenia działań z prostego, takie jak te <xref:System.Activities.Expressions.VariableValue%601> i <xref:System.Activities.Expressions.VariableReference%601>, które zapewniają dostęp do zmiennej jeden przepływ pracy za pomocą operatora działań złożonych działań takich jak <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> i <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> tę ofertę dostęp do pełnego zakresu języka Visual Basic w celu uzyskania wyniku. Wyrażenie dodatkowe działania mogą być tworzone przez pochodząca od <xref:System.Activities.CodeActivity%601> lub <xref:System.Activities.NativeActivity%601>.  
  
## <a name="using-expressions"></a>Za pomocą wyrażeń  
 Korzysta z projektanta przepływów pracy <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> i <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> dla wszystkie wyrażenia w projektach języka Visual Basic i <xref:Microsoft.CSharp.Activities.CSharpValue%601> i <xref:Microsoft.CSharp.Activities.CSharpReference%601> wyrażeń w C# projektów przepływu pracy.  
  
> [!NOTE]
>  Obsługa C# wyrażeń w projekty przepływu pracy została wprowadzona w programie .NET Framework 4.5. Aby uzyskać więcej informacji, zobacz [ C# wyrażeń](csharp-expressions.md).  
  
 Generowany przez projektanta przepływów pracy są zapisywane w XAML, gdzie wyrażeń pojawiają się w nawiasach kwadratowych, jak w poniższym przykładzie.  
  
```xml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:Int32" Default="1" Name="a" />  
    <Variable x:TypeArguments="x:Int32" Default="2" Name="b" />  
    <Variable x:TypeArguments="x:Int32" Default="3" Name="c" />  
    <Variable x:TypeArguments="x:Int32" Default="0" Name="r" />  
  </Sequence.Variables>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[r]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[a + b + c]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Sequence>  
```  
  
 Podczas definiowania przepływu pracy w kodzie, można używać dowolnego wyrażenia działań. Poniższy przykład przedstawia użycie skład operator działań do dodania trzech liczb.  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int> {  
                Expression = new Add<int, int, int> {  
                    Left = new Add<int, int, int> {  
                        Left = new InArgument<int>(a),  
                        Right = new InArgument<int>(b)  
                    },  
                    Right = new InArgument<int>(c)  
                }  
            }  
        }  
    }  
};  
```  
  
 Tym samym przepływie pracy mogą być wyrażone w bardziej bardziej kompaktowy przy użyciu C# wyrażeń lambda, jak pokazano w poniższym przykładzie.  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int>((ctx) => a.Get(ctx) + b.Get(ctx) + c.Get(ctx))  
        }  
    }  
};  
```  
  
 Przepływ pracy można również wyrazić za pomocą języka Visual Basic wyrażenia działań, jak pokazano w poniższym przykładzie.  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int>(new VisualBasicValue<int>("a + b + c"))  
        }  
    }  
};  
```  
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a>Rozszerzanie wyrażeń dostępne przy użyciu wyrażenia niestandardowego działania  
 Wyrażenia w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] można rozszerzać, co umożliwia dodatkowe wyrażenia działań ma zostać utworzony. Poniższy przykład pokazuje działanie, które zwraca sumę trzech wartości całkowitych.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Activities;  
  
namespace ExpressionsDemo  
{  
    public sealed class AddThreeValues : CodeActivity<int>  
    {  
        public InArgument<int> Value1 { get; set; }  
        public InArgument<int> Value2 { get; set; }  
        public InArgument<int> Value3 { get; set; }  
  
        protected override int Execute(CodeActivityContext context)  
        {  
            return Value1.Get(context) +   
                   Value2.Get(context) +   
                   Value3.Get(context);  
        }  
    }  
}  
```  
  
 Za pomocą tego nowego działania można przepisać poprzedniej przepływu pracy, który dodaje trzy wartości, jak pokazano w poniższym przykładzie.  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int> {  
                Expression = new AddThreeValues() {  
                    Value1 = new InArgument<int>(a),  
                    Value2 = new InArgument<int>(b),  
                    Value3 = new InArgument<int>(c)  
                }  
            }  
        }  
    }  
};  
```  
  
 Aby uzyskać więcej informacji na temat przy użyciu wyrażeń w kodzie, zobacz [tworzenia przepływów pracy, działań i wyrażeń przy użyciu technologii kodu](authoring-workflows-activities-and-expressions-using-imperative-code.md).
