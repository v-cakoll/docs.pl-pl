---
title: Używanie zmiennych z reguł składników .NET Framework 3.5
ms.date: 03/30/2017
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
ms.openlocfilehash: 64d47564076e19e152e30b6ab0cb3900ce53cfa1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512857"
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a>Używanie zmiennych z reguł składników .NET Framework 3.5
Ten przykład przedstawia sposób tworzenia przepływu pracy, który używa <xref:System.Activities.Statements.Interop> działanie, aby zintegrować działanie niestandardowe napisane w [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] używającej zasadach i regułach. Przepływ pracy przekazuje dane do działania niestandardowego przez powiązanie zmienne udostępnianych przez działanie niestandardowe właściwości zależności.  
  
## <a name="sample-walkthrough"></a>Przewodnik po przykładzie  
  
#### <a name="to-examine-travelrulelibrary"></a>Aby zbadać TravelRuleLibrary  
  
1.  W programie Visual Studio Otwórz plik rozwiązania InteropWith35RuleSet.sln.  
  
2.  Otwórz TravelRuleSet.cs w Projektancie przepływu pracy.  
  
     Niestandardowe działania sekwencyjnego, który zawiera <xref:System.Workflow.Activities.PolicyActivity> jest wyświetlana.  
  
3.  Kliknij dwukrotnie działanie zasad DiscountPolicy, aby sprawdzić zasady.  
  
     Edytor reguł pojawia się, aby wyświetlić zasady.  
  
4.  Kliknij prawym przyciskiem myszy `DiscountPolicy` i wybierz **Wyświetl kod** opcję, aby sprawdzić kod obok kodu C# dla działania.  
  
     Sprawdź ustawienie właściwości zależności `DiscountLevel`. Jest to równoważne argumentów [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]. Aby uzyskać więcej informacji na temat argumentów, zobacz [zmienne i argumenty](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 Jest to projekt sekwencyjnego przepływu pracy, który używa <xref:System.Activities.Statements.Interop> działania integracji z niestandardowego zestawu reguł utworzonych w `TravelRuleLibrary` projektu. Zmienne są tworzone na najwyższym poziomie <xref:System.Activities.Statements.Sequence> działania. <xref:System.Activities.Statements.Interop> To działanie służy do integrowania z `TravelRuleSet` działania. Zmienne, które są zadeklarowane na <xref:System.Activities.Statements.Sequence> są używane do powiązania właściwości zależności.  
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania InteropWith35RuleSet.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`