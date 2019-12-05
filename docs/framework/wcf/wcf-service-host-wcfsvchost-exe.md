---
title: Host usługi WCF (WcfSvcHost.exe)
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: c855fe7cc804fac14348990b7a6f5f84a0956b0c
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802411"
---
# <a name="wcf-service-host-wcfsvchostexe"></a>Host usługi WCF (WcfSvcHost.exe)

Windows Communication Foundation (WCF) Host usługi (WcfSvcHost. exe) umożliwia uruchomienie debugera programu Visual Studio (F5) w celu automatycznego hostowania i testowania wdrożonej usługi. Następnie można przetestować usługę za pomocą klienta testowego WCF (WcfTestClient. exe) lub własnego klienta, aby znaleźć i naprawić wszelkie potencjalne błędy.

## <a name="wcf-service-host"></a>Host usługi WCF

Host usługi WCF wylicza usługi w projekcie usługi WCF, ładuje tej konfiguracji projektu, a następnie tworzy wystąpienie hosta dla każdej usługi, które znajdzie. Narzędzie jest zintegrowane z programem Visual Studio za pomocą szablonu usługi WCF i jest wywoływane po rozpoczęciu debugowania projektu.

Korzystając z hosta usługi WCF, można hostować usługę WCF (w projekcie biblioteki usługi WCF) bez konieczności pisania dodatkowego kodu lub zatwierdzania do określonego hosta podczas opracowywania.

> [!NOTE]
> Host usługi WCF nie obsługuje częściowej relacji zaufania. Jeśli chcesz używać usługi WCF w częściowej relacji zaufania, nie należy używać szablonu projektu biblioteki usług WCF w programie Visual Studio do kompilowania usługi. Zamiast tego należy utworzyć nową witrynę sieci Web w programie Visual Studio, wybierając szablon witryny sieci Web usługi WCF, który może hostować usługę na serwerze WebSerwer, na którym jest obsługiwane częściowe zaufanie WCF.

## <a name="project-types-hosted-by-wcf-service-host"></a>Typy projektów hostowane przez hosta usługi WCF

Host usługi WCF może hostować następujące typy projektów biblioteki usług WCF: Biblioteka usług WCF, biblioteka usługi sekwencyjnego przepływu pracy, biblioteka usługi przepływu pracy automatu i Biblioteka usługi zespolonej. Host usługi WCF może również hostować te usługi, które mogą być dodawane do projektu biblioteki usług przy użyciu funkcji **Dodaj element** . Obejmuje to usługi WCF, usługi automatu Stanów WF, usług sekwencyjnej WF, usługi automatu języka XAML i usługi sekwencyjnej języka XAML WF.

Należy jednak pamiętać, że narzędzie nie pomoże Ci skonfigurować hosta. W przypadku tego zadania należy ręcznie edytować plik App. config. Narzędzie nie sprawdza także plików konfiguracji zdefiniowanych przez użytkownika.

> [!CAUTION]
> Nie należy używać hosta usługi WCF do hostowania usług w środowisku produkcyjnym, ponieważ nie zostały one zaprojektowane do tego celu.  Host usługi WCF nie obsługuje wymagań dotyczących niezawodności, zabezpieczeń i możliwości zarządzania w tym środowisku. Zamiast tego należy korzystać z usług IIS, ponieważ zapewnia ona doskonałe funkcje niezawodności i monitorowania, a także jest preferowanym rozwiązaniem dla usług hostingu. Po zakończeniu opracowywania usług należy przeprowadzić migrację usług z hosta usługi WCF do programu IIS.

## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Scenariusze korzystania z hosta usługi WCF w programie Visual Studio

W poniższej tabeli wymieniono wszystkie parametry w oknie dialogowym **argumenty wiersza polecenia** , które można znaleźć, klikając prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** w programie Visual Studio, wybierając **Właściwości**, a następnie wybierając kartę **debugowanie** i klikając polecenie **Uruchom projekt**. Parametry te są przydatne podczas konfigurowania hosta usługi WCF.

|Parametr|Znaczenie|
|---------------|-------------|
|`/client`|Opcjonalny parametr określający ścieżkę do pliku wykonywalnego, który ma zostać uruchomiony po hostowaniu usług. Spowoduje to uruchomienie klienta testowego WCF po hostie.|
|`/clientArg`|Określ ciąg jako argument, który jest przesyłany do niestandardowej aplikacji klienckiej.|
|`/?`|Wyświetla tekst pomocy.|

#### <a name="using-wcf-test-client"></a>Korzystanie z klienta testowego WCF

Po utworzeniu nowego projektu usługi WCF i naciśnięciu klawisza F5 w celu uruchomienia debugera, Host usługi WCF rozpocznie hostowanie wszystkich usług znalezionych w projekcie. Klient testowy WCF zostanie automatycznie otwarty i zostanie wyświetlona lista punktów końcowych usługi zdefiniowanych w pliku konfiguracji. W oknie głównym można testować parametry i wywoływać usługę.

Aby upewnić się, że klient testowy WCF jest używany, kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** w programie Visual Studio, wybierz polecenie **Właściwości**, a następnie wybierz kartę **debugowanie** . kliknij przycisk **Start Project** i upewnij się, że w oknie dialogowym **argumenty wiersza polecenia** pojawiają się następujące elementy.

`/client:WcfTestClient.exe`

#### <a name="using-a-custom-client"></a>Korzystanie z niestandardowego klienta

Aby użyć niestandardowego klienta, kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** w programie Visual Studio, wybierz polecenie **Właściwości**, a następnie wybierz kartę **debugowanie** . kliknij przycisk **Start Project** i edytuj parametr `/client` w oknie dialogowym **argumenty wiersza polecenia** , aby wskazać niestandardowego klienta, jak pokazano w poniższym przykładzie.

