---
title: Używanie AsyncOperationContext w przykładzie działania
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: 4358a364a3f7ec69b7c1c548fcf82fe494f37505
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275006"
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a>Używanie AsyncOperationContext w przykładzie działania
W tym przykładzie pokazano, jak tworzyć niestandardowe <xref:System.Activities.CodeActivity> , który używa <xref:System.Activities.AsyncCodeActivityContext> do wykonywania pracy asynchronicznie poza przepływu pracy.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Korzysta z przykładowym działaniem <xref:System.IO.FileStream.BeginWrite%2A> i <xref:System.IO.FileStream.EndWrite%2A> metod <xref:System.IO.FileStream> klasy do asynchronicznego zapisu danych do pliku. Wzorzec wprowadzone w tym miejscu mogą być dostosowane do użytku z innych metod asynchronicznych. Podczas wykonywania operacji asynchronicznej może wykonywać inne działania w przepływie pracy, ale nie może zostać utrwalona przepływu pracy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Otwórz rozwiązanie przykładowe Async.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj i uruchom rozwiązanie.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`