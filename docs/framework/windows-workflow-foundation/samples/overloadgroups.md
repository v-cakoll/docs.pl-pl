---
title: OverloadGroups
ms.date: 03/30/2017
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
ms.openlocfilehash: 0773e76d36b25ad5485cc8912c7012815412de9f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514139"
---
# <a name="overloadgroups"></a>OverloadGroups
W tym przykładzie składa się z działania (`CreateLocation`), który ma dwa interesujące cechy:  
  
1.  Jest to niektóre wymagane argumenty i opcjonalnie niektóre z nich.  
  
2.  Umożliwia użytkownikowi określenie podać jedną z dwóch różnych zestawów argumentów.  
  
 Te zachowania, są wykonywane za pomocą te dwie funkcje:  
  
-   `[isRequired]` weryfikuje, że właściwość określonego działania jest przypisywanie, a jeśli nie, zgłosi wyjątek.  
  
-   `[OverloadGroup]` umieszcza razem zestawu argumentów, tak, aby wybrać przy użyciu jednego zestawu, lub inny użytkownik działania. Użytkownik nie może używać argumentów z różnych grup przeciążenie to samo wystąpienie.  
  
 Po skonfigurowaniu różnych przepływów pracy, należy wywołać <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> co powoduje zwrócenie <xref:System.Activities.Validation.ValidationResults> zbiór <xref:System.Activities.Validation.Constraint>. Drukuj <xref:System.Activities.Validation.Constraint> obiekty do konsoli.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Otwórz **OverloadGroups.sln** przykładowe rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj i uruchom rozwiązanie.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
