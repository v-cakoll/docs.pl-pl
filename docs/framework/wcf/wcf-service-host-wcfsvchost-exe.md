---
title: Host usługi WCF (WcfSvcHost.exe)
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: c000ad3ba53f103cb1a24a9a7fbc71049ba707c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-service-host-wcfsvchostexe"></a>Host usługi WCF (WcfSvcHost.exe)
Host usługi Windows Communication Foundation (WCF) (WcfSvcHost.exe) umożliwia uruchamianie debugera programu Visual Studio (F5), aby automatycznie udostępniać i testowanie usługi, które zostały zaimplementowane. Następnie można testować przy użyciu usługi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testowanie klienta (WcfTestClient.exe) lub własnego klienta, aby znaleźć i rozwiązać wszelkie potencjalne błędy.  
  
## <a name="wcf-service-host"></a>Host usługi WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host usługi wylicza usług w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu usługi ładuje konfigurację projektu i tworzy wystąpienie hosta dla każdej usługi, która znajdzie. Narzędzie jest zintegrowany z programu Visual Studio za pośrednictwem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] szablonu usługi i jest wywoływana po rozpoczęciu debugowania projektu.  
  
 Za pomocą [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi, może obsługiwać [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi (w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu biblioteki usługi) bez pisania kodu dodatkowe lub zobowiązuje się do określonego hosta podczas programowania.  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host usługi nie obsługuje zaufania częściowego. Jeśli chcesz użyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi w przypadku zaufania częściowego, nie używaj [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] szablon projektu biblioteki usługi w programie Visual Studio do tworzenia usługi. Zamiast tego utworzyć nowe witryny sieci Web w programie Visual Studio, wybierając [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] szablonu usługi witryny sieci Web, który może obsługiwać usługę w serwerze sieci Web, na którym [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] częściowego zaufania jest obsługiwana.  
  
## <a name="project-types-hosted-by-wcf-service-host"></a>Typy projektów obsługiwane przez Host usługi WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host usługi może zawierać następujące [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteki typów projektów usług: [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteki usługi, sekwencyjnych Biblioteka usługi przepływu pracy, Biblioteka usługi przepływu pracy maszyny stanu i biblioteki usługi zespolonego. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host usługi może również obsługiwać tych usług, które mogą zostać dodane do usługi biblioteki projektu za pomocą **Dodaj element** funkcji. Dotyczy to również [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi, usługa maszyny stanu WF, usługa Sekwencyjna WF, XAML WF stanu usługi i usługa Sekwencyjna WF XAML.  
  
 Należy zauważyć, jednak, że narzędzie nie będą pomocne podczas konfigurowania hosta. Dla tego zadania należy ręcznie zmienić pliku App.config. Narzędzie nie sprawdza również pliki konfiguracji użytkownika.  
  
> [!CAUTION]
>  Nie należy używać [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi hosta usług w środowisku produkcyjnym nie została zaprojektowana w tym celu.  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host usługi nie obsługuje niezawodności, zabezpieczeń i możliwości zarządzania wymaganiami takim środowisku. Zamiast tego należy użyć usług IIS, ponieważ zapewnia lepszą niezawodność i funkcji monitorowania i to preferowane rozwiązanie dla usług hostingu. Po zakończeniu tworzenia usługi należy zmigrować usługi z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi IIS.  
  
## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Scenariusze korzystania z hosta usługi WCF w programie Visual Studio  
 W poniższej tabeli wymieniono wszystkich parametrów w **argumenty wiersza polecenia** okno dialogowe, które można znaleźć, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** w programie Visual Studio, wybierając **Właściwości**, wybierając **debugowania** kartę i klikając **uruchomić projekt**. Te parametry są przydatne w konfigurowaniu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi.  
  
|Parametr|Znaczenie|  
|---------------|-------------|  
|`/client`|Opcjonalny parametr, który określa ścieżkę do pliku wykonywalnego do uruchomienia po hostowanych usług. Spowoduje to uruchomienie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta testowego po hosting.|  
|`/clientArg`|Określ ciąg jako argument, który jest przekazywany do aplikacji klienckiej niestandardowych.|  
|`/?`|Wyświetla tekst pomocy.|  
  
#### <a name="using-wcf-test-client"></a>Za pomocą klienta testowego WCF  
 Po utworzeniu nowego [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi projektu, a następnie naciśnij klawisz F5, aby uruchomić debugera, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi uruchamia hosting wszystkie usługi znalezione w projekcie. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Klient testowy automatycznie otwiera i wyświetla listę punktów końcowych usługi zdefiniowane w pliku konfiguracyjnym. W oknie głównym można przetestować parametry, a wywołania usługi.  
  
 Aby upewnić się, że [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Klient testowy jest używany, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** w programie Visual Studio, wybierz **właściwości**, a następnie wybierz pozycję **debugowania**kartę. Kliknij przycisk **uruchomić projekt** i upewnij się, że następujące pojawia się w **argumenty wiersza polecenia** okno dialogowe.  
  
 `/client:WcfTestClient.exe`  
  
#### <a name="using-a-custom-client"></a>Przy użyciu niestandardowego klienta  
 Aby użyć niestandardowego klienta, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** w programie Visual Studio, wybierz **właściwości**, a następnie wybierz pozycję **debugowania** kartę. Kliknij przycisk **uruchomić projekt** i edytować `/client` parametru w **argumenty wiersza polecenia** okno dialogowe, aby wskazywał niestandardowego klienta, jak wskazano w poniższym przykładzie.  
  
 `/client:"path/CustomClient.exe"`  
  
 Kiedy naciśniesz klawisz F5, aby uruchomić usługę ponownie, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host usługi jest automatycznie uruchamiana niestandardowego klienta podczas uruchamiania debugera.  
  
 Można również użyć `/clientArg:` parametru w celu określenia ciągu jako argument, który jest przekazywany do aplikacji klienckiej niestandardowych, jak wskazano w poniższym przykładzie.  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 Na przykład jeśli używasz szablonu biblioteki usługi zespolonego służy następujące argumenty wiersza polecenia  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### <a name="specifying-no-client"></a>Określanie nie klienta  
 Aby określić, że klient nie będzie używany po [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** w programie Visual Studio, wybierz **właściwości**, a następnie wybierz pozycję  **Debugowanie** kartę. Kliknij przycisk **uruchomić projekt** i pozostawić **argumenty wiersza polecenia** puste okno dialogowe.  
  
#### <a name="using-a-custom-host"></a>Przy użyciu hosta niestandardowego  
 Aby użyć hosta niestandardowego, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** w programie Visual Studio, wybierz **właściwości**, a następnie wybierz pozycję **debugowania** kartę. Kliknij przycisk **Start programu zewnętrznego** i wprowadź pełną ścieżkę do hosta niestandardowego. Można również użyć **argumenty wiersza polecenia** okno dialogowe, aby określić argumenty do przekazania do hosta.  
  
## <a name="wcf-service-host-user-interface"></a>Interfejs użytkownika Host usługi WCF  
 Jeśli początkowo wywołania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi (naciskając klawisz F5 w programie Visual Studio), **Host usługi WCF** automatycznie zostanie otwarte okno. Gdy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host usługi jest uruchomiona, ikona programu jest wyświetlana w obszarze powiadomień. Kliknij dwukrotnie ikonę, aby otworzyć **Host usługi WCF** okna  
  
 Jeśli wystąpią błędy podczas hostingu usług, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zostanie otwarte okno dialogowe hosta usługi, aby wyświetlić odpowiednie informacje.  
  
 **Host usługi WCF** głównego okna zawiera dwa menu:  
  
-   **Plik**: zawiera **Zamknij** i **zakończenia** poleceń. Po kliknięciu **Zamknij**, **Host usługi WCF** okno dialogowe zostanie zamknięte, ale nadal znajdować się usług. Po kliknięciu **zakończenia**, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] też zamknąć hosta usługi. Zatrzymuje to również wszystkich hostowanych usług.  
  
-   **Pomoc**: zawiera **o** polecenia, który zawiera informacje o wersji. Zawiera także **pomocy** polecenie, które można otworzyć pliku pomocy.  
  
 Głównym **Host usługi WCF** okna zawiera dwa obszary:  
  
-   Pierwszy obszar jest **usługi**. Zawiera listę, która zawiera podstawowe informacje o wszystkich usług. Następujące informacje:  
  
    -   **Usługa**: Wyświetla listę wszystkich usług.  
  
    -   **Stan**: Wyświetla stan usługi. Prawidłowe wartości to "Uruchomiono", "ZATRZYMANO" i "Error".  
  
    -   **Adres metadanych**: Wyświetla adres metadanych usługi.  
  
-   Drugi ma **dodatkowe informacje**. Wyświetla szczegółowe wyjaśnienie stan usługi zaznaczenie określonego wiersza usługi **usługi** obszaru. Jeśli stan jest błąd, można wyświetlić pełny komunikat o błędzie na ekranie.  
  
## <a name="stopping-wcf-service-host"></a>Zatrzymywanie Host usługi WCF  
 Można zamknąć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi z następujących czterech metod:  
  
-   Zatrzymaj sesję debugowania w programie Visual Studio.  
  
-   Wybierz **zakończenia** z **pliku** w menu **Host usługi WCF** okna.  
  
-   Wybierz **zakończenia** z menu kontekstowego [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi ikona na pasku zadań, w obszarze powiadomień systemu.  
  
-   Zakończ [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Klient testowy, jeśli jest on używany.  
  
## <a name="using-service-host-without-administrator-privilege"></a>Przy użyciu hosta usługi bez uprawnień administratora  
 Aby umożliwić użytkownikom bez uprawnień administratora do opracowywania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług, list kontroli dostępu (listy kontroli dostępu) jest tworzony dla przestrzeni nazw "http://+:8731/Design_Time_Addresses" podczas instalacji programu Visual Studio. Listy ACL ustawiono (UI), która obejmuje wszystkie interaktywne użytkownicy zalogowani do komputera. Administratorzy mogą dodawać lub usuwać użytkowników z tej listy ACL lub Otwórz dodatkowych portów. Tej listy ACL umożliwia użytkownikom używanie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatycznie hosta usługi (wcfSvcHost.exe) bez przyznania im uprawnień administratora.  
  
 Można zmodyfikować dostępu za pomocą narzędzia netsh.exe w [!INCLUDE[wv](../../../includes/wv-md.md)] przy użyciu konta administratora z podniesionymi uprawnieniami. Oto przykład użycia netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Aby uzyskać więcej informacji dotyczących netsh.exe, zobacz "[jak używać narzędzia Netsh.exe i przełączniki wiersza polecenia](http://go.microsoft.com/fwlink/?LinkId=97877)".  
  
## <a name="see-also"></a>Zobacz też  
 [Testowy klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
