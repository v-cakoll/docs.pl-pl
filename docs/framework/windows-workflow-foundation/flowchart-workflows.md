---
title: Schemat blokowy przepływów pracy
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: dd013e47da881c16d1fa469dfc3e3c4f2a86b6e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514527"
---
# <a name="flowchart-workflows"></a><span data-ttu-id="b7950-102">Schemat blokowy przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="b7950-102">Flowchart Workflows</span></span>
<span data-ttu-id="b7950-103">Schemat blokowy jest dobrze znanego modelu projektowania programów.</span><span class="sxs-lookup"><span data-stu-id="b7950-103">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="b7950-104">Schemat blokowy działania jest zwykle używane do implementowania niesekwencyjnych przepływy pracy, ale może służyć do sekwencyjnego przepływy pracy, jeśli nie `FlowDecision` węzły są używane.</span><span class="sxs-lookup"><span data-stu-id="b7950-104">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>  
  
## <a name="flowchart-workflow-structure"></a><span data-ttu-id="b7950-105">Schemat blokowy strukturę przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b7950-105">Flowchart Workflow Structure</span></span>  
 <span data-ttu-id="b7950-106">Schemat blokowy działania jest to działanie, które zawiera kolekcję działań do wykonania.</span><span class="sxs-lookup"><span data-stu-id="b7950-106">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="b7950-107">Zaprezentowane również zawierać przepływu sterowania elementów takich jak <xref:System.Activities.Statements.FlowDecision> i <xref:System.Activities.Statements.FlowSwitch%601> który bezpośrednie wykonywanie między zawartych działań na podstawie wartości zmiennych.</span><span class="sxs-lookup"><span data-stu-id="b7950-107">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>  
  
## <a name="types-of-flow-nodes"></a><span data-ttu-id="b7950-108">Typy węzłów przepływu</span><span class="sxs-lookup"><span data-stu-id="b7950-108">Types of Flow Nodes</span></span>  
 <span data-ttu-id="b7950-109">Różnych typów elementów są używane w zależności od typu sterowaniu przepływem wymagana, gdy element jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="b7950-109">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="b7950-110">Typy elementów schemat blokowy:</span><span class="sxs-lookup"><span data-stu-id="b7950-110">Types of flowchart elements include:</span></span>  
  
-   <span data-ttu-id="b7950-111">`FlowStep` — Modele jeden krok wykonywania w schemacie blokowym.</span><span class="sxs-lookup"><span data-stu-id="b7950-111">`FlowStep` - Models one step of execution in the flowchart.</span></span>  
  
-   <span data-ttu-id="b7950-112">`FlowDecision` -Wykonanie gałęzie oparciu warunek typu Boolean, podobnie jak <xref:System.Activities.Statements.If>.</span><span class="sxs-lookup"><span data-stu-id="b7950-112">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>  
  
-   <span data-ttu-id="b7950-113">`FlowSwitch` — Wykonanie gałęzie na podstawie wyłącznego przełącznika, podobnie jak <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="b7950-113">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>  
  
 <span data-ttu-id="b7950-114">Każde łącze ma `Action` właściwość, która definiuje <xref:System.Activities.ActivityAction> który może służyć do wykonywania działań podrzędnych oraz co najmniej jedną `Next` właściwości, które definiują, które element lub elementy do wykonania, gdy bieżący element kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="b7950-114">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>  
  
### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="b7950-115">Tworzenie sekwencji podstawowe działania z węzłem FlowStep</span><span class="sxs-lookup"><span data-stu-id="b7950-115">Creating a Basic Activity Sequence with a FlowStep Node</span></span>  
 <span data-ttu-id="b7950-116">Modelowanie podstawowe sekwencji, w którym dwa działania wykonać z kolei `FlowStep` element jest używany.</span><span class="sxs-lookup"><span data-stu-id="b7950-116">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="b7950-117">W poniższym przykładzie dwa `FlowStep` elementy są używane do wykonywania dwóch działań w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="b7950-117">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>  
  
```xml  
<Flowchart>  
  <FlowStep>      
  <Assign DisplayName="Get Name">  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:String">[result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:String">["User"]</InArgument>  
    </Assign.Value>  
  </Assign>  
    <FlowStep.Next>  
      <FlowStep>  
        <WriteLine Text="["Hello, " & result]"/>  
</FlowStep>  
    </FlowStep.Next>  
  </FlowStep>  
</Flowchart>  
```  
  
### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="b7950-118">Tworzenie schematu blokowego warunkowego z węzłem elementu FlowDecision</span><span class="sxs-lookup"><span data-stu-id="b7950-118">Creating a Conditional Flowchart with a FlowDecision Node</span></span>  
 <span data-ttu-id="b7950-119">Modelowanie węzła warunkowego przepływu w przepływie pracy schematu blokowego (oznacza to, do utworzenia łącza, który działa jako tradycyjnych schemat blokowy decyzji symbol), <xref:System.Activities.Statements.FlowDecision> węzła jest używany.</span><span class="sxs-lookup"><span data-stu-id="b7950-119">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="b7950-120"><xref:System.Activities.Statements.FlowDecision.Condition%2A> Właściwości węzła ustawiono wyrażenie definiujące warunek, i <xref:System.Activities.Statements.FlowDecision.True%2A> i <xref:System.Activities.Statements.FlowDecision.False%2A> właściwości są ustawione na <xref:System.Activities.Statements.FlowNode> wystąpień do wykonania, jeśli wyrażenie ma `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="b7950-120">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="b7950-121">Poniższy przykład przedstawia sposób definiowania przepływu pracy korzystającego z <xref:System.Activities.Statements.FlowDecision> węzła.</span><span class="sxs-lookup"><span data-stu-id="b7950-121">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>  
  
```xml  
<Flowchart>  
  <FlowStep>  
    <Read Result="[s]"/>  
    <FlowStep.Next>  
      <FlowDecision>  
        <IsEmpty Input="[s]" />  
        <FlowDecision.True>  
    <FlowStep>  
            <Write Text="Empty"/>  
    </FlowStep>  
        </FlowDecision.True>  
        <FlowDecision.False>  
    <FlowStep>  
            <Write Text="Non-Empty"/>  
          </FlowStep>  
        </FlowDecision.False>  
      </FlowDecision>  
    </FlowStep.Next>  
  </FlowStep>  
</Flowchart>  
```  
  
### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="b7950-122">Tworzenie przełącznika wyłącznego z węzłem elementu FlowSwitch</span><span class="sxs-lookup"><span data-stu-id="b7950-122">Creating an Exclusive Switch with a FlowSwitch Node</span></span>  
 <span data-ttu-id="b7950-123">Modelowanie schemat blokowy jest wybranej ścieżki wyłącznego oparte na wartość zgodną <xref:System.Activities.Statements.FlowSwitch%601> węzła jest używany.</span><span class="sxs-lookup"><span data-stu-id="b7950-123">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="b7950-124"><xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Właściwość jest ustawiona na <xref:System.Activities.Activity%601> z parametrem typu <xref:System.Object> definiuje wartość do dopasowania opcji przed.</span><span class="sxs-lookup"><span data-stu-id="b7950-124">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="b7950-125"><xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> Właściwość definiuje słownik kluczy i <xref:System.Activities.Statements.FlowNode> obiekty do dopasowania do wyrażenia warunkowego, a zestaw <xref:System.Activities.Statements.FlowNode> obiektów, które definiują sposób wykonywania powinien przepływu Jeśli w danym przypadku pasuje do wyrażenia warunkowego.</span><span class="sxs-lookup"><span data-stu-id="b7950-125">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="b7950-126"><xref:System.Activities.Statements.FlowSwitch%601> Definiuje również <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> właściwość, która definiuje sposób wykonywania powinien przepływu Jeśli nie przypadków zgodne wyrażenie warunku.</span><span class="sxs-lookup"><span data-stu-id="b7950-126">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="b7950-127">W poniższym przykładzie pokazano sposób definiowania przepływu pracy korzystającego z <xref:System.Activities.Statements.FlowSwitch%601> elementu.</span><span class="sxs-lookup"><span data-stu-id="b7950-127">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>  
  
```xml  
<Flowchart>  
    <FlowSwitch>  
      <FlowStep x:Key="Red">  
        <WriteRed/>  
      </FlowStep>  
      <FlowStep x:Key="Blue">  
        <WriteBlue/>  
      </FlowStep>  
      <FlowStep x:Key="Green">  
        <WriteGreen/>  
      </FlowStep>  
    </FlowSwitch>  
</Flowchart>  
```
