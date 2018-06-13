---
title: Korzystając ze zmiennych z zestaw reguł .NET Framework 3.5
ms.date: 03/30/2017
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
ms.openlocfilehash: 9fa6eaf58aaddc4673f08ec9a9001647a494877d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516859"
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a>Korzystając ze zmiennych z zestaw reguł .NET Framework 3.5
Ten przykład przedstawia sposób tworzenia przepływu pracy korzystającego z <xref:System.Activities.Statements.Interop> działania integracji działań niestandardowych w [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] używającej zasad i reguł. Przepływ pracy przekazuje dane do działania niestandardowego przez powiązanie zmiennych, właściwości zależności udostępnianych przez działania niestandardowego.  
  
## <a name="sample-walkthrough"></a>Przykładowe wskazówki  
  
#### <a name="to-examine-travelrulelibrary"></a>Aby sprawdzić TravelRuleLibrary  
  
1.  Za pomocą programu Visual Studio Otwórz plik rozwiązania InteropWith35RuleSet.sln.  
  
2.  Otwórz TravelRuleSet.cs w Projektancie przepływów pracy.  
  
     Niestandardowe działania sekwencyjnego, który zawiera <xref:System.Workflow.Activities.PolicyActivity> jest wyświetlany.  
  
3.  Kliknij dwukrotnie działanie zasad DiscountPolicy do sprawdzenia zasad.  
  
     Edytor reguł pojawia się, aby wyświetlić zasady.  
  
4.  Kliknij prawym przyciskiem myszy `DiscountPolicy` i wybierz **kod widoku** opcję, aby sprawdzić kod obok kodu C# dla działania.  
  
     Sprawdź ustawienie właściwości zależności `DiscountLevel`. Jest to równoważne argumentów [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]. Aby uzyskać więcej informacji na temat argumentami, zobacz [zmiennych i argumenty](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`