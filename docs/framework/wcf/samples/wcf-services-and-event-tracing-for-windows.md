---
title: Usługi i śledzenie zdarzeń programu WCF dla systemu Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: b8a1f30f20aa2c541a574a070b3644569d633ca2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183212"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Usługi i śledzenie zdarzeń programu WCF dla systemu Windows
W tym przykładzie pokazano, jak używać śledzenia analitycznego w programie Windows Communication Foundation (WCF) do emitowania zdarzeń w funkcji śledzenia zdarzeń dla systemu Windows (ETW). Ślady analityczne są zdarzenia emitowane w kluczowych punktach w stosie WCF, które umożliwiają rozwiązywanie problemów z usługami WCF w środowisku produkcyjnym.

 Śledzenia analitycznego w usługach WCF jest śledzenie, które można włączyć w środowisku produkcyjnym przy minimalnym wpływie na wydajność. Te ślady są emitowane jako zdarzenia do sesji ETW.

 Ten przykład zawiera podstawową usługę WCF, w której zdarzenia są emitowane z usługi do dziennika zdarzeń, które można wyświetlić za pomocą Podglądu zdarzeń. Istnieje również możliwość uruchomienia dedykowanej sesji ETW, która nasłuchuje zdarzeń z usługi WCF. Przykład zawiera skrypt do tworzenia dedykowanej sesji ETW, która przechowuje zdarzenia w pliku binarnym, który można odczytać za pomocą Podglądu zdarzeń.

#### <a name="to-use-this-sample"></a>Aby użyć tej próbki

1. Za pomocą programu Visual Studio 2012 otwórz plik rozwiązania EtwAnalyticTraceSample.sln.

2. Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.

3. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL+F5.

     W przeglądarce sieci Web kliknij pozycję **Calculator.svc**. Identyfikator URI dokumentu WSDL dla usługi powinien pojawić się w przeglądarce. Skopiuj ten identyfikator URI.

     Domyślnie usługa rozpoczyna nasłuchiwanie żądań na `http://localhost:1378/Calculator.svc`porcie 1378 .

4. Uruchom klienta testowego WCF (WcfTestClient.exe).

     Klient testowy WCF (WcfTestClient.exe) `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`znajduje się pod adresem .  Domyślnym programem dir instalacji programu `C:\Program Files\Microsoft Visual Studio 10.0`Visual Studio 2012 jest .

5. W kliencie testowym WCF dodaj usługę, wybierając **pozycję Plik**, a następnie **Dodaj usługę**.

     Dodaj adres punktu końcowego w polu wprowadzania. Wartość domyślna to `http://localhost:1378/Calculator.svc`.

6. Otwórz aplikację Podgląd zdarzeń.

     Przed wywołaniem usługi uruchom Podgląd zdarzeń i upewnij się, że dziennik zdarzeń nasłuchuje śledzenia zdarzeń emitowanych z usługi WCF.

7. W menu **Start** wybierz polecenie **Narzędzia administracyjne**, a następnie **pozycję Podgląd zdarzeń**.  Włącz dzienniki **analityczne** i **debugowania.**

8. W widoku drzewa w Podglądzie zdarzeń przejdź do **pozycji Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Application Server-Applications**. Kliknij prawym przyciskiem myszy **pozycję Serwer aplikacji ,** wybierz polecenie **Widok**, a następnie pozycję **Pokaż dzienniki analityczne i debugowania**.

     Upewnij się, że zaznaczono opcję **Pokaż dzienniki analityczne i debugowania.**

9. Włącz dziennik **analityczny.**

     W widoku drzewa w Podglądzie zdarzeń przejdź do **pozycji Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Application Server-Applications**. Kliknij prawym przyciskiem myszy pozycję **Analityczna** i wybierz polecenie **Włącz dziennik**.

#### <a name="to-test-the-service"></a>Aby przetestować usługę

1. Przełącz się z powrotem do `Divide` klienta testowego WCF i kliknij dwukrotnie i zachowaj wartości domyślne, które określają mianownik 0.

     Jeśli mianownik wynosi 0, usługa zgłasza błąd.

2. Obserwuj zdarzenia emitowane z usługi.

     Przełącz się z powrotem do Podglądu zdarzeń i przejdź do **Podglądu zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **Application Server-Applications**. Kliknij prawym przyciskiem myszy pozycję **Analityczna** i wybierz polecenie **Odśwież**.

     Zdarzenia śledzenia analitycznego WCF są wyświetlane w podglądzie zdarzeń. Należy zauważyć, że ponieważ błąd został zgłoszony przez usługę zdarzenie śledzenia błędów jest wyświetlane w podglądzie zdarzeń.

3. Powtórz kroki 1 i 2, ale z prawidłowymi wejściami. Wartość parametru `N2` może być dowolną liczbą inną niż 0.

     Odśwież kanał analityczny, aby wyświetlić zdarzenia WCF nie obejmują żadnych zdarzeń błędów.

 Przykład pokazuje zdarzenia śledzenia analitycznego emitowane z usługi WCF.

#### <a name="to-cleanup-optional"></a>Aby wyczyścić (opcjonalnie)

1. Otwórz Podgląd zdarzeń.

2. Przejdź do **przeglądarki zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **application-server-applications**. Kliknij prawym przyciskiem myszy pozycję **Analityczna** i wybierz polecenie **Wyłącz dziennik**.

3. Przejdź do **przeglądarki zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, a następnie **application-server-applications**. Kliknij prawym przyciskiem myszy pozycję **Analityczna** i wybierz polecenie **Wyczyść dziennik**.

4. Wybierz opcję **Wyczyść,** aby wyczyścić zdarzenia.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Zobacz też

- [Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
