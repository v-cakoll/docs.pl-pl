---
title: Walidacja relacji działań
ms.date: 03/30/2017
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
ms.openlocfilehash: 50f08118fb5ad4d9b8fe809e7ab3cc5d57f28149
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394688"
---
# <a name="activity-relationships-validation"></a>Walidacja relacji działań
W tym przykładzie składa się z trzech działań `CreateCity`, `CreateState`, i `CreateCountry`. `CreateCity` musi znajdować się wewnątrz `CreateState` działania i `CreateState` musi znajdować się wewnątrz `CreateCountry` działania. Na potrzeby tego przykładu logikę weryfikacji jest w kodzie `CreateState` działania w XAML dla `CreateCity` działania. Oba ograniczenia mają takie samo zachowanie.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Udostępnia następujące trzy działań pomocnika, które umożliwiają deweloperom zweryfikować relacji między działaniami:  
  
 <xref:System.Activities.Validation.GetParentChain>  
 Zawiera zbiór wszystkich działań, które należą do elementu nadrzędnego bieżącego węzła  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 Zawiera zbiór wszystkich działań, które należą do podrzędnych drzewa w bieżącego węzła, z wyłączeniem bieżącego węzła  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 Zawiera zbiór wszystkich działań w tym samym drzewie jako bieżącego węzła  
  
 W tym przykładzie <xref:System.Activities.Statements.ForEach%601> to działanie służy do zaprezentowania zbiorze zwróconym przez <xref:System.Activities.Validation.GetParentChain>. Dla każdego elementu w kolekcji, jego typ jest porównywany z `CreateCountry` (lub `CreateState` Jeśli `CreateCity` jest weryfikowany), a kiedy zostanie znalezione dopasowanie Flaga wynik jest ustawiona na `true`. Na koniec <xref:System.Activities.Validation.AssertValidation> służy do generowania błąd sprawdzania poprawności, jeśli ustawiono flagę wynik `false`.  
  
### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie przykładowe ContainmentValidation.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie.  
  
3.  Naciśnij klawisze CTRL + F5, aby uruchomić program.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
