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
# <a name="flowchart-workflows"></a>Przepływy pracy schematów blokowych

Schemat blokowy jest dobrze znanym paradygmatem projektowania programów. Działanie schematu blokowego jest zwykle używane do implementowania niesekwencyjnych przepływów pracy, ale może `FlowDecision` być używane dla sekwencyjnych przepływów pracy, jeśli nie są używane żadne węzły.

## <a name="flowchart-workflow-structure"></a>Struktura przepływu pracy schematu blokowego

 Działanie schematu blokowego jest działanie, które zawiera zbiór działań do wykonania.  Schematy blokowe zawierają również elementy <xref:System.Activities.Statements.FlowDecision> <xref:System.Activities.Statements.FlowSwitch%601> sterujące przepływem, takie jak i bezpośrednie wykonywanie między zawartymi działaniami na podstawie wartości zmiennych.

## <a name="types-of-flow-nodes"></a>Typy węzłów przepływu

 Różne typy elementów są używane w zależności od typu kontroli przepływu wymagane podczas wykonywania elementu. Typy elementów schematu blokowego obejmują:

- `FlowStep`- Modele jeden krok wykonania w schematze blokowym.

- `FlowDecision`- Wykonanie oddziałów na podstawie warunku <xref:System.Activities.Statements.If>logicznego, podobnego do .

- `FlowSwitch`– Wykonanie oddziałów oparte na wyłącznym <xref:System.Activities.Statements.Switch%601>przełączniku, podobnym do .

Każde łącze ma `Action` właściwość, która <xref:System.Activities.ActivityAction> definiuje, który może służyć `Next` do wykonywania działań podrzędnych i co najmniej jedną właściwości, które definiują, który element lub elementy do wykonania po zakończeniu wykonywania bieżącego elementu.

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>Tworzenie podstawowej sekwencji działań za pomocą węzła FlowStep

Aby modelować podstawową sekwencję, w której `FlowStep` dwie działania są wykonywane z kolei, używany jest element. W poniższym przykładzie dwa `FlowStep` elementy są używane do wykonywania dwóch działań w sekwencji.

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>Tworzenie warunkowego schematu blokowego z węzłem FlowDecision

Aby modelować węzeł przepływu warunkowego w przepływie pracy schematu blokowego (czyli w celu utworzenia łącza, które działa jako symbol decyzji tradycyjnego schematu blokowego), <xref:System.Activities.Statements.FlowDecision> używany jest węzeł. Właściwość <xref:System.Activities.Statements.FlowDecision.Condition%2A> węzła jest ustawiona na wyrażenie, które <xref:System.Activities.Statements.FlowDecision.True%2A> definiuje <xref:System.Activities.Statements.FlowDecision.False%2A> warunek, a <xref:System.Activities.Statements.FlowNode> właściwości i właściwości są ustawione `true` na `false`wystąpienia do wykonania, jeśli wyrażenie ocenia lub . W poniższym przykładzie pokazano, jak zdefiniować przepływ pracy, który używa węzła. <xref:System.Activities.Statements.FlowDecision>

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>Tworzenie przełącznika wyłącznego za pomocą węzła FlowSwitch

Aby modelować schemat blokowy, w którym wybrano <xref:System.Activities.Statements.FlowSwitch%601> jedną ścieżkę wyłączną na podstawie pasującej wartości, używany jest węzeł. Właściwość <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> jest ustawiona na <xref:System.Activities.Activity%601> z <xref:System.Object> parametrem typu, który definiuje wartość, aby dopasować wybory. Właściwość <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> definiuje słownik kluczy <xref:System.Activities.Statements.FlowNode> i obiektów, aby dopasować do wyrażenia <xref:System.Activities.Statements.FlowNode> warunkowego i zestaw obiektów, które definiują sposób wykonywania należy przepływ, jeśli dana sprawa pasuje do wyrażenia warunkowego. Definiuje <xref:System.Activities.Statements.FlowSwitch%601> również <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> właściwość, która definiuje sposób wykonywania należy przepływać, jeśli żadne przypadki nie pasują do wyrażenia warunku. W poniższym przykładzie pokazano, jak zdefiniować <xref:System.Activities.Statements.FlowSwitch%601> przepływ pracy, który używa elementu.

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
