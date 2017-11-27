---
title: "Jeślilub przy użyciu reguł"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5cd0859db8071f9af130756fdc9b34726199be9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ifelse-with-rules"></a>Jeślilub przy użyciu reguł
W tym przykładzie pokazano sposób użycia warunek reguły z <xref:System.Workflow.Activities.IfElseActivity> działania.  
  
 Próbka przechodzi w `OrderValue` parametru z hosta. Wartość parametru jest używana w warunku reguły na pierwszej gałęzi <xref:System.Workflow.Activities.IfElseActivity> działania. Jeśli wartość jest mniejsza niż 10 000, wykonuje pierwszej gałęzi i <xref:System.Workflow.Activities.CodeActivity> działania w pierwszym oddziału drukuje **uzyskać zatwierdzenia przez menedżera** do konsoli. Jeśli wartość jest większa niż 10 000, <xref:System.Workflow.Activities.CodeActivity> działania w drugim gałęzi wykonuje i wyświetla **uzyskać zatwierdzenie VP**.  
  
### <a name="to-build-the-sample"></a>Aby samodzielnie tworzyć przykładowy  
  
1.  Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom rozwiązania bez debugowania, naciskając klawisze CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
-   W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze IfElseWithRules\bin\debug (lub folderu IfElseWithRules\bin dla używanej wersji programu Visual Basic przykładu) znajdujący się poniżej głównego folderu przykładowej.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
