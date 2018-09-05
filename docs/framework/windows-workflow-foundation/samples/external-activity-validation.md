---
title: Walidacja działania zewnętrznego
ms.date: 03/30/2017
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
ms.openlocfilehash: 4805bec3deed0779b02687b11dd487e673802925
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527810"
---
# <a name="external-activity-validation"></a>Walidacja działania zewnętrznego
Niniejszy przykład pokazuje, jak dodać logikę walidacji do wbudowanego działania, których nie jesteś autorem. Logikę weryfikacji, który składa się z wymuszenie stałego włączenia wszystkie <xref:System.Activities.Statements.If> działania obecne w przepływie pracy, albo mieć ich <xref:System.Activities.Statements.If.Then%2A> zestaw właściwości lub ich <xref:System.Activities.Statements.If.Else%2A> zestaw właściwości. Ponadto logikę weryfikacji obejmuje sprawdzanie wszystkich <xref:System.Activities.Statements.Pick> działania w przepływie pracy mają więcej niż jednej gałęzi, a jeśli tak nie jest rzeczywiście, generowane jest ostrzeżenie.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Ten przykład umożliwia utworzenie przepływu pracy z wystąpieniem każde działanie, aby sprawdzić poprawność: <xref:System.Activities.Statements.If> działania i <xref:System.Activities.Statements.Pick> działania. Element <xref:System.Activities.Validation.Constraint> jest tworzony dla każdego zachowanie walidacji. Ograniczenia utworzone w tym przykładzie są `ConstraintError_IfShouldHaveThenOrElse` i `ConstraintWarning_PickHasOneBranch`. Następnie te ograniczenia są dodawane do `AdditionalConstraints` zbiór <xref:System.Activities.Validation.ValidationSettings> wystąpienia. Na koniec `static` <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> metoda <xref:System.Activities.Validation.ActivityValidationServices> jest wywoływana, aby sprawdzić poprawność działania w przepływie pracy i sprawdzanie poprawności, wyniki są drukowane do konsoli.  
  
> [!NOTE]
>  Warunki ograniczające zasady można dodać do dowolnego działania. Na przykład można dodać ograniczenia zasad, aby <xref:System.Activities.Statements.Sequence> lub <xref:System.Activities.Statements.Parallel> działania.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik ExternalActivityValidation.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy Ctrl + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`