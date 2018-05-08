---
title: Wdrażanie usługi WCF hostowanej przez Internetowe usługi informacyjne
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 59f18d8487deb52f5ecb5b5c814ec9bdbc74e2cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Wdrażanie usługi WCF hostowanej przez Internetowe usługi informacyjne
Tworzenie i wdrażanie usługi Windows Communication Foundation (WCF), którą w Internet Information Services (IIS) obejmuje następujące zadania:  
  
-   Upewnij się, że usługi IIS, platformy ASP.NET, WCF i składników aktywacji programu WCF jest prawidłowo zainstalowany i zarejestrowany.  
  
-   Tworzenie nowej aplikacji usług IIS lub ponowne użycie istniejących [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji.  
  
-   Utwórz plik .svc dla usługi WCF.  
  
-   Wdrażanie implementacji usługi do aplikacji usług IIS.  
  
-   Konfigurowanie usługi WCF.  
  
 Aby uzyskać szczegółowe wskazówki dotyczące tworzenia usługi WCF hostowanych przez usługi IIS, zobacz [porady: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Upewnij się, że są usługi IIS, platformy ASP.NET i WCF zainstalowany i zarejestrowany  
 Usługi WCF, usług IIS i platformy ASP.NET muszą być zainstalowane dla usług WCF hostowanych przez usługi IIS do poprawnego działania. Procedury instalowania usługi WCF (jako część [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]), platformy ASP.NET i IIS się różnić w zależności od wersji systemu operacyjnego używany. Aby uzyskać więcej informacji o instalowaniu usług WCF i [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], zobacz [Instalator sieci Web platformy Microsoft .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=201185). Instrukcje dotyczące instalowania usług IIS można znaleźć w folderze [Instalowanie programu IIS](http://go.microsoft.com/fwlink/?LinkId=201188).  
  
 Proces instalowania [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] automatycznie rejestruje WCF z programem IIS, jeśli usługi IIS znajduje się już na komputerze. Jeśli po zainstalowaniu usług IIS [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], dodatkowe krok jest wymagany do zarejestrowania WCF z usługami IIS i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Można to zrobić, w zależności od używanego systemu operacyjnego:  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], Windows 7 i [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]: Użyj [narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) narzędzie do rejestracji WCF w usłudze IIS: Aby użyć tego narzędzia, wpisz **ServiceModelReg.exe /i /x** w programie Visual Studio Wiersz polecenia. Można otworzyć tego polecenia monit przez kliknięcie przycisku start, wybierając **wszystkie programy**, **programu Microsoft Visual Studio 2012**, **programu Visual Studio Tools**, i  **Wiersz polecenia programu Visual Studio**  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)]: Zainstaluj podskładnik Windows Communication Foundation aktywacji składników [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]. Aby to zrobić, w Panelu sterowania, kliknij przycisk **Dodaj lub usuń programy** , a następnie **Dodaj\/Usuń składniki systemu Windows**. Aktywuje **Kreator składników systemu Windows**.  
  
