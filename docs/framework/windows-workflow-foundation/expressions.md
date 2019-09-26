---
title: Wyrażenia — WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 62b278825de6242075e89e3b243b6d6d8ef4d599
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306204"
---
# <a name="expressions"></a><span data-ttu-id="ff8f8-102">Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="ff8f8-102">Expressions</span></span>

<span data-ttu-id="ff8f8-103">Wyrażenie Windows Workflow Foundation (WF) to wszelkie działania zwracające wynik.</span><span class="sxs-lookup"><span data-stu-id="ff8f8-103">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="ff8f8-104">Wszystkie działania wyrażeń są wyprowadzane <xref:System.Activities.Activity%601>pośrednio z, która <xref:System.Activities.OutArgument> zawiera właściwość <xref:System.Activities.Activity%601.Result%2A> o nazwie jako wartość zwracana działania.</span><span class="sxs-lookup"><span data-stu-id="ff8f8-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="ff8f8-105">jest dostarczany z szerokim zakresem działań związanych z wyrażeniami <xref:System.Activities.Expressions.VariableValue%601> prostymi, takimi jak i <xref:System.Activities.Expressions.VariableReference%601>, które zapewniają dostęp do pojedynczej zmiennej przepływu pracy za <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> pośrednictwem działań operatora, do złożonych działań, takich jak i <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> tej oferty dostęp do pełnego zakresu Visual Basic języka w celu utworzenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="ff8f8-105">ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="ff8f8-106">Dodatkowe działania dotyczące wyrażeń można tworzyć poprzez wyprowadzanie z <xref:System.Activities.CodeActivity%601> lub <xref:System.Activities.NativeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="ff8f8-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>

## <a name="using-expressions"></a><span data-ttu-id="ff8f8-107">Używanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="ff8f8-107">Using Expressions</span></span>
 <span data-ttu-id="ff8f8-108">Projektant przepływu pracy <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> używa <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> i dla wszystkich wyrażeń <xref:Microsoft.CSharp.Activities.CSharpValue%601> w projektach Visual Basic i i <xref:Microsoft.CSharp.Activities.CSharpReference%601> dla wyrażeń w C# projektach przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ff8f8-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>

> [!NOTE]
> <span data-ttu-id="ff8f8-109">Obsługa C# wyrażeń w projektach przepływu pracy została wprowadzona w .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="ff8f8-109">Support for C# expressions in workflow projects was introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="ff8f8-110">Aby uzyskać więcej informacji, zobacz [ C# Expressions](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ff8f8-110">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

 <span data-ttu-id="ff8f8-111">Przepływy pracy utworzone przez projektanta są zapisywane w języku XAML, gdzie wyrażenia są ujęte w nawiasy kwadratowe, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ff8f8-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>

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

 <span data-ttu-id="ff8f8-112">Podczas definiowania przepływu pracy w kodzie, można użyć dowolnego działania wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="ff8f8-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="ff8f8-113">W poniższym przykładzie pokazano sposób użycia kompozycji działań operatora w celu dodania trzech liczb:</span><span class="sxs-lookup"><span data-stu-id="ff8f8-113">The following example shows the usage of a composition of operator activities to add three numbers:</span></span>

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

 <span data-ttu-id="ff8f8-114">Ten sam przepływ pracy można wyrazić bardziej kompaktowo przy C# użyciu wyrażeń lambda, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ff8f8-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example:</span></span>
  
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

## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="ff8f8-115">Rozszerzanie dostępnych wyrażeń z niestandardowymi działaniami wyrażeń</span><span class="sxs-lookup"><span data-stu-id="ff8f8-115">Extending Available Expressions with Custom Expression Activities</span></span>

 <span data-ttu-id="ff8f8-116">Wyrażenia w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] programie mają rozszerzalny Zezwalanie na tworzenie dodatkowych działań wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="ff8f8-116">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="ff8f8-117">Poniższy przykład pokazuje działanie zwracające sumę trzech wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="ff8f8-117">The following example shows an activity that returns a sum of three integer values.</span></span>

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

 <span data-ttu-id="ff8f8-118">Przy użyciu tego nowego działania można ponownie napisać poprzedni przepływ pracy, który dodał trzy wartości, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ff8f8-118">With this new activity you can rewrite the previous workflow that added three values as shown in the following example:</span></span>

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

 <span data-ttu-id="ff8f8-119">Aby uzyskać więcej informacji na temat używania wyrażeń w kodzie, zobacz [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="ff8f8-119">For more information about using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
