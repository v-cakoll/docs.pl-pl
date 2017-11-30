---
title: "Przy użyciu działań kolekcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 84218f16f846e640baea663efc7153a40a6c764a
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="using-collection-activities"></a>Przy użyciu działań kolekcji
W tym przykładzie przedstawiono sposób użycia działań kolekcji (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, i <xref:System.Activities.Statements.RemoveFromCollection%601>) z klasy, która implementuje <xref:System.Collections.ICollection> interfejs oraz sposobu tworzenia działań niestandardowych, który przechodzi przez kolekcję do wydrukować zawartość każdego elementu w kolekcji. Działania niestandardowe, nosi nazwę `PrintCollection`, drukuje do konsoli elementu członkami kolekcji o nazwie `Numbers`.  
  
 W poniższej tabeli opisano cztery działania, które zapewniają manipulowania kolekcji dla przepływów pracy.  
  
|Nazwa działania|Opis|  
|-------------------|-----------------|  
|<xref:System.Activities.Statements.AddToCollection%601>|Dodaje element do kolekcji.|  
|<xref:System.Activities.Statements.ClearCollection%601>|Usuwa wszystkie elementy w kolekcji|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|Zwraca `true` Jeśli określony element istnieje w kolekcji.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|Usuwa element z kolekcji.|  
  
 Próbka składa się z dwóch rozwiązań, co w katalogu CodedWorkflow, a drugą w katalogu DesignerWorkflow. Pokazują one dwa różne sposoby używania działań dla tych samych celów.  
  
|Rozwiązanie|Opis|Główne pliki|  
|-|-|-|  
|CodedWorkflow|Aplikacja kliencka przykładowych pokazano, jak można wywołać działania kolekcji programowo.|**PrintCollection.cs**: działanie pomocnika drukowanie do konsoli każdego elementu w kolekcji.<br /><br /> **Plik program.cs**: programowane kompilacje działania sequence, zawiera szereg działań kolekcji, która go uruchomi.|  
|DesignerWorkflow|Aplikacja kliencka przykładowych pokazano, jak używać działań kolekcji deklaratywnie w Projektancie przepływów pracy.|**CollectionWorkflow.xaml**: deklaratywnie utworzone za pomocą projektanta, który korzysta z kolekcji działań przepływu pracy.<br /><br /> **PrintCollection.cs**: działanie pomocnika drukowanie do konsoli każdego elementu w kolekcji.<br /><br /> **Plik program.cs**: wywołuje przepływu pracy opisanego w CollectionWorkflow.xaml.|  
  
 W pokazu elementu członkami kolekcji `Numbers` są drukowane na konsoli przy użyciu niestandardowy działanie o nazwie `PrintCollection`.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania Collection.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`