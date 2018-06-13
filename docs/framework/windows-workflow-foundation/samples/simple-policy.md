---
title: Proste zasad
ms.date: 03/30/2017
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
ms.openlocfilehash: dff3979d75fdeb5a45be3940af3568c26f5e8f98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515899"
---
# <a name="simple-policy"></a>Proste zasad
Ten przykład przedstawia sposób użycia <xref:System.Workflow.Activities.PolicyActivity> działania w przepływie pracy.  
  
 Sekwencyjny przepływ pracy, w tym przykładzie jest tworzona przy użyciu <xref:System.Workflow.Activities.PolicyActivity> działania. Przepływ pracy definiuje `orderValue`, `customerType`, i `discount` pola, które są używane do definiowania produktu discount przepływu pracy. Od reguł zdefiniowanych w pliku reguł wartość Rabat na podstawie `orderValue` i `customerType`. `orderValue` i `customerType` są ustawione w `SimplePolicyWorkflow` definicji klasy i można ich zmieniać do zmiany zachowania. Wynikowa rabat są zapisywane do konsoli w <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> obsługi zdarzeń, który jest zdefiniowany w `SimplePolicyWorkflow` klasy.  
  
### <a name="to-build-the-sample"></a>Aby samodzielnie tworzyć przykładowy  
  
1.  Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom rozwiązania bez debugowania, naciskając klawisze CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
-   W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze SimplePolicy\bin\debug (lub folderu SimplePolicy\bin dla używanej wersji programu Visual Basic przykładu) znajdujący się poniżej głównego folderu przykładowej.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Zasady zaawansowane](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
