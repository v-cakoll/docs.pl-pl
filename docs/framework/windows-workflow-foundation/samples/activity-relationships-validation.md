---
title: "Sprawdzanie poprawności relacje działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93cb5e93791c001e3795408a4c6b77be772f26e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="activity-relationships-validation"></a>Sprawdzanie poprawności relacje działania
Ten przykład zawiera trzy działań `CreateCity`, `CreateState`, i `CreateCountry`. `CreateCity`musi znajdować się wewnątrz `CreateState` działania, a `CreateState` musi znajdować się wewnątrz `CreateCountry` działania. Na potrzeby tej próbki, logikę weryfikacji jest w kodzie `CreateState` działania, a w języku XAML dla `CreateCity` działania. Zarówno ograniczeń ma takie samo zachowanie.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Udostępnia następujące trzy działania pomocnika, które umożliwiają deweloperom zweryfikować relacje między działaniami:  
  
 <xref:System.Activities.Validation.GetParentChain>  
 Zapewnia zbiór wszystkich działań, które należą do obiektu nadrzędnego bieżącego węzła  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 Zapewnia zbiór wszystkich działań, które należą do poddrzewa bieżącego węzła, z wyłączeniem bieżącego węzła  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 Zapewnia zbiór wszystkich działań w tym samym drzewie jako bieżącego węzła  
  
 W przykładzie <xref:System.Activities.Statements.ForEach%601> to działanie służy do przeprowadzenie kolekcji zwróconej przez <xref:System.Activities.Validation.GetParentChain>. Dla każdego elementu w kolekcji, jego typ jest porównywany z `CreateCountry` (lub `CreateState` Jeśli `CreateCity` jest sprawdzana), a gdy dopasowanie znajduje się wynik flaga jest ustawiona na `true`. Na koniec <xref:System.Activities.Validation.AssertValidation> służy do generowania błąd sprawdzania poprawności, jeśli ustawiono flagę wynik `false`.  
  
### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie próbki ContainmentValidation.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie.  
  
3.  Naciśnij klawisze CTRL + F5, aby uruchomić program.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
