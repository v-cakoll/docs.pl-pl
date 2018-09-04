---
title: Działanie IfElse za pomocą reguł
ms.date: 03/30/2017
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
ms.openlocfilehash: 31906f04149a0ca7659201965ca565c7fa2af305
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500532"
---
# <a name="ifelse-with-rules"></a>Działanie IfElse za pomocą reguł
W tym przykładzie przedstawiono użycie warunku reguły z <xref:System.Workflow.Activities.IfElseActivity> działania.  
  
 Przykład przekazuje `OrderValue` parametru z hosta. Wartość parametru jest używana w warunku reguły w pierwszej gałęzi <xref:System.Workflow.Activities.IfElseActivity> działania. Jeśli wartość jest mniejsza niż 10 000, wykonuje pierwszej gałęzi i <xref:System.Workflow.Activities.CodeActivity> drukuje działania w pierwszej gałęzi **Pobierz menedżera o zatwierdzenie** do konsoli. Jeśli wartość jest większa niż 10 000, <xref:System.Workflow.Activities.CodeActivity> działania w drugim gałęzi wykonuje i drukuje **Rozpoczynanie zatwierdzenia VP**.  
  
### <a name="to-build-the-sample"></a>Aby skompilować przykład  
  
1.  Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom rozwiązanie bez debugowania, naciskając klawisze CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
-   W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze IfElseWithRules\bin\debug (lub folder IfElseWithRules\bin wersję przykładu w Visual Basic), który znajduje się poniżej głównego folderu dla przykładu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
