---
title: Expressions1
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 7643279c2db5608c028e0a1213802ab609a2d347
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704287"
---
# <a name="expressions"></a><span data-ttu-id="1c2cd-102">Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="1c2cd-102">Expressions</span></span>
<span data-ttu-id="1c2cd-103">Wyrażenie Windows Workflow Foundation (WF) są wszystkie działania, które zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="1c2cd-103">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="1c2cd-104">Wszystkie działania wyrażenie dziedziczyć pośrednio <xref:System.Activities.Activity%601>, który zawiera <xref:System.Activities.OutArgument> właściwość o nazwie <xref:System.Activities.Activity%601.Result%2A> jako wartość zwracaną przez działanie.</span><span class="sxs-lookup"><span data-stu-id="1c2cd-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="1c2cd-105">jest dostarczany z szerokiej gamy wyrażenia działań z prostego, takie jak te <xref:System.Activities.Expressions.VariableValue%601> i <xref:System.Activities.Expressions.VariableReference%601>, które zapewniają dostęp do zmiennej jeden przepływ pracy za pomocą operatora działań złożonych działań takich jak <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> i <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> tę ofertę dostęp do pełnego zakresu języka Visual Basic w celu uzyskania wyniku.</span><span class="sxs-lookup"><span data-stu-id="1c2cd-105">ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="1c2cd-106">Wyrażenie dodatkowe działania mogą być tworzone przez pochodząca od <xref:System.Activities.CodeActivity%601> lub <xref:System.Activities.NativeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="1c2cd-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>  
  
## <a name="using-expressions"></a><span data-ttu-id="1c2cd-107">Za pomocą wyrażeń</span><span class="sxs-lookup"><span data-stu-id="1c2cd-107">Using Expressions</span></span>  
 <span data-ttu-id="1c2cd-108">Korzysta z projektanta przepływów pracy <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> i <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> dla wszystkie wyrażenia w projektach języka Visual Basic i <xref:Microsoft.CSharp.Activities.CSharpValue%601> i <xref:Microsoft.CSharp.Activities.CSharpReference%601> wyrażeń w C# projektów przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1c2cd-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c2cd-109">Obsługa C# wyrażeń w projekty przepływu pracy została wprowadzona w systemie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c2cd-109">Support for C# expressions in workflow projects was introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="1c2cd-110">Aby uzyskać więcej informacji, zobacz [ C# wyrażeń](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1c2cd-110">For more information, see [C# Expressions](csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="1c2cd-111">Generowany przez projektanta przepływów pracy są zapisywane w XAML, gdzie wyrażeń pojawiają się w nawiasach kwadratowych, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1c2cd-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>  
  
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
  
 <span data-ttu-id="1c2cd-112">Podczas definiowania przepływu pracy w kodzie, można używać dowolnego wyrażenia działań.</span><span class="sxs-lookup"><span data-stu-id="1c2cd-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="1c2cd-113">Poniższy przykład przedstawia użycie skład operator działań do dodania trzech liczb.</span><span class="sxs-lookup"><span data-stu-id="1c2cd-113">The following example shows the usage of a composition of operator activities to add three numbers.</span></span>  
  
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
  
 <span data-ttu-id="1c2cd-114">Tym samym przepływie pracy mogą być wyrażone w bardziej bardziej kompaktowy przy użyciu C# wyrażeń lambda, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1c2cd-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="1c2cd-115">Przepływ pracy można również wyrazić za pomocą języka Visual Basic wyrażenia działań, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1c2cd-115">The workflow can also be expressed by using Visual Basic expression activities, as shown in the following example.</span></span>  
  
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
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="1c2cd-116">Rozszerzanie wyrażeń dostępne przy użyciu wyrażenia niestandardowego działania</span><span class="sxs-lookup"><span data-stu-id="1c2cd-116">Extending Available Expressions with Custom Expression Activities</span></span>  
 <span data-ttu-id="1c2cd-117">Wyrażenia w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] można rozszerzać, co umożliwia dodatkowe wyrażenia działań ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="1c2cd-117">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="1c2cd-118">Poniższy przykład pokazuje działanie, które zwraca sumę trzech wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="1c2cd-118">The following example shows an activity that returns a sum of three integer values.</span></span>  
  
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
  
 <span data-ttu-id="1c2cd-119">Za pomocą tego nowego działania można przepisać poprzedniej przepływu pracy, który dodaje trzy wartości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1c2cd-119">With this new activity you can rewrite the previous workflow that added three values as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="1c2cd-120">Aby uzyskać więcej informacji na temat przy użyciu wyrażeń w kodzie, zobacz [tworzenia przepływów pracy, działań i wyrażeń przy użyciu technologii kodu](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="1c2cd-120">For more information about using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
