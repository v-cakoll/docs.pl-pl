---
title: Przepływy pracy schematów blokowych
description: W tym artykule opisano działanie Flowchart, które zazwyczaj służy do implementowania niesekwencyjnych przepływów pracy w programie Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: ce0661653a1d50b3f7264246b810faabbd12bf5f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419918"
---
# <a name="flowchart-workflows"></a><span data-ttu-id="01c8a-103">Przepływy pracy schematów blokowych</span><span class="sxs-lookup"><span data-stu-id="01c8a-103">Flowchart Workflows</span></span>

<span data-ttu-id="01c8a-104">Schemat blokowy to dobrze znany model służący do projektowania programów.</span><span class="sxs-lookup"><span data-stu-id="01c8a-104">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="01c8a-105">Działanie Flowchart jest zwykle używane do implementowania przepływów pracy, które nie są sekwencyjne, ale mogą być używane dla sekwencyjnych przepływów pracy, jeśli nie `FlowDecision` są używane żadne węzły.</span><span class="sxs-lookup"><span data-stu-id="01c8a-105">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>

## <a name="flowchart-workflow-structure"></a><span data-ttu-id="01c8a-106">Struktura przepływu pracy schematu blokowego</span><span class="sxs-lookup"><span data-stu-id="01c8a-106">Flowchart workflow structure</span></span>

 <span data-ttu-id="01c8a-107">Działanie Flowchart jest działaniem zawierającym kolekcję działań do wykonania.</span><span class="sxs-lookup"><span data-stu-id="01c8a-107">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="01c8a-108">Schematy blokowe zawierają również elementy sterowania przepływem, takie jak <xref:System.Activities.Statements.FlowDecision> i <xref:System.Activities.Statements.FlowSwitch%601> bezpośrednie wykonywanie między zawartymi działaniami na podstawie wartości zmiennych.</span><span class="sxs-lookup"><span data-stu-id="01c8a-108">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>

## <a name="types-of-flow-nodes"></a><span data-ttu-id="01c8a-109">Typy węzłów przepływu</span><span class="sxs-lookup"><span data-stu-id="01c8a-109">Types of flow nodes</span></span>

 <span data-ttu-id="01c8a-110">Różne typy elementów są używane w zależności od typu sterowania przepływem wymaganego, gdy element jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="01c8a-110">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="01c8a-111">Typy elementów schematu blokowego obejmują:</span><span class="sxs-lookup"><span data-stu-id="01c8a-111">Types of flowchart elements include:</span></span>

- <span data-ttu-id="01c8a-112">`FlowStep`— Modeluje jeden krok wykonywania w schemacie blokowym.</span><span class="sxs-lookup"><span data-stu-id="01c8a-112">`FlowStep` - Models one step of execution in the flowchart.</span></span>

- <span data-ttu-id="01c8a-113">`FlowDecision`— Wykonywanie gałęzi na podstawie warunku logicznego, podobnego do <xref:System.Activities.Statements.If> .</span><span class="sxs-lookup"><span data-stu-id="01c8a-113">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>

- <span data-ttu-id="01c8a-114">`FlowSwitch`— Wykonywanie gałęzi opartych na wyłącznym przełączniku, podobnie jak w przypadku programu <xref:System.Activities.Statements.Switch%601> .</span><span class="sxs-lookup"><span data-stu-id="01c8a-114">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>

<span data-ttu-id="01c8a-115">Każdy link ma `Action` Właściwość, która definiuje <xref:System.Activities.ActivityAction> , która może służyć do wykonywania działań podrzędnych, oraz co najmniej jednej `Next` właściwości, która definiuje element lub elementy, które mają zostać wykonane po zakończeniu bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="01c8a-115">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="01c8a-116">Tworzenie podstawowej sekwencji działania z węzłem FlowStep</span><span class="sxs-lookup"><span data-stu-id="01c8a-116">Creating a basic activity sequence with a FlowStep node</span></span>

