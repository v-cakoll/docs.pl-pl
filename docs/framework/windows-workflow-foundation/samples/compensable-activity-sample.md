---
title: Przykładowe działanie kompensacyjne
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 3bf1d120cd700830a98f53495f7e9989ffec73db
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46528960"
---
# <a name="compensable-activity-sample"></a>Przykładowe działanie kompensacyjne
W tym przykładzie przedstawiono sposób użycia `CompensableActivity` działania do definiowania zadań do wykonania dla danej akcji podczas wykonywania normalnych i pracy, które są niezbędne do wykonania celu kompensacji tę akcję, jeśli to konieczne w późniejszym czasie.  Pierwsza część przykład pokazuje, jak jednostki pracy kompensacyjne mogą być definiowane w Windows Workflow Foundation (WF) przy użyciu `CompensableActivity` działanie i jak są one wykonywane w pomyślnym uruchomieniu.  Druga część przykład pokazuje, jak te same jednostki pracy kompensacyjne automatycznie zajmie się rekompensaty po osiągnięciu nieoczekiwane zdarzenie, a wystąpienie przepływu pracy zostało anulowane.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Za pomocą programu Visual Studio 2010, otwórz CompensableActivity.sln.  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom aplikację, naciskając klawisz F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`