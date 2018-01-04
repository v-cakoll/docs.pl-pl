---
title: "Lokalny kanał"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1298b4b96006837f0634040c5c615adfa3a1a11b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="local-channel"></a>Lokalny kanał
Lokalny kanał jest [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kanał transportu, który jest używany do komunikacji w obrębie tej samej domenie aplikacji. Jest to przydatne w przypadku scenariuszy, w którym klient i usługa są uruchomione w tej samej domenie aplikacji należy unikać obciążenie typowe stosu kanału WCF (serializacji i deserializacji wiadomości).  
  
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
