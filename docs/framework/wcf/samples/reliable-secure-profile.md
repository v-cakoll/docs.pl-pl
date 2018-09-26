---
title: Niezawodny bezpieczny profil
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
author: BrucePerlerMS
ms.openlocfilehash: 8bb7c6f9835fc7c0926e918563f85a28281f8a89
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073570"
---
# <a name="reliable-secure-profile"></a>Niezawodny bezpieczny profil
W tym przykładzie przedstawiono sposób tworzenia usług WCF i [niezawodny bezpieczny profil](https://go.microsoft.com/fwlink/?LinkId=178140) (RSP). Niniejszy przykład pokazuje implementację [Utwórz połączenie](https://go.microsoft.com/fwlink/?LinkId=178141) kanału, który może być składana, wraz z niezawodną obsługę komunikatów i opcjonalnie bezpiecznego kanału do tworzenia niezawodnych bezpiecznych powiązań, na podstawie RSP specyfikacji.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>Dyskusja  
 Niniejszy przykład pokazuje scenariusz exchange niezawodnych komunikatów dwukierunkowe asynchronicznych. Usługa ma kontrakt dupleksowy, a klient implementuje kontraktu dwustronnego wywołania zwrotnego. Klient inicjuje żądanie do usługi, dla którego odpowiedź jest oczekiwana w ramach oddzielnego połączenia. Komunikat żądania są wysyłane w niezawodny sposób. Klient nie chce otworzyć punkcie końcowym nasłuchiwania na jej końcu. W związku z tym sonduje usługę za pomocą żądań tworzenia połączenia usługi do odesłania odpowiedź na kanale kopii tego żądania Utwórz połączenie. Niniejszy przykład pokazuje, jak bezpieczne, niezawodne paradygmacie komunikacji za pośrednictwem protokołu HTTP bez klient udostępnianie nasłuchiwania punktu końcowego (i utworzenie wyjątku zapory).  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Otwórz **ReliableSecureProfile** rozwiązania.  
  
2.  Kliknij prawym przyciskiem myszy **usługi** projektu w **Eksploratora rozwiązań**, wybierz opcję **debugowania**, **Uruchom nowe wystąpienie** z menu kontekstowego. Spowoduje to uruchomienie się hosta usługi.  
  
3.  Kliknij prawym przyciskiem myszy **klienta** projektu w **Eksploratora rozwiązań**, wybierz opcję **debugowania**, **Uruchom nowe wystąpienie** z menu kontekstowego. Spowoduje to uruchomienie się klient.  
  
4.  Wpisz dowolny ciąg, w wierszu polecenia w oknie konsoli klienta, a następnie naciśnij klawisz ENTER. Spowoduje to wysłanie ciągu wejściowego do usługi, która oblicza skrót ciągu.  
  
5.  Wyniki można wyświetlać w systemie windows klienta, gdy usługi ponownie wywołuje operacji kontraktu dwustronnego wywołania zwrotnego, aby wyświetlić wynik, w oknie konsoli klienta. Brak zamierzone opóźnienie w usłudze, aby zasymulować długotrwałej operacji przetwarzania danych.  
  
6.  Monitorowanie ruchu HTTP (przez żaden z narzędziami, takimi jak Monitor sieci, narzędzie Fiddler i tak dalej do monitorowania sieci online) pokazuje, że między klientem a usługą ustanowione sekwencji do komunikacji, zgodnie z niezawodny bezpieczny profil oraz w jaki sposób klienta sonduje usługę za pomocą żądań Utwórz połączenie. Gdy usługa pobiera gotowy do odesłania przetwarzania odpowiedzi, używa kanału zwrotnego z ostatniego żądania Utwórz połączenie do odesłania wyniki.  
  
7.  Naciśnij klawisz ENTER w oknie konsoli usługi, aby zamknąć tę usługę. Naciśnij klawisz ENTER w oknie konsoli klienta, aby zamknąć klienta.
