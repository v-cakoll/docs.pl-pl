---
title: Niezawodny bezpieczny profil
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 89a6d5c2e485699a55c77797c34eaca2c9848c40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-secure-profile"></a>Niezawodny bezpieczny profil
W tym przykładzie pokazano, jak utworzyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i [niezawodny bezpieczny profil](http://go.microsoft.com/fwlink/?LinkId=178140) (źródło). W tym przykładzie pokazano wykonania [Utwórz połączenie](http://go.microsoft.com/fwlink/?LinkId=178141) kanału, które mogą być składane, wraz z niezawodna obsługa komunikatów i opcjonalnie bezpiecznego kanału do tworzenia bezpiecznego niezawodna powiązania oparte na specyfikacji źródło.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>Omówienie  
 W przykładzie pokazano scenariusza exchange niezawodnej komunikatów dwukierunkowe asynchronicznych. Usługa ma kontraktu dwukierunkowego i klient implementuje kontraktu dwustronnego wywołania zwrotnego. Klient inicjuje żądanie do usługi, dla którego odpowiedzi jest oczekiwany w ramach oddzielnego połączenia. Niezawodnie jest wysyłany komunikat żądania. Klient nie chce się otworzyć punktu końcowego nasłuchiwania na jej końcu. W związku z tym sonduje usługę za pomocą żądań tworzenia połączenia usługi do odesłania odpowiedzi na kanału zwrotnego tego żądania tworzenia połączenia. W tym przykładzie pokazano, jak ma bezpiecznej komunikacji dupleksowej niezawodnej za pośrednictwem protokołu HTTP bez klienta udostępnianie punktu końcowego nasłuchiwania (i tworzenie wyjątek zapory).  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Otwórz **ReliableSecureProfile** rozwiązania.  
  
2.  Kliknij prawym przyciskiem myszy **usługi** projektu w **Eksploratora rozwiązań**, wybierz pozycję **debugowania**, **Start nowe wystąpienie** z menu kontekstowego. Spowoduje to uruchomienie skonfigurować hosta usługi.  
  
3.  Kliknij prawym przyciskiem myszy **klienta** projektu w **Eksploratora rozwiązań**, wybierz pozycję **debugowania**, **Start nowe wystąpienie** z menu kontekstowego. Spowoduje to uruchomienie klienta.  
  
4.  Wpisz dowolny ciąg w wierszu polecenia dla okna konsoli klienta, a następnie naciśnij klawisz ENTER. Ciąg wejściowy to wysyła do usługi, która oblicza skrót tego ciągu.  
  
5.  Wyświetlić wynik w systemie windows klienta, gdy usługa wywołuje operacja kontraktu dwustronnego wywołania zwrotnego, aby wyświetlić wyniki w oknie konsoli klienta. W usłudze, aby symulować długotrwałej operacji przetwarzania danych jest zamierzone opóźnienia.  
  
6.  Monitorowanie ruchu HTTP (przy użyciu jednej z sieci online monitorowania takich narzędzi jak Monitor sieci, Fiddler i tak dalej) pokazuje, że między klientem a usługą nawiązaniu sekwencji komunikacji ustanowione przez niezawodny bezpieczny profil i w jaki sposób klienta Przystawka sonduje usługę za pomocą żądań tworzenia połączenia. Gdy usługa pobiera gotowy do odesłania przetworzonych odpowiedzi, używa kanału zwrotnego z ostatniego żądania tworzenia połączenia do odesłania wyniki.  
  
7.  W oknie konsoli usługi, aby zamknąć tę usługę, naciśnij klawisz ENTER. Dla okna konsoli klienta, aby zamknąć klienta, naciśnij klawisz ENTER.
