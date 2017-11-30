---
title: "Ograniczenia typów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d42be018b6a92237b5914c180d329138fb95e7dc
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`