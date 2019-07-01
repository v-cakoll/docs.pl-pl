---
title: Usługi hostingowe
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
ms.openlocfilehash: b1a0a07876e9cc111e8c5eef56f208d7bf2cb49f
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487700"
---
# <a name="hosting-services"></a>Usługi hostingowe
Stanie się aktywna, usługa musi być hostowany w środowisku uruchomieniowym, tworzy go, która określa jego kontekstu i okresu istnienia. Usługi Windows Communication Foundation (WCF) są przeznaczone do uruchamiania w każdym procesie Windows obsługuje kodu zarządzanego.  
  
 Usługi WCF zapewnia ujednolicony model programowania służący do budowania aplikacji usługowych. Ten model programowania spójność i jest niezależna od środowiska wykonawczego, w której wdrażana jest usługa. W praktyce oznacza to, że kod usługi wygląda ten sam niezależnie od opcji hostingu.  
  
 Te opcje z zakresu od działających w aplikacji konsoli aby server w środowiskach, takich jak Windows, Usługa uruchomiona w ramach procesu roboczego zarządzane przez Internetowe usługi informacyjne (IIS) lub przez Windows Process Activation Service (WAS) hostingu. Deweloperzy wybrać Środowisko hostingu, który spełnia wymagania dotyczące wdrażania usługi. Te wymagania mogą pochodzić od platformy, na którym aplikacja zostanie wdrożona, transport, na którym należy wysyłać i odbierać wiadomości, lub typu odtwarzanie procesów i innych Zarządzanie procesem wymagane w celu zapewnienia dostępności odpowiednich lub na niektórych inne wymagania zarządzania lub niezawodności. Następna sekcja zawiera informacje i wskazówki dotyczące obsługi opcji.  
  
## <a name="hosting-options"></a>Opcje hostingu  
  
