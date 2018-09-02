---
title: Używanie działań kolekcji
ms.date: 03/30/2017
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
ms.openlocfilehash: a92208583ddf1c0d5d85b5af6a250a15ac8851b9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422630"
---
# <a name="using-collection-activities"></a>Używanie działań kolekcji
W tym przykładzie pokazano, jak skorzystać z działań kolekcji (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, i <xref:System.Activities.Statements.RemoveFromCollection%601>) przy użyciu klasy, która implementuje <xref:System.Collections.ICollection> interfejs oraz sposób tworzenia działań niestandardowych, który iteruje po kolekcji Wydrukuj zawartość każdego elementu w kolekcji. Niestandardowe działanie, które nosi `PrintCollection`, drukuje do konsoli elementu Członkowie kolekcji o nazwie `Numbers`.  
  
 W poniższej tabeli opisano cztery działań, które zapewniają manipulowania kolekcji dla przepływów pracy.  
  
|Nazwa działania|Opis|  
|-------------------|-----------------|  
|<xref:System.Activities.Statements.AddToCollection%601>|Dodaje element do kolekcji.|  
|<xref:System.Activities.Statements.ClearCollection%601>|Czyści wszystkie elementy w kolekcji|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|Zwraca `true` Jeśli określony element istnieje w kolekcji.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|Usuwa element z kolekcji.|  
  
 Przykład składa się z dwóch rozwiązań, jeden w obszarze Katalog CodedWorkflow, a druga w katalogu DesignerWorkflow. Pokazują one dwa różne sposoby użycia działań w tym samym celu.  
  
|Rozwiązanie|Opis|Pliki główne|  
|-|-|-|  
|CodedWorkflow|Przykładowa aplikacja kliencka, która pokazuje, jak programowo wywoływanie działań kolekcji.|**PrintCollection.cs**: działanie pomocnika, aby wyświetlić w konsoli każdy element w kolekcji.<br /><br /> **Plik program.cs**: programowe kompilacje działania sekwencji, który zawiera szereg działań kolekcji i wykonuje ten.|  
|DesignerWorkflow|Przykładowa aplikacja kliencka, która pokazuje, jak skorzystać z działań kolekcji deklaratywnie w Projektancie przepływu pracy.|**CollectionWorkflow.xaml**: przepływ pracy w sposób deklaratywny za pomocą projektanta, który używa działań kolekcji.<br /><br /> **PrintCollection.cs**: działanie pomocnika, aby wyświetlić w konsoli każdy element w kolekcji.<br /><br /> **Plik program.cs**: wywołuje opisany w CollectionWorkflow.xaml przepływ pracy.|  
  
 Podczas pokazu, element elementów członkowskich kolekcji `Numbers` są drukowane w konsoli przy użyciu działania niestandardowy o nazwie `PrintCollection`.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania Collection.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`