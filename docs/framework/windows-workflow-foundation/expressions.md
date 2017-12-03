---
title: Expressions1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d42249f19b2d9acebf547be9e590813d6bbf7a33
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="expressions"></a><span data-ttu-id="ff9c9-102">Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="ff9c9-102">Expressions</span></span>
<span data-ttu-id="ff9c9-103">A [!INCLUDE[wf](../../../includes/wf-md.md)] wyrażenie jest żadnych działań, które zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="ff9c9-103">A [!INCLUDE[wf](../../../includes/wf-md.md)] expression is any activity that returns a result.</span></span> <span data-ttu-id="ff9c9-104">Wszystkie działania wyrażeń pośrednio pochodzi od <xref:System.Activities.Activity%601>, który zawiera <xref:System.Activities.OutArgument> właściwości o nazwie <xref:System.Activities.Activity%601.Result%2A> jako wartości zwracane działania.</span><span class="sxs-lookup"><span data-stu-id="ff9c9-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="ff9c9-105">jest dostarczany z szeroką gamę działania wyrażeń z prostego, takich jak te <xref:System.Activities.Expressions.VariableValue%601> i <xref:System.Activities.Expressions.VariableReference%601>, które zapewniają dostęp do zmiennej w jednym przepływie pracy za pomocą operatora działań dla działań złożonych takich jak <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> i <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> tej oferty dostęp do rozmaitych języka Visual Basic w celu utworzenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="ff9c9-105"> ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="ff9c9-106">Można tworzyć dodatkowe wyrażenie działania przez wynikających z <xref:System.Activities.CodeActivity%601> lub <xref:System.Activities.NativeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="ff9c9-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>  
  
## <a name="using-expressions"></a><span data-ttu-id="ff9c9-107">Za pomocą wyrażeń</span><span class="sxs-lookup"><span data-stu-id="ff9c9-107">Using Expressions</span></span>  
 <span data-ttu-id="ff9c9-108">Korzysta z projektanta przepływów pracy <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> i <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> dla wszystkie wyrażenia w projektach Visual Basic i <xref:Microsoft.CSharp.Activities.CSharpValue%601> i <xref:Microsoft.CSharp.Activities.CSharpReference%601> dla wyrażenia w C# projektów przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ff9c9-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff9c9-109">Obsługa wyrażeń C# w projektach przepływu pracy została wprowadzona w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff9c9-109">Support for C# expressions in workflow projects was introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="ff9c9-110">[Wyrażeń C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ff9c9-110"> [C# Expressions](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="ff9c9-111">Utworzone przez projektanta przepływów pracy są zapisywane w kodzie XAML, gdzie wyrażenia są wyświetlane w nawiasach kwadratowych, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ff9c9-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ff9c9-112">Podczas definiowania przepływu pracy w kodzie, można używać żadnych działań wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ff9c9-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="ff9c9-113">W poniższym przykładzie przedstawiono użycie kompozycji działań operatora, aby dodać trzech cyfr.</span><span class="sxs-lookup"><span data-stu-id="ff9c9-113">The following example shows the usage of a composition of operator activities to add three numbers.</span></span>  
  
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
  
 <span data-ttu-id="ff9c9-114">Tym samym przepływie pracy można wyrazić więcej compactly przy użyciu języka C# wyrażenia lambda, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ff9c9-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ff9c9-115">Przepływ pracy może być również wyrażona za pomocą działania wyrażeń języka Visual Basic, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ff9c9-115">The workflow can also be expressed by using Visual Basic expression activities, as shown in the following example.</span></span>  
  
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
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="ff9c9-116">Rozszerzanie wyrażenia dostępne z wyrażenia niestandardowego działania</span><span class="sxs-lookup"><span data-stu-id="ff9c9-116">Extending Available Expressions with Custom Expression Activities</span></span>  
 <span data-ttu-id="ff9c9-117">Wyrażenia w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] można rozszerzać, co pozwala na działania wyrażeń dodatkowe ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="ff9c9-117">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="ff9c9-118">Poniższy przykład przedstawia działanie, które zwraca sumę trzy wartości całkowite.</span><span class="sxs-lookup"><span data-stu-id="ff9c9-118">The following example shows an activity that returns a sum of three integer values.</span></span>  
  
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
  
 <span data-ttu-id="ff9c9-119">Z tego nowego działania można przepisać poprzedniej przepływu pracy, który dodaje trzy wartości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ff9c9-119">With this new activity you can rewrite the previous workflow that added three values as shown in the following example.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="ff9c9-120">za pomocą wyrażeń w kodzie, zobacz [tworzenia przepływów pracy, działań i kod Imperatywne za pomocą wyrażenia](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="ff9c9-120"> using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
