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
ms.openlocfilehash: ebaa5c2f3a2e1770a50a401fb6771d8c5ad3ba63
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972230"
---
# <a name="wpf-xaml-browser-applications-overview"></a>Przegląd Aplikacje przeglądarek WPF XAML
<a name="introduction"></a>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]łączy funkcje aplikacji sieci Web i aplikacji z aplikacjami rozbudowanymi. Na przykład aplikacje sieci Web XBAP mogą być wdrażane na serwerze sieci Web i uruchamiane z przeglądarki Internet Explorer lub Firefox. Podobnie jak w przypadku aplikacji z rozbudowanymi aplikacjami klienckimi, aplikacje XBAP mogą korzystać z możliwości platformy WPF. Tworzenie aplikacji XBAP jest również podobne do rozbudowanych wdrożeń klientów. Ten temat zawiera proste, górne wprowadzenie do programowania aplikacji XBAP i opisuje, gdzie Programowanie aplikacji XBAP różni się od standardowego rozbudowanego środowiska programistycznego.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Tworzenie nowej aplikacji przeglądarki XAML (XBAP)](#creating_a_new_xaml_browser_application_xbap)  
  
- [Wdrażanie aplikacji XBAP](#deploying_a_xbap)  
  
- [Komunikacja ze stroną sieci Web hosta](#communicating_with_the_host_web_page)  
  
- [Zagadnienia dotyczące zabezpieczeń XBAP](#xbap_security_considerations)  
  
- [Zagadnienia dotyczące wydajności w czasie uruchamiania aplikacji XBAP](#xbap_start_time_performance_considerations)  
  
<a name="creating_a_new_xaml_browser_application_xbap"></a>   
## <a name="creating-a-new-xaml-browser-application-xbap"></a>Tworzenie nowej aplikacji przeglądarki XAML (XBAP)  
 Najprostszym sposobem tworzenia nowego projektu XBAP jest Microsoft Visual Studio. Podczas tworzenia nowego projektu wybierz z listy szablonów pozycję **Aplikacja przeglądarki WPF** . Aby uzyskać więcej informacji, zobacz [jak: Utwórz nowy projekt](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))aplikacji w przeglądarce WPF.  
  
 Po uruchomieniu projektu XBAP zostanie on otwarty w oknie przeglądarki, a nie w oknie autonomicznym. Gdy debugujesz aplikację XBAP z programu Visual Studio, aplikacja jest uruchamiana z uprawnieniem strefa internetowa i w związku z tym generuje wyjątki zabezpieczeń w przypadku przekroczenia tych uprawnień. Aby uzyskać więcej informacji, [](../security-wpf.md) Zobacz zabezpieczenia i [WPF częściowe zabezpieczenia zaufania](../wpf-partial-trust-security.md).  
  
> [!NOTE]
>  Jeśli nie opracowujesz programu Visual Studio lub chcesz dowiedzieć się więcej o plikach projektu, zobacz [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md).  
  
<a name="deploying_a_xbap"></a>   
## <a name="deploying-an-xbap"></a>Wdrażanie aplikacji XBAP  
 Podczas kompilowania aplikacji XBAP dane wyjściowe obejmują następujące trzy pliki:  
  
|Plik|Opis|  
|----------|-----------------|  
|Plik wykonywalny (. exe)|Zawiera skompilowany kod i ma rozszerzenie. exe.|  
|Manifest aplikacji (manifest)|Zawiera metadane skojarzone z aplikacją i ma rozszerzenie. manifest.|  
|Manifest wdrożenia (. XBAP)|Ten plik zawiera informacje używane w technologii ClickOnce do wdrażania aplikacji i ma rozszerzenie. XBAP.|  
  
 Wdrażasz aplikacje XBAP na serwerze sieci Web, na przykład [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] lub w nowszych wersjach. Nie trzeba instalować .NET Framework na serwerze sieci Web, ale trzeba zarejestrować [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] typy MIME (Multipurpose Internet Mail Extensions) i rozszerzenia nazw plików. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług iis 5,0 i iis 6,0 do wdrażania aplikacji WPF](how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).  
  
 Aby przygotować serwer XBAP do wdrożenia, skopiuj plik. exe i powiązane z nim manifesty do serwera sieci Web. Utwórz stronę HTML zawierającą hiperłącze, aby otworzyć manifest wdrożenia, który jest plikiem z rozszerzeniem. XBAP. Gdy użytkownik kliknie link do pliku. XBAP, ClickOnce automatycznie obsługuje Mechanics pobierania i uruchamiania aplikacji. Poniższy przykładowy kod pokazuje stronę HTML zawierającą hiperłącze wskazujące na aplikację XBAP.  
  
```html
<html>   
    <head></head>  
    <body>   
        <a href="XbapEx.xbap">Click this link to launch the application</a>  
    </body>   
</html>  
```  
  
 Można również hostować aplikacje XBAP w ramce strony sieci Web. Utwórz stronę sieci Web z co najmniej jedną ramką. Ustaw właściwość source ramki na plik manifestu wdrożenia. Jeśli chcesz użyć wbudowanego mechanizmu do komunikacji między hostowaną stroną sieci Web i aplikacją XBAP, musisz hostować aplikację w ramce. Poniższy przykładowy kod pokazuje stronę HTML z dwiema ramkami, Źródło dla drugiej ramki jest ustawione na aplikacje XBAP.  
  
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
  
### <a name="clearing-cached-xbaps"></a>Czyszczenie buforowanych aplikacji XBAP  
 W niektórych sytuacjach po ponownym skompilowaniu i uruchomieniu aplikacji XBAP może zostać otwarta wcześniejsza wersja aplikacji XBAP. Na przykład takie zachowanie może wystąpić, gdy numer wersji zestawu aplikacji XBAP jest statyczny, a program XBAP zostanie uruchomiony z wiersza polecenia. W takim przypadku ze względu na to, że numer wersji między wersją w pamięci podręcznej (wersja, która była wcześniej uruchomiona) i Nowa wersja nie są takie same, Nowa wersja aplikacji XBAP nie zostanie pobrana. Zamiast tego zostanie załadowana buforowana wersja.  
  
 W takich sytuacjach można usunąć wersję z pamięci podręcznej za pomocą polecenia **Mage** (zainstalowanego z programem Visual Studio lub Windows SDK) w wierszu polecenia. Następujące polecenie czyści pamięć podręczną aplikacji.  
  
 ```console
 Mage.exe -cc
 ```
  
 To polecenie gwarantuje, że została uruchomiona Najnowsza wersja aplikacji XBAP. Podczas debugowania aplikacji w programie Visual Studio należy uruchomić najnowszą wersję programu XBAP. Ogólnie rzecz biorąc należy zaktualizować numer wersji wdrożenia przy każdej kompilacji. Aby uzyskać więcej informacji na temat programu Mage, zobacz [plik Mage. exe (narzędzie tworzenia i edycji manifestów)](../../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
<a name="communicating_with_the_host_web_page"></a>   
## <a name="communicating-with-the-host-web-page"></a>Komunikacja ze stroną sieci Web hosta  
 Gdy aplikacja jest hostowana w ramce HTML, można komunikować się ze stroną sieci Web, która zawiera aplikację XBAP. Można to zrobić przez pobranie <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> <xref:System.Windows.Interop.BrowserInteropHelper>właściwości. Ta właściwość zwraca obiekt skryptu, który reprezentuje okno HTML. Następnie można uzyskać dostęp do właściwości, metod i zdarzeń w [obiekcie Window](https://go.microsoft.com/fwlink/?LinkId=160274) przy użyciu zwykłej składni z kropką. Możesz również uzyskać dostęp do metod skryptu i zmiennych globalnych. Poniższy przykład pokazuje, jak pobrać obiekt skryptu i zamknąć przeglądarkę.  
  
 [!code-csharp[XbapBrowserInterop#10](~/samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]  
  
### <a name="debugging-xbaps-that-use-hostscript"></a>Debugowanie aplikacji XBAP korzystających z HostScript  
 Jeśli aplikacja XBAP używa <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> obiektu do komunikowania się z oknem HTML, istnieją dwa ustawienia, które należy określić do uruchomienia i debugowania aplikacji w programie Visual Studio. Aplikacja musi mieć dostęp do swojej witryny pochodzenia i należy uruchomić aplikację ze stroną HTML zawierającą aplikację XBAP. W poniższych krokach opisano, jak sprawdzić te dwa ustawienia:  
  
1. W programie Visual Studio Otwórz właściwości projektu.  
  
2. Na karcie **zabezpieczenia** kliknij przycisk **Zaawansowane**.  
  
     Zostanie wyświetlone okno dialogowe Zaawansowane ustawienia zabezpieczeń.  
  
3. Upewnij się, że pole wyboru **Udziel aplikacji dostępu do jej lokacji pochodzenia** jest zaznaczone, a następnie kliknij przycisk **OK**.  
  
4. Na karcie **debugowanie** wybierz opcję **Uruchom przeglądarkę z adresem URL** i określ adres URL strony HTML zawierającej aplikacje XBAP.  
  
5. W programie Internet Explorer kliknij przycisk **Narzędzia** , a następnie wybierz pozycję **Opcje internetowe**.  
  
     Zostanie wyświetlone okno dialogowe Opcje internetowe.  
  
6. Kliknij przycisk **zaawansowane** kartę.  
  
7. Na liście **Ustawienia** w obszarze **zabezpieczenia**zaznacz pole wyboru **Zezwalaj na uruchamianie aktywnej zawartości w plikach na moim komputerze** .  
  
8. Kliknij przycisk **OK**.  
  
     Zmiany zostaną wprowadzone po ponownym uruchomieniu programu Internet Explorer.  
  
> [!CAUTION]
>  Włączenie aktywnej zawartości w programie Internet Explorer może spowodować zagrożenie dla komputera. Jeśli nie chcesz zmieniać ustawień zabezpieczeń programu Internet Explorer, możesz uruchomić stronę HTML z serwera i dołączyć debuger programu Visual Studio do procesu.  
  
<a name="xbap_security_considerations"></a>   
## <a name="xbap-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń XBAP  
 Aplikacje XBAP są zwykle wykonywane w piaskownicy zabezpieczeń częściowej relacji zaufania, które są ograniczone do zestawu uprawnień strefy internetowej. W związku z tym implementacja musi obsługiwać podzestaw elementów WPF, które są obsługiwane przez strefę internetową, lub należy podwyższyć poziom uprawnień aplikacji. Aby uzyskać więcej informacji, zobacz [zabezpieczenia](../security-wpf.md).  
  
 Gdy używasz <xref:System.Windows.Controls.WebBrowser> kontrolki w aplikacji, WPF wewnętrznie tworzy wystąpienie natywnej kontrolki ActiveX WebBrowser. Gdy aplikacja jest częścią zaufania XBAP działającą w programie Internet Explorer, formant ActiveX jest uruchamiany w dedykowanym wątku procesu programu Internet Explorer. W związku z tym obowiązują następujące ograniczenia:  
  
- <xref:System.Windows.Controls.WebBrowser> Formant powinien zapewniać zachowanie podobne do przeglądarki hosta, w tym ograniczeń zabezpieczeń. Niektóre z tych ograniczeń zabezpieczeń można kontrolować za pomocą ustawień zabezpieczeń programu Internet Explorer. Aby uzyskać więcej informacji, zobacz [zabezpieczenia](../security-wpf.md).  
  
- Wyjątek jest zgłaszany, gdy aplikacje XBAP są ładowane na stronie HTML.  
  
- Dane wejściowe są w osobnym wątku z platformy WPF <xref:System.Windows.Controls.WebBrowser>, więc nie można przechwycić wejścia z klawiatury, a stan IME nie jest udostępniony.  
  
- Czas lub kolejność nawigowania mogą być różne ze względu na kontrolkę ActiveX uruchomioną w innym wątku. Na przykład przechodzenie do strony nie zawsze jest anulowane przez uruchomienie innego żądania nawigacji.  
  
- Niestandardowa Kontrolka ActiveX może mieć problemy z komunikacją, ponieważ aplikacja WPF działa w osobnym wątku.  
  
- <xref:System.Windows.Interop.HwndHost.MessageHook>nie zostanie zgłoszone, <xref:System.Windows.Interop.HwndHost> ponieważ nie można podtworzyć podklasy okna uruchomionego w innym wątku lub procesie.  
  
### <a name="creating-a-full-trust-xbap"></a>Tworzenie pełnego zaufania XBAP  
 Jeśli Twoje aplikacje XBAP wymagają pełnego zaufania, możesz zmienić projekt, aby włączyć to uprawnienie. W poniższych krokach opisano sposób włączania pełnego zaufania:  
  
1. W programie Visual Studio Otwórz właściwości projektu.  
  
2. Na karcie **zabezpieczenia** wybierz opcję **to jest aplikacja pełnego zaufania** .  
  
 To ustawienie wprowadza następujące zmiany:  
  
- W pliku `<TargetZone>` projektu wartość elementu jest zmieniana na `Custom`.  
  
- W manifeście aplikacji (App. manifest) `Unrestricted="true"` atrybut jest dodawany do<xref:System.Security.PermissionSet> elementu.  
  
    ```xml
    <PermissionSet class="System.Security.PermissionSet"   
                   version="1"   
                   ID="Custom"   
                   SameSite="site"   
                   Unrestricted="true" />  
    ```  
  
### <a name="deploying-a-full-trust-xbap"></a>Wdrażanie aplikacji XBAP z pełnym zaufaniem  
 W przypadku wdrażania pełnego zaufania XBAP, który nie jest zgodny z modelem zaufanego wdrażania ClickOnce, zachowanie, gdy użytkownik uruchomi aplikację, będzie zależeć od strefy zabezpieczeń. W niektórych przypadkach podczas próby zainstalowania tego użytkownika zostanie wyświetlone ostrzeżenie. Użytkownik może wybrać opcję kontynuowania lub anulowania instalacji. W poniższej tabeli opisano zachowanie aplikacji dla każdej strefy zabezpieczeń i czynności, które należy wykonać, aby aplikacja mogła uzyskać pełne zaufanie.  
  
|Strefa zabezpieczeń|Zachowanie|Pobieranie pełnego zaufania|  
|-------------------|--------------|------------------------|  
|Komputer lokalny|Automatyczne pełne zaufanie|Nie jest wymagana żadna akcja.|  
|Intranet i Zaufane witryny|Monituj o pełne zaufanie|Podpisz element XBAP przy użyciu certyfikatu, aby użytkownik widział źródło w monicie.|  
|Internet|Niepowodzenie z "zaufaniem nieudzielonym"|Podpisz element XBAP przy użyciu certyfikatu.|  
  
> [!NOTE]
>  Zachowanie opisane w poprzedniej tabeli dotyczy w pełni zaufanych aplikacji XBAP, które nie są zgodne z zaufanym modelem wdrażania ClickOnce.  
  
 Zaleca się użycie zaufanego modelu wdrażania ClickOnce do wdrażania pełnego zaufania XBAP. Ten model umożliwia aplikacji XBAP automatyczne przydzielanie pełnego zaufania, niezależnie od strefy zabezpieczeń, dzięki czemu użytkownik nie będzie monitowany. W ramach tego modelu należy podpisać aplikację z certyfikatem z zaufanego wydawcy. Aby uzyskać więcej informacji, zobacz [Omówienie wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview) i [wprowadzenie do podpisywania kodu](https://go.microsoft.com/fwlink/?LinkId=166327).  
  
<a name="xbap_start_time_performance_considerations"></a>   
## <a name="xbap-start-time-performance-considerations"></a>Zagadnienia dotyczące wydajności w czasie uruchamiania aplikacji XBAP  
 Ważnym aspektem wydajności aplikacji XBAP jest jego godzina rozpoczęcia. Jeśli XBAP to pierwsza aplikacja WPF do załadowania, czas *zimnego uruchomienia* może wynosić dziesięć sekund lub dłużej. Jest to spowodowane tym, że strona postęp jest renderowana przez WPF, a zarówno środowisko CLR, jak i WPF muszą mieć zimny start, aby wyświetlić aplikację.  
  
 Począwszy od .NET Framework 3,5 z dodatkiem SP1, czas zimnego uruchamiania programu XBAP został skorygowany przez wyświetlenie strony niezarządzanego postępu w cyklu wdrażania. Strona postęp pojawia się niemal natychmiast po uruchomieniu aplikacji, ponieważ jest wyświetlana przez natywny kod hostingu i renderowany w kodzie HTML.  
  
 Ponadto ulepszone współbieżność sekwencji pobierania ClickOnce skraca czas rozpoczęcia do dziesięciu procent. Gdy ClickOnce pobiera i sprawdza poprawność manifestów, rozpocznie się pobieranie aplikacji, a pasek postępu zostanie zaktualizowany.  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie w programie Visual Studio debugowania aplikacji przeglądarki XAML w celu wywoływania usługi internetowej](configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)
- [Wdrażanie aplikacji WPF](deploying-a-wpf-application-wpf.md)
