---
title: "Korzystając ze zmiennych z zestaw reguł .NET Framework 3.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9b5cc982aaad92258102b313d8fc19a9ff1521a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a>Korzystając ze zmiennych z zestaw reguł .NET Framework 3.5
Ten przykład przedstawia sposób tworzenia przepływu pracy korzystającego z <xref:System.Activities.Statements.Interop> działania integracji działań niestandardowych w [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] używającej zasad i reguł. Przepływ pracy przekazuje dane do działania niestandardowego przez powiązanie zmiennych, właściwości zależności udostępnianych przez działania niestandardowego.  
  
## <a name="sample-walkthrough"></a>Przykładowe wskazówki  
  
#### <a name="to-examine-travelrulelibrary"></a>Aby sprawdzić TravelRuleLibrary  
  
1.  Przy użyciu [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], otwórz plik rozwiązania InteropWith35RuleSet.sln.  
  
2.  Otwórz TravelRuleSet.cs w Projektancie przepływów pracy.  
  
     Niestandardowe działania sekwencyjnego, który zawiera <xref:System.Workflow.Activities.PolicyActivity> jest wyświetlany.  
  
3.  Kliknij dwukrotnie działanie zasad DiscountPolicy do sprawdzenia zasad.  
  
     Edytor reguł pojawia się, aby wyświetlić zasady.  
  
4.  Kliknij prawym przyciskiem myszy `DiscountPolicy` i wybierz **kod widoku** opcję, aby sprawdzić kod obok kodu C# dla działania.  
  
     Sprawdź ustawienie właściwości zależności `DiscountLevel`. Jest to równoważne argumentów [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]argumenty, zobacz [zmiennych i argumenty](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 Jest to projekt sekwencyjnego przepływu pracy, który używa <xref:System.Activities.Statements.Interop> działania integracji z niestandardowego zestawu reguł utworzonych w `TravelRuleLibrary` projektu. Zmienne utworzone na najwyższym poziomie <xref:System.Activities.Statements.Sequence> działania. <xref:System.Activities.Statements.Interop> To działanie służy do integracji z `TravelRuleSet` działania. Zmienne, które są zadeklarowane na <xref:System.Activities.Statements.Sequence> są używane w celu powiązania właściwości zależności.  
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania InteropWith35RuleSet.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`  
  
## <a name="see-also"></a>Zobacz też
