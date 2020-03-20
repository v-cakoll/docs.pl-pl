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
# <a name="expressions"></a>Wyrażenia

Wyrażenie Fundacji przepływu pracy systemu Windows (WF) jest dowolnym działaniem, które zwraca wynik. Wszystkie działania wyrażenia pochodzą pośrednio z <xref:System.Activities.Activity%601> <xref:System.Activities.OutArgument> , <xref:System.Activities.Activity%601.Result%2A> który zawiera właściwość o nazwie jako wartość zwracana działania. [!INCLUDE[wf1](../../../includes/wf1-md.md)]łączy się z szeroką gamą działań <xref:System.Activities.Expressions.VariableValue%601> <xref:System.Activities.Expressions.VariableReference%601>ekspresji, od prostych, takich jak i , które <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> zapewniają <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> dostęp do zmiennej pojedynczego przepływu pracy za pośrednictwem działań operatora, do złożonych działań, takich jak i które oferują dostęp do pełnej szerokości języka Visual Basic, aby uzyskać wynik. Dodatkowe działania wyrażenia można tworzyć, <xref:System.Activities.CodeActivity%601> wyprowadzając z pliku . <xref:System.Activities.NativeActivity%601>

## <a name="using-expressions"></a>Używanie wyrażeń
 Projektant przepływu pracy <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> używa i dla wszystkich wyrażeń <xref:Microsoft.CSharp.Activities.CSharpReference%601> w projektach języka Visual Basic i <xref:Microsoft.CSharp.Activities.CSharpValue%601> dla wyrażeń w projektach przepływu pracy języka C#.

> [!NOTE]
> Obsługa wyrażeń języka C# w projektach przepływu pracy została wprowadzona w .NET Framework 4.5. Aby uzyskać więcej informacji, zobacz [Wyrażenia języka C#](csharp-expressions.md).

 Przepływy pracy tworzone przez projektanta są zapisywane w języku XAML, gdzie wyrażenia są wyświetlane ujęte w nawiasach kwadratowych, jak w poniższym przykładzie.

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

 Podczas definiowania przepływu pracy w kodzie można użyć żadnych działań wyrażeń. Poniższy przykład pokazuje użycie kompozycji działań operatora, aby dodać trzy liczby:

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

 Ten sam przepływ pracy można wyrazić bardziej zwartą przy użyciu wyrażeń lambda języka C#, jak pokazano w poniższym przykładzie:
  
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

## <a name="extending-available-expressions-with-custom-expression-activities"></a>Rozszerzanie dostępnych wyrażeń za pomocą działań wyrażenia niestandardowego

 Wyrażenia w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] są rozszerzalne, co pozwala na dodatkowe działania wyrażenia, które mają być tworzone. W poniższym przykładzie pokazano działanie, które zwraca sumę trzech wartości całkowitych.

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

 Za pomocą tego nowego działania można przepisać poprzedni przepływ pracy, który dodał trzy wartości, jak pokazano w poniższym przykładzie:

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

 Aby uzyskać więcej informacji na temat używania wyrażeń w kodzie, zobacz [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywu](authoring-workflows-activities-and-expressions-using-imperative-code.md).
