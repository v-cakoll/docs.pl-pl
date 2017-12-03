---
title: "Wdrażanie usługi WCF hostowanej przez Internetowe usługi informacyjne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9b19e111e11097cbb4b4af60ae0b28956a4a381
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Wdrażanie usługi WCF hostowanej przez Internetowe usługi informacyjne
Tworzenie i wdrażanie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi hostowanej w Internet Information Services (IIS) obejmuje następujące zadania:  
  
-   Upewnij się, że usługi IIS, ASP.NET, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składnika aktywacji są poprawnie zainstalowane i zarejestrowane.  
  
-   Tworzenie nowej aplikacji usług IIS lub ponowne użycie istniejących [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji.  
  
-   Tworzenie pliku svc [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
-   Wdrażanie implementacji usługi do aplikacji usług IIS.  
  
-   Skonfiguruj [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
 Aby uzyskać szczegółowy przewodnik tworzenia hostowanych przez usługi IIS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, zobacz [porady: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Upewnij się, że są usługi IIS, platformy ASP.NET i WCF zainstalowany i zarejestrowany  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], Usługi IIS i platformy ASP.NET musi być zainstalowana hostowanych przez usługi IIS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, aby mógł działać poprawnie. Procedury instalowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (jako część [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]), platformy ASP.NET i IIS się różnić w zależności od wersji systemu operacyjnego używany. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Instalowanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], zobacz [Instalator sieci Web platformy Microsoft .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=201185). Instrukcje dotyczące instalowania usług IIS można znaleźć w folderze [Instalowanie programu IIS](http://go.microsoft.com/fwlink/?LinkId=201188).  
  
 Proces instalacji [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] automatycznie rejestruje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] z programem IIS, jeśli usługi IIS znajduje się już na komputerze. Jeśli po zainstalowaniu usług IIS [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], dodatkowy krok jest wymagany do zarejestrowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] z usługami IIS i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Można to zrobić, w zależności od używanego systemu operacyjnego:  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], Windows 7 i [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]: Użyj [narzędzie rejestracji modelu ServiceModel (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) narzędzie do rejestrowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] z usługami IIS: Aby użyć tego narzędzia, wpisz **ServiceModelReg.exe /i /x** w Wiersz polecenia programu Visual Studio. Można otworzyć tego polecenia monit przez kliknięcie przycisku start, wybierając **wszystkie programy**, **programu Microsoft Visual Studio 2012**, **programu Visual Studio Tools**, i  **Wiersz polecenia programu Visual Studio**  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)]: Zainstaluj podskładnik Windows Communication Foundation aktywacji składników [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]. Aby to zrobić, w Panelu sterowania, kliknij przycisk **Dodaj lub usuń programy** , a następnie **Dodaj\/Usuń składniki systemu Windows**. Aktywuje **Kreator składników systemu Windows**.  
  
