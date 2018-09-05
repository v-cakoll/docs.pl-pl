---
title: Typy ograniczeń
ms.date: 03/30/2017
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
ms.openlocfilehash: 202a2c7b3a3fc400552e42c8606457964af66af2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506615"
---
# <a name="constraint-types"></a>Typy ograniczeń
W tym przykładzie przedstawiono dwa różne sposoby, aby zastosować ograniczenia do przepływu pracy, jest jednym z wewnątrz działania (Kompilacja) i jest jednym z poza nim (zasady). W tym scenariuszu działanie (z firmy zajmującej się oprogramowaniem firmy 3rth) chce, aby zweryfikować relacji między dwa argumenty. W tym przypadku koszt powinna być mniejsza niż lub równa. Jest to ograniczenie kompilacji ogólnej walidacji.  
  
 Następnie wybierz właściciel chce, aby dodać niektóre sprawdzanie poprawności do to ogólne działanie. W jego przypadku Piotr większość swoich produktów jako 9,99 USD lub mniej. Dlatego używa ograniczenia zasad, który jest w górnej części `CreateProduct` działania.  
  
 W przykładzie:  
  
 Tworzenie działania (Kompilacja) musi:  
  
-   Tworzenie ograniczenia (`PriceGreaterThanCost`). Jest to, gdzie znajduje się całą logikę weryfikacji.  
  
-   Zastąp `System.Activities.CodeActivity.OnGetConstraints()` i Dodaj ograniczenie (`PriceGreaterThanCost`) do ograniczenia <xref:System.Collections.IList>.  
  
 Tworzenie przepływu pracy (zasady) musi:  
  
-   Tworzenie przepływu pracy z wystąpieniem działanie do sprawdzania poprawności (`CreateProduct`).  
  
-   Tworzenie ograniczenia (`MaxPrice`).  
  
-   Tworzenie <xref:System.Activities.Validation.ValidationSettings> wystąpienia (`validationSettings`) i Dodaj ograniczenie (`MaxPrice`) do kolekcji `AdditionalConstraints`. W tym miejscu Autor przepływu pracy można dodać ograniczenia zasad do żadnych działań, takich jak sekwencji lub równolegle.  
  
-   Wywołaj <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, co powoduje zwrócenie <xref:System.Activities.Validation.ValidationResults> zbiór <xref:System.Activities.Validation.ValidationError> obiektów.  
  
-   (Opcjonalnie) Drukuj <xref:System.Activities.Validation.ValidationError> obiektów.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Otwórz rozwiązanie przykładowe ConstraintTypes.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj i uruchom rozwiązanie.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`