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
# <a name="flowchart-workflows"></a>Przepływy pracy schematów blokowych

Schemat blokowy jest dobrze znanego modelu do projektowania programów. Schemat blokowy działania jest zazwyczaj używana do zaimplementowania niż sekwencyjne przepływy pracy, ale może służyć do sekwencyjne przepływy pracy, jeśli nie `FlowDecision` węzły są używane.

## <a name="flowchart-workflow-structure"></a>Struktura przepływu pracy schematu blokowego

 Działania to działanie, które zawiera zbiór działań do wykonania.  Blokowe również zawierać elementy kontroli przepływu takich jak <xref:System.Activities.Statements.FlowDecision> i <xref:System.Activities.Statements.FlowSwitch%601> , bezpośrednie wykonywanie między zawarte działania na podstawie wartości zmiennych.

## <a name="types-of-flow-nodes"></a>Typy węzłów usługi flow

 Różne rodzaje elementów są używane w zależności od typu sterowanie przepływem wymagana, gdy element jest wykonywany. Typy elementów schematu blokowego:

- `FlowStep` — Jeden krok modele wykonywania w schemacie blokowym.

- `FlowDecision` -Wykonywania gałęzi oparciu o warunek logiczny, podobnie jak <xref:System.Activities.Statements.If>.

- `FlowSwitch` — Wykonanie gałęzi na podstawie wyłączne przełącznika, podobne do <xref:System.Activities.Statements.Switch%601>.

Każde połączenie ma `Action` właściwość, która definiuje <xref:System.Activities.ActivityAction> można wykonać działania podrzędne i co najmniej jeden `Next` właściwości, które definiują, które element lub elementy do wykonania, gdy bieżący element kończy działanie.

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>Tworzenie sekwencji podstawowe działania za pomocą węzła FlowStep

Do modelowania podstawowe sekwencji, w której dwa działania, wykonywanie z kolei `FlowStep` element jest używany. W poniższym przykładzie dwa `FlowStep` elementy są używane do wykonywania dwóch działań w sekwencji.

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>Tworzenie warunkowe schematu blokowego za pomocą węzła FlowDecision

Do modelowania węzeł przepływ warunkowego w przepływie pracy schematu blokowego (oznacza to, aby utworzyć link, który działa jako tradycyjnych schemat blokowy decyzji symbol), <xref:System.Activities.Statements.FlowDecision> węzeł służy. <xref:System.Activities.Statements.FlowDecision.Condition%2A> Właściwości węzła jest ustawiona na wyrażenie, który definiuje warunek, a <xref:System.Activities.Statements.FlowDecision.True%2A> i <xref:System.Activities.Statements.FlowDecision.False%2A> właściwości są ustawione na <xref:System.Activities.Statements.FlowNode> wystąpień do wykonania, jeśli wyrażenie ma `true` lub `false`. Poniższy przykład pokazuje jak zdefiniować przepływ pracy, który używa <xref:System.Activities.Statements.FlowDecision> węzła.

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>Tworzenie Przełącz wyłączne z węzłem FlowSwitch

Do modelowania blokowego, w którym jeden wyłączne ścieżka jest zaznaczona na podstawie o pasującej wartości <xref:System.Activities.Statements.FlowSwitch%601> węzła jest używany. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Właściwość jest ustawiona na <xref:System.Activities.Activity%601> z parametrem typu <xref:System.Object> definiuje wartość, aby dopasować opcje względem. <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> Właściwość definiuje słownik kluczy i <xref:System.Activities.Statements.FlowNode> obiekty do dopasowywania wyrażenia warunkowego oraz zestaw <xref:System.Activities.Statements.FlowNode> obiekty, które definiują przepływ wykonania Jeśli dany przypadek pasuje do wyrażenia warunkowego. <xref:System.Activities.Statements.FlowSwitch%601> Definiuje również <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> właściwość, która definiuje przepływ wykonania Jeśli żadne przypadki zgodne wyrażenie warunku. Poniższy przykład pokazuje, jak zdefiniować przepływ pracy, który używa <xref:System.Activities.Statements.FlowSwitch%601> elementu.

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
