---
title: Publikowanie usług WCF
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: b62b2616233eb81e64945e997a2efe17973dedd2
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009081"
---
# <a name="wcf-service-publishing"></a>Publikowanie usług WCF

Publikowanie usług Windows Communication Foundation (WCF) pomaga w postępu z wcześniejsze środowisko projektowe dostarczane przez hosta usługi WCF i klienta testowego WCF do faktycznego wdrażania aplikacji w środowisku produkcyjnym do celów testowych. Przed przekazaniem do planu wdrażania końcowego umożliwia publikowanie usług Windows Communication Foundation (WCF) sprawdź, czy usługi WCF prawidłowo i jest gotowa do opublikowania. Możesz również wdrożyć biblioteki usługi WCF do testowania różnych miejsc docelowych.

## <a name="supported-services-and-target-locations"></a>Obsługiwane usługi i lokalizacji docelowej

Publikowanie usług WCF obsługuje Publikowanie usług WCF, utworzony na podstawie zestawu szablony Biblioteka usług WCF i ich elementów szablony, które obejmują następujące czynności:

-   Szablon Biblioteka usług WCF za pomocą szablonu elementu.

-   Biblioteka usługi syndykacji.

Te szablony usług można znaleźć, wybierając **pliku** > **nowy projekt** > [**języka Visual Basic** lub **Visual C#**] > **WCF**. W przypadku innych szablonów usług WCF w tej lokalizacji (w tym aplikacja usługi przepływu pracy WCF i aplikacja usługi WCF), można opublikować za pomocą [jednym kliknięciem publikowania dla aplikacji sieci web](https://msdn.microsoft.com/library/dd465337\(v=vs.110\).aspx).

Usługi mogą być publikowane w następujących lokalizacjach docelowych.

-   Lokalne usługi IIS.

-   File System.

-   Witryny FTP.

## <a name="using-wcf-service-publishing"></a>Przy użyciu usługi WCF Publikowanie usług

Wykonaj poniższe kroki, aby wdrożyć implementacji usługi:

1.  Otwórz program Visual Studio z podwyższonym poziomem uprawnień (kliknij prawym przyciskiem myszy plik wykonywalny, a następnie wybierz **Uruchom jako administrator** aby go otworzyć).  Jeśli używasz usług IIS 7.0 lub nowszym, upewnij się, że zainstalowano składnik "I usług IIS 6 konfiguracji zgodność z metabazą" przy użyciu "Windows Włącz lub wyłącz funkcje" w Panelu sterowania.

2.  Otwórz projekt usługi, wybierz opcję **kompilacji** > **Publikuj \<Nazwa projektu >** z menu głównego, lub kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**i kliknij przycisk **Publikuj**.

3.  **Publikuj** zostanie wyświetlone okno. Kliknij przycisk **...** . przycisk, aby określić lokalizację docelową, wdrożona usługa. Możesz wybrać, aby wdrożyć aplikację do lokalnych usług IIS, System plików lub witryny FTP. Jeśli wdrożenie aplikacji do lokalnych usług IIS, można wybrać witryny sieci Web i utworzyć aplikację sieci web, znajdujący się w nim, klikając **Tworzenie nowej aplikacji sieci Web** ikonę w prawym górnym rogu.

4.  Po kliknięciu **Publikuj** w głównym oknie programu Visual Studio wdroży aplikację określona lokalizacja docelowa i kopiuje pliki Web.config, .svc i zestaw do katalogu docelowego. . Nazwa .svc będzie "ProjectName.ServiceName.svc". Po pomyślnym opublikowaniu usługi, możesz znaleźć popularne łącze w oknie programu Visual Studio danych wyjściowych podobny do "Łączenie z HYPERLINK"http://localhost/WebApplicationFolderName" http://localhost/WebApplicationFolderName ...". Można nacisnąć klawisz CTRL i kliknij link, aby otworzyć stronę przeglądarki w programie Visual Studio, aby wyświetlić strukturę katalogów usługi.

     Jeśli nie możesz przejść do witryny, może być, ponieważ katalog przeglądarki nie jest włączone w usługach IIS. Postępuj zgodnie z poradami w sekcji "Rzeczy można spróbować", aby ją włączyć. Alternatywnie, możesz bezpośrednio wpisać"HYPERLINK"http://localhost/WebApplicationFolderName" http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc", aby wyświetlić stronę usługi.

Możesz użyć **Publikuj** Aby określić, jeśli chcesz skopiować zestaw, konfiguracji i pliku svc dla wszystkich usług zdefiniowane w projekcie do lokalizacji docelowej, a Nadpisz istniejące pliki w lokalizacji docelowej.

Jeśli zdecydujesz się wdrożyć aplikację do lokalnych usług IIS, mogą wystąpić błędy związane z konfiguracją usług IIS. Upewnij się, że usługi IIS zostały zainstalowane. Możesz wprowadzić `http://localhost` w pasku adresu przeglądarki i sprawdź czy usługi IIS domyślna strona wyświetla. W niektórych przypadkach problemów może być spowodowane przez niepoprawne rejestracji programu ASP.NET lub usługi WCF w usługach IIS. Możesz otworzyć wiersz polecenia programisty dla programu Visual Studio i uruchom polecenie `aspnet_regiis.exe -ir` Rozwiązywanie problemów dotyczących rejestracji programu ASP.NET lub uruchom polecenie `ServiceModelReg.exe –ia` do Rozwiązywanie problemów dotyczących rejestracji WCF.

## <a name="files-generated-for-publishing"></a>Pliki generowane publikowania
 Biblioteki usługi WCF można było hostowanych w sieci Web, za pomocą narzędzia są tworzone następujące pliki: pliki zestawu, plik Web.config i .svc pliku. Wszystkie pliki są kopiowane do lokalizacji docelowej. Następnie opublikowaniu usługi.

### <a name="assembly-files"></a>Pliki zestawu
 Po opublikowaniu usługi WCF za pomocą tego narzędzia, usługi jest automatycznie skompilowane na początku i pliki zestawu są generowane w projekcie usługi po kompilacji.

### <a name="svc-file"></a>. Plik SVC
 Operację publikowania generuje plik *.svc dla każdej usługi WCF, czy plik istnieje lub nie, aby zapewnić ważność wersji. Istnieją dwa różne rodzaje plików svc: jeden dla biblioteki usługi WCF i Biblioteka usługi Syndication i inną sekwencyjnego i Biblioteka usługi przepływu pracy maszyny stanu. Wygenerowany \*.svc plik jest kopiowany do folderu głównego w lokalizacji docelowej.

### <a name="webconfig-file"></a>Plik Web.config
 Każdorazowo, gdy projekt jest publikowany w lokalizacji docelowych określonych tworzony jest plik Web.config.

 Wygenerowany plik Web.config zawiera sekcje sieci Web, które są przydatne w przypadku hostingu w sieci Web i zawartość pliku App.config dla biblioteki usługi WCF z następującymi zmianami:

-   Adres podstawowy jest wyłączone.

-   Ustawienia w `<diagnostics>` elementu są wykluczane w celu zachowania ustawień śledzenia platformy docelowej.

## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>Publikowanie usług WCF za pomocą powiązania innego niż HTTP w usługach IIS
 Jeśli używasz IIS 7.0 lub później, możesz opublikować usług WCF za pomocą powiązania protokołu HTTP w usługach IIS. Należy wykonać niektóre wstępne konfiguracje. Aby uzyskać więcej informacji, zobacz Tematy w [Hosting w usłudze aktywacji procesów Windows](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).

## <a name="security"></a>Zabezpieczenia
 Publikowanie lokalnych usług IIS wymaga uprawnień administratora, ponieważ wymaga usług IIS, uruchomiony na koncie administratora. Jeśli użytkownik bez uprawnień administratora otwiera publikowania usługi WCF, usług IIS nie jest dostępna jako lokalizacji docelowej. Publikowanie w systemie plików lub witryny FTP działa bez uprawnień administratora.

## <a name="see-also"></a>Zobacz też

- [Szablony programu Visual Studio na potrzeby programu WCF](../../../docs/framework/wcf/wcf-vs-templates.md)
- [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [Testowy klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)