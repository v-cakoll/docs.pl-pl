---
title: Przepływy pracy schematów blokowych
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: 1840f677929509e4902498c5aa8920f49cb13496
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773597"
---
# <a name="flowchart-workflows"></a><span data-ttu-id="96d54-102">Przepływy pracy schematów blokowych</span><span class="sxs-lookup"><span data-stu-id="96d54-102">Flowchart Workflows</span></span>

<span data-ttu-id="96d54-103">Schemat blokowy jest dobrze znanego modelu do projektowania programów.</span><span class="sxs-lookup"><span data-stu-id="96d54-103">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="96d54-104">Schemat blokowy działania jest zazwyczaj używana do zaimplementowania niż sekwencyjne przepływy pracy, ale może służyć do sekwencyjne przepływy pracy, jeśli nie `FlowDecision` węzły są używane.</span><span class="sxs-lookup"><span data-stu-id="96d54-104">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>

## <a name="flowchart-workflow-structure"></a><span data-ttu-id="96d54-105">Struktura przepływu pracy schematu blokowego</span><span class="sxs-lookup"><span data-stu-id="96d54-105">Flowchart workflow structure</span></span>

 <span data-ttu-id="96d54-106">Działania to działanie, które zawiera zbiór działań do wykonania.</span><span class="sxs-lookup"><span data-stu-id="96d54-106">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="96d54-107">Blokowe również zawierać elementy kontroli przepływu takich jak <xref:System.Activities.Statements.FlowDecision> i <xref:System.Activities.Statements.FlowSwitch%601> , bezpośrednie wykonywanie między zawarte działania na podstawie wartości zmiennych.</span><span class="sxs-lookup"><span data-stu-id="96d54-107">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>

## <a name="types-of-flow-nodes"></a><span data-ttu-id="96d54-108">Typy węzłów usługi flow</span><span class="sxs-lookup"><span data-stu-id="96d54-108">Types of flow nodes</span></span>

 <span data-ttu-id="96d54-109">Różne rodzaje elementów są używane w zależności od typu sterowanie przepływem wymagana, gdy element jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="96d54-109">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="96d54-110">Typy elementów schematu blokowego:</span><span class="sxs-lookup"><span data-stu-id="96d54-110">Types of flowchart elements include:</span></span>

- <span data-ttu-id="96d54-111">`FlowStep` — Jeden krok modele wykonywania w schemacie blokowym.</span><span class="sxs-lookup"><span data-stu-id="96d54-111">`FlowStep` - Models one step of execution in the flowchart.</span></span>

- <span data-ttu-id="96d54-112">`FlowDecision` -Wykonywania gałęzi oparciu o warunek logiczny, podobnie jak <xref:System.Activities.Statements.If>.</span><span class="sxs-lookup"><span data-stu-id="96d54-112">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>

- <span data-ttu-id="96d54-113">`FlowSwitch` — Wykonanie gałęzi na podstawie wyłączne przełącznika, podobne do <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="96d54-113">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>

<span data-ttu-id="96d54-114">Każde połączenie ma `Action` właściwość, która definiuje <xref:System.Activities.ActivityAction> można wykonać działania podrzędne i co najmniej jeden `Next` właściwości, które definiują, które element lub elementy do wykonania, gdy bieżący element kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="96d54-114">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="96d54-115">Tworzenie sekwencji podstawowe działania za pomocą węzła FlowStep</span><span class="sxs-lookup"><span data-stu-id="96d54-115">Creating a basic activity sequence with a FlowStep node</span></span>

<span data-ttu-id="96d54-116">Do modelowania podstawowe sekwencji, w której dwa działania, wykonywanie z kolei `FlowStep` element jest używany.</span><span class="sxs-lookup"><span data-stu-id="96d54-116">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="96d54-117">W poniższym przykładzie dwa `FlowStep` elementy są używane do wykonywania dwóch działań w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="96d54-117">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="96d54-118">Tworzenie warunkowe schematu blokowego za pomocą węzła FlowDecision</span><span class="sxs-lookup"><span data-stu-id="96d54-118">Creating a conditional flowchart with a FlowDecision node</span></span>

<span data-ttu-id="96d54-119">Do modelowania węzeł przepływ warunkowego w przepływie pracy schematu blokowego (oznacza to, aby utworzyć link, który działa jako tradycyjnych schemat blokowy decyzji symbol), <xref:System.Activities.Statements.FlowDecision> węzeł służy.</span><span class="sxs-lookup"><span data-stu-id="96d54-119">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="96d54-120"><xref:System.Activities.Statements.FlowDecision.Condition%2A> Właściwości węzła jest ustawiona na wyrażenie, który definiuje warunek, a <xref:System.Activities.Statements.FlowDecision.True%2A> i <xref:System.Activities.Statements.FlowDecision.False%2A> właściwości są ustawione na <xref:System.Activities.Statements.FlowNode> wystąpień do wykonania, jeśli wyrażenie ma `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="96d54-120">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="96d54-121">Poniższy przykład pokazuje jak zdefiniować przepływ pracy, który używa <xref:System.Activities.Statements.FlowDecision> węzła.</span><span class="sxs-lookup"><span data-stu-id="96d54-121">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="96d54-122">Tworzenie Przełącz wyłączne z węzłem FlowSwitch</span><span class="sxs-lookup"><span data-stu-id="96d54-122">Creating an exclusive switch with a FlowSwitch node</span></span>

<span data-ttu-id="96d54-123">Do modelowania blokowego, w którym jeden wyłączne ścieżka jest zaznaczona na podstawie o pasującej wartości <xref:System.Activities.Statements.FlowSwitch%601> węzła jest używany.</span><span class="sxs-lookup"><span data-stu-id="96d54-123">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="96d54-124"><xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Właściwość jest ustawiona na <xref:System.Activities.Activity%601> z parametrem typu <xref:System.Object> definiuje wartość, aby dopasować opcje względem.</span><span class="sxs-lookup"><span data-stu-id="96d54-124">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="96d54-125"><xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> Właściwość definiuje słownik kluczy i <xref:System.Activities.Statements.FlowNode> obiekty do dopasowywania wyrażenia warunkowego oraz zestaw <xref:System.Activities.Statements.FlowNode> obiekty, które definiują przepływ wykonania Jeśli dany przypadek pasuje do wyrażenia warunkowego.</span><span class="sxs-lookup"><span data-stu-id="96d54-125">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="96d54-126"><xref:System.Activities.Statements.FlowSwitch%601> Definiuje również <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> właściwość, która definiuje przepływ wykonania Jeśli żadne przypadki zgodne wyrażenie warunku.</span><span class="sxs-lookup"><span data-stu-id="96d54-126">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="96d54-127">Poniższy przykład pokazuje, jak zdefiniować przepływ pracy, który używa <xref:System.Activities.Statements.FlowSwitch%601> elementu.</span><span class="sxs-lookup"><span data-stu-id="96d54-127">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>

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
