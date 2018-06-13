---
title: Ograniczenia typów
ms.date: 03/30/2017
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
ms.openlocfilehash: 53e5975017c3a27ede8ad07cd93f78f71df2d3e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517511"
---
# <a name="constraint-types"></a>Ograniczenia typów
W tym przykładzie pokazano dwa różne sposoby, aby zastosować ograniczenia do przepływu pracy, jest jednym z wewnątrz działania (Kompilacja) i jeden jest z poza (zasady). W tym scenariuszu działania (firmy 3rth firm) chce, aby sprawdzić poprawność relacji między dwa argumenty. W takim przypadku koszt powinna być mniejsza niż lub równa cenie. Jest to ograniczenie ogólne weryfikacji kompilacji.  
  
 Następnie chce dodać niektóre sprawdzania poprawności tego ogólnego działania właściciela sklepu. W przypadku jego Maciej chce większość jego produktów niż 9,99 $ lub mniej. Tak, używa ograniczenia zasad, które jest nad `CreateProduct` działania.  
  
 W przykładzie:  
  
 Określony przez autora działania (Kompilacja) musi:  
  
-   Tworzenie ograniczenia (`PriceGreaterThanCost`). Jest to, gdzie znajduje się całą logikę sprawdzania poprawności.  
  
-   Zastąpienie `System.Activities.CodeActivity.OnGetConstraints()` i Dodaj ograniczenie (`PriceGreaterThanCost`) do ograniczenia <xref:System.Collections.IList>.  
  
 Autor przepływu pracy (zasady) musi:  
  
-   Tworzenie przepływów pracy przy użyciu wystąpienia działania do sprawdzania poprawności (`CreateProduct`).  
  
-   Tworzenie ograniczenia (`MaxPrice`).  
  
-   Utwórz <xref:System.Activities.Validation.ValidationSettings> wystąpienia (`validationSettings`) i Dodaj ograniczenie (`MaxPrice`) do kolekcji `AdditionalConstraints`. W tym miejscu autorem przepływu pracy można dodać zasad ograniczeń do żadnego działania, takie jak sekwencji lub równolegle.  
  
-   Wywołanie <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, która zwraca <xref:System.Activities.Validation.ValidationResults> Kolekcja <xref:System.Activities.Validation.ValidationError> obiektów.  
  
-   (Opcjonalnie) Drukuj <xref:System.Activities.Validation.ValidationError> obiektów.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Otwórz rozwiązanie próbki ConstraintTypes.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Tworzenie i uruchamianie rozwiązania.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`