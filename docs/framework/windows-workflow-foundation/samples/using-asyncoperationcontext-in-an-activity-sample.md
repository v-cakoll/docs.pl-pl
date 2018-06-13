---
title: Przy użyciu AsyncOperationContext w przykładowym działania
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: da7b62ef9e29621d1e6ee1046afb5455af1164bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515500"
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a>Przy użyciu AsyncOperationContext w przykładowym działania
W tym przykładzie pokazano, jak utworzyć niestandardowy <xref:System.Activities.CodeActivity> używającą <xref:System.Activities.AsyncCodeActivityContext> do wykonywania pracy asynchronicznie poza przepływ pracy.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Przykładowe działanie używa <xref:System.IO.FileStream.BeginWrite%2A> i <xref:System.IO.FileStream.EndWrite%2A> metody <xref:System.IO.FileStream> klasy do asynchronicznego zapisu danych do pliku. Wzorzec wprowadzone w tym miejscu, mogą być dostosowywane do użycia z innych metod asynchronicznych. Podczas wykonywania operacji asynchronicznej innych działań w przepływie pracy można wykonać, ale nie może zostać utrwalona przepływ pracy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Otwórz rozwiązanie próbki Async.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Tworzenie i uruchamianie rozwiązania.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`