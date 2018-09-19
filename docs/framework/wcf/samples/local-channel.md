---
title: Lokalny kanał
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 731fcfde52a6b1277551f7d70f795c721fc99dd8
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46002713"
---
# <a name="local-channel"></a>Lokalny kanał
Lokalny kanał jest Windows Communication Foundation (WCF) kanał transportu, który jest używany do komunikacji w ramach tej samej domenie aplikacji. Jest to przydatne w scenariuszach, w którym klient i usługa są uruchomione w tej samej domenie aplikacji i należy unikać obciążenie typowe stosu kanału WCF (serializacji i deserializacji komunikatów).  
  
## <a name="demonstrates"></a>Demonstracje  
 Lokalny kanał  
  
## <a name="discussion"></a>Dyskusja  
 Przykład składa się z dwóch plików projektu:  
  
-   **LocalChannel**: programowe reprezentacja kanałów lokalnych w bieżącej domenie aplikacji. W tym projekcie wysyłania składnika umieszcza komunikat w kolejce w pamięci i odbieranie składnika cofnąć kolejki komunikatów do jej otrzymania.  
  
-   **ClientAndService**: ten projekt hostuje usługę w aplikacji konsoli, a następnie uruchamia klienta do wywołania z usług w ramach tej samej domenie aplikacji.  
  
 Projekt lokalny kanał pomija stosu kanału i zwiększyć szybkość procesu serializacji. Kanał transportowy lokalnego jest implementowany przy użyciu kolejki w celu transportu wywołań usługi od klienta do usługi i zwraca wartość z powrotem do klienta. Zamiast serializacji, parametrów i zwracanych wartości, przykładowy skrypt kopiuje obiektów.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Twórz i uruchamiaj rozwiązania LocalChannel.  
  
2.  Host usługi jest uruchomiona, a klient wywołuje usługę za pomocą lokalnego kanału. Aby wyświetlić wyniki wywołania usługi zostanie wyświetlone okno konsoli.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
