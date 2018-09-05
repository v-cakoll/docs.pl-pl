---
title: Proste zasady
ms.date: 03/30/2017
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
ms.openlocfilehash: 7f189e4d1811cb0b7dd9138b944bfd0552481690
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561267"
---
# <a name="simple-policy"></a>Proste zasady
Ten przykład ilustruje sposób używania <xref:System.Workflow.Activities.PolicyActivity> działania w przepływie pracy.  
  
 Sekwencyjny przepływ pracy w tym przykładzie jest tworzona przy użyciu <xref:System.Workflow.Activities.PolicyActivity> działania. Przepływ pracy określa `orderValue`, `customerType`, i `discount` pola, które są używane do definiowania produkt z rabatami przepływu pracy. Od reguł zdefiniowanych w pliku reguł ustaw wartość Rabat na wersję, która opiera się na `orderValue` i `customerType`. `orderValue` i `customerType` są ustawiane w `SimplePolicyWorkflow` definicji klasy i można ją zmienić na zmiany zachowania. Rabat wynikowe są zapisywane do konsoli w <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> programu obsługi zdarzeń, która jest zdefiniowana w `SimplePolicyWorkflow` klasy.  
  
### <a name="to-build-the-sample"></a>Aby skompilować przykład  
  
1.  Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom rozwiązanie bez debugowania, naciskając klawisze CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
-   W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze SimplePolicy\bin\debug (lub folder SimplePolicy\bin wersję przykładu w Visual Basic), który znajduje się poniżej głównego folderu dla przykładu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Zasady zaawansowane](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
