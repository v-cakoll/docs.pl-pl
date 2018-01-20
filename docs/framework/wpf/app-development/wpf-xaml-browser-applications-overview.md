---
title: "Przegląd Aplikacje przeglądarek WPF XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XBAP [WPF], XAML browser application
- WPF XAML browser applications (XBAP)
- XAML browser applications (XBAP)
- browser-hosted applications [WPF]
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
caps.latest.revision: "47"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f4f410f0f6c209dbc43642a15ae85a788390f4a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="wpf-xaml-browser-applications-overview"></a>Przegląd Aplikacje przeglądarek WPF XAML
<a name="introduction"></a>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]łączy funkcje aplikacji sieci Web i aplikacje wzbogaconego klienta. Takich jak aplikacje sieci Web XBAP można wdrożyć na serwerze sieci Web i uruchomiona z programu Internet Explorer lub przeglądarki Firefox. Jak aplikacje wzbogaconego klienta XBAP mogą wykorzystać możliwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tworzenie aplikacji XBAP również jest podobny do rozwoju wzbogaconego klienta. W tym temacie przedstawia proste, wysokiego poziomu wprowadzenie do rozwoju XBAP oraz gdy programowanie XBAP różni się od standardowego programowanie wzbogaconego klienta.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Tworzenie nowej aplikacji przeglądarki XAML (XBAP)](#creating_a_new_xaml_browser_application_xbap)  
  
-   [Wdrażanie XBAP](#deploying_a_xbap)  
  
-   [Podczas komunikacji z hostem strony sieci Web](#communicating_with_the_host_web_page)  
  
-   [Zagadnienia dotyczące zabezpieczeń XBAP](#xbap_security_considerations)  
  
-   [Zagadnienia związane z wydajnością XBAP początkowy czas](#xbap_start_time_performance_considerations)  
  
<a name="creating_a_new_xaml_browser_application_xbap"></a>   
## <a name="creating-a-new-xaml-browser-application-xbap"></a>Tworzenie nowej aplikacji przeglądarki XAML (XBAP)  
 Najprostszym sposobem, aby utworzyć nowy projekt XBAP jest z [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)]. Podczas tworzenia nowego projektu, zaznacz **aplikacji przeglądarki WPF** z listy szablonów. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji przeglądarki WPF](http://msdn.microsoft.com/library/72ef4d90-e163-42a1-8df0-ea7ccfd1901f).  
  
 Po uruchomieniu projektów XBAP zostanie otwarty w oknie przeglądarki zamiast autonomicznej okna. Podczas debugowania XBAP z [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], aplikacja jest uruchamiana z uprawnieniami strefy Internet i w związku z tym będzie zgłaszać wyjątki zabezpieczeń, w przypadku przekroczenia te uprawnienia. Aby uzyskać więcej informacji, zobacz [zabezpieczeń](../../../../docs/framework/wpf/security-wpf.md) i [WPF częściowego zaufania zabezpieczeń](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
> [!NOTE]
>  Jeśli nie opracowujesz z [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] lub chcesz dowiedzieć się więcej o plikach projektu, zobacz [kompilowania aplikacji WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
<a name="deploying_a_xbap"></a>   
## <a name="deploying-an-xbap"></a>Wdrażanie XBAP  
 Podczas konstruowania XBAP danych wyjściowych zawiera trzy następujące pliki:  
  
|Plik|Opis|  
|----------|-----------------|  
|Plik wykonywalny (.exe)|Zawiera skompilowany kod, a ma rozszerzenia .exe.|  
|Manifest aplikacji (manifest)|Zawiera metadane skojarzone z aplikacją i ma rozszerzenie ".manifest".|  
|Manifest rozmieszczenia (.xbap)|Ten plik zawiera informacje o który [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] używa do wdrażania aplikacji i ma rozszerzenie .xbap.|  
  
 Na serwerze sieci Web wdrażanie na przykład XBAP [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] lub nowszy. Nie trzeba instalować [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] w sieci Web serwera, ale jest zarejestrowanie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] typów i nazwę pliku rozszerzenia. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług IIS w wersji 5.0 i usług IIS 6.0, aby wdrożyć aplikacje WPF](../../../../docs/framework/wpf/app-development/how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).  
  
 Do Twojej XBAP przygotowania do wdrożenia, skopiuj .exe i manifestów skojarzone z serwerem sieci Web. Utwórz stronę HTML, który zawiera hiperłącza do Otwórz plik manifestu wdrożenia, który jest plik z rozszerzeniem .xbap. Gdy użytkownik kliknie łącze do pliku .xbap [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] automatycznie obsługuje sposobu pobierania i uruchamiania aplikacji. Poniższy przykład kodu pokazuje stronę HTML, który zawiera hiperłącze wskazujące XBAP.  
  
```html
<html>   
    <head></head>  
    <body>   
        <a href="XbapEx.xbap">Click this link to launch the application</a>  
    </body>   
</html>  
```  
  
 Może również obsługiwać XBAP w ramce strony sieci Web. Utwórz stronę sieci Web z jedną lub więcej ramek. Ustaw właściwości source ramki do pliku manifestu wdrożenia. Jeśli chcesz używać do komunikacji między hostingu strony sieci Web i XBAP wbudowany mechanizm musi być hostem aplikacji w ramce. Poniższy przykładowy kod przedstawia stronę HTML z dwóch ramek źródła dla drugiej ramki ma ustawioną wartość XBAP.  
  
```html
<html>   
    <head>
        <title>A page with frames</title>
    </head>  
    <frameset cols="50%,50%">   
        <frame src="introduction.htm">   
        <frame src="XbapEx.xbap">   
    </frameset>   
</html>  
```  
  
### <a name="clearing-cached-xbaps"></a>Czyszczenie pamięci podręcznej XBAP  
 W niektórych sytuacjach po ponowne kompilowanie i uruchamianie programu XBAP może się okazać, wcześniejszej wersji XBAP do otwarcia. Na przykład ten problem może wystąpić, gdy numer wersji zestawu XBAP jest statyczna i XBAP jest uruchamiany z poziomu wiersza polecenia. W takim przypadku ponieważ numer wersji między buforowanej wersji (wersja, który został wcześniej uruchomiony) i nowa wersja jest taka sama, nowa wersja XBAP nie jest pobierana. Zamiast tego została załadowana wersja buforowana.  
  
 W takich sytuacjach należy usunąć wersja buforowana przy użyciu **obraz** polecenia (zainstalowane z programem Visual Studio lub [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)]) w wierszu polecenia. Następujące polecenie spowoduje wyczyszczenie pamięci podręcznej aplikacji.  
  
 ```console
 Mage.exe -cc
 ```
  
 To polecenie gwarantuje, że jest uruchomiona najnowsza wersja programu XBAP. Podczas debugowania aplikacji w [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], najnowsza wersja programu XBAP powinna być uruchamiana. Ogólnie rzecz biorąc należy zaktualizować numer wersji wdrożenia dla każdej kompilacji. Aby uzyskać więcej informacji na temat obraz, zobacz [Mage.exe (Generowanie manifestu i edytowania narzędzie)](../../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
<a name="communicating_with_the_host_web_page"></a>   
## <a name="communicating-with-the-host-web-page"></a>Podczas komunikacji z hostem strony sieci Web  
 Kiedy aplikacja znajduje się w ramce HTML, może komunikować się z strony sieci Web, który zawiera XBAP. Aby to zrobić, pobierania <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> właściwość <xref:System.Windows.Interop.BrowserInteropHelper>. Ta właściwość zwraca obiekt skryptu, który reprezentuje okna HTML. Następnie dostępnych właściwości, metod i zdarzeń na [obiekt window](http://go.microsoft.com/fwlink/?LinkId=160274) za pomocą składni z kropkami regularne. Można także przejść metody skryptu i zmiennych globalnych. Poniższy przykład pokazuje, jak można pobrać obiektu skryptu i zamknij przeglądarkę.  
  
 [!code-csharp[XbapBrowserInterop#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]  
  
### <a name="debugging-xbaps-that-use-hostscript"></a>Debugowanie aplikacji, które używają HostScript XBAP  
 Jeśli Twoje XBAP używa <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> obiektu do komunikowania się z okna HTML istnieją dwa ustawienia, które należy określić by przeprowadzić debugowanie aplikacji w [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]. Aplikacja musi mieć dostęp do witryny pochodzenia i należy uruchomić aplikację w strony HTML, który zawiera XBAP. W poniższych krokach opisano sposób sprawdzania te dwa ustawienia:  
  
1.  W programie Visual Studio Otwórz właściwości projektu.  
  
2.  Na **zabezpieczeń** , kliknij pozycję **zaawansowane**.  
  
     Zostanie wyświetlone okno dialogowe Zaawansowane ustawienia zabezpieczeń.  
  
3.  Upewnij się, że **udzielić dostępu aplikacji do witryny pochodzenia** Sprawdź pole wyboru zostało zaznaczone, a następnie kliknij przycisk **OK**.  
  
4.  Na **debugowania** wybierz opcję **Start przeglądarki z adresem URL** opcję i określić adres URL strony HTML, który zawiera XBAP.  
  
5.  W programie Internet Explorer, kliknij przycisk **narzędzia** przycisk, a następnie wybierz **Opcje internetowe**.  
  
     Zostanie wyświetlone okno dialogowe Opcje internetowe.  
  
6.  Kliknij przycisk **zaawansowane** kartę.  
  
7.  W **ustawienia** w obszarze **zabezpieczeń**, sprawdź **Pozwól na uruchamianie plików na tym komputerze w zawartości active** pole wyboru.  
  
8.  Kliknij przycisk **OK**.  
  
     Zmiany zostaną wprowadzone po ponownym uruchomieniu programu Internet Explorer.  
  
> [!CAUTION]
>  Włączanie zawartość w programie Internet Explorer mogą zagrożenie komputera. Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń i prywatności w programie Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=179286). Jeśli nie chcesz zmienić ustawienia zabezpieczeń programu Internet Explorer, można uruchomić strony HTML od serwera i dołączyć [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] debugera do procesu.  
  
<a name="xbap_security_considerations"></a>   
## <a name="xbap-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń XBAP  
 XBAP zwykle wykonywany w piaskownicy zabezpieczenia częściowego zaufania, który jest ograniczony do strefy zestaw uprawnień internetowych. W rezultacie implementacji musi obsługiwać podzbiór [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy, które są obsługiwane w strefie Internet lub należy podnieść uprawnienia aplikacji. Aby uzyskać więcej informacji, zobacz [zabezpieczeń](../../../../docs/framework/wpf/security-wpf.md).  
  
 Jeśli używasz <xref:System.Windows.Controls.WebBrowser> kontroli w aplikacji WPF wewnętrznie tworzy macierzystego formantu WebBrowser ActiveX. Gdy aplikacja jest XBAP częściowego zaufania, w programie Internet Explorer, formantu ActiveX uruchamia się w dedykowanym wątku procesu programu Internet Explorer. W związku z tym obowiązują następujące ograniczenia:  
  
-   <xref:System.Windows.Controls.WebBrowser> Sterowania powinien być zachowanie jest podobne do przeglądarki hosta, w tym ograniczenia zabezpieczeń. Niektóre z tych ograniczeń zabezpieczeń mogą być kontrolowane przez ustawienia zabezpieczeń programu Internet Explorer. Aby uzyskać więcej informacji, zobacz [zabezpieczeń](../../../../docs/framework/wpf/security-wpf.md).  
  
-   Gdy XBAP jest załadowany międzydomenowego na stronie HTML, jest zgłaszany wyjątek.  
  
-   Dane wejściowe są w oddzielnym wątku z WPF <xref:System.Windows.Controls.WebBrowser>, dlatego nie może zostać przechwycone klawiatury i nie jest udostępniony stan edytora IME.  
  
-   Kolejność nawigacji lub termin mogą się różnić z powodu formantu ActiveX uruchomiona w innym wątku. Na przykład nawigowania do strony jest nie zawsze anulowany przez uruchomienie kolejnego żądania nawigacji.  
  
-   Niestandardowe kontrolki ActiveX może mieć problemy z komunikacją, ponieważ aplikacji WPF działa w oddzielnym wątku.  
  
-   <xref:System.Windows.Interop.HwndHost.MessageHook>nie pobrać zgłoszone, ponieważ <xref:System.Windows.Interop.HwndHost> nie podklasy okna uruchomiona w innym wątku lub procesu.  
  
### <a name="creating-a-full-trust-xbap"></a>Tworzenie XBAP pełnego zaufania  
 Jeśli Twoje XBAP wymaga pełnego zaufania, można zmienić projekt tak, aby włączyć te uprawnienia. W poniższych krokach opisano sposób włączania pełnego zaufania:  
  
1.  W programie Visual Studio Otwórz właściwości projektu.  
  
2.  Na **zabezpieczeń** wybierz opcję **to jest aplikacja pełne zaufanie** opcji.  
  
 To ustawienie powoduje, że następujące zmiany:  
  
-   W pliku projektu `<TargetZone>` wartość elementu jest zmieniana na `Custom`.  
  
-   W manifeście aplikacji (app.manifest) `Unrestricted="true"` jest dodawany atrybut `PermissionSet` elementu.  
  
    ```xml
    <PermissionSet class="System.Security.PermissionSet"   
                   version="1"   
                   ID="Custom"   
                   SameSite="site"   
                   Unrestricted="true" />  
    ```  
  
### <a name="deploying-a-full-trust-xbap"></a>Wdrażanie XBAP pełnego zaufania  
 Podczas wdrażania XBAP pełnego zaufania, który nie jest zgodna z modelu wdrażania zaufanych ClickOnce zachowania, gdy użytkownik uruchomi aplikację będzie zależeć od strefy zabezpieczeń. W niektórych przypadkach użytkownik otrzyma ostrzeżenie po podjęciu próby go zainstalować. Użytkownik może wybrać kontynuować, lub Anuluj instalację. W poniższej tabeli opisano zachowanie aplikacji dla każdej strefy zabezpieczeń i co trzeba zrobić dla aplikacji do otrzymania pełnego zaufania.  
  
|Strefa zabezpieczeń|Zachowanie|Pobieranie pełnego zaufania|  
|-------------------|--------------|------------------------|  
|Komputer lokalny|Automatyczne pełnego zaufania|Nie jest potrzebne nie działanie.|  
|W intranecie i zaufanych witryn|Monituj o pełnym zaufaniu|Podpisywać XBAP przy użyciu certyfikatu, użytkownik zobaczy źródła w wierszu.|  
|Internet|Nie powiodło się "Nieudzielenia zaufania"|Zaloguj się XBAP przy użyciu certyfikatu.|  
  
> [!NOTE]
>  Zachowanie opisane w poprzedniej tabeli dotyczy XBAP pełnego zaufania, które nie są zgodne z modelu wdrażania zaufanych ClickOnce.  
  
 Zalecane jest, użyj modelu wdrażania zaufanych ClickOnce do wdrażania XBAP pełnego zaufania. Ten model umożliwia Twojej XBAP mieć uprawnienia pełnego zaufania automatycznie, niezależnie od strefy zabezpieczeń, dzięki czemu użytkownik nie jest monitowany. Jako część tego modelu musisz zarejestrować aplikację za pomocą certyfikatu z zaufanego wydawcę. Aby uzyskać więcej informacji, zobacz [zaufane Omówienie wdrożenia aplikacji](/visualstudio/deployment/trusted-application-deployment-overview) i [wprowadzenie do podpisywania kodu](http://go.microsoft.com/fwlink/?LinkId=166327).  
  
<a name="xbap_start_time_performance_considerations"></a>   
## <a name="xbap-start-time-performance-considerations"></a>Zagadnienia związane z wydajnością XBAP początkowy czas  
 Ważnym aspektem wydajności XBAP jest jego czas rozpoczęcia. Jeśli pierwsza aplikacja WPF załadować, jest XBAP *zimny start* należy dziesięć sekund lub więcej. To dlatego strona postępu jest renderowany przez WPF i CLR i WPF należy chłodni uruchomić, aby wyświetlić aplikacji.  
  
 Począwszy od [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], czas zimnego XBAP skuteczność została osłabiona przez wyświetlanie na stronie Postęp niezarządzane wczesnym etapie cyklu wdrażania. Strona postępu jest wyświetlana niemal natychmiast po uruchomieniu aplikacji, ponieważ jest on wyświetlany przez hostingu kodu natywnego i renderowania w formacie HTML.  
  
 Ponadto ulepszone współbieżności [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] sekwencji pobierania poprawia czas rozpoczęcia przez maksymalnie 10 procent. Po [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] pliki do pobrania i sprawdza poprawność manifestów, uruchamia pobierania aplikacji i uruchamia pasek postępu do aktualizacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie w programie Visual Studio debugowania aplikacji przeglądarki XAML w celu wywoływania usługi internetowej](../../../../docs/framework/wpf/app-development/configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)  
 [Wdrażanie aplikacji WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)
