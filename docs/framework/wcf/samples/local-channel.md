---
title: Lokalny kanał
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 87e140395ac2fb5702d8655cf970da8a60c991ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144510"
---
# <a name="local-channel"></a>Lokalny kanał
Kanał lokalny to kanał transportu Programu Windows Communication Foundation (WCF), który jest używany do komunikacji w tej samej domenie aplikacji. Jest to przydatne w scenariuszach, w których klient i usługa są uruchomione w tej samej domenie aplikacji i obciążenie typowego stosu kanału WCF (serializacji i deserializacji wiadomości) należy unikać.  
  
## <a name="demonstrates"></a>Demonstracje  
 Lokalny kanał  
  
## <a name="discussion"></a>Dyskusji  
 Próbka składa się z dwóch plików projektu:  
  
- **LocalChannel**: Programowa reprezentacja kanału lokalnego w bieżącej domenie aplikacji. W tym projekcie składnik wysyłania umieszcza wiadomość w kolejce w pamięci, a składnik odbierający usuwa kolejki wiadomości, aby ją odebrać.  
  
- **ClientAndService:** Ten projekt obsługuje usługę w aplikacji konsoli, a następnie uruchamia klienta, aby wywołać usługę z tej samej domeny aplikacji.  
  
 Projekt kanału lokalnego pomija zarówno stos kanału, jak i proces serializacji, aby zwiększyć szybkość. Kanał transportu lokalnego jest implementowany przy użyciu kolejki do transportu wywołań usługi od klienta do usługi i do powrotu wartości do klienta. Zamiast serializacji parametrów i zwracanych wartości, próbka kopiuje obiekty.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Tworzenie i uruchamianie rozwiązania LocalChannel.  
  
2. Host usługi jest uruchamiany, a klient wywołuje usługę przy użyciu kanału lokalnego. Pojawi się okno konsoli, aby wyświetlić wyniki wywołania usługi.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
