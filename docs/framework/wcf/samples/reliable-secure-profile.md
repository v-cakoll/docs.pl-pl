---
title: Niezawodny bezpieczny profil
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
ms.openlocfilehash: 9ddd0d78396bba6712650620e6b46c62f13337e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144217"
---
# <a name="reliable-secure-profile"></a>Niezawodny bezpieczny profil

W tym przykładzie pokazano, jak skomponować WCF i [Reliable Secure Profile (RSP)](http://www.ws-i.org/Profiles/ReliableSecureProfile-1.0.html). W tym przykładzie pokazano implementację kanału [Make Connection,](http://docs.oasis-open.org/ws-rx/wsmc/200702/wsmc-1.0-spec-cs-01.pdf) który może składać się razem z niezawodną wiadomością i opcjonalnie bezpiecznym kanałem do utworzenia niezawodnego bezpiecznego powiązania na podstawie specyfikacji RSP.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>Dyskusji  
 W tym przykładzie pokazano niezawodny scenariusz wymiany komunikatów dwukierunkowych. Usługa ma umowę dupleksu i klient implementuje umowy wywołania zwrotnego dupleksu. Klient inicjuje żądanie do usługi, dla których oczekuje się odpowiedzi na oddzielne połączenie. Komunikat żądania jest wysyłany niezawodnie. Klient nie chce otworzyć punktu końcowego nasłuchiwania na jego końcu. W związku z tym sonduje usługi z "Make Connection" żądań dla usługi, aby wysłać odpowiedź na tylnym kanale tego żądania "Make Connection". W tym przykładzie pokazano, jak mieć bezpieczne niezawodne komunikacji dupleksu za pośrednictwem protokołu HTTP bez klienta uwidaczniania punktu końcowego nasłuchiwania (i tworzenia wyjątku zapory).  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Otwórz rozwiązanie **ReliableSecureProfile.**  
  
2. Kliknij prawym przyciskiem myszy projekt **usługi** w **Eksploratorze rozwiązań**, wybierz polecenie **Debugowanie**, **Uruchom nowe wystąpienie** z menu kontekstowego. Spowoduje to uruchomienie hosta usługi.  
  
3. Kliknij prawym przyciskiem myszy projekt **Klienta** w **Eksploratorze rozwiązań**, wybierz polecenie **Debugowanie**, **Uruchom nowe wystąpienie** z menu kontekstowego. Spowoduje to uruchomienie klienta.  
  
4. Wpisz dowolny ciąg w wierszu w oknie konsoli klienta i kliknij przycisk ENTER. Spowoduje to wysłanie ciągu wejściowego do usługi, która oblicza skrót tego ciągu.  
  
5. Wyświetl wynik w oknach klienta, gdy usługa odwołuje operację umowy wywołania zwrotnego dupleksu, aby wyświetlić wynik w oknie konsoli klienta. Istnieje zamierzone opóźnienie w usłudze, aby symulować długotrwałą operację przetwarzania danych.  
  
6. Monitorowanie ruchu HTTP (za pomocą dowolnego narzędzia do monitorowania sieci online, takiego jak Monitor sieci, Skrzypek itd.) pokazuje, że między klientem a usługą ustanawia się sekwencję komunikacji określoną w profilu Reliable Secure Profile oraz sposób, w jaki klient jest ustanawiany sonduje usługę za pomocą żądań "Nawiązuj połączenie". Gdy usługa przygotowuje się do odesłania przetworzonej odpowiedzi, używa kanału wstecznego ostatniego żądania "Nawiązuj połączenie", aby odesłać wyniki.  
  
7. Naciśnij klawisz ENTER w oknie konsoli serwisowej, aby zamknąć usługę. Naciśnij klawisz ENTER w oknie konsoli klienta, aby zamknąć klienta.
