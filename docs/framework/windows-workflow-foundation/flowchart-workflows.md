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
# <a name="flowchart-workflows"></a>Przepływy pracy schematów blokowych

Schemat blokowy to dobrze znany model służący do projektowania programów. Działanie Flowchart jest zwykle używane do implementowania przepływów pracy, które nie są sekwencyjne, ale mogą być używane dla sekwencyjnych przepływów pracy, jeśli nie `FlowDecision` są używane żadne węzły.

## <a name="flowchart-workflow-structure"></a>Struktura przepływu pracy schematu blokowego

 Działanie Flowchart jest działaniem zawierającym kolekcję działań do wykonania.  Schematy blokowe zawierają również elementy sterowania przepływem, takie jak <xref:System.Activities.Statements.FlowDecision> i <xref:System.Activities.Statements.FlowSwitch%601> bezpośrednie wykonywanie między zawartymi działaniami na podstawie wartości zmiennych.

## <a name="types-of-flow-nodes"></a>Typy węzłów przepływu

 Różne typy elementów są używane w zależności od typu sterowania przepływem wymaganego, gdy element jest wykonywany. Typy elementów schematu blokowego obejmują:

- `FlowStep`— Modeluje jeden krok wykonywania w schemacie blokowym.

- `FlowDecision`— Wykonywanie gałęzi na podstawie warunku logicznego, podobnego do <xref:System.Activities.Statements.If> .

- `FlowSwitch`— Wykonywanie gałęzi opartych na wyłącznym przełączniku, podobnie jak w przypadku programu <xref:System.Activities.Statements.Switch%601> .

Każdy link ma `Action` Właściwość, która definiuje <xref:System.Activities.ActivityAction> , która może służyć do wykonywania działań podrzędnych, oraz co najmniej jednej `Next` właściwości, która definiuje element lub elementy, które mają zostać wykonane po zakończeniu bieżącego elementu.

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>Tworzenie podstawowej sekwencji działania z węzłem FlowStep

Aby modelować podstawową sekwencję, w której dwie działania są wykonywane z kolei, `FlowStep` element jest używany. W poniższym przykładzie dwa `FlowStep` elementy są używane do wykonywania dwóch działań w sekwencji.

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>Tworzenie elementu Flowchart warunkowego z węzłem FlowDecision

Aby modelować węzeł przepływu warunkowego w przepływie pracy schematu blokowego (to oznacza, aby utworzyć łącze, które działa jako symbol decyzji tradycyjnego schematu blokowego), <xref:System.Activities.Statements.FlowDecision> jest używany węzeł. <xref:System.Activities.Statements.FlowDecision.Condition%2A>Właściwość węzła jest ustawiona na wyrażenie definiujące warunek, a <xref:System.Activities.Statements.FlowDecision.True%2A> <xref:System.Activities.Statements.FlowDecision.False%2A> właściwości i są ustawiane na wystąpienia, które <xref:System.Activities.Statements.FlowNode> mają być wykonywane, jeśli wyrażenie zwróci wartość `true` lub `false` . Poniższy przykład pokazuje, jak zdefiniować przepływ pracy korzystający z <xref:System.Activities.Statements.FlowDecision> węzła.

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>Tworzenie wyłącznego przełącznika przy użyciu węzła FlowSwitch

Aby modelować schemat blokowy, w którym wybrano jedną ścieżkę wyłączną na podstawie pasującej wartości, <xref:System.Activities.Statements.FlowSwitch%601> jest używany węzeł. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>Właściwość jest ustawiona na <xref:System.Activities.Activity%601> Typ z parametrem typu <xref:System.Object> , który definiuje wartość do dopasowania opcji. <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>Właściwość definiuje słownik kluczy i <xref:System.Activities.Statements.FlowNode> obiektów do dopasowania względem wyrażenia warunkowego oraz zestaw <xref:System.Activities.Statements.FlowNode> obiektów, które definiują sposób przepływu wykonywania, jeśli dany przypadek pasuje do wyrażenia warunkowego. <xref:System.Activities.Statements.FlowSwitch%601>Definiuje również <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> Właściwość, która definiuje sposób przepływu wykonywania, jeśli żadne przypadki nie pasują do wyrażenia warunku. Poniższy przykład ilustruje sposób definiowania przepływu pracy korzystającego z <xref:System.Activities.Statements.FlowSwitch%601> elementu.

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