`/client:"path/CustomClient.exe"`

Po naciśnięciu klawisza F5 w celu ponownego uruchomienia usługi Host usługi WCF automatycznie uruchamia niestandardowego klienta po uruchomieniu debugera.

Można również użyć parametru `/clientArg:`, aby określić ciąg jako argument, który jest przesyłany do niestandardowej aplikacji klienckiej, jak pokazano w poniższym przykładzie.

`/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`

Na przykład jeśli używasz szablonu biblioteki usługi zespolonej, możesz użyć następujących argumentów wiersza polecenia,

`/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`

#### <a name="specifying-no-client"></a>Określanie braku klienta

Aby określić, że żaden klient nie będzie używany po uruchomieniu usługi WCF, kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** w programie Visual Studio, wybierz polecenie **Właściwości**, a następnie wybierz kartę **debugowanie** . kliknij przycisk **Start Project** i pozostaw puste okno dialogowe **argumenty wiersza polecenia** .

#### <a name="using-a-custom-host"></a>Korzystanie z hosta niestandardowego

Aby użyć niestandardowego hosta, kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** w programie Visual Studio, wybierz polecenie **Właściwości**, a następnie wybierz kartę **debugowanie** . kliknij przycisk **Uruchom program zewnętrzny** i wprowadź pełną ścieżkę do niestandardowego hosta. Można również użyć okna dialogowego **argumenty wiersza polecenia** , aby określić argumenty, które mają być przekazane do hosta.

## <a name="wcf-service-host-user-interface"></a>Interfejs użytkownika hosta usługi WCF

Po pierwszym wywołaniu hosta usługi WCF (naciskając klawisz F5 w programie Visual Studio) zostanie automatycznie otwarte okno **hosta usługi WCF** . Gdy host usługi WCF jest uruchomiony, ikona programu jest wyświetlana w obszarze powiadomień. Kliknij dwukrotnie ikonę, aby otworzyć okno **hosta usługi WCF** .

Gdy wystąpią błędy podczas hostingu usługi, zostanie otwarte okno dialogowe Host usługi WCF w celu wyświetlenia odpowiednich informacji.

Główne okno **hosta usługi WCF** zawiera dwa menu:

- **Plik**: zawiera polecenia **Close** i **Exit** . Po kliknięciu przycisku **Zamknij**okno dialogowe **host usługi WCF** zostanie zamknięte, ale usługi nadal będą hostowane. Po kliknięciu przycisku **Zakończ**, Host usługi WCF również zostanie zamknięty. Spowoduje to również zatrzymanie wszystkich usług hostowanych.

- **Pomoc**: zawiera polecenie **about** zawierające informacje o wersji. Zawiera również polecenie **pomocy** , które może otworzyć plik pomocy.

Główne okno **hosta usługi WCF** zawiera dwa obszary:

- Pierwszy obszar to **Usługa**. Zawiera listę zawierającą podstawowe informacje o wszystkich usługach. Informacje obejmują:

  - **Usługa**: zawiera listę wszystkich usług.

  - **Stan**: wyświetla stan usługi. Prawidłowe wartości to "uruchomiona", "zatrzymana" i "Error".

  - **Adres metadanych**: wyświetla adres metadanych usług.

- Drugi obszar zawiera **dodatkowe informacje**. Wyświetla szczegółowe wyjaśnienie stanu usługi w przypadku wybrania w obszarze **usługi** określonego wiersza usługi. Jeśli stan ma wartość błąd, na ekranie można wyświetlić pełny komunikat o błędzie.

## <a name="stopping-wcf-service-host"></a>Zatrzymywanie hosta usługi WCF

Hosta usługi WCF można zamknąć na następujące cztery sposoby:

- Zatrzymaj sesję debugowania w programie Visual Studio.

- Wybierz pozycję **Wyjdź** z menu **plik** w oknie **hosta usługi WCF** .

- Wybierz pozycję **Wyjdź** z menu kontekstowego ikony zasobnika hosta usługi WCF w obszarze powiadomień systemu.

- Wyjdź z klienta testowego WCF, jeśli jest używany.

## <a name="using-service-host-without-administrator-privilege"></a>Korzystanie z hosta usługi bez uprawnień administratora

Aby umożliwić użytkownikom bez uprawnień administratora opracowywanie usług WCF, podczas instalacji programu Visual Studio jest tworzona lista kontroli dostępu (Access Control) dla przestrzeni nazw "http://+:8731/Design_Time_Addresses". Lista ACL jest ustawiona na (UI), która obejmuje wszystkich użytkowników interakcyjnych zalogowanych na komputerze. Administratorzy mogą dodawać lub usuwać użytkowników z tej listy kontroli dostępu lub otwierać dodatkowe porty. Ta lista kontroli dostępu umożliwia użytkownikom korzystanie z funkcji Autohost usługi WCF (wcfSvcHost. exe) bez udzielania im uprawnień administratora.

Dostęp można modyfikować za pomocą narzędzia Netsh. exe w [!INCLUDE[wv](../../../includes/wv-md.md)] na koncie administratora z podwyższonym poziomem uprawnień. Poniżej przedstawiono przykład użycia narzędzia Netsh. exe.

```console
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>
```

Aby uzyskać więcej informacji na temat narzędzia Netsh. exe, zobacz "[jak używać narzędzia Netsh. exe i przełączników wiersza polecenia](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10))".

## <a name="see-also"></a>Zobacz także

- [Testowy klient WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
