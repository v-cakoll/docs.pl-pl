---
title: Usługi i śledzenie zdarzeń programu WCF dla systemu Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: e1ee7154e2ad5b22ff0debcdd15d5809fc55df13
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044514"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Usługi i śledzenie zdarzeń programu WCF dla systemu Windows
Ten przykład pokazuje, jak używać śledzenia analitycznego w Windows Communication Foundation (WCF) do emisji zdarzeń w usłudze śledzenie zdarzeń systemu Windows (ETW). Ślady analityczne to zdarzenia emitowane w kluczowych punktach w stosie WCF, które umożliwiają rozwiązywanie problemów z usługami WCF w środowisku produkcyjnym.

 Śledzenie analityczne w usługach WCF to śledzenie, które można włączyć w środowisku produkcyjnym z minimalnym wpływem na wydajność. Te ślady są emitowane jako zdarzenia do sesji ETW.

 Ten przykład obejmuje podstawową usługę WCF, w której zdarzenia są emitowane z usługi do dziennika zdarzeń, które można wyświetlić przy użyciu Podgląd zdarzeń. Istnieje również możliwość uruchomienia dedykowanej sesji ETW, która nasłuchuje zdarzeń z usługi WCF. Przykład zawiera skrypt służący do tworzenia dedykowanej sesji ETW, która przechowuje zdarzenia w pliku binarnym, który można odczytać przy użyciu Podgląd zdarzeń.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2012 Otwórz plik rozwiązania EtwAnalyticTraceSample. sln.

2. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

3. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.

     W przeglądarce sieci Web kliknij pozycję **Kalkulator. svc**. Identyfikator URI dokumentu WSDL dla usługi powinien pojawić się w przeglądarce. Skopiuj ten identyfikator URI.

     Domyślnie usługa zaczyna nasłuchiwanie żądań na porcie 1378 `http://localhost:1378/Calculator.svc`.

4. Uruchom klienta testowego WCF (WcfTestClient. exe).

     Klient testowy WCF (WcfTestClient. exe) znajduje się w lokalizacji `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.  Domyślny katalog instalacji programu Visual Studio 2012 to `C:\Program Files\Microsoft Visual Studio 10.0`.

5. W ramach klienta testowego WCF Dodaj usługę, wybierając pozycję **plik**, a następnie **Dodaj usługę**.

     Dodaj adres punktu końcowego w polu wejściowym. Wartość domyślna to `http://localhost:1378/Calculator.svc`.

6. Otwórz aplikację Podgląd zdarzeń.

     Przed wywołaniem usługi Uruchom Podgląd zdarzeń i upewnij się, że dziennik zdarzeń nasłuchuje zdarzeń śledzenia emitowanych z usługi WCF.

7. Z menu **Start** wybierz pozycję **Narzędzia administracyjne**, a następnie **Podgląd zdarzeń**.  Włącz dzienniki **analityczne** i **debugowania** .

8. W widoku drzewa w Podgląd zdarzeń przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy pozycję **serwer aplikacji — aplikacje**, wybierz polecenie **Widok**, a następnie **Pokaż dzienniki analityczne i debugowania**.

     Upewnij się, że jest zaznaczona opcja **Pokaż dzienniki analityczne i debugowania** .

9. Włącz dziennik **analityczny** .

     W widoku drzewa w Podgląd zdarzeń przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz pozycję **Włącz dziennik**.

#### <a name="to-test-the-service"></a>Aby przetestować usługę

1. Wróć do klienta testowego WCF i kliknij dwukrotnie `Divide` i Zachowaj wartości domyślne, które określają mianownik równy 0.

     Jeśli mianownik ma wartość 0, usługa zgłosi błąd.

2. Obserwuj zdarzenia emitowane z usługi.

     Przełącz się z powrotem do Podgląd zdarzeń i przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz polecenie **Odśwież**.

     Zdarzenia śledzenia analitycznego WCF są wyświetlane w Podglądzie zdarzeń. Zwróć uwagę, że ponieważ błąd został zgłoszony przez usługę, w Podglądzie zdarzeń jest wyświetlane zdarzenie śledzenia błędów.

3. Powtórz kroki 1 i 2, ale z prawidłowymi danymi wejściowymi. Wartość `N2` parametru może być dowolną liczbą inną niż 0.

     Odśwież kanał analityczny, aby wyświetlić zdarzenia WCF nie uwzględniają żadnych zdarzeń błędów.

 Przykład demonstruje zdarzenia śledzenia analitycznego emitowane z usługi WCF.

#### <a name="to-cleanup-optional"></a>Aby oczyścić (opcjonalnie)

1. Otwórz Podgląd zdarzeń.

2. Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **aplikacje aplikacji**. Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz polecenie **Wyłącz dziennik**.

3. Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **aplikacje aplikacji**. Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz pozycję **Wyczyść dziennik**.

4. Wybierz opcję **Wyczyść** , aby wyczyścić zdarzenia.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady monitorowania oprogramowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
