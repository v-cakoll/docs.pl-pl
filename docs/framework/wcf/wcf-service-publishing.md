---
title: Publikowanie usług WCF
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: 90d2a841fa5ce14b1ad5295b3bb6493df0350339
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321238"
---
# <a name="wcf-service-publishing"></a>Publikowanie usług WCF

Publikowanie usług Windows Communication Foundation (WCF) ułatwia wykonywanie operacji na wczesnym środowisku programistycznym udostępnianym przez hosta usługi WCF i klienta testowego WCF w celu rzeczywistego wdrożenia aplikacji w środowisku produkcyjnym na potrzeby testowania. Przed zatwierdzeniem do ostatecznego planu wdrożenia możesz użyć funkcji publikowania usług Windows Communication Foundation (WCF), aby sprawdzić, czy usługa WCF działa prawidłowo i czy jest gotowa do opublikowania. Możesz również wybrać wdrożenie bibliotek usługi WCF w różnych lokalizacjach docelowych na potrzeby testowania.

## <a name="supported-services-and-target-locations"></a>Obsługiwane usługi i lokalizacje docelowe

Publikowanie usługi WCF obsługuje Publikowanie usług WCF utworzonych na podstawie zestawu szablonów bibliotek usługi WCF oraz odpowiadających im szablonów elementów, takich jak:

- Szablon biblioteki usługi WCF z szablonem elementu.

- Biblioteka usługi zespolonej.

