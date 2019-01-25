---
title: Host usługi WCF (WcfSvcHost.exe)
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: 6a8ed677ceaf9b86b67ec2558eb4e31c23d4c57e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505643"
---
# <a name="wcf-service-host-wcfsvchostexe"></a>Host usługi WCF (WcfSvcHost.exe)
Host usług Windows Communication Foundation (WCF) (WcfSvcHost.exe) można uruchomić debugera programu Visual Studio (F5), aby automatycznie obsługiwać i przetestować usługę, w których zaimplementowano. Następnie można testować usługę za pomocą klienta Test WCF (WcfTestClient.exe) lub własnego klienta, aby znaleźć i naprawić wszelkie potencjalne błędy.  
  
## <a name="wcf-service-host"></a>Host usługi WCF  
 Host usługi WCF wylicza usługi w projekcie usługi WCF, ładuje tej konfiguracji projektu, a następnie tworzy wystąpienie hosta dla każdej usługi, które znajdzie. Narzędzie jest zintegrowana w programie Visual Studio przy użyciu szablonu usługi WCF i jest wywoływana po rozpoczęciu debugowania projektu.  
  
 Za pomocą Host usługi WCF, mogą hostowanie usługi WCF (w projekcie biblioteki usługi WCF) bez konieczności pisania dodatkowego kodu lub zatwierdzania do określonego hosta podczas programowania.  
  
> [!NOTE]
>  Host usługi WCF nie obsługuje częściowego zaufania. Jeśli chcesz użyć usługi WCF w trybie częściowego zaufania, nie używaj szablonu projektu biblioteki usługi WCF w programie Visual Studio do tworzenia usługi. Zamiast tego należy utworzyć nowe witryny sieci Web w programie Visual Studio, wybierając szablon witryny sieci Web WCF usługi, który może hostować usługi w serwerze sieci Web, jest obsługiwane WCF częściowego zaufania.  
  
## <a name="project-types-hosted-by-wcf-service-host"></a>Typy projektów obsługiwane przez Host usługi WCF  
 Host usługi WCF, mogą obsługiwać następujące typy projektu biblioteki usługi WCF: Biblioteki usługi WCF, Biblioteka usługi sekwencyjnego przepływu pracy, Biblioteka usługi przepływu pracy automatu stanów i Biblioteka usługi syndykacji. Host usługi WCF może również obsługiwać te usługi, które mogą być dodawane do usługi biblioteki projektu za pomocą **elementu Dodawanie** funkcji. W tym usługi WCF, WF stanu usługi, usługa Sekwencyjna WF, XAML WF stanu usługi i usługa Sekwencyjna WF XAML.  
  
 Możesz należy jednak zauważyć, że narzędzie pomoże nie można skonfigurować hosta. W tym celu należy ręcznie zmodyfikować plik App.config. Narzędzie nie sprawdza również pliki konfiguracyjne zdefiniowane przez użytkownika.  
  
> [!CAUTION]
>  Nie należy używać hosta usługi WCF do hostowania usług w środowisku produkcyjnym, ponieważ nie został zaprojektowany do tego celu.  Host usługi WCF nie obsługuje niezawodności, bezpieczeństwa i wymagania dotyczące możliwości zarządzania takim środowisku. Zamiast tego należy użyć usług IIS, ponieważ zapewnia doskonałą niezawodność oraz funkcji monitorowania i to preferowane rozwiązanie do hostowania usług. Po zakończeniu tworzenia usług, należy przeprowadzić migrację usług od hosta usługi WCF w programie IIS.  
  
## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Scenariusze użycia Host usługi WCF w programie Visual Studio  
 Poniższa tabela zawiera listę wszystkich parametrów w **argumenty wiersza polecenia** okno dialogowe, które można znaleźć, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** w programie Visual Studio, wybierając **Właściwości**, a następnie wybierając pozycję **debugowania** kartę i klikając **uruchomić projekt**. Parametry te są przydatne w konfigurowaniu Host usługi WCF.  
  
|Parametr|Znaczenie|  
|---------------|-------------|  
|`/client`|Opcjonalny parametr, który określa ścieżkę do pliku wykonywalnego do uruchomienia po znajdują się usługi. Spowoduje to uruchomienie klienta testowego WCF następujące hostingu.|  
|`/clientArg`|Określ ciąg jako argument, który jest przekazywany do aplikacji niestandardowych klienta.|  
|`/?`|Wyświetla tekst pomocy.|  
  
#### <a name="using-wcf-test-client"></a>Za pomocą klienta testowego WCF  
 Po utworzeniu nowego projektu usługi WCF i naciśnij klawisz F5, aby uruchomić debuger, rozpoczyna się Host usługi WCF obsługujący wszystkie usługi, które znajdzie się w projekcie. Testowy klient WCF automatycznie otwiera i wyświetla listę punktów końcowych usługi zdefiniowane w pliku konfiguracyjnym. W oknie głównym można przetestować parametrów i wywołania usługi.  
  
 Aby upewnić się, że klient testowy WCF jest używany, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** w programie Visual Studio, wybierz **właściwości**, a następnie wybierz **debugowania** kartę. Kliknij przycisk **uruchomić projekt** i upewnij się, że następujące pojawia się w **argumenty wiersza polecenia** okno dialogowe.  
  
 `/client:WcfTestClient.exe`  
  
