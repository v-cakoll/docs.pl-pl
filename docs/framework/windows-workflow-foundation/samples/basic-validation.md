---
title: Podstawowe sprawdzanie poprawności
ms.date: 03/30/2017
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
ms.openlocfilehash: 74d99e2d426e9ea5701fad80418fdf019112cc9e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083325"
---
# <a name="basic-validation"></a>Podstawowe sprawdzanie poprawności
W tym przykładzie składa się z działań `CreateProduct`, która sprawdza, czy jego `Cost` argument jest mniejszy niż lub równa jego `Price` argumentu.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Istnieją dwa autorów, którzy sprawdzania poprawności, autor działania (tworzy logikę weryfikacji dla działania) i autor przepływu pracy, który wywołuje usług weryfikacji dla określonego przepływu pracy. W tym scenariuszu działanie chce, aby wymusić na to, że każde wystąpienie swojej działalności, musi mieć mniejszy lub równy koszt niż cena.  
  
 Tworzenie działania (wewnątrz działania) musi:  
  
-   Tworzenie ograniczenia (`PriceGreaterThanCost`). Jest to, gdzie znajduje się całą logikę weryfikacji.  
  
-   Zastąp `System.Activities.CodeActivity.OnGetConstraints()` i Dodaj ograniczenie (`PriceGreaterThanCost`) do ograniczenia <xref:System.Collections.IList>.  
  
 Tworzenie przepływu pracy (główny program) musi:  
  
-   Tworzenie przepływu pracy z wystąpieniem działanie do sprawdzania poprawności (`CreateProduct`).  
  
-   Wywołaj <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, co powoduje zwrócenie <xref:System.Activities.Validation.ValidationResults> zbiór <xref:System.Activities.Validation.ValidationError>.  
  
-   (Opcjonalnie) Drukuj <xref:System.Activities.Validation.ValidationError> obiektów.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Otwórz rozwiązanie przykładowe BasicValidation.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj i uruchom rozwiązanie.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`