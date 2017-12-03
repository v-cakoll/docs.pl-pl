---
title: "Sprawdzanie poprawności działania zewnętrzne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6ebc79fa582a32ccc252e6c22b9b223870da7e44
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="external-activity-validation"></a>Sprawdzanie poprawności działania zewnętrzne
W tym przykładzie pokazano, jak dodać logikę weryfikacji wbudowane działania, których nie jesteś Autor. Logikę weryfikacji składa się z wymuszenie wszystkich <xref:System.Activities.Statements.If> przedstawia działań w przepływie pracy, musisz być ich <xref:System.Activities.Statements.If.Then%2A> zestaw właściwości lub ich <xref:System.Activities.Statements.If.Else%2A> zestawu właściwości. Ponadto logikę weryfikacji obejmuje sprawdzania wszystkie <xref:System.Activities.Statements.Pick> działania w przepływie pracy mają więcej niż jednej gałęzi i jeśli nie jest wielkość liter, generowany jest ostrzeżenie.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Ten przykład tworzy przepływ pracy z wystąpieniem każde działanie do sprawdzania poprawności: <xref:System.Activities.Statements.If> działania i <xref:System.Activities.Statements.Pick> działania. A <xref:System.Activities.Validation.Constraint> jest tworzona dla każdej zachowanie sprawdzania poprawności. Ograniczenia utworzone w tym przykładzie są `ConstraintError_IfShouldHaveThenOrElse` i `ConstraintWarning_PickHasOneBranch`. Następnie tych warunków ograniczających są dodawane do `AdditionalConstraints` Kolekcja <xref:System.Activities.Validation.ValidationSettings> wystąpienia. Na koniec `static` <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> metoda <xref:System.Activities.Validation.ActivityValidationServices> jest wywoływane w celu weryfikacji działań w przepływie pracy i weryfikacji wyników wydrukowaniu się do konsoli.  
  
> [!NOTE]
>  Warunki ograniczające zasady można dodać do żadnego działania. Na przykład można dodać ograniczenia zasad do <xref:System.Activities.Statements.Sequence> lub <xref:System.Activities.Statements.Parallel> działania.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik ExternalActivityValidation.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze Ctrl + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`