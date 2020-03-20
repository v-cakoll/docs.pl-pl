---
title: Wyrażenia - WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 93fe449e8fa6c50f715d842c2ef6a9ecbd31aff2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182937"
---
# <a name="expressions"></a><span data-ttu-id="8e899-102">Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="8e899-102">Expressions</span></span>

<span data-ttu-id="8e899-103">Wyrażenie Fundacji przepływu pracy systemu Windows (WF) jest dowolnym działaniem, które zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="8e899-103">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="8e899-104">Wszystkie działania wyrażenia pochodzą pośrednio z <xref:System.Activities.Activity%601> <xref:System.Activities.OutArgument> , <xref:System.Activities.Activity%601.Result%2A> który zawiera właściwość o nazwie jako wartość zwracana działania.</span><span class="sxs-lookup"><span data-stu-id="8e899-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="8e899-105">łączy się z szeroką gamą działań <xref:System.Activities.Expressions.VariableValue%601> <xref:System.Activities.Expressions.VariableReference%601>ekspresji, od prostych, takich jak i , które <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> zapewniają <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> dostęp do zmiennej pojedynczego przepływu pracy za pośrednictwem działań operatora, do złożonych działań, takich jak i które oferują dostęp do pełnej szerokości języka Visual Basic, aby uzyskać wynik.</span><span class="sxs-lookup"><span data-stu-id="8e899-105">ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="8e899-106">Dodatkowe działania wyrażenia można tworzyć, <xref:System.Activities.CodeActivity%601> wyprowadzając z pliku . <xref:System.Activities.NativeActivity%601></span><span class="sxs-lookup"><span data-stu-id="8e899-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>

## <a name="using-expressions"></a><span data-ttu-id="8e899-107">Używanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="8e899-107">Using Expressions</span></span>
 <span data-ttu-id="8e899-108">Projektant przepływu pracy <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> używa i dla wszystkich wyrażeń <xref:Microsoft.CSharp.Activities.CSharpReference%601> w projektach języka Visual Basic i <xref:Microsoft.CSharp.Activities.CSharpValue%601> dla wyrażeń w projektach przepływu pracy języka C#.</span><span class="sxs-lookup"><span data-stu-id="8e899-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>

> [!NOTE]
> <span data-ttu-id="8e899-109">Obsługa wyrażeń języka C# w projektach przepływu pracy została wprowadzona w .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="8e899-109">Support for C# expressions in workflow projects was introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="8e899-110">Aby uzyskać więcej informacji, zobacz [Wyrażenia języka C#](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8e899-110">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

 <span data-ttu-id="8e899-111">Przepływy pracy tworzone przez projektanta są zapisywane w języku XAML, gdzie wyrażenia są wyświetlane ujęte w nawiasach kwadratowych, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8e899-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>

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

 <span data-ttu-id="8e899-112">Podczas definiowania przepływu pracy w kodzie można użyć żadnych działań wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="8e899-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="8e899-113">Poniższy przykład pokazuje użycie kompozycji działań operatora, aby dodać trzy liczby:</span><span class="sxs-lookup"><span data-stu-id="8e899-113">The following example shows the usage of a composition of operator activities to add three numbers:</span></span>

```csharp
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

 <span data-ttu-id="8e899-114">Ten sam przepływ pracy można wyrazić bardziej zwartą przy użyciu wyrażeń lambda języka C#, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8e899-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example:</span></span>
  
```csharp
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

## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="8e899-115">Rozszerzanie dostępnych wyrażeń za pomocą działań wyrażenia niestandardowego</span><span class="sxs-lookup"><span data-stu-id="8e899-115">Extending Available Expressions with Custom Expression Activities</span></span>

 <span data-ttu-id="8e899-116">Wyrażenia w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] są rozszerzalne, co pozwala na dodatkowe działania wyrażenia, które mają być tworzone.</span><span class="sxs-lookup"><span data-stu-id="8e899-116">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="8e899-117">W poniższym przykładzie pokazano działanie, które zwraca sumę trzech wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="8e899-117">The following example shows an activity that returns a sum of three integer values.</span></span>

```csharp
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

 <span data-ttu-id="8e899-118">Za pomocą tego nowego działania można przepisać poprzedni przepływ pracy, który dodał trzy wartości, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8e899-118">With this new activity you can rewrite the previous workflow that added three values as shown in the following example:</span></span>

```csharp
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

 <span data-ttu-id="8e899-119">Aby uzyskać więcej informacji na temat używania wyrażeń w kodzie, zobacz [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywu](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="8e899-119">For more information about using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
