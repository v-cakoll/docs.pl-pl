---
title: Wdrażanie usługi WCF hostowanej przez Internetowe usługi informacyjne
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: b2b58de703a0864ac0666cb4738a95726e28bcaf
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740104"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Wdrażanie usługi WCF hostowanej przez Internetowe usługi informacyjne
Tworzenia i wdrażania usług Windows Communication Foundation (WCF), który znajduje się w Internet Information Services (IIS) obejmuje następujące zadania:  
  
-   Upewnij się, że usługi IIS, ASP.NET, usługi WCF i składników aktywacji programu WCF jest poprawnie zainstalowany i zarejestrowany.  
  
-   Tworzenie nowej aplikacji usług IIS lub ponownego użycia istniejącej [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji.  
  
-   Utwórz plik .svc dla usługi WCF.  
  
-   Wdrażanie implementacji usługi do aplikacji usług IIS.  
  
-   Konfigurowanie usługi WCF.  
  
 Aby uzyskać szczegółowy przewodnik dotyczący tworzenia usługi WCF hostowanej przez usługi IIS, zobacz [instrukcje: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Upewnij się, że usługi IIS, ASP.NET i WCF poprawnie zainstalowany i zarejestrowany  
 Musi być zainstalowany WCF, usług IIS i platformy ASP.NET dla usługi WCF hostowanej przez usługi IIS do poprawnego działania. Procedury instalowania usługi WCF (jako część [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]), platformy ASP.NET i IIS różnią się w zależności od używanej wersji systemu operacyjnego. Aby uzyskać więcej informacji o instalowaniu programu WCF i [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], zobacz [Instalator sieci Web programu Microsoft .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=201185). Instrukcje dotyczące instalowania usług IIS, można znaleźć w folderze [Instalowanie programu IIS](https://go.microsoft.com/fwlink/?LinkId=201188).  
  
 Proces instalacji [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] automatycznie rejestruje WCF za pomocą programu IIS, jeśli usługi IIS znajduje się już na komputerze. Jeśli po zainstalowaniu usług IIS [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], dodatkowy krok jest wymagany do zarejestrowania WCF za pomocą programu IIS i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Można to zrobić w następujący sposób, w zależności od używanego systemu operacyjnego:  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], Windows 7, a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]: Użyj [narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) narzędzie do rejestracji programu WCF za pomocą programu IIS: Aby użyć tego narzędzia, wpisz **ServiceModelReg.exe /i /x** w programie Visual Studio Wiersz polecenia. Można otworzyć tego polecenia, w wierszu przez kliknięcie przycisku start, wybierając **wszystkie programy**, **Microsoft Visual Studio 2012**, **Visual Studio Tools**, i  **Wiersz polecenia programu Visual Studio**  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)]: Instalowanie składników aktywacji programu Windows Communication Foundation podskładnik [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]. Aby to zrobić, w Panelu sterowania, kliknij przycisk **apletu Dodaj lub usuń programy** i następnie **Dodaj\//usuwanie składników Windows**. Aktywuje **Kreator składników stron Windows**.  
  