#### <a name="using-a-custom-client"></a>Za pomocą niestandardowego klienta  
 Aby użyć niestandardowego klienta, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** w programie Visual Studio, wybierz **właściwości**, a następnie wybierz **debugowania** kartę. Kliknij przycisk **uruchomić projekt** i edytować `/client` parametru w **argumenty wiersza polecenia** okno dialogowe, aby wskazywał niestandardowych klienta, jak wskazano w poniższym przykładzie.  
  
 `/client:"path/CustomClient.exe"`  
  
 Po naciśnięciu klawisza F5, aby ponownie uruchomić usługę, Host usługi WCF automatycznie uruchamia niestandardowy klienta, podczas uruchamiania debugera.  
  
 Można również użyć `/clientArg:` parametru, aby określić ciąg jako argument, który jest przekazywany do aplikacji klienta, jak wskazano w poniższym przykładzie.  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 Na przykład jeśli używasz szablonu Biblioteka usługi Syndication służy następujące argumenty wiersza polecenia  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### <a name="specifying-no-client"></a>Określanie klienta nie  
 Aby określić, że żaden klient będzie używany po hostowanie usługi WCF, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** w programie Visual Studio, wybierz **właściwości**, a następnie wybierz **debugowania** kartę. Kliknij przycisk **uruchomić projekt** i pozostawić **argumenty wiersza polecenia** puste okno dialogowe.  
  
#### <a name="using-a-custom-host"></a>Przy użyciu hosta niestandardowego  
 Aby użyć niestandardowego hosta, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** w programie Visual Studio, wybierz **właściwości**, a następnie wybierz **debugowania** kartę. Kliknij przycisk **Uruchom zewnętrzny Program** i wprowadź pełną ścieżkę do niestandardowego hosta. Można również użyć **argumenty wiersza polecenia** okno dialogowe, aby określić argumenty do przekazania do hosta.  
  
## <a name="wcf-service-host-user-interface"></a>Interfejs użytkownika hosta usługi WCF  
 Po początkowym wywołaniu Host usługi WCF (naciskając klawisz F5 w programie Visual Studio), **Host usługi WCF** automatycznie zostanie otwarte okno. Gdy Host usługi WCF jest uruchomiona, ikonę programu pojawia się w obszarze powiadomień. Kliknij dwukrotnie ikonę aby otworzyć **Host usługi WCF** okna  
  
 Gdy występują błędy podczas hostingu usług, aby wyświetlić odpowiednie informacje zostanie otwarte okno dialogowe Host usługi WCF.  
  
 **Host usługi WCF** okno główne zawiera dwa menu:  
  
-   **Plik**: Zawiera **Zamknij** i **zakończenia** poleceń. Po kliknięciu **Zamknij**, **Host usługi WCF** okno dialogowe zostanie zamknięte, ale usług w dalszym ciągu być obsługiwane. Po kliknięciu **zakończenia**, Host usługi WCF również zostanie zamknięta. Spowoduje to również zatrzymanie wszystkich hostowanych usług.  
  
-   **Pomoc**: Zawiera **o** polecenia, który zawiera informacje o wersji. Zawiera ona także **pomocy** polecenie, które można otworzyć pliku pomocy.  
  
 Głównym **Host usługi WCF** okno zawiera dwa obszary:  
  
-   Pierwszy obszar jest **usługi**. Zawiera listę, która zawiera podstawowe informacje o wszystkich usług. Następujące informacje:  
  
    -   **Usługa**: Wyświetla listę wszystkich usług.  
  
    -   **Stan**: Wyświetla stan usługi. Prawidłowe wartości to "Uruchomiona", "Stopped" i "Error".  
  
    -   **Adres metadanych**: Wyświetla adres metadanych usługi.  
  
-   Drugi ma **dodatkowe informacje**. Wyświetla szczegółowy opis stan usługi, po wybraniu określonego wiersza usługi w **usługi** obszaru. Jeśli stan jest błąd, możesz wyświetlić pełną treść błędu na ekranie.  
  
## <a name="stopping-wcf-service-host"></a>Zatrzymywanie hosta usługi WCF  
 Host usługi WCF można zamknąć następujące cztery sposoby:  
  
-   Zatrzymaj sesję debugowania w programie Visual Studio.  
  
-   Wybierz **zakończenia** z **pliku** menu **Host usługi WCF** okna.  
  
-   Wybierz **zakończenia** z menu kontekstowego w zasobniku Host usługi WCF w obszarze powiadomień systemu.  
  
-   Jeśli jest używany, należy zamknąć klienta testowego WCF.  
  
## <a name="using-service-host-without-administrator-privilege"></a>Przy użyciu usługi hosta bez uprawnień administratora  
 Aby umożliwić użytkownikom bez uprawnień administratora do tworzenia usług WCF, (listę kontroli dostępu) jest tworzony dla przestrzeni nazw "http://+:8731/Design_Time_Addresses" podczas instalacji programu Visual Studio. Lista ACL jest równa (UI), która obejmuje wszystkie interaktywne użytkownicy zalogowani na maszynie. Administratorzy mogą dodawać lub usuwać użytkowników z tej listy ACL lub otwarcie dodatkowych portów. Ta lista ACL umożliwia użytkownikom używanie Host automatycznie usługi WCF (wcfSvcHost.exe) bez nadawania im uprawnień administratora.  
  
 Możesz zmodyfikować dostępu przy użyciu narzędzia netsh.exe w [!INCLUDE[wv](../../../includes/wv-md.md)] przy użyciu konta administratora z podniesionymi uprawnieniami. Oto przykład użycia netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Aby uzyskać więcej informacji na temat netsh.exe, zobacz "[sposób użycia narzędzia Netsh.exe i przełączniki wiersza polecenia](https://go.microsoft.com/fwlink/?LinkId=97877)".  
  
## <a name="see-also"></a>Zobacz także
- [Testowy klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