<span data-ttu-id="01c8a-117">Aby modelować podstawową sekwencję, w której dwie działania są wykonywane z kolei, `FlowStep` element jest używany.</span><span class="sxs-lookup"><span data-stu-id="01c8a-117">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="01c8a-118">W poniższym przykładzie dwa `FlowStep` elementy są używane do wykonywania dwóch działań w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="01c8a-118">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>

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
        <WriteLine Text="Hello, " & [result]/>
      </FlowStep>
    </FlowStep.Next>
  </FlowStep>
</Flowchart>
```

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="01c8a-119">Tworzenie elementu Flowchart warunkowego z węzłem FlowDecision</span><span class="sxs-lookup"><span data-stu-id="01c8a-119">Creating a conditional flowchart with a FlowDecision node</span></span>

<span data-ttu-id="01c8a-120">Aby modelować węzeł przepływu warunkowego w przepływie pracy schematu blokowego (to oznacza, aby utworzyć łącze, które działa jako symbol decyzji tradycyjnego schematu blokowego), <xref:System.Activities.Statements.FlowDecision> jest używany węzeł.</span><span class="sxs-lookup"><span data-stu-id="01c8a-120">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="01c8a-121"><xref:System.Activities.Statements.FlowDecision.Condition%2A>Właściwość węzła jest ustawiona na wyrażenie definiujące warunek, a <xref:System.Activities.Statements.FlowDecision.True%2A> <xref:System.Activities.Statements.FlowDecision.False%2A> właściwości i są ustawiane na wystąpienia, które <xref:System.Activities.Statements.FlowNode> mają być wykonywane, jeśli wyrażenie zwróci wartość `true` lub `false` .</span><span class="sxs-lookup"><span data-stu-id="01c8a-121">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="01c8a-122">Poniższy przykład pokazuje, jak zdefiniować przepływ pracy korzystający z <xref:System.Activities.Statements.FlowDecision> węzła.</span><span class="sxs-lookup"><span data-stu-id="01c8a-122">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="01c8a-123">Tworzenie wyłącznego przełącznika przy użyciu węzła FlowSwitch</span><span class="sxs-lookup"><span data-stu-id="01c8a-123">Creating an exclusive switch with a FlowSwitch node</span></span>

<span data-ttu-id="01c8a-124">Aby modelować schemat blokowy, w którym wybrano jedną ścieżkę wyłączną na podstawie pasującej wartości, <xref:System.Activities.Statements.FlowSwitch%601> jest używany węzeł.</span><span class="sxs-lookup"><span data-stu-id="01c8a-124">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="01c8a-125"><xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>Właściwość jest ustawiona na <xref:System.Activities.Activity%601> Typ z parametrem typu <xref:System.Object> , który definiuje wartość do dopasowania opcji.</span><span class="sxs-lookup"><span data-stu-id="01c8a-125">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="01c8a-126"><xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>Właściwość definiuje słownik kluczy i <xref:System.Activities.Statements.FlowNode> obiektów do dopasowania względem wyrażenia warunkowego oraz zestaw <xref:System.Activities.Statements.FlowNode> obiektów, które definiują sposób przepływu wykonywania, jeśli dany przypadek pasuje do wyrażenia warunkowego.</span><span class="sxs-lookup"><span data-stu-id="01c8a-126">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="01c8a-127"><xref:System.Activities.Statements.FlowSwitch%601>Definiuje również <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> Właściwość, która definiuje sposób przepływu wykonywania, jeśli żadne przypadki nie pasują do wyrażenia warunku.</span><span class="sxs-lookup"><span data-stu-id="01c8a-127">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="01c8a-128">Poniższy przykład ilustruje sposób definiowania przepływu pracy korzystającego z <xref:System.Activities.Statements.FlowSwitch%601> elementu.</span><span class="sxs-lookup"><span data-stu-id="01c8a-128">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>

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