-   Windows 7:  
  
 Na koniec należy sprawdzić, czy program ASP.NET jest skonfigurowana do używania programu .NET Framework w wersji 4. Można to zrobić, uruchamiając narzędzie ASPNET_Regiis i — opcja. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Narzędzie rejestracji programu ASP.NET w usługach IIS](http://go.microsoft.com/fwlink/?LinkId=201186)  
  
## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Tworzenie nowej aplikacji usług IIS lub ponownego użycia istniejącej aplikacji ASP.NET  
 Hostowanych przez usługi IIS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi musi znajdować się wewnątrz aplikacji usług IIS. Można utworzyć nowej aplikacji usług IIS do hosta [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wyłącznie usług. Alternatywnie można wdrożyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi do istniejącej aplikacji, która obecnie prowadzi hosting [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] zawartości (takich jak strony .aspx i usług sieci Web ASP.NET [ASMX]). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]tych opcji, zobacz "hostingu WCF Side-by-Side ASP.NET" i "Hosting usług WCF usług w tryb zgodności ASP.NET" części [usługi WCF i platformy ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
 Należy pamiętać, że [!INCLUDE[iis601](../../../../includes/iis601-md.md)] i nowszych wersjach okresowego ponownego uruchamiania izolowanej zorientowane obiektowo programowania aplikacji. Wartość domyślna to 1740 minut. Maksymalna obsługiwana wartość to 71,582 minut. Ponowne uruchomienie, można wyłączyć. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]tę właściwość, zobacz [PeriodicRestartTime](http://go.microsoft.com/fwlink/?LinkId=109968).  
  
## <a name="create-an-svc-file-for-the-wcf-service"></a>Tworzenie pliku svc dla usługi WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usług hostowanych w usługach IIS są reprezentowane jako specjalne zawartości plików (SVC) wewnątrz aplikacji usług IIS. Ten model jest podobny do sposobu ASMX strony są reprezentowane wewnątrz aplikacji IIS jako plików .asmx. Zawiera w pliku svc [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-dyrektywę przetwarzania określonych ([@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)), która umożliwia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hostingu infrastruktury do aktywacji usług hostowanych w odpowiedzi na wiadomości przychodzących. Następująca instrukcja jest najbardziej typowych składni w pliku svc.  
  
```  
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>  
```  
  
 Składa się z [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy i jeden atrybut `Service`. Wartość `Service` atrybut jest języka wspólnego (CLR) typu nazwa pospolita implementacji usługi. Ta dyrektywa Using jest zasadniczo równoważne tworzenie hosta usługi przy użyciu następującego kodu.  
  
```  
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );  
```  
  
 Można również wykonać dodatkowej konfiguracji hostingu, takich jak tworzenie listy adres podstawowy usługi. Można również użyć niestandardowej <xref:System.ServiceModel.Activation.ServiceHostFactory> rozszerzenie dyrektywy do użycia z niestandardowe rozwiązania hostingu. Aplikacji programu IIS, które hostują [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług nie są odpowiedzialni za zarządzanie tworzeniem i okresem istnienia <xref:System.ServiceModel.ServiceHost> wystąpień. Zarządzanej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hosting infrastruktury tworzy niezbędne <xref:System.ServiceModel.ServiceHost> wystąpienie dynamicznie po odebraniu pierwszego żądania dla pliku svc. Wystąpienie nie jest zwalniany, dopóki albo jest ono zamknięte jawnie przez kod lub gdy aplikacja zostanie odtworzony.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Składnia dla plików SVC, zobacz [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).  
  
## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Wdrażanie implementacji usługi do aplikacji usług IIS  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usług hostowanych w usługach IIS, użyj tego samego modelu kompilacji dynamicznej jako [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]. Tylko jako z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], można wdrożyć kod implementacji hostowanych przez usługi IIS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług na kilka sposobów, w różnych lokalizacjach, w następujący sposób:  
  
-   Jako plik dll prekompilowany znajduje się w globalnej pamięci podręcznej zestawów (GAC) lub w katalogu \bin aplikacji. Prekompilowane pliki binarne, nie zostaną zaktualizowane wdrażania nowej wersji biblioteki klas.  
  
-   Ponieważ pliki źródłowe cofanie skompilowanych znajduje się w katalogu \App_Code aplikacji. Podczas przetwarzania żądania pierwszej aplikacji dynamicznie wymagane są plików źródłowych znajdujących się w tym katalogu. Wszystkie zmiany do plików w katalogu \App_Code spowodować całej aplikacji ponownego przetworzenia i ponownie kompilowana po odebraniu żądania dalej.  
  
-   Cofanie skompilowanego kodu wprowadzanych bezpośrednio w pliku svc. W kodzie można również wbudowanej znajduje się w pliku svc usługi, po zakończeniu @ServiceHost dyrektywy. Wszelkie zmiany kodu wbudowanego spowodować aplikacji ponownego przetworzenia i ponownie kompilowana po odebraniu żądania dalej.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] modelu kompilacji, zobacz [omówienie kompilacji programu ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94773).  
  
## <a name="configure-the-wcf-service"></a>Konfigurowanie usługi WCF  
 Hostowanych przez usługi IIS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi przechowywania ich konfiguracji w pliku Web.config aplikacji. Usługi hostowanych przez usługi IIS używają tej samej składni jak i elementy konfiguracji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług hostowanych poza usług IIS. Jednak następujące ograniczenia są unikatowe dla środowiska hostingu usług IIS:  
  
-   Adresów bazowych usług hostowanych przez usługi IIS.  
  
-   Aplikacjom obsługującym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi poza usług IIS można kontrolować adres podstawowy usługi one hosta przekazując zestaw podstawowy adres identyfikatorów URI <xref:System.ServiceModel.ServiceHost> konstruktora lub poprzez świadczenie [ \<hosta >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) element w konfiguracji usługi. Usług hostowanych w usługach IIS nie mają możliwość kontrolowania ich adres podstawowy; adres podstawowy usługi hostowanych przez usługi IIS jest adresem jego pliku svc.  
  
### <a name="endpoint-addresses-for-iis-hosted-services"></a>Adresy punktów końcowych dla usług hostowanych przez usługi IIS  
 Podczas udostępniania w usługach IIS, adresy punktów końcowych zawsze są traktowane jako względem adresu w pliku SVC, który reprezentuje usługę. Na przykład jeśli podstawowy adres [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa jest http://localhost/Application1/MyService.svc przy użyciu następującej konfiguracji punktu końcowego.  
  
```xml  
<endpoint address="anotherEndpoint" .../>  
```  
  
 Zapewnia to punktu końcowego, który jest osiągalny w "http://localhost/Application1/MyService.svc/anotherEndpoint".  
  
 Podobnie, używającą pusty ciąg jako adres względny elementu konfiguracji punktu końcowego zawiera punkt końcowy w http://localhost/Application1/MyService.svc, czyli adres podstawowy.  
  
```xml  
<endpoint address="" ... />  
```  
  
 Należy zawsze używać punktu końcowego względne adresy dla punktów końcowych usług hostowanych przez usługi IIS. Podając w pełni kwalifikowany adres punktu końcowego (na przykład http://localhost/MyService.svc) może prowadzić do błędów w ramach wdrożenia usługi, jeśli adres punktu końcowego nie wskazuje aplikacji usług IIS obsługującym usługę Udostępnianie punktu końcowego. Przy użyciu punktu końcowego względne adresy dla usług hostowanych pozwala uniknąć tych potencjalnych konfliktów.  
  
### <a name="available-transports"></a>Transporty dostępne  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usługi obsługiwane w wersji 5.1 usług IIS i [!INCLUDE[iis601](../../../../includes/iis601-md.md)] są ograniczone do komunikacji oparte na protokole HTTP. Na tych platformach usług IIS konfigurowanie usług hostingowych umożliwia powiązanie protokołu HTTP powoduje wystąpienie błędu podczas aktywacji usługi. Aby uzyskać [!INCLUDE[iisver](../../../../includes/iisver-md.md)], obsługiwanych transportów obejmują HTTP, Net.TCP Net.Pipe, Net.MSMQ i msmq.formatname dla zapewnienia zgodności z istniejącymi aplikacjami usługi MSMQ.  
  
### <a name="http-transport-security"></a>Zabezpieczenia transportu HTTP  
 Hostowanych przez usługi IIS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług można wykorzystać HTTP transportu zabezpieczeń (na przykład schematy HTTPS i HTTP uwierzytelniania, takie jak Basic, szyfrowane i zintegrowane uwierzytelnianie systemu Windows), tak długo, jak obsługuje katalog wirtualny usług IIS, który zawiera usługi te ustawienia. Ustawienia zabezpieczeń transportu HTTP w powiązaniu hostowany punkt końcowy musi odpowiadać ustawienia zabezpieczeń transportu na katalog wirtualny usług IIS, która go zawiera.  
  
 Na przykład [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punkt końcowy jest skonfigurowana do używania uwierzytelniania digest protokołu HTTP musi znajdować się w katalogu wirtualnym usług IIS, skonfigurowanej na potrzeby uwierzytelniania szyfrowanego protokołu HTTP. Niedopasowane kombinacji ustawień usług IIS i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego ustawienia doprowadzi do błędu podczas aktywacji usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Hostowanie przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Internetowe usługi informacyjne najlepsze rozwiązania dotyczące hostowania](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
