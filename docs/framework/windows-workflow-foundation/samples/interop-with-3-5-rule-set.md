---
title: Współdziałanie z zestawem reguł 3.5
ms.date: 03/30/2017
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
ms.openlocfilehash: 5ea5454ef80bfd83611ed20392782d99cd8c0c25
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43872634"
---
# <a name="interop-with-35-rule-set"></a>Współdziałanie z zestawem reguł 3.5
Ten przykład demonstruje użycie <xref:System.Activities.Statements.Interop> działania w celu integracji z niestandardowych działań w [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] przy użyciu <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` i reguł. Przekazuje dane do działania niestandardowego przez powiązanie [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] zmiennych, które będą udostępniane przez działanie niestandardowe właściwości zależności.  
  
## <a name="requirements"></a>Wymagania  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.Activities.Statements.Interop> działanie, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` działania w [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] przy użyciu właściwości zależności  
  
## <a name="discussion"></a>Dyskusja  
 W przykładzie pokazano jednego ze scenariuszy integracji w celu integracji z [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] działania. Ten przykład obejmuje [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] działania niestandardowego, który wywołuje <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` działania.  
  
## <a name="travelrulelibrary"></a>TravelRuleLibrary  
 Otwieranie TravelRuleSet.cs w Projektancie zawiera niestandardowe działanie sekwencyjne, zawierający w następujący sposób działania zasad  
  
 ![Działania Interop](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")  
  
 Kliknij dwukrotnie **DiscountPolicy** działanie zasad, aby sprawdzić zasady. Edytor reguł pojawi się reguł.  
  
 ![Edytor zestawu reguł](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")  
  
 Kliknij prawym przyciskiem myszy **DiscountPolicy** działania, a następnie wybierz pozycję **Wyświetl kod** opcję, aby zbadać obok kodu C# kod, który łączy się z tego działania. Sprawdź ustawienie właściwości zależności `DiscountLevel`. Jest to równoważne <xref:System.Activities.Argument> w [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].  
  
```  
public static DependencyProperty DiscountLevelProperty = DependencyProperty.Register("DiscountLevel", typeof(int), typeof(TravelRuleSet));  
  
[DescriptionAttribute("DiscountLevel")]  
[CategoryAttribute("DiscountLevel Category")]  
[BrowsableAttribute(true)]  
[DesignerSerializationVisibilityAttribute(DesignerSerializationVisibility.Visible)]  
public int DiscountLevel  
{  
   get  
   {  
return ((int)base.GetValue(TravelRuleSet.DiscountLevelProperty)));  
   }  
   set  
   {  
base.SetValue(TravelRuleSet.DiscountLevelProperty, value);  
   }  
}  
```  
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 Jest to [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] projektu sekwencyjnego przepływu pracy, który używa <xref:System.Activities.Statements.Interop> działania integracji z zestawu utworzonego w projekcie TravelRuleLibrary reguł niestandardowych. Zmienne są tworzone na najwyższym poziomie <xref:System.Activities.Statements.Sequence> w następujący sposób.  
  
 ![Zmienne](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")  
  
 ![Eksplorator rozwiązań](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")  
  
 Na koniec <xref:System.Activities.Statements.Interop> to działanie służy do integrowania z TravelRuleSet. Zmienne, które zostały wcześniej zgłoszone <xref:System.Activities.Statements.Sequence> są używane do powiązania właściwości zależności.  
  
 ![Typ działania](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")  
  
 ![Strzałka](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")  
  
 ![Właściwości](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
