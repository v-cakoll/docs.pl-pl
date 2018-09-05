---
title: Podstawowa kompozycja działań
ms.date: 03/30/2017
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
ms.openlocfilehash: ade8187ca44a8182b55cf0f01e5bfe5a9a747255
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518379"
---
# <a name="basic-activity-composition"></a>Podstawowa kompozycja działań
W tym przykładzie przedstawiono sposób tworzenia niestandardowych działań i działań dostarczane przez system, aby tworzyć więcej działań niestandardowych.  
  
 Przepływ pracy przy użyciu działania przeglądu planuje ankiety z listy pytań, a następnie generuje odpowiedzi otrzymywanych.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Ta próbka używa trzech działań niestandardowych. `ReadLine` to proste <xref:System.Activities.NativeActivity> \<ciągu > tworząca <xref:System.Activities.Bookmark> podczas zaplanowanych, a następnie ustawia `Return` <xref:System.Activities.OutArgument%601> wartości za pomocą którego <xref:System.Activities.Bookmark> zostanie wznowione. `Prompt` jest <xref:System.Activities.Activity%601> \<ciągu > przyjmującej <xref:System.Activities.InArgument%601>< ciąg\> o nazwie `Text` i zwraca odpowiedź w użytkowników `Result` <xref:System.Activities.OutArgument%601> \<ciągu >. `Prompt` Używa działania <xref:System.Activities.Statements.Sequence> i <xref:System.Activities.Statements.WriteLine> działań, które są dostarczane jako część programu .NET Framework i zawiera również niestandardowe `ReadLine` działania w celu uzyskania danych wejściowych użytkownika. Ostatnie niestandardowe działanie jest `Survey` działania. Jest <xref:System.Activities.Activity>< ICollection\<ciągu >>.  To działanie pobiera <xref:System.Activities.InArgument%601>< IEnumerable < ciąg\>> o nazwie `Questions` i wypełnia `Result` się argumentu z odpowiedzi. `Survey` Używa działania <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> i <xref:System.Activities.Statements.AddToCollection%601> z .NET Framework i wymaga `Prompt` dotyczące zadawania pytań ankiety i uzyskiwania odpowiedzi.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Otwórz **BasicActivityComposition.sln** przykładowe rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj i uruchom rozwiązanie.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`