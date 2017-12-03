---
title: "Współdziałanie z zestawu reguł w wersji 3.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5f5d8dd02d325d196cdceccea37624c9b2c1a01d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="interop-with-35-rule-set"></a>Współdziałanie z zestawu reguł w wersji 3.5
W tym przykładzie przedstawiono użycie <xref:System.Activities.Statements.Interop> działania integracji z działań niestandardowych w [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] przy użyciu <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` i zasady. Przekazuje dane do działania niestandardowego przez powiązanie [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] zmienne do właściwości zależności udostępnianych przez działania niestandardowego.  
  
## <a name="requirements"></a>Wymagania  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.Activities.Statements.Interop>działanie, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` działania w [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] z właściwości zależności  
  
## <a name="discussion"></a>Omówienie  
 W przykładzie pokazano jednego ze scenariuszy integracji dla integracji z [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] działania. Ten przykład zawiera [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] działania niestandardowego, który wywołuje <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` działania.  
  
## <a name="travelrulelibrary"></a>TravelRuleLibrary  
 Otwieranie TravelRuleSet.cs w Projektancie zawiera niestandardowe działanie sekwencyjne zawierający w następujący sposób działania zasad  
  
 ![Działania Interop](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")  
  
 Kliknij dwukrotnie **DiscountPolicy** działanie zasad do sprawdzenia zasad. Aby wyświetlić zasady zostanie wyświetlony Edytor reguły.  
  
 ![Edytor zestawu reguł](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")  
  
 Kliknij prawym przyciskiem myszy **DiscountPolicy** działanie i wybierz **kod widoku** opcję do zbadania obok kodu C# kod, który łączy się z tego działania. Sprawdź ustawienie właściwości zależności `DiscountLevel`. Jest to równoważne <xref:System.Activities.Argument> w [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].  
  
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
 Jest to [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] projektu sekwencyjnego przepływu pracy, który używa <xref:System.Activities.Statements.Interop> działania integracji z zestawu utworzonego w projekcie TravelRuleLibrary reguł niestandardowych. Zmienne utworzone na najwyższym poziomie <xref:System.Activities.Statements.Sequence> w następujący sposób.  
  
 ![Zmienne](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")  
  
 ![Eksplorator rozwiązań](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")  
  
 Ponadto <xref:System.Activities.Statements.Interop> to działanie służy do integracji z TravelRuleSet. Zmienne, które zostały zgłoszone wcześniej na <xref:System.Activities.Statements.Sequence> są używane w celu powiązania właściwości zależności.  
  
 ![Typ działania](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")  
  
 ![Strzałka](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")  
  
 ![Właściwości](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