Te szablony usług można znaleźć, wybierając kolejno pozycje **plik** > **Nowy projekt** > [**Visual Basic** lub **Visual C#** ] > **WCF**. W przypadku innych szablonów usługi WCF w tej lokalizacji (w tym aplikacji usługi przepływu pracy WCF i aplikacji usługi WCF) można opublikować publikację przy użyciu [jednego kliknięcia dla aplikacji sieci Web](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110)).

Usługę można opublikować w następujących lokalizacjach docelowych.

- Lokalne usługi IIS.

- System plików.

- Witryna FTP.

## <a name="using-wcf-service-publishing"></a>Korzystanie z publikowania usługi WCF

Wykonaj następujące kroki, aby wdrożyć implementację usługi:

1. Otwórz program Visual Studio z podniesionymi uprawnieniami (kliknij prawym przyciskiem myszy plik wykonywalny i wybierz polecenie **Uruchom jako administrator** , aby go otworzyć).  W przypadku korzystania z usług IIS 7,0 lub nowszych upewnij się, że zainstalowano składnik "usług IIS 6 metabazy usług IIS i zgodność konfiguracji" przy użyciu opcji "Włącz lub wyłącz funkcje systemu Windows" w panelu sterowania.

2. Otwórz projekt usługi, wybierz opcję **kompiluj** > **Publish \<Project Name >** z menu głównego lub kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i kliknij pozycję **Publikuj**.

3. Zostanie wyświetlone okno **Publikowanie** . Kliknij przycisk **...** . , aby określić lokalizację docelową, w której ma zostać wdrożona usługa. Możesz wybrać opcję wdrożenia aplikacji w lokalnych usługach IIS, systemie plików lub witrynie FTP. Jeśli aplikacja jest wdrażana w lokalnych usługach IIS, możesz wybrać witrynę internetową i utworzyć w niej aplikację sieci Web, klikając ikonę **Utwórz nową aplikację sieci Web** w prawym górnym rogu.

4. Po kliknięciu przycisku **Publikuj** w oknie głównym program Visual Studio wdroży aplikację w określonej lokalizacji docelowej i skopiuje pliki Web. config, svc i Assembly do katalogu docelowego. . Nazwa. svc to "ProjectName. ServiceName. svc". Po pomyślnym opublikowaniu usługi można znaleźć Hotlink w oknie danych wyjściowych programu Visual Studio, które wygląda podobnie do "łączenia z `http://localhost/WebApplicationFolderName...`". Naciśnij klawisz CTRL i kliknij link, aby otworzyć stronę przeglądarki w programie Visual Studio, aby wyświetlić strukturę katalogu usług.

     Jeśli nie możesz przejść do witryny, może to być spowodowane tym, że przeglądarka katalogów nie jest włączona w usługach IIS. Postępuj zgodnie ze wskazówkami w sekcji "czynności, które możesz wypróbować", aby je włączyć. Alternatywnie możesz bezpośrednio wpisać `http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc`, aby wyświetlić stronę usługi.

Możesz użyć funkcji **Publikuj** , aby określić, czy chcesz skopiować plik zestawu, konfiguracji i pliku SVC dla wszystkich usług zdefiniowanych w projekcie do lokalizacji docelowej, i zastąpić istniejące pliki w miejscu docelowym.

W przypadku wybrania opcji wdrożenia aplikacji w lokalnych usługach IIS mogą wystąpić błędy związane z konfiguracją usług IIS. Upewnij się, że usługi IIS są prawidłowo zainstalowane. Możesz wprowadzić `http://localhost` na pasku adresu przeglądarki i sprawdzić, czy zostanie wyświetlona domyślna strona usług IIS. W niektórych przypadkach przyczyną problemów może być również nieprawidłowa Rejestracja ASP.NET lub WCF w usługach IIS. Możesz otworzyć wiersz polecenia dla deweloperów dla programu Visual Studio i uruchomić polecenie `aspnet_regiis.exe -ir`, aby rozwiązać problemy z rejestracją ASP.NET lub uruchomić polecenie `ServiceModelReg.exe –ia`, aby rozwiązać problemy z rejestracją programu WCF.

## <a name="files-generated-for-publishing"></a>Pliki wygenerowane do opublikowania
 Aby biblioteka usług WCF mogła być hostowana w sieci Web, następujące pliki są generowane przez narzędzie: pliki zestawu, plik Web. config i plik SVC. Wszystkie pliki zostaną skopiowane do lokalizacji docelowej. Następnie usługa jest publikowana.

### <a name="assembly-files"></a>Pliki zestawu
 Po opublikowaniu usługi WCF przy użyciu tego narzędzia usługa zostanie automatycznie skompilowana, a pliki zestawu są generowane w projekcie usługi po skompilowaniu.

### <a name="svc-file"></a>. Plik SVC
 Operacja publikowania generuje plik *. svc dla każdej usługi WCF, niezależnie od tego, czy plik istnieje, czy nie, aby upewnić się, że wersja jest poprawna. Istnieją dwa różne rodzaje plików SVC: jeden dla biblioteki usług WCF i Biblioteka usługi zespolonej, a drugi dla sekwencyjnej i stanowej biblioteki usługi przepływu pracy. Wygenerowany plik @no__t -0. svc zostanie skopiowany do folderu głównego w lokalizacji docelowej.

### <a name="webconfig-file"></a>Plik Web. config
 Za każdym razem, gdy projekt usługi jest publikowany w określonej lokalizacji docelowej, tworzony jest plik Web. config.

 Wygenerowany plik Web. config zawiera sekcje sieci Web, które są przydatne w przypadku hostingu w sieci Web, oraz zawartość pliku App. config dla biblioteki usługi WCF z następującymi zmianami:

- Adres podstawowy jest wykluczony.

- Ustawienia w elemencie `<diagnostics>` są wykluczone, aby zachować ustawienia śledzenia platformy docelowej.

## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>Publikowanie usług WCF z powiązaniami innymi niż HTTP z usługami IIS
 W przypadku korzystania z usług IIS 7.0 lub nowszych można opublikować usługi WCF z powiązaniami innymi niż HTTP z usługami IIS. Należy wykonać pewne wstępne konfiguracje. Aby uzyskać więcej informacji, zobacz tematy dotyczące [hostingu w usłudze aktywacji procesów systemu Windows](./feature-details/hosting-in-windows-process-activation-service.md).

## <a name="security"></a>Zabezpieczenia
 Publikowanie w lokalnych usługach IIS wymaga uprawnień administratora, ponieważ usługi IIS wymagają uruchomienia na koncie administratora. Jeśli użytkownik bez uprawnień administratora otworzy opcję publikowanie usługi WCF, usługi IIS nie są dostępne jako lokalizacja docelowa. Publikowanie w systemie plików lub witryna FTP działa bez uprawnień administratora.

## <a name="see-also"></a>Zobacz także

- [Szablony programu Visual Studio na potrzeby programu WCF](wcf-vs-templates.md)
- [Host usługi WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Testowy klient WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
