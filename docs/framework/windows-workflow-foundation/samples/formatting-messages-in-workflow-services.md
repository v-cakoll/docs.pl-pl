---
title: Formatowanie wiadomości w usługach przepływu pracy
ms.date: 03/30/2017
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
ms.openlocfilehash: eb9a6b3a83a28154dc968bd4c1c41d34028bdd41
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389140"
---
# <a name="formatting-messages-in-workflow-services"></a>Formatowanie wiadomości w usługach przepływu pracy
Niniejszy przykład pokazuje jak innego użytkownika, typy mogą być używane w działań dotyczących komunikatów (WF usługi). Usługa próbki jest usługą zatwierdzenia proste wydatków i udostępnia trzy operacje. `ApproveExpense` pobiera typ kontraktu danych i pokazuje, jak używać znanych typów. Operacja zwraca `true` lub `false` oparte na ilości wydatków. `ApprovePO` Typ elementu XmlSerializer przyjmuje i zwraca `true` lub `false` oparte na ilości wydatków.`ApprovedVendor` pobiera typ kontraktu komunikatu i zwraca `true` lub `false` czy dostawca jest na liście zatwierdzonych dostawców, czy żądanie pochodzi z działu finansowego (dział finansowy może używać dowolnego dostawcy).  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Załaduj projekt rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompiluj projekt.  
  
2.  Najpierw uruchom usługę, wygenerowane w \FormatterService\bin\debug\ [katalog podstawowy rozwiązania]  
  
3.  Po drugie Uruchom aplikację klienta, wygenerowane w \FormatterClient\bin\debug [katalog podstawowy rozwiązania].  
  
4.  Klient wywołuje trzy operacje w usłudze i drukuje wyniki. Po zakończeniu naciśnij klawisz ENTER, aby zamknąć klienta, a następnie usługi.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`