#### <a name="self-hosting-in-a-managed-application"></a>Hostingu samodzielnego w zarządzanej aplikacji  
 Usługi WCF, mogą być hostowane w dowolnej aplikacji zarządzanych. Jest najbardziej elastyczna opcja, ponieważ wymaga co najmniej infrastruktury do wdrożenia. Osadź kod dla usługi w kodzie aplikacji zarządzanej a następnie utwórz i otwórz wystąpienie <xref:System.ServiceModel.ServiceHost> Aby udostępnić usługę. Aby uzyskać więcej informacji, zobacz [jak: Hostowanie usługi WCF w zarządzanej aplikacji](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Ta opcja umożliwia dwa typowe scenariusze: Usługi WCF uruchomionych aplikacji konsoli i aplikacji wzbogaconego klienta, takich jak oparty na Windows Presentation Foundation (WPF) lub Windows Forms (WinForms). Hostowanie usługi WCF w aplikacji konsoli jest zazwyczaj przydatne podczas fazy opracowywania aplikacji. To sprawia, że ich łatwe debugowanie, ułatwia uzyskanie informacji o śledzeniu, aby dowiedzieć się, co dzieje się w aplikacji i łatwe przenoszenie, kopiując je do nowej lokalizacji. Ta opcja hostingu również ułatwia zaawansowane aplikacje klienckie, takie jak aplikacje WPF i WinForms, do komunikowania się ze światem zewnętrznym. Na przykład współpracy peer-to-peer klient używa WPF interfejs użytkownika, który hostuje również usługi WCF, która umożliwia innym klientom nawiązać z nim i udostępnianie informacji.  
  
#### <a name="managed-windows-services"></a>Usługi zarządzane Windows  
 Ta opcja hostingu składa się z rejestrowania domena aplikacji (AppDomain), który jest hostem usługi WCF jako usługa zarządzana Windows (znana wcześniej jako usługi NT), dlatego, że okres istnienia procesu usługi jest kontrolowane przez Menedżera sterowania usługami (SCM) Usługi Windows. Podobnie jak opcji własnym hostingu tego rodzaju Środowisko hostingu wymaga, że niektóre kod hostingu są zapisywane jako część aplikacji. Usługa jest wdrażana jako usługą Windows i usługi WCF, powodując on dziedziczyć z <xref:System.ServiceProcess.ServiceBase> klasy, a także z WCF usługi interfejsu kontraktu. <xref:System.ServiceModel.ServiceHost> Następnie zostanie utworzony i otwarty w terminie zgodnym z przesłoniętą <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metody i zamknięte w terminie zgodnym z przesłoniętą <xref:System.ServiceProcess.ServiceBase.OnStop> metody. Klasa Instalatora, która dziedziczy <xref:System.Configuration.Install.Installer> również musi być implementowana program ma być zainstalowany jako usługa Windows przez narzędzie Installutil.exe. Aby uzyskać więcej informacji, zobacz [jak: Hostowanie usługi WCF w usłudze Windows zarządzanych](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md). Scenariusz wynikające z zarządzanych usług Windows opcja hostingu jest długotrwałe usługi WCF hostowane poza usługą IIS w bezpiecznym środowisku, który nie jest aktywowany do komunikatu. Okres istnienia usługi steruje zamiast tego systemu operacyjnego. Ta opcja hostingu jest dostępny we wszystkich wersjach systemu Windows.  
  
#### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)  
 Opcja hostingu usług IIS jest zintegrowany z programem ASP.NET i korzysta z funkcji, które oferują te technologie, takie jak proces zamykania odtwarzania, bezczynny, monitorowania kondycji procesu i aktywacja oparta na komunikatach. Na [!INCLUDE[wxp](../../../includes/wxp-md.md)] i [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] systemów operacyjnych, jest to preferowane rozwiązanie do hostowania aplikacji usług sieci Web, które muszą być wysoce dostępny i o wysokim stopniu skalowalności. Usługi IIS oferuje również zintegrowane funkcje zarządzania, które klienci oczekują od produktu server klasy korporacyjnej. Ta opcja hostingu wymaga, aby poprawnie skonfigurować usługi IIS, ale nie wymaga się, że każdy kod hostingu zapisywane jako część aplikacji. Aby uzyskać więcej informacji o sposobie konfigurowania programu IIS hostowanie usługi WCF, zobacz [jak: Hostowanie usługi WCF w programie IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
 Należy pamiętać, że usług hostowanych przez usługi IIS można używać tylko protokołu HTTP. Jego implementacji w usługach IIS 5.1 wprowadził pewne ograniczenia dotyczące [!INCLUDE[wxp](../../../includes/wxp-md.md)]. Aktywacja oparta na komunikatach udostępniane na potrzeby usługi WCF IIS 5.1 w [!INCLUDE[wxp](../../../includes/wxp-md.md)] blokuje wszystkie inne obsługiwanej samodzielnie usługi WCF na tym samym komputerze z przy użyciu portu 80 do komunikowania się. Usługi WCF mogą być uruchamiane w tym samym procesie puli/procesu roboczego elementu AppDomain/aplikacji, jak inne aplikacje, gdy hostowany przez usługi IIS 6.0 w [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Jednak ponieważ WCF i IIS 6.0 używa stosu protokołu HTTP (HTTP.sys) trybu jądra, innych samodzielnie hostowanej usługi WCF, które są uruchomione na tym samym komputerze, w odróżnieniu od usług IIS 5.1 usług IIS 6.0 mogą udostępniać portu 80.  
  
#### <a name="windows-process-activation-service-was"></a>Usługa aktywacji procesów systemu Windows (WAS)  
 Usługa aktywacji procesów systemu Windows (WAS) jest nowy proces aktywacji mechanizm [!INCLUDE[lserver](../../../includes/lserver-md.md)] są również dostępne na [!INCLUDE[wv](../../../includes/wv-md.md)]. Zachowuje on znanego modelu procesów usług IIS 6.0 (pule aplikacji i aktywacja oparta na komunikatach procesu) i hosting funkcji (takich jak natychmiastową ochronę przed błędami, monitorowanie kondycji i odtwarzanie), ale usuwa zależność od protokołu HTTP z aktywacji Architektura. Usługi IIS 7.0 używa WAS do wykonywania aktywacji oparta na komunikatach za pośrednictwem protokołu HTTP. Dodatkowe składniki programu WCF także podłączyć do WAS zapewnienie aktywacja oparta na komunikatach za pośrednictwem innych protokołów obsługiwanych przez usługi WCF, takich jak TCP, usługi MSMQ i nazwanych potoków. Dzięki temu, że aplikacje, które używają protokołów komunikacyjnych korzystanie z funkcji usług IIS jak odtwarzanie procesów, szybkie ochrony i wspólny system konfiguracji, które były tylko dostępne dla aplikacji opartych na protokole HTTP.  
  
 Ta opcja hostingu wymaga, który został skonfigurowany w sposób prawidłowo, ale nie wymaga pisania żadnego kodu hostingu jako część aplikacji. Aby uzyskać więcej informacji na temat sposobu konfigurowania został hostingu, zobacz [jak: Hostowanie usługi WCF w WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="choosing-a-hosting-environment"></a>Wybierając Środowisko hostingu  
 Poniższa tabela zawiera podsumowanie kluczowych korzyści i scenariuszy związany z każdą z opcji hostingu.  
  
|Środowisko hostingu|Typowe scenariusze|Kluczowe korzyści i ograniczenia|  
|-------------------------|----------------------|----------------------------------|  
|Zarządzanej aplikacji ("może być samodzielnie hostowane")|— Aplikacje konsoli używany podczas programowania.<br />— WinForm zaawansowane i uzyskiwanie dostępu do usług aplikacji klienckich programu WPF.|-Elastyczne.<br />— Łatwa do wdrożenia.<br />-Nie przedsiębiorstwa dla usług.|  
|Usługi Windows (znana wcześniej jako usługi NT)|-Długotrwałych usługi WCF hostowane poza usługą IIS.|-Usługa okres istnienia procesu kontrolowane przez system operacyjny nieaktywnej wiadomości.<br />-Obsługiwane przez wszystkie wersje systemu Windows.<br />— Bezpieczne środowisko.|  
|IIS 5.1, IIS 6.0|— Uruchamianie usługi WCF side-by-side z zawartością programu ASP.NET w Internecie przy użyciu protokołu HTTP.|— Odtwarzanie procesów.<br />— Shutdown bezczynności.<br />-Przetwarzanie, monitorowanie kondycji.<br />— Aktywacja oparta na komunikatach.<br />— Tylko protokół HTTP.|  
|Usługa aktywacji procesów systemu Windows (WAS)|— Uruchamianie usługi WCF bez konieczności instalowania usług IIS w Internecie przy użyciu różnych protokołów transportu.|— Usługi IIS nie jest wymagana.<br />— Odtwarzanie procesów.<br />— Shutdown bezczynności.<br />-Przetwarzanie, monitorowanie kondycji.<br />— Aktywacja oparta na komunikatach.<br />-Współpracuje z HTTP, TCP i nazwane potoki oraz usługi MSMQ.|  
|IIS 7.0|— Uruchamianie usługi WCF z zawartością programu ASP.NET.<br />— Uruchamianie usługi WCF w Internecie przy użyciu różnych protokołów transportu.|-NIE korzyści.<br />— Zintegrowane z zawartością programu ASP.NET i IIS.|  
  
 Wybór Środowisko hostingu, zależy od wersji systemu Windows, na którym została wdrożona transportów wymaga do wysyłania wiadomości i typ procesu i odtwarzania domen aplikacji, który wymaga. Poniższa tabela podsumowuje dane związane z tych wymagań.  
  
|Środowisko hostingu|Dostępne platformy|Transporty obsługiwane|Proces i odtwarzania elementu AppDomain|  
|-------------------------|---------------------------|--------------------------|-------------------------------------|  
|Aplikacje zarządzane ("może być samodzielnie hostowane")|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> net.msmq|Nie|  
|Usługi Windows (znana wcześniej jako usługi NT)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> net.msmq|Nie|  
|IIS 5.1|[!INCLUDE[wxp](../../../includes/wxp-md.md)]|HTTP|Tak|  
|IIS 6,0|[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]|HTTP|Tak|  
|Usługa aktywacji procesów systemu Windows (WAS)|[!INCLUDE[wv](../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> net.msmq|Yes|  
  
 Należy zauważyć, że uruchomiona usługa lub dowolnego rozszerzenia z hosta niezaufanego naruszeń zabezpieczeń. Ponadto należy pamiętać, że podczas otwierania <xref:System.ServiceModel.ServiceHost> w ramach personifikacji, aplikacja musi zapewnić, że użytkownik nie zaloguje się off, na przykład, buforując <xref:System.Security.Principal.WindowsIdentity> użytkownika.  
  
## <a name="see-also"></a>Zobacz także

- [Wymagania systemowe](../../../docs/framework/wcf/wcf-system-requirements.md)
- [Podstawowy cykl życia programowania](../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md)
- [Instrukcje: Hostowanie usługi WCF w programie IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Instrukcje: Hostowanie usługi WCF w WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)
- [Instrukcje: Hostowanie usługi WCF w usłudze Windows zarządzanych](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
