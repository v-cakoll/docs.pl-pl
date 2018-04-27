---
title: Expressions1
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 293e59bd53607b7ca4c3d9075cb4bb0c4be4d4da
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="expressions"></a>Wyrażenia
Wyrażenie Windows Workflow Foundation (WF) to żadnych działań, które zwraca wynik. Wszystkie działania wyrażeń pośrednio pochodzi od <xref:System.Activities.Activity%601>, który zawiera <xref:System.Activities.OutArgument> właściwości o nazwie <xref:System.Activities.Activity%601.Result%2A> jako wartości zwracane działania. [!INCLUDE[wf1](../../../includes/wf1-md.md)] jest dostarczany z szeroką gamę działania wyrażeń z prostego, takich jak te <xref:System.Activities.Expressions.VariableValue%601> i <xref:System.Activities.Expressions.VariableReference%601>, które zapewniają dostęp do zmiennej w jednym przepływie pracy za pomocą operatora działań dla działań złożonych takich jak <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> i <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> tej oferty dostęp do rozmaitych języka Visual Basic w celu utworzenia wyniku. Można tworzyć dodatkowe wyrażenie działania przez wynikających z <xref:System.Activities.CodeActivity%601> lub <xref:System.Activities.NativeActivity%601>.  
  
## <a name="using-expressions"></a>Za pomocą wyrażeń  
 Korzysta z projektanta przepływów pracy <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> i <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> dla wszystkie wyrażenia w projektach Visual Basic i <xref:Microsoft.CSharp.Activities.CSharpValue%601> i <xref:Microsoft.CSharp.Activities.CSharpReference%601> dla wyrażenia w C# projektów przepływu pracy.  
  
> [!NOTE]
>  Obsługa wyrażeń C# w projektach przepływu pracy została wprowadzona w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [C# wyrażenia](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).  
  
 Utworzone przez projektanta przepływów pracy są zapisywane w kodzie XAML, gdzie wyrażenia są wyświetlane w nawiasach kwadratowych, jak w poniższym przykładzie.  
  
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
  
 Podczas definiowania przepływu pracy w kodzie, można używać żadnych działań wyrażenia. W poniższym przykładzie przedstawiono użycie kompozycji działań operatora, aby dodać trzech cyfr.  
  
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
  
 Tym samym przepływie pracy można wyrazić więcej compactly przy użyciu języka C# wyrażenia lambda, jak pokazano w poniższym przykładzie.  
  
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
  
 Przepływ pracy może być również wyrażona za pomocą działania wyrażeń języka Visual Basic, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a>Rozszerzanie wyrażenia dostępne z wyrażenia niestandardowego działania  
 Wyrażenia w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] można rozszerzać, co pozwala na działania wyrażeń dodatkowe ma zostać utworzony. Poniższy przykład przedstawia działanie, które zwraca sumę trzy wartości całkowite.  
  
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
  
 Z tego nowego działania można przepisać poprzedniej przepływu pracy, który dodaje trzy wartości, jak pokazano w poniższym przykładzie.  
  
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
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] za pomocą wyrażeń w kodzie, zobacz [tworzenia przepływów pracy, działań i kod Imperatywne za pomocą wyrażenia](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).
