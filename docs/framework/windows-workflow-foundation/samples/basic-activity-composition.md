---
title: "Podstawowe działanie kompozycji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e8a4255eed0b957aaa5be16a807ab07d78e9fa1
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="basic-activity-composition"></a>Podstawowe działanie kompozycji
W tym przykładzie pokazano, jak utworzyć niestandardowe działania i działania dostarczane przez system do tworzenia działań niestandardowych więcej.  
  
 Przepływ pracy korzystający z działania przeglądu planuje listę pytania ankiety, a następnie wyprowadza odpowiedzi otrzymywanych.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 W tym przykładzie używa trzech działań niestandardowych. `ReadLine`jest prostą <xref:System.Activities.NativeActivity> \<ciąg > tworzącą <xref:System.Activities.Bookmark> podczas zaplanowane, a następnie ustawia `Return` <xref:System.Activities.OutArgument%601> wartości, z którym <xref:System.Activities.Bookmark> zostanie wznowione. `Prompt`jest <xref:System.Activities.Activity%601> \<ciąg > pobierającej <xref:System.Activities.InArgument%601>< ciąg\> o nazwie `Text` i zwraca użytkowników odpowiedzi w `Result` <xref:System.Activities.OutArgument%601> \<ciąg >. `Prompt` Używa działania <xref:System.Activities.Statements.Sequence> i <xref:System.Activities.Statements.WriteLine> działania, które jest dostarczane jako część programu .NET Framework i zawiera też niestandardowa `ReadLine` działania dotyczące pobierania danych wejściowych użytkownika. Ostatnie niestandardowe działanie jest `Survey` działania. Jest <xref:System.Activities.Activity>< ICollection\<ciąg >>.  To działanie ma <xref:System.Activities.InArgument%601>< IEnumerable < ciąg\>> o nazwie `Questions` i wypełnia `Result` limit argumentu z odpowiedzi. `Survey` Używa działania <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> i <xref:System.Activities.Statements.AddToCollection%601> z programu .NET Framework i wymaga `Prompt` działania udzielenia odpowiedzi na pytania ankiety i uzyskiwanie odpowiedzi.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Otwórz **BasicActivityComposition.sln** przykładowe rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Tworzenie i uruchamianie rozwiązania.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`