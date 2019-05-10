---
title: Przegląd Aplikacje przeglądarek WPF XAML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XBAP [WPF], XAML browser application
- WPF XAML browser applications (XBAP)
- XAML browser applications (XBAP)
- browser-hosted applications [WPF]
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
ms.openlocfilehash: d536d141d1ac7126c5a3339f75ba374d3e071806
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591405"
---
# <a name="wpf-xaml-browser-applications-overview"></a>Przegląd Aplikacje przeglądarek WPF XAML
<a name="introduction"></a>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] łączy funkcje aplikacji wzbogaconego klienta i aplikacji sieci Web. Takich jak aplikacje sieci Web aplikacji XBAP można wdrożyć na serwerze sieci Web i uruchomić z programu Internet Explorer lub przeglądarki Firefox. Np. aplikacji wzbogaconego klienta aplikacji XBAP korzystać z zalet możliwości WPF. Opracowywanie aplikacji XBAP także jest podobna do rozwoju wzbogaconego klienta. Ten temat zawiera proste, ogólne wprowadzenie do programowania XBAP i w tym artykule opisano, gdzie rozwoju XBAP różni się od tworzenia w standardzie wzbogaconego klienta.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Tworzenie nowej aplikacji przeglądarki XAML (XBAP)](#creating_a_new_xaml_browser_application_xbap)  
  
- [Wdrażania XBAP](#deploying_a_xbap)  
  
- [Podczas komunikowania się ze stroną sieci Web hosta](#communicating_with_the_host_web_page)  
  
- [XBAP Security Considerations](#xbap_security_considerations)  
  
- [Zagadnienia związane z wydajnością XBAP początek godziny](#xbap_start_time_performance_considerations)  
  
<a name="creating_a_new_xaml_browser_application_xbap"></a>   
## <a name="creating-a-new-xaml-browser-application-xbap"></a>Tworzenie nowej aplikacji przeglądarki XAML (XBAP)  
 Najprostszym sposobem, aby utworzyć nowy projekt XBAP jest program Microsoft Visual Studio. Podczas tworzenia nowego projektu, wybierz **aplikacja przeglądarki środowiska WPF** z listy szablonów. Aby uzyskać więcej informacji, zobacz [jak: Utwórz nowy projekt aplikacji przeglądarki WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)).  
  
 Kiedy uruchamiasz projekt XBAP, zostanie otwarty w oknie przeglądarki, zamiast autonomicznych okna. Podczas debugowania XBAP z programu Visual Studio, aplikacja zostanie uruchomiona przy użyciu uprawnień strefy Internet i w związku z tym będzie zgłaszać wyjątki zabezpieczeń przekroczeniu te uprawnienia. Aby uzyskać więcej informacji, zobacz [zabezpieczeń](../security-wpf.md) i [WPF częściowego zaufania zabezpieczeń](../wpf-partial-trust-security.md).  
  
> [!NOTE]
>  Jeśli nie jest tworzona przy użyciu programu Visual Studio lub jeśli chcesz, aby dowiedzieć się więcej na temat plików projektu, zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md).  
  
<a name="deploying_a_xbap"></a>   
## <a name="deploying-an-xbap"></a>Wdrażania XBAP  
 W przypadku tworzenia XBAP, dane wyjściowe obejmują następujące trzy pliki:  
  
|Plik|Opis|  
|----------|-----------------|  
|Plik wykonywalny (.exe)|Zawiera kod skompilowany, a ma rozszerzenie .exe.|  
|Manifest aplikacji (manifest)|Zawiera metadane skojarzone z aplikacją i ma rozszerzenie .manifest.|  
|Manifest wdrażania (.xbap)|Ten plik zawiera informacje, że ClickOnce używa do wdrożenia aplikacji, a ma rozszerzeniem XBAP.|  
  
 Wdrożeniem aplikacji XBAP do serwera sieci Web, na przykład [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] lub nowszy. Nie trzeba zainstalować program .NET Framework na serwerze sieci Web, ale należy zarejestrować [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] typów i nazw plików rozszerzeń. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług IIS 5.0 oraz IIS 6.0, aby wdrożyć aplikacje WPF](how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).  
  
 Przygotować swoje XBAP do wdrożenia, należy skopiować .exe i manifesty skojarzone z serwerem sieci Web. Utwórz stronę HTML, która zawiera hiperłącze można otworzyć pliku manifestu wdrożenia, jest to plik z rozszerzeniem XBAP. Gdy użytkownik kliknie łącze do pliku XBAP, ClickOnce automatycznie obsługuje mechanika pobierania i uruchamiania aplikacji. Poniższy przykład kodu pokazuje stronę HTML, która zawiera hiperłącze, które wskazuje XBAP.  
  
```html
<html>   
    <head></head>  
    <body>   
        <a href="XbapEx.xbap">Click this link to launch the application</a>  
    </body>   
</html>  
```  
  
 Może również obsługiwać XBAP w ramce strony sieci Web. Utwórz stronę sieci Web z jedną lub więcej ramek. Ustaw właściwość source ramki do pliku manifestu wdrożenia. Jeśli chcesz używać wbudowany mechanizm do komunikowania się od hostowania stron sieci Web i XBAP musi być hostem aplikacji w ramce. Poniższy przykład kodu pokazuje strony HTML przy użyciu dwóch ramek źródła dla drugiej ramki jest ustawiona na XBAP.  
  
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
  
### <a name="clearing-cached-xbaps"></a>Clearing Cached XBAPs  
 W niektórych sytuacjach po ponowne tworzenie i uruchamianie usługi XBAP może się okazać, otwarciu starszą wersję XBAP. Na przykład to zachowanie może wystąpić, gdy numer wersji zestawu XBAP jest statyczna i XBAP jest uruchamiany z wiersza polecenia. W tym przypadku ponieważ numer wersji między pamięci podręcznej wersji (wersja, która została wcześniej uruchomiona) i nowa wersja pozostają takie same, nową wersję XBAP nie zostanie pobrana. Zamiast tego jest ładowany w pamięci podręcznej wersji.  
  
 W takich sytuacjach można usunąć pamięci podręcznej wersji przy użyciu **Mage** polecenia (zainstalowany za pomocą programu Visual Studio lub zestawu Windows SDK) w wierszu polecenia. Następujące polecenie powoduje wyczyszczenie pamięci podręcznej aplikacji.  
  
 ```console
 Mage.exe -cc
 ```
  
 To polecenie gwarantuje, że jest uruchomiona najnowsza wersja usługi XBAP. Podczas debugowania aplikacji w programie Visual Studio, należy uruchomić najnowszą wersję swojej XBAP. Ogólnie rzecz biorąc należy zaktualizować numer wersji wdrażania każdej kompilacji. Aby uzyskać więcej informacji na temat Mage zobacz [Mage.exe (Manifest Generation i narzędzia do edytowania)](../../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
<a name="communicating_with_the_host_web_page"></a>   
## <a name="communicating-with-the-host-web-page"></a>Podczas komunikowania się ze stroną sieci Web hosta  
 Gdy aplikacja jest obsługiwana w ramce HTML, mogą komunikować się ze stroną sieci Web, zawierającą XBAP. Można to zrobić, trwa pobieranie <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> właściwość <xref:System.Windows.Interop.BrowserInteropHelper>. Ta właściwość zwraca obiekt skryptu, który reprezentuje okno HTML. Właściwości, metody i zdarzenia mogą następnie dostęp na [obiekt okna](https://go.microsoft.com/fwlink/?LinkId=160274) przy użyciu składni z kropkami regularne. Można także przejść metody skryptów i zmiennych globalnych. Poniższy przykład przedstawia sposób pobierania obiektu skryptu i zamknij przeglądarkę.  
  
 [!code-csharp[XbapBrowserInterop#10](~/samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]  
  
### <a name="debugging-xbaps-that-use-hostscript"></a>Debugowanie aplikacji XBAP, które używają HostScript  
 Jeśli korzysta z Twojego XBAP <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> obiektu do komunikowania się z okna kodu HTML, istnieją dwa ustawienia, które należy określić w celu uruchamiania i debugowania aplikacji w programie Visual Studio. Aplikacja musi mieć dostęp do witryny pochodzenia i należy uruchomić aplikację za pomocą strony HTML, który zawiera XBAP. W poniższych krokach opisano, jak sprawdzić te dwa ustawienia:  
  
1. W programie Visual Studio Otwórz właściwości projektu.  
  
2. Na **zabezpieczeń** kliknij pozycję **zaawansowane**.  
  
     Zostanie wyświetlone okno dialogowe Zaawansowane ustawienia zabezpieczeń.  
  
3. Upewnij się, że **przyznać aplikacji dostęp do witryny pochodzenia** zaznacz pole wyboru zostało zaznaczone, a następnie kliknij przycisk **OK**.  
  
4. Na **debugowania** zaznacz **uruchamiania przeglądarki z adresem URL** opcji, a następnie określ adres URL strony HTML, który zawiera XBAP.  
  
5. W programie Internet Explorer kliknij **narzędzia** przycisk, a następnie wybierz pozycję **Opcje internetowe**.  
  
     Zostanie wyświetlone okno dialogowe Opcje internetowe.  
  
6. Kliknij przycisk **zaawansowane** kartę.  
  
7. W **ustawienia** w obszarze **zabezpieczeń**, sprawdź **active zawartości do uruchamiania w plikach na moim komputerze** pole wyboru.  
  
8. Kliknij przycisk **OK**.  
  
     Zmiany zostaną wprowadzone po ponownym uruchomieniu programu Internet Explorer.  
  
> [!CAUTION]
>  Włączanie aktywna zawartość w programie Internet Explorer może zagrożenie komputera. Jeśli nie chcesz zmienić ustawienia zabezpieczeń programu Internet Explorer, możesz uruchomić stronę HTML z serwera i dołączyć debuger programu Visual Studio do procesu.  
  
<a name="xbap_security_considerations"></a>   
## <a name="xbap-security-considerations"></a>XBAP Security Considerations  
 XBAP zazwyczaj wykonywane w piaskownicy zabezpieczeń częściowego zaufania, który jest ograniczony do zestaw uprawnień strefy Internet. W związku z tym Twoja implementacja musi obsługiwać podzbiór elementów WPF, które są obsługiwane w strefie Internet lub należy podnieść poziom uprawnień aplikacji. Aby uzyskać więcej informacji, zobacz [zabezpieczeń](../security-wpf.md).  
  
 Kiedy używasz <xref:System.Windows.Controls.WebBrowser> kontrolki w aplikacji WPF tworzy wewnętrznie macierzystym formancie WebBrowser ActiveX. Gdy aplikacja jest XBAP częściowego zaufania, w programie Internet Explorer, formant ActiveX jest uruchamiany w dedykowanym wątku proces programu Internet Explorer. W związku z tym obowiązują następujące ograniczenia:  
  
- <xref:System.Windows.Controls.WebBrowser> Kontrolki powinien zapewniać zachowanie podobne do przeglądarce hosta, w tym ograniczenia zabezpieczeń. Niektóre z tych ograniczeń zabezpieczeń mogą być kontrolowane przez ustawienia zabezpieczeń programu Internet Explorer. Aby uzyskać więcej informacji, zobacz [zabezpieczeń](../security-wpf.md).  
  
- Wyjątek jest generowany, gdy XBAP jest załadowany międzydomenowe na stronie HTML.  
  
- Dane wejściowe są w oddzielnym wątku z WPF <xref:System.Windows.Controls.WebBrowser>, dlatego nie można przechwytywać dane wejściowe z klawiatury i nie jest udostępniony stan edytora IME.  
  
- Kolejność nawigacji lub termin może się różnić z powodu formantu ActiveX, uruchomiony w innym wątku. Na przykład przechodząc do strony jest nie zawsze anulowane przez uruchomienie kolejnego żądania nawigacji.  
  
- Niestandardowy formant ActiveX może mieć problemy z komunikacją, ponieważ aplikacja WPF działa w oddzielnym wątku.  
  
- <xref:System.Windows.Interop.HwndHost.MessageHook> nie uzyskać zgłaszane, ponieważ <xref:System.Windows.Interop.HwndHost> nie podklasy okna uruchomionego w innym wątku lub procesu.  
  
### <a name="creating-a-full-trust-xbap"></a>Tworzenie XBAP pełnego zaufania  
 Jeśli Twoje XBAP wymaga pełnego zaufania, można zmienić projekt tak, aby włączyć te uprawnienia. W poniższych krokach opisano sposób włączania pełnego zaufania:  
  
1. W programie Visual Studio Otwórz właściwości projektu.  
  
2. Na **zabezpieczeń** zaznacz **jest to aplikacja w trybie pełnego zaufania** opcji.  
  
 To ustawienie powoduje następujące zmiany:  
  
- W pliku projektu `<TargetZone>` wartość elementu jest zmieniana na `Custom`.  
  
- W manifeście aplikacji (app.manifest) `Unrestricted="true"` jest dodawany atrybut "<xref:System.Security.PermissionSet> elementu.  
  
    ```xml
    <PermissionSet class="System.Security.PermissionSet"   
                   version="1"   
                   ID="Custom"   
                   SameSite="site"   
                   Unrestricted="true" />  
    ```  
  
### <a name="deploying-a-full-trust-xbap"></a>Wdrażania XBAP pełnego zaufania  
 Podczas wdrażania XBAP pełnego zaufania, który nie jest zgodna z modelu wdrażania zaufanych ClickOnce zachowanie, gdy użytkownik uruchamia aplikację będzie zależeć od strefy zabezpieczeń. W niektórych przypadkach użytkownik zostanie wyświetlone ostrzeżenie, gdy próbują zainstalować ją. Użytkownik może zdecydować kontynuować, lub Anuluj instalację. W poniższej tabeli opisano zachowanie aplikacji dla każdej strefy zabezpieczeń i co należy zrobić dla aplikacji otrzymać pełne zaufanie.  
  
|Strefa zabezpieczeń|Zachowanie|Pobieranie pełnego zaufania|  
|-------------------|--------------|------------------------|  
|Komputer lokalny|Automatyczne pełnego zaufania|Jest wymagana żadna akcja.|  
|W intranecie i zaufanych witryn|Monituj o pełnym zaufaniu|Zaloguj się XBAP przy użyciu certyfikatu, tak, aby użytkownik zobaczy źródła w wierszu polecenia.|  
|Internet|Kończy się błędem "Nie udzielono zaufania"|Zaloguj się XBAP przy użyciu certyfikatu.|  
  
> [!NOTE]
>  To zachowanie opisane w poprzedniej tabeli dla aplikacji XBAP pełnego zaufania, które nie są zgodne z modelu wdrażania zaufanych ClickOnce.  
  
 Zalecane jest użycie modelu wdrażania zaufanych ClickOnce do wdrażania XBAP pełnego zaufania. Ten model umożliwia Twojej XBAP należy przyznać pełne zaufanie automatycznie, niezależnie od strefy zabezpieczeń, dzięki czemu użytkownik nie jest monitowany. W ramach tego modelu musisz zarejestrować aplikację przy użyciu certyfikatu z zaufanego wydawcę. Aby uzyskać więcej informacji, zobacz [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview) i [wprowadzenie do podpisywania kodu](https://go.microsoft.com/fwlink/?LinkId=166327).  
  
<a name="xbap_start_time_performance_considerations"></a>   
## <a name="xbap-start-time-performance-considerations"></a>Zagadnienia związane z wydajnością XBAP początek godziny  
 Ważnym aspektem wydajności XBAP jest jego czas rozpoczęcia. Jeśli pierwszą aplikację WPF, aby załadować, XBAP *zimnego* należy dziesięć sekund lub więcej. Jest to spowodowane przez WPF wyrenderowaniu strony postępu i CLR i WPF należy zimnego uruchomić, aby wyświetlić aplikację.  
  
 Począwszy od [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], czas zimnego startu XBAP skuteczność została osłabiona przez stroną niezarządzanych postępu na wczesnym etapie cyklu wdrażania. Na stronie Postęp jest niemal natychmiast pojawi się po uruchomieniu aplikacji, ponieważ jest on wyświetlany przez natywny kod hostingu i renderowania w formacie HTML.  
  
 Ponadto ulepszone współbieżności sekwencji pobierania ClickOnce poprawia czas rozpoczęcia przez maksymalnie 10 procent. Po ClickOnce pliki do pobrania i sprawdza poprawność manifestów, uruchamiania pobierania aplikacji i pasek postępu rozpoczyna się do aktualizacji.  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie w programie Visual Studio debugowania aplikacji przeglądarki XAML w celu wywoływania usługi internetowej](configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)
- [Wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md)
