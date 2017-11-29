---
title: "Schemat blokowy przepływów pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 568725f9a112756a773eddab9f56411f4d4fa86e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="flowchart-workflows"></a>Schemat blokowy przepływów pracy
Schemat blokowy jest dobrze znanego modelu projektowania programów. Schemat blokowy działania jest zwykle używane do implementowania niesekwencyjnych przepływy pracy, ale może służyć do sekwencyjnego przepływy pracy, jeśli nie `FlowDecision` węzły są używane.  
  
## <a name="flowchart-workflow-structure"></a>Schemat blokowy strukturę przepływu pracy  
 Schemat blokowy działania jest to działanie, które zawiera kolekcję działań do wykonania.  Zaprezentowane również zawierać przepływu sterowania elementów takich jak <xref:System.Activities.Statements.FlowDecision> i <xref:System.Activities.Statements.FlowSwitch%601> który bezpośrednie wykonywanie między zawartych działań na podstawie wartości zmiennych.  
  
## <a name="types-of-flow-nodes"></a>Typy węzłów przepływu  
 Różnych typów elementów są używane w zależności od typu sterowaniu przepływem wymagana, gdy element jest wykonywana. Typy elementów schemat blokowy:  
  
-   `FlowStep`— Modele jeden krok wykonywania w schemacie blokowym.  
  
-   `FlowDecision`-Wykonanie gałęzie oparciu warunek typu Boolean, podobnie jak <xref:System.Activities.Statements.If>.  
  
-   `FlowSwitch`— Wykonanie gałęzie na podstawie wyłącznego przełącznika, podobnie jak <xref:System.Activities.Statements.Switch%601>.  
  
 Każde łącze ma `Action` właściwość, która definiuje <xref:System.Activities.ActivityAction> który może służyć do wykonywania działań podrzędnych oraz co najmniej jedną `Next` właściwości, które definiują, które element lub elementy do wykonania, gdy bieżący element kończy działanie.  
  
### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>Tworzenie sekwencji podstawowe działania z węzłem FlowStep  
 Modelowanie podstawowe sekwencji, w którym dwa działania wykonać z kolei `FlowStep` element jest używany. W poniższym przykładzie dwa `FlowStep` elementy są używane do wykonywania dwóch działań w sekwencji.  
  
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
  
### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>Tworzenie schematu blokowego warunkowego z węzłem elementu FlowDecision  
 Modelowanie węzła warunkowego przepływu w przepływie pracy schematu blokowego (oznacza to, do utworzenia łącza, który działa jako tradycyjnych schemat blokowy decyzji symbol), <xref:System.Activities.Statements.FlowDecision> węzła jest używany. <xref:System.Activities.Statements.FlowDecision.Condition%2A> Właściwości węzła ustawiono wyrażenie definiujące warunek, i <xref:System.Activities.Statements.FlowDecision.True%2A> i <xref:System.Activities.Statements.FlowDecision.False%2A> właściwości są ustawione na <xref:System.Activities.Statements.FlowNode> wystąpień do wykonania, jeśli wyrażenie ma `true` lub `false`. Poniższy przykład przedstawia sposób definiowania przepływu pracy korzystającego z <xref:System.Activities.Statements.FlowDecision> węzła.  
  
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
  
### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>Tworzenie przełącznika wyłącznego z węzłem elementu FlowSwitch  
 Modelowanie schemat blokowy jest wybranej ścieżki wyłącznego oparte na wartość zgodną <xref:System.Activities.Statements.FlowSwitch%601> węzła jest używany. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Właściwość jest ustawiona na <xref:System.Activities.Activity%601> z parametrem typu <xref:System.Object> definiuje wartość do dopasowania opcji przed. <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> Właściwość definiuje słownik kluczy i <xref:System.Activities.Statements.FlowNode> obiekty do dopasowania do wyrażenia warunkowego, a zestaw <xref:System.Activities.Statements.FlowNode> obiektów, które definiują sposób wykonywania powinien przepływu Jeśli w danym przypadku pasuje do wyrażenia warunkowego. <xref:System.Activities.Statements.FlowSwitch%601> Definiuje również <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> właściwość, która definiuje sposób wykonywania powinien przepływu Jeśli nie przypadków zgodne wyrażenie warunku. W poniższym przykładzie pokazano sposób definiowania przepływu pracy korzystającego z <xref:System.Activities.Statements.FlowSwitch%601> elementu.  
  
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