-   Windows 7:  
  
 Na koniec należy sprawdzić, czy program ASP.NET jest skonfigurowana do używania programu .NET Framework w wersji 4. Można to zrobić, uruchamiając narzędzie ASPNET_Regiis i — opcja. Aby uzyskać więcej informacji, zobacz [narzędzie rejestracji programu ASP.NET usług IIS](http://go.microsoft.com/fwlink/?LinkId=201186)  
  
## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Tworzenie nowej aplikacji usług IIS lub ponownego użycia istniejącej aplikacji ASP.NET  
 Usługi WCF hostowanych przez usługi IIS muszą znajdować się wewnątrz aplikacji usług IIS. Można utworzyć nowej aplikacji usług IIS do obsługi usług WCF wyłącznie. Alternatywnie można wdrożyć usługi WCF do istniejącej aplikacji, która obecnie prowadzi hosting [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] zawartości (takich jak strony .aspx i usług sieci Web ASP.NET [ASMX]). Aby uzyskać więcej informacji o tych opcjach, zobacz "hostingu WCF Side-by-Side ASP.NET" i "Hostingu usług WCF w trybie zgodności ASP.NET" sekcje w [usługi WCF i platformy ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
 Należy pamiętać, że [!INCLUDE[iis601](../../../../includes/iis601-md.md)] i nowszych wersjach okresowego ponownego uruchamiania izolowanej zorientowane obiektowo programowania aplikacji. Wartość domyślna to 1740 minut. Maksymalna obsługiwana wartość to 71,582 minut. Ponowne uruchomienie, można wyłączyć. Aby uzyskać więcej informacji na temat tej właściwości, zobacz [PeriodicRestartTime](http://go.microsoft.com/fwlink/?LinkId=109968).  
  
## <a name="create-an-svc-file-for-the-wcf-service"></a>Tworzenie pliku svc dla usługi WCF  
 Usługi WCF hostowanej w programie IIS są reprezentowane jako specjalne zawartości plików (SVC) wewnątrz aplikacji usług IIS. Ten model jest podobny do sposobu ASMX strony są reprezentowane wewnątrz aplikacji IIS jako plików .asmx. Pliku svc zawiera dyrektywę przetwarzania specyficzne dla usługi WCF ([@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)), która umożliwia WCF obsługujący infrastruktury do aktywacji usług hostowanych w odpowiedzi na wiadomości przychodzących. Następująca instrukcja jest najbardziej typowych składni w pliku svc.  
  
```  
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>  
```  
  
 Składa się z [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy i jeden atrybut `Service`. Wartość `Service` atrybut jest języka wspólnego (CLR) typu nazwa pospolita implementacji usługi. Ta dyrektywa Using jest zasadniczo równoważne tworzenie hosta usługi przy użyciu następującego kodu.  
  
```  
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );  
```  
  
 Można również wykonać dodatkowej konfiguracji hostingu, takich jak tworzenie listy adres podstawowy usługi. Można również użyć niestandardowej <xref:System.ServiceModel.Activation.ServiceHostFactory> rozszerzenie dyrektywy do użycia z niestandardowe rozwiązania hostingu. Aplikacji programu IIS, które prowadzą hosting usług WCF nie są odpowiedzialni za zarządzanie tworzeniem i okresem istnienia <xref:System.ServiceModel.ServiceHost> wystąpień. Zarządzane WCF infrastruktury hostingu tworzy niezbędne <xref:System.ServiceModel.ServiceHost> wystąpienie dynamicznie po odebraniu pierwszego żądania dla pliku svc. Wystąpienie nie jest zwalniany, dopóki albo jest ono zamknięte jawnie przez kod lub gdy aplikacja zostanie odtworzony.  
  
 Aby uzyskać więcej informacji na temat składni plików .svc zobacz [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).  
  
## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Wdrażanie implementacji usługi do aplikacji usług IIS  
 Usługi WCF hostowanej w programie IIS korzystania z tego samego modelu kompilacji dynamicznej jako [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]. Tylko jako z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], wdrożyć kod implementacji usługi WCF hostowanych przez usługi IIS na kilka sposobów, w różnych lokalizacjach, w następujący sposób:  
  
-   Jako plik dll prekompilowany znajduje się w globalnej pamięci podręcznej zestawów (GAC) lub w katalogu \bin aplikacji. Prekompilowane pliki binarne, nie zostaną zaktualizowane wdrażania nowej wersji biblioteki klas.  
  
-   Ponieważ pliki źródłowe cofanie skompilowanych znajduje się w katalogu \App_Code aplikacji. Podczas przetwarzania żądania pierwszej aplikacji dynamicznie wymagane są plików źródłowych znajdujących się w tym katalogu. Wszystkie zmiany do plików w katalogu \App_Code spowodować całej aplikacji ponownego przetworzenia i ponownie kompilowana po odebraniu żądania dalej.  
  
-   Cofanie skompilowanego kodu wprowadzanych bezpośrednio w pliku svc. W kodzie można również wbudowanej znajduje się w pliku svc usługi, po zakończeniu @ServiceHost dyrektywy. Wszelkie zmiany kodu wbudowanego spowodować aplikacji ponownego przetworzenia i ponownie kompilowana po odebraniu żądania dalej.  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] modelu kompilacji, zobacz [omówienie kompilacji programu ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94773).  
  
## <a name="configure-the-wcf-service"></a>Konfigurowanie usługi WCF  
 Usługi WCF hostowanych przez usługi IIS przechowywania ich konfiguracji w pliku Web.config aplikacji. Usług hostowanych przez usługi IIS korzystają z tej samej elementy konfiguracji i składni jako usługi WCF hostowanej poza usług IIS. Jednak następujące ograniczenia są unikatowe dla środowiska hostingu usług IIS:  
  
-   Adresów bazowych usług hostowanych przez usługi IIS.  
  
-   Aplikacje hostingu usług WCF poza usług IIS można kontrolować adres podstawowy usługi one hosta przez przekazanie zestaw podstawowy adres identyfikatorów URI <xref:System.ServiceModel.ServiceHost> konstruktora lub poprzez świadczenie [ \<hosta >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) element konfiguracji usługi. Usług hostowanych w usługach IIS nie mają możliwość kontrolowania ich adres podstawowy; adres podstawowy usługi hostowanych przez usługi IIS jest adresem jego pliku svc.  
  
### <a name="endpoint-addresses-for-iis-hosted-services"></a>Adresy punktów końcowych dla usług hostowanych przez usługi IIS  
 Podczas udostępniania w usługach IIS, adresy punktów końcowych zawsze są traktowane jako względem adresu w pliku SVC, który reprezentuje usługę. Na przykład, jeśli adres podstawowy usługi WCF jest http://localhost/Application1/MyService.svc przy użyciu następującej konfiguracji punktu końcowego.  
  
```xml  
<endpoint address="anotherEndpoint" .../>  
```  
  
 Zapewnia to punktu końcowego, który można uzyskać pod adresem "http://localhost/Application1/MyService.svc/anotherEndpoint".  
  
 Podobnie elementu konfiguracji punktu końcowego używającej ciąg pusty adres względny zawiera punkt końcowy w http://localhost/Application1/MyService.svc, czyli adres podstawowy.  
  
```xml  
<endpoint address="" ... />  
```  
  
 Należy zawsze używać punktu końcowego względne adresy dla punktów końcowych usług hostowanych przez usługi IIS. Podając w pełni kwalifikowany adres punktu końcowego (na przykład http://localhost/MyService.svc) może prowadzić do błędów w ramach wdrożenia usługi, jeśli adres punktu końcowego nie wskazuje aplikacji usług IIS obsługującym usługę Udostępnianie punktu końcowego. Przy użyciu punktu końcowego względne adresy dla usług hostowanych pozwala uniknąć tych potencjalnych konfliktów.  
  
### <a name="available-transports"></a>Transporty dostępne  
 Usługi WCF hostowanej w wersji 5.1 usług IIS i [!INCLUDE[iis601](../../../../includes/iis601-md.md)] są ograniczone do komunikacji oparte na protokole HTTP. Na tych platformach usług IIS konfigurowanie usług hostingowych umożliwia powiązanie protokołu HTTP powoduje wystąpienie błędu podczas aktywacji usługi. Aby uzyskać [!INCLUDE[iisver](../../../../includes/iisver-md.md)], obsługiwanych transportów obejmują HTTP, Net.TCP Net.Pipe, Net.MSMQ i msmq.formatname dla zapewnienia zgodności z istniejącymi aplikacjami usługi MSMQ.  
  
### <a name="http-transport-security"></a>Zabezpieczenia transportu HTTP  
 Usługi WCF hostowanych przez usługi IIS można wykorzystać HTTP transportu zabezpieczeń (na przykład schematy HTTPS i HTTP uwierzytelniania, takie jak Basic, szyfrowane i zintegrowane uwierzytelnianie systemu Windows) katalog wirtualny usług IIS, który zawiera usługę obsługuje te Ustawienia. Ustawienia zabezpieczeń transportu HTTP w powiązaniu hostowany punkt końcowy musi odpowiadać ustawienia zabezpieczeń transportu na katalog wirtualny usług IIS, która go zawiera.  
  
 Na przykład punktu końcowego WCF skonfigurowana do używania uwierzytelniania digest protokołu HTTP musi znajdować się w katalogu wirtualnym usług IIS, skonfigurowanej na potrzeby uwierzytelniania szyfrowanego protokołu HTTP. Niedopasowane kombinacji ustawień usług IIS i punktu końcowego WCF spowodować błąd podczas aktywacji usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Hostowanie przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
