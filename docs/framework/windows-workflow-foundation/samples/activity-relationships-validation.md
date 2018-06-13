---
title: Sprawdzanie poprawności relacje działania
ms.date: 03/30/2017
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
ms.openlocfilehash: e6dd0e6a7b48444073ebae378e21c1b45977a1f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515111"
---
# <a name="activity-relationships-validation"></a>Sprawdzanie poprawności relacje działania
Ten przykład zawiera trzy działań `CreateCity`, `CreateState`, i `CreateCountry`. `CreateCity` musi znajdować się wewnątrz `CreateState` działania, a `CreateState` musi znajdować się wewnątrz `CreateCountry` działania. Na potrzeby tej próbki, logikę weryfikacji jest w kodzie `CreateState` działania, a w języku XAML dla `CreateCity` działania. Zarówno ograniczeń ma takie samo zachowanie.  
  
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
