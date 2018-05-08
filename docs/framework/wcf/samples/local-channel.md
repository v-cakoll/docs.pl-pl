---
title: Lokalny kanał
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 2473704c751ad0ea2d2a00bf7f3ea43d6e39498f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="local-channel"></a>Lokalny kanał
Lokalny kanał to kanał transportu Windows Communication Foundation (WCF) używanego do komunikacji w obrębie tej samej domenie aplikacji. Jest to przydatne w przypadku scenariuszy, w którym klient i usługa są uruchomione w tej samej domenie aplikacji należy unikać obciążenie typowe stosu kanału WCF (serializacji i deserializacji wiadomości).  
  
## <a name="demonstrates"></a>Demonstracje  
 Lokalny kanał  
  
## <a name="discussion"></a>Omówienie  
 Przykład obejmuje dwa pliki projektu:  
  
-   **LocalChannel**: programowe reprezentację lokalnego kanału w bieżącej domenie aplikacji. W tym projekcie wysyłania składnika umieszcza wiadomości w kolejce w pamięci, a odbierania składnika cofnąć kolejki wiadomości odebrane.  
  
-   **ClientAndService**: ten projekt obsługuje usługę w aplikacji konsoli, a następnie uruchomi klienta do wywołania przez usługę w tej samej domenie aplikacji.  
  
 Projekt lokalnego kanału pomija zarówno stosu kanału i przyspieszyć proces serializacji. Kanał transportu lokalnego jest zaimplementowany przy użyciu kolejki transportu wywołań usługi z klienta do usługi i zwraca wartość z powrotem do klienta. Zamiast serializacji, parametrów i zwracanych wartości, próbki kopiuje obiektów.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Tworzenie i uruchamianie rozwiązania LocalChannel.  
  
2.  Host usługi jest uruchomiona, a klient wywołuje usługę za pomocą lokalnego kanału. Aby wyświetlić wyniki wywołania usługi pojawi się okno konsoli.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