-   Windows 7:  
  
 Na koniec należy sprawdzić, czy program ASP.NET jest skonfigurowany do używania programu .NET Framework w wersji 4. Możesz to zrobić, uruchamiając narzędzie ASPNET_Regiis za pomocą – i opcji. Aby uzyskać więcej informacji, zobacz [narzędzie rejestracji usług IIS platformy ASP.NET](https://go.microsoft.com/fwlink/?LinkId=201186)  
  
## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Tworzenie nowej aplikacji usług IIS lub ponowne użycie istniejącej aplikacji ASP.NET  
 Usługi WCF hostowanych przez usługi IIS muszą znajdować się wewnątrz aplikacji IIS. Można utworzyć nowej aplikacji usług IIS do hostowania usług WCF wyłącznie. Alternatywnie, można wdrożyć usługi WCF do istniejącej aplikacji, który jest już hostem [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] zawartości (takiej jak strony aspx oraz usług sieci Web platformy ASP.NET [ASMX]). Aby uzyskać więcej informacji o tych opcjach, zobacz "Hosting usług WCF Side-by-Side za pomocą platformy ASP.NET" i "Hosting usług WCF w trybie zgodności ASP.NET" sekcje w [usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
 Należy pamiętać, że [!INCLUDE[iis601](../../../../includes/iis601-md.md)] i nowszych wersjach okresowego ponownego uruchamiania izolowanych aplikacji programowania obiektowego. Wartość domyślna to 1740 minut. Wartość maksymalna obsługiwana jest 71,582 minut. Można wyłączyć ponowne uruchomienie. Aby uzyskać więcej informacji na temat tej właściwości, zobacz [PeriodicRestartTime](https://go.microsoft.com/fwlink/?LinkId=109968).  
  
## <a name="create-an-svc-file-for-the-wcf-service"></a>Utwórz plik .svc dla usługi WCF  
 Usługi WCF hostowane w usługach IIS są reprezentowane jako specjalne zawartości plików (SVC) wewnątrz aplikacji usług IIS. Model ten jest podobny do sposobu ASMX strony są reprezentowane w aplikacji usług IIS jako plików .asmx. Plik .svc zawiera dyrektywy przetwarzania specyficznego dla usługi WCF ([\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)) umożliwiająca WCF obsługującego infrastrukturę do aktywowania usługi hostowanej w odpowiedzi na wiadomości przychodzące. Najczęściej składnia dla plików .svc jest w następującej instrukcji.  
  
```  
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>  
```  
  
 Składa się z [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy i jeden atrybut `Service`. Wartość `Service` atrybut jest wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) Nazwa typu implementacji usługi. Ta dyrektywa Using odpowiada zasadzie tworzenia hosta usługi, używając następującego kodu.  
  
```csharp  
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );  
```  
  
 Można również wykonać dodatkowej konfiguracji hostingu, takich jak tworzenie listy adresami podstawowymi dla usługi. Można też używać niestandardowego <xref:System.ServiceModel.Activation.ServiceHostFactory> rozszerzenie dyrektywy do użytku z niestandardowych rozwiązań hostingu. Aplikacje usług IIS, które prowadzą hosting usług WCF nie są odpowiedzialni za zarządzanie tworzeniem i okresem istnienia <xref:System.ServiceModel.ServiceHost> wystąpień. Zarządzana infrastruktura WCF hostingu tworzy niezbędne <xref:System.ServiceModel.ServiceHost> wystąpienia dynamicznie po odebraniu pierwszego żądania dla pliku .svc. Wystąpienie jest zwalniany dopiero to wystąpienie jest zamykane jawnie przez kod lub gdy aplikacja zostanie odtworzony.  
  
 Aby uzyskać więcej informacji na temat składni plików .svc zobacz [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).  
  
## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Wdrażanie implementacji usługi do aplikacji usług IIS  
 Usługi WCF hostowane w usługach IIS, użyj tego samego modelu kompilacji dynamicznej w postaci [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]. Podobnie jak [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], kod implementacji usługi WCF hostowanej przez usługi IIS na kilka sposobów, w różnych miejscach, można wdrożyć w następujący sposób:  
  
-   Zgodnie z plikiem dll wstępnie skompilowanym znajduje się w globalnej pamięci podręcznej zestawów (GAC) lub w katalogu \bin aplikacji. Wstępnie skompilowane pliki binarne nie są aktualizowane, dopóki nie wdrożono nową wersję biblioteki klas.  
  
-   Ponieważ pliki źródłowe nie skompilowanego znajduje się w katalogu \App_Code aplikacji. Pliki źródłowe, znajduje się w tym katalogu wymaganych dynamicznie podczas przetwarzania żądania pierwszej aplikacji. Wszelkie zmiany do plików w katalogu \App_Code spowodować całej aplikacji do odtwarzania i ponownie kompilowane, gdy zostanie odebrane żądanie dalej.  
  
-   Ponieważ nie skompilowanego kodu są umieszczone bezpośrednio w pliku svc. Kod implementacji można również bezpośrednio znajduje się w pliku .svc usługi, po \@dyrektywy ServiceHost. Wszelkie zmiany kodu wbudowanego spowodować, że aplikacja do odtwarzania i ponownie kompilowane, gdy zostanie odebrane żądanie dalej.  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] modelu kompilacji, zobacz [omówienie kompilacji programu ASP.NET](https://go.microsoft.com/fwlink/?LinkId=94773).  
  
## <a name="configure-the-wcf-service"></a>Konfigurowanie usługi WCF  
 Usługi WCF hostowanych przez usługi IIS przechowywania ich konfiguracji w pliku Web.config aplikacji. Usług hostowanych przez usługi IIS korzystają z tych samych elementów konfiguracji i składni, jako usługi WCF hostowane poza usługą IIS. Jednak następujące ograniczenia są unikatowe dla środowiska macierzystego w usługach IIS:  
  
-   Bazowy adresy dla usług hostowanych przez usługi IIS.  
  
-   Aplikacje, hostingu usług WCF poza programem IIS kontrolować adres podstawowy usługi ich obsługi, przekazując zestaw podstawowy adres identyfikatorów URI <xref:System.ServiceModel.ServiceHost> konstruktora lub poprzez świadczenie [ \<host >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) elementu w konfiguracji usługi. Usług hostowanych w usługach IIS ma możliwość kontrolowania ich adres bazowy; adres podstawowy usługi hostowanych przez usługi IIS jest adres jego pliku .svc.  
  
### <a name="endpoint-addresses-for-iis-hosted-services"></a>Adresy punktów końcowych usług hostowanych przez usługi IIS  
 W przypadku hostowania w usługach IIS, adresy punktów końcowych są zawsze traktowane względem adresu pliku SVC, który reprezentuje usługę. Na przykład, jeśli podstawowy adres usługi WCF http://localhost/Application1/MyService.svc o następującej konfiguracji punktu końcowego.  
  
```xml  
<endpoint address="anotherEndpoint" .../>  
```  
  
 Zapewnia to punkt końcowy, który można z Tobą skontaktować w "http://localhost/Application1/MyService.svc/anotherEndpoint".  
  
 Podobnie, elementu konfiguracji punktu końcowego używającej pusty ciąg jako względny adres udostępnia punkt końcowy dostępny na http://localhost/Application1/MyService.svc, czyli adres podstawowy.  
  
```xml  
<endpoint address="" ... />  
```  
  
 Należy zawsze używać punktu końcowego względnych adresów dla punktów końcowych usług hostowanych przez usługi IIS. Podając w pełni kwalifikowany adres punktu końcowego (na przykład http://localhost/MyService.svc) może prowadzić do błędów we wdrożeniu usługi, jeśli adres punktu końcowego nie wskazuje aplikacji usług IIS obsługującym usługę Udostępnianie punktu końcowego. Za pomocą adresy punktów końcowych względną dla usług hostowanych pozwala uniknąć tych potencjalnych konfliktów.  
  
### <a name="available-transports"></a>Dostępne transportu  
 Usługi WCF hostowane w usługach IIS 5.1 i [!INCLUDE[iis601](../../../../includes/iis601-md.md)] są ograniczone do komunikacji w opartych na protokole HTTP. Na tych platformach usług IIS konfigurowania usługi hostowanej, aby użyć powiązania protokołu HTTP powoduje wystąpienie błędu podczas aktywacji usługi. Aby uzyskać [!INCLUDE[iisver](../../../../includes/iisver-md.md)], obsługiwanych transportów obejmują HTTP, Net.TCP, Net.Pipe, Net.MSMQ i msmq.formatname dla zapewnienia zgodności z istniejącymi aplikacjami usługi MSMQ.  
  
### <a name="http-transport-security"></a>Zabezpieczenia transportu HTTP  
 Usługi WCF hostowanych przez usługi IIS można skorzystać z protokołu HTTP transport security (na przykład HTTPS i HTTP schematy uwierzytelniania, takich jak podstawowe, szyfrowane i zintegrowane uwierzytelnianie Windows), tak długo, jak wirtualny katalog IIS, które zawiera tę usługę, obsługuje te Ustawienia. Ustawienia zabezpieczenia transportu HTTP w powiązaniu hostowany punkt końcowy musi odpowiadać ustawienia zabezpieczenia transportu na katalog wirtualny usług IIS, która go zawiera.  
  
 Na przykład punktu końcowego WCF skonfigurowany do używania uwierzytelniania szyfrowanego HTTP musi znajdować się w wirtualny katalog IIS, na który również jest skonfigurowane na potrzeby uwierzytelniania szyfrowanego protokołu HTTP. Niedopasowane kombinacje ustawień usług IIS i ustawienia punktu końcowego WCF powodować wystąpienie błędu podczas aktywacji usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Hostowanie przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Windows Server AppFabric funkcje hostingu](https://go.microsoft.com/fwlink/?LinkId=201276)
