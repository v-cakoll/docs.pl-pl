---
title: Publikowanie usług WCF
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: 9f76ab11e9697fc5af5c507d4dc9d944c433c918
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-service-publishing"></a>Publikowanie usług WCF
Publikowanie usługi Windows Communication Foundation (WCF) pomaga w postępu wczesne środowiska programowania udostępniane przez [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi i [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta testowego faktycznie wdrażanie aplikacji do środowiska produkcyjnego środowisko do celów testowych. Przed dokonaniem planu wdrożenia końcowego umożliwia publikowanie usługi Windows Communication Foundation (WCF) upewnij się, że Twoje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługa wykonuje poprawnie i jest gotowy do opublikowania. Można również wdrożyć Twojej [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi biblioteki do testowania różnych miejsc docelowych.  
  
## <a name="supported-services-and-target-locations"></a>Obsługiwane usługi i lokalizacji docelowej  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Usługa publikowania obsługuje publikowanie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług utworzone na podstawie zestawu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Szablony bibliotek usługi oraz ich odpowiednich szablony elementów, które obejmują następujące:  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Biblioteka usługi szablon na podstawie szablonu elementu.  
  
-   Biblioteka usługi zespolonego.  
  
 Te szablony usług można znaleźć, wybierając **pliku** -> **nowy projekt** -> **Visual Basic** lub **Visual C#**  ->  **WCF**. W przypadku innych szablonów usługi WCF w tej lokalizacji (w tym aplikacji usługi przepływu pracy WCF i aplikacji usługi WCF) można opublikować za pomocą [jednym kliknięciem publikowania aplikacji sieci web](https://msdn.microsoft.com/library/dd465337\(v=vs.110\).aspx).  
  
 Usługi mogą być publikowane w następujących lokalizacjach docelowych.  
  
-   Lokalne usługi IIS.  
  
-   File System.  
  
-   Witryny FTP.  
  
## <a name="using-wcf-service-publishing"></a>Przy użyciu programu WCF Publikowanie usług  
 Wykonaj poniższe kroki, aby wdrożyć implementacji usługi:  
  
1.  Otwórz program Visual Studio z podwyższonym poziomem uprawnień (kliknij prawym przyciskiem myszy plik wykonywalny i użyj "Uruchom jako Administrator", aby uruchomić go).  Jeśli używasz usług IIS 7.0 lub nowszy, upewnij się, czy zostały zainstalowane przy użyciu składnika "Usług IIS i IIS6 konfiguracji zgodność z metabazą" "" lub wyłącz funkcje systemu Windows "w Panelu sterowania.  
  
2.  Otwórz projekt usługi, wybierz **kompilacji**->**publikowania \<Nazwa projektu >** z menu głównego, lub kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**i kliknij przycisk **publikowania**.  
  
3.  **Publikowania** zostanie wyświetlone okno. Kliknij przycisk **...** . przycisk, aby określić lokalizację docelową, wdrożona usługa. Można wybrać do wdrożenia aplikacji w lokalnych usług IIS, System plików lub witryny FTP. Jeśli wdrażana aplikacja lokalne usługi IIS, można wybrać witryny sieci Web i utworzyć aplikację sieci web, w obszarze, klikając **Tworzenie nowej aplikacji sieci Web** ikonę w prawym górnym rogu.  
  
4.  Po kliknięciu **publikowania** w oknie głównym programu Visual Studio wdraża aplikację określona lokalizacja docelowa i kopiuje pliki Web.config, SVC i zestawu do katalogu docelowego. . Nazwa .svc będzie "ProjectName.ServiceName.svc". Po pomyślnym opublikowaniu usługi popularne łącze można znaleźć w oknie programu Visual Studio dane wyjściowe, które jest podobny do "Łączenie HYPERLINK"http://localhost/WebApplicationFolderName" http://localhost/WebApplicationFolderName ...". Można nacisnąć klawisze CTRL i kliknij łącze, aby otworzyć stronę przeglądarki w programie Visual Studio, aby wyświetlić strukturę katalogu usługi.  
  
     Jeśli nie możesz przeglądać do lokacji, może ponieważ przeglądarka katalogów jest wyłączona w usługach IIS. Wykonaj porady w sekcji "Czynności możesz spróbować", aby ją włączyć. Można również bezpośrednio można wpisać"HYPERLINK"http://localhost/WebApplicationFolderName" http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc", aby wyświetlić stronę usługi.  
  
 Można użyć **publikowania** Określ, czy chcesz skopiować zestaw, konfiguracji i pliku svc dla wszystkich usług zdefiniowanych w projekcie do lokalizacji docelowej i nadpisać istniejące pliki w miejscu docelowym.  
  
 Jeśli chcesz wdrożyć aplikację na lokalne usługi IIS, mogą wystąpić błędy związane z instalacji usług IIS. Upewnij się, że usługi IIS są poprawnie zainstalowane. Można wpisać "HYPERLINK"http://localhost" http://localhost" w Twojej przeglądarce i sprawdź, czy domyślna strona usług IIS jest wyświetlane, odkąd.  W niektórych przypadkach problemów może być spowodowane przez platformę ASP.NET lub [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] niewłaściwy rejestracji w usługach IIS. Można otworzyć wiersz polecenia programu Visual Studio i uruchom polecenie "aspnet_regiis.exe - ir", aby rozwiązać problemy dotyczące rejestracji programu ASP.NET lub uruchom polecenie "ServiceModelReg.exe — ia" poprawka WCF rejestracji problemów.  
  
## <a name="files-generated-for-publishing"></a>Pliki utworzone dla publikacji  
 Przed [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteki usługi może być hostowana w sieci Web, następujące pliki są generowane przez narzędzie: zestaw plików, pliku Web.config i pliku svc. Wszystkie pliki są kopiowane do lokalizacji docelowej. Następnie publikowany jest opis usługi.  
  
### <a name="assembly-files"></a>Pliki zestawu  
 Po opublikowaniu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi przy użyciu tego narzędzia, usługa jest automatycznie skompilowane na początku i pliki zestawu są generowane w projekcie usługi po budynku.  
  
### <a name="svc-file"></a>. Pliku SVC  
 Operacja publikowania generuje plik *.svc dla każdego [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi, czy plik istnieje lub nie, aby upewnić się, ważność wersji. Istnieją dwa typy plików svc: jeden dla [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteki usługi i zespolonego usługi biblioteki, a innym sekwencyjnego i Biblioteka usługi przepływu pracy komputera stanu. Wygenerowany \*pliku svc jest kopiowany do folderu głównego w lokalizacji docelowej.  
  
### <a name="webconfig-file"></a>Plik Web.config  
 Zawsze, gdy projekt jest opublikowana w lokalizacji docelowej określonej tworzenia pliku Web.config.  
  
 Wygenerowany plik Web.config zawiera sekcje sieci Web, które są przydatne w przypadku usługi hostingu sieci Web i zawartość pliku App.config dla [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteki usługi z następującymi zmianami:  
  
-   Adres podstawowy jest wyłączone.  
  
-   Ustawienia w `<diagnostics>` elementu są wykluczane w celu zachowania ustawień śledzenia platformy docelowej.  
  
## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>Publikowanie usług WCF z powiązaniami innych niż HTTP w usługach IIS  
 Jeśli używasz IIS 7.0 lub nowszej, możesz opublikować [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług z powiązaniami innych niż HTTP do usług IIS. Należy wykonać niektóre wstępnej konfiguracji. Aby uzyskać więcej informacji, zobacz Tematy w [Hosting w usłudze aktywacji procesów systemu Windows](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
## <a name="security"></a>Zabezpieczenia  
 Publikowanie do lokalnych usług IIS wymaga uprawnień administratora, ponieważ wymaga usług IIS uruchomiona na koncie administratora. Jeśli użytkownik bez uprawnień administratora otwiera [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] publikowania usługi, usługi IIS nie jest dostępny jako lokalizację docelową. Publikowanie do systemu plików lub witrynę FTP działa bez uprawnień administratora.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony programu Visual Studio na potrzeby programu WCF](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Testowy klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
