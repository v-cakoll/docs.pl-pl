---
title: Przepływy pracy schematów blokowych
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: b84b0de34f8869d9775fe0694e74c340cc16a6b3
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249067"
---
# <a name="flowchart-workflows"></a><span data-ttu-id="871ac-102">Przepływy pracy schematów blokowych</span><span class="sxs-lookup"><span data-stu-id="871ac-102">Flowchart Workflows</span></span>

<span data-ttu-id="871ac-103">Schemat blokowy jest dobrze znanym paradygmatem projektowania programów.</span><span class="sxs-lookup"><span data-stu-id="871ac-103">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="871ac-104">Działanie schematu blokowego jest zwykle używane do implementowania niesekwencyjnych przepływów pracy, ale może `FlowDecision` być używane dla sekwencyjnych przepływów pracy, jeśli nie są używane żadne węzły.</span><span class="sxs-lookup"><span data-stu-id="871ac-104">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>

## <a name="flowchart-workflow-structure"></a><span data-ttu-id="871ac-105">Struktura przepływu pracy schematu blokowego</span><span class="sxs-lookup"><span data-stu-id="871ac-105">Flowchart workflow structure</span></span>

 <span data-ttu-id="871ac-106">Działanie schematu blokowego jest działanie, które zawiera zbiór działań do wykonania.</span><span class="sxs-lookup"><span data-stu-id="871ac-106">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="871ac-107">Schematy blokowe zawierają również elementy <xref:System.Activities.Statements.FlowDecision> <xref:System.Activities.Statements.FlowSwitch%601> sterujące przepływem, takie jak i bezpośrednie wykonywanie między zawartymi działaniami na podstawie wartości zmiennych.</span><span class="sxs-lookup"><span data-stu-id="871ac-107">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>

## <a name="types-of-flow-nodes"></a><span data-ttu-id="871ac-108">Typy węzłów przepływu</span><span class="sxs-lookup"><span data-stu-id="871ac-108">Types of flow nodes</span></span>

 <span data-ttu-id="871ac-109">Różne typy elementów są używane w zależności od typu kontroli przepływu wymagane podczas wykonywania elementu.</span><span class="sxs-lookup"><span data-stu-id="871ac-109">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="871ac-110">Typy elementów schematu blokowego obejmują:</span><span class="sxs-lookup"><span data-stu-id="871ac-110">Types of flowchart elements include:</span></span>

- <span data-ttu-id="871ac-111">`FlowStep`- Modele jeden krok wykonania w schematze blokowym.</span><span class="sxs-lookup"><span data-stu-id="871ac-111">`FlowStep` - Models one step of execution in the flowchart.</span></span>

- <span data-ttu-id="871ac-112">`FlowDecision`- Wykonanie oddziałów na podstawie warunku <xref:System.Activities.Statements.If>logicznego, podobnego do .</span><span class="sxs-lookup"><span data-stu-id="871ac-112">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>

- <span data-ttu-id="871ac-113">`FlowSwitch`– Wykonanie oddziałów oparte na wyłącznym <xref:System.Activities.Statements.Switch%601>przełączniku, podobnym do .</span><span class="sxs-lookup"><span data-stu-id="871ac-113">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>

<span data-ttu-id="871ac-114">Każde łącze ma `Action` właściwość, która <xref:System.Activities.ActivityAction> definiuje, który może służyć `Next` do wykonywania działań podrzędnych i co najmniej jedną właściwości, które definiują, który element lub elementy do wykonania po zakończeniu wykonywania bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="871ac-114">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="871ac-115">Tworzenie podstawowej sekwencji działań za pomocą węzła FlowStep</span><span class="sxs-lookup"><span data-stu-id="871ac-115">Creating a basic activity sequence with a FlowStep node</span></span>

<span data-ttu-id="871ac-116">Aby modelować podstawową sekwencję, w której `FlowStep` dwie działania są wykonywane z kolei, używany jest element.</span><span class="sxs-lookup"><span data-stu-id="871ac-116">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="871ac-117">W poniższym przykładzie dwa `FlowStep` elementy są używane do wykonywania dwóch działań w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="871ac-117">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="871ac-118">Tworzenie warunkowego schematu blokowego z węzłem FlowDecision</span><span class="sxs-lookup"><span data-stu-id="871ac-118">Creating a conditional flowchart with a FlowDecision node</span></span>

<span data-ttu-id="871ac-119">Aby modelować węzeł przepływu warunkowego w przepływie pracy schematu blokowego (czyli w celu utworzenia łącza, które działa jako symbol decyzji tradycyjnego schematu blokowego), <xref:System.Activities.Statements.FlowDecision> używany jest węzeł.</span><span class="sxs-lookup"><span data-stu-id="871ac-119">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="871ac-120">Właściwość <xref:System.Activities.Statements.FlowDecision.Condition%2A> węzła jest ustawiona na wyrażenie, które <xref:System.Activities.Statements.FlowDecision.True%2A> definiuje <xref:System.Activities.Statements.FlowDecision.False%2A> warunek, a <xref:System.Activities.Statements.FlowNode> właściwości i właściwości są ustawione `true` na `false`wystąpienia do wykonania, jeśli wyrażenie ocenia lub .</span><span class="sxs-lookup"><span data-stu-id="871ac-120">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="871ac-121">W poniższym przykładzie pokazano, jak zdefiniować przepływ pracy, który używa węzła. <xref:System.Activities.Statements.FlowDecision></span><span class="sxs-lookup"><span data-stu-id="871ac-121">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="871ac-122">Tworzenie przełącznika wyłącznego za pomocą węzła FlowSwitch</span><span class="sxs-lookup"><span data-stu-id="871ac-122">Creating an exclusive switch with a FlowSwitch node</span></span>

<span data-ttu-id="871ac-123">Aby modelować schemat blokowy, w którym wybrano <xref:System.Activities.Statements.FlowSwitch%601> jedną ścieżkę wyłączną na podstawie pasującej wartości, używany jest węzeł.</span><span class="sxs-lookup"><span data-stu-id="871ac-123">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="871ac-124">Właściwość <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> jest ustawiona na <xref:System.Activities.Activity%601> z <xref:System.Object> parametrem typu, który definiuje wartość, aby dopasować wybory.</span><span class="sxs-lookup"><span data-stu-id="871ac-124">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="871ac-125">Właściwość <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> definiuje słownik kluczy <xref:System.Activities.Statements.FlowNode> i obiektów, aby dopasować do wyrażenia <xref:System.Activities.Statements.FlowNode> warunkowego i zestaw obiektów, które definiują sposób wykonywania należy przepływ, jeśli dana sprawa pasuje do wyrażenia warunkowego.</span><span class="sxs-lookup"><span data-stu-id="871ac-125">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="871ac-126">Definiuje <xref:System.Activities.Statements.FlowSwitch%601> również <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> właściwość, która definiuje sposób wykonywania należy przepływać, jeśli żadne przypadki nie pasują do wyrażenia warunku.</span><span class="sxs-lookup"><span data-stu-id="871ac-126">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="871ac-127">W poniższym przykładzie pokazano, jak zdefiniować <xref:System.Activities.Statements.FlowSwitch%601> przepływ pracy, który używa elementu.</span><span class="sxs-lookup"><span data-stu-id="871ac-127">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>

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
