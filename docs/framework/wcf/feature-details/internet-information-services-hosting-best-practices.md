---
title: Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 119f14df9d46883a33272903558d83128501b293
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495765"
---
# <a name="internet-information-services-hosting-best-practices"></a>Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych
W tym temacie przedstawiono najlepsze rozwiązania dotyczące hostingu usług Windows Communication Foundation (WCF).  
  
## <a name="implementing-wcf-services-as-dlls"></a>Wdrażanie usługi WCF w postaci bibliotek DLL  
 Wdrażanie usługi WCF usługi jako plik DLL, która została wdrożona w katalogu \bin aplikacji sieci Web umożliwia ponowne użycie usługi poza modelu aplikacji sieci Web, na przykład w środowisku testowym, który nie może być wdrożony Internet Information Services (IIS).  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>Hosty usługi w aplikacjach hostowanych przez usługi IIS  
 Nie należy używać imperatywnych hosta samodzielnego interfejsów API do Utwórz nowe hosty usługi tego nasłuchiwania na metod transportu sieciowego nieobsługiwane natywnie przez usługi IIS, środowisko macierzyste (na przykład [!INCLUDE[iis601](../../../../includes/iis601-md.md)] do hostów protokołu TCP usługi, ponieważ komunikacji protokołu TCP nie jest obsługiwany macierzyście na [!INCLUDE[iis601](../../../../includes/iis601-md.md)]). Ta metoda nie jest zalecane. Hosty usługi utworzone imperatively nie są znane w środowisku hostingu usług IIS. Punkt krytyczne jest, że przetwarzanie programach imperatively utworzony usług nie uwzględniono kwestie przez usługi IIS podczas określania, czy obsługi puli aplikacji jest w stanie bezczynności. Wynik jest aplikacji, które mają takie imperatively utworzone hosty środowisku hostingu usług IIS i usuwa agresywnie procesy hosta usług IIS.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>Identyfikatory URI i hostowanych przez usługi IIS punkty końcowe  
 Punktów końcowych dla usług hostowanych przez usługi IIS powinny być skonfigurowane przy użyciu względne identyfikatory Uniform Resource (URI), nie bezwzględne adresów. Gwarantuje to, że adres punktu końcowego znajduje się w zestawie adresów URI, które należą do obsługi aplikacji i zapewnia, że aktywacji opartej na komunikatach się stanie, zgodnie z oczekiwaniami.  
  
## <a name="state-management-and-process-recycling"></a>Stan zarządzania i odtwarzanie procesów  
 Środowisko hostingu usług IIS jest zoptymalizowana pod kątem usług, które nie obsługują stanu lokalnego w pamięci. Usługi IIS odtwarza proces hosta w odpowiedzi na szereg zdarzeń wewnętrznych i zewnętrznych, powoduje każdy stan volatile przechowywane wyłącznie w pamięci, aby zostać utracone. Usług hostowanych w usługach IIS należy przechowywać stanu zewnętrznych do procesu (na przykład w bazie danych) lub w pamięci podręcznej w pamięci, które mogą być łatwo ponownego utworzenia, jeśli aplikacja Odtwórz zdarzeń występuje.  
  
> [!NOTE]
>  Protokoły usług WCF jest używana dla komunikatu warstwę niezawodności i zabezpieczeń użyj volatile stanu w pamięci. Niezawodne sesje WCF i sesji zabezpieczeń może zakończyć nieoczekiwanie z powodu odtwarzania aplikacji. Aplikacje hostowanych przez usługi IIS należy używać tych protokołów albo zależy od czegoś innego niż klucza sesji wprowadzone do usługi WCF w celu korelowanie stanu warstwy aplikacji (na przykład konstrukcja warstwy aplikacji lub korelacji niestandardowy nagłówek) lub wyłącz Odtwarzanie dla aplikacji hostowanej procesów usług IIS.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Optymalizowanie wydajności w scenariuszach warstwy środkowej  
 Aby uzyskać optymalną wydajność w *scenariusza warstwy środkowej*— to usługa, która uwidacznia innych usług w odpowiedzi na komunikaty przychodzące — raz wystąpienia klienta usługi WCF do zdalnej usługi i użyć go ponownie w wielu przychodzące żądania. Tworzenie wystąpień klienci usługi WCF jest kosztowna operacja względem co wywołanie w istniejącym wystąpieniu klienta usługi i scenariusze warstwy środkowej okazuje wzrost wydajności różne przez buforowanie żądań klientów zdalnych. Klienci usługi WCF są bezpieczne wątkowo, więc nie można zsynchronizować dostęp do klienta przez wiele wątków.  
  
 Scenariusze warstwy środkowej również utworzyć różne wzrost wydajności przy użyciu asynchronicznej interfejsów API generowanych przez `svcutil /a` opcji. `/a` Opcji powoduje, że [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania `BeginXXX/EndXXX` metod dla każdej operacji usługi, dzięki czemu potencjalnie długotrwałe wywołania usługi zdalnego ma zostać wykonane na wątki w tle.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>Usługi WCF w scenariuszach wieloadresowego lub wielu nazwanego  
 Można wdrożyć usługi WCF wewnątrz farmę serwerów sieci Web usług IIS, gdy zestaw komputerów, używają tej samej nazwy zewnętrznych (takich jak http://www.contoso.com) , ale są indywidualnie adresowane przez różne nazwy hostów (na przykład http://www.contoso.com może kierować ruch do dwóch różnych maszyn o nazwie http://machine1.internal.contoso.com i http://machine2.internal.contoso.com). Ten scenariusz wdrażania jest w pełni obsługiwany przez usługi WCF, ale wymaga specjalnej konfiguracji witryny sieci Web usług IIS hosting usług WCF do wyświetlenia poprawna nazwa hosta (zewnętrzne) w metadanych usługi (Web Services Description Language).  
  
 Aby upewnić się, czy prawidłowa nazwa hosta jest wyświetlany w metadanych usługi WCF generuje, konfigurowania tożsamości domyślnej witryny sieci Web usług IIS, który jest hostem usług WCF do użycia jawna nazwa hosta. Na przykład komputery, które znajdują się wewnątrz farmy www.contoso.com powinien używać powiązania witryny usług IIS z *:80:www.contoso.com dla protokołu HTTP i \*: 443:www.contoso.com dla protokołu HTTPS.  
  
 Powiązania witryny sieci Web usług IIS można skonfigurować za pomocą przystawki usług IIS programu Microsoft Management Console (MMC).  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Pule aplikacji uruchomionych w różnych kontekstów użytkownika zastąpić zestawy z innych kont w folderze tymczasowym  
 Aby upewnić się, że pule aplikacji uruchomionych w różnych kontekstów użytkownika nie można zastąpić zestawy z innych kont, w tymczasowym [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pliki z folderu, użyj różnych tożsamości i foldery tymczasowe dla różnych aplikacji. Na przykład, jeśli masz dwie /Application1 aplikacji wirtualnych i / Aplikacja2, możesz utworzyć dwie pule aplikacji, A i B, z dwóch różnych tożsamości. Puli aplikacji, A można uruchomić tożsamość użytkownika w jednym (Użytkownik1) podczas, gdy pula aplikacji B może działać w ramach innego tożsamości użytkownika (Użytkownik2) oraz skonfigurować /Application1 A użycia i /Application2, aby użyć B.  
  
 W pliku Web.config, można skonfigurować w folderze tymczasowym przy użyciu \< system.web/compilation/@tempFolder>. Dla /Application1 może być "c:\tempForUser1" i w Aplikacja2 może być "c:\tempForUser2". Przyznać odpowiednie uprawnienia do zapisu w tych folderach dwóch tożsamości.  
  
 Następnie Użytkownik2 nie można zmienić folder generowania kodu dla /application2 (w obszarze c:\tempForUser1).  
  
## <a name="enabling-asynchronous-processing"></a>Włączanie przetwarzania asynchronicznego  
 Domyślnie komunikaty wysyłane do usługi WCF hostowanych w usługach IIS 6.0 i starsze są przetwarzane w sposób synchronicznego. ASP.NET wywołuje WCF w jego własnym wątku (wątku roboczego ASP.NET) i WCF wykorzystuje inny wątek przetwarzania żądania. Na wątku roboczego ASP.NET przechowuje WCF, dopóki nie ukończy jego przetwarzanie. Prowadzi to do synchronicznego przetwarzania żądania. Asynchroniczne przetwarzanie żądania umożliwia większą skalowalność, ponieważ zmniejsza liczbę wątków wymagane do przetwarzania żądań, które — WCF nie posiada w wątku ASP.NET podczas przetwarzania żądania. Użycie asynchronicznego zachowania nie jest zalecane dla komputerów z systemem usług IIS 6.0, ponieważ nie istnieje sposób ograniczania żądań przychodzących, które otwarcia serwerowi *"odmowa usługi"* ataków (DOS). Począwszy od usług IIS 7.0, przepustnicy równoczesnych żądań wprowadzono: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`. Z tej nowej przepustnicy jest bezpiecznie korzystać przetwarzania asynchronicznego.  Domyślnie w usługach IIS 7.0 modułu i asynchroniczne procedury obsługi są rejestrowane. Jeśli to zostało wyłączone, możesz ręcznie włączyć asynchronicznego przetwarzania żądań w pliku Web.config aplikacji. Ustawienia używane są zależne od użytkownika `aspNetCompatibilityEnabled` ustawienie. Jeśli masz `aspNetCompatibilityEnabled` ustawioną `false`, skonfiguruj `System.ServiceModel.Activation.ServiceHttpModule` pokazane na poniższy fragment konfiguracji.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="false" />      
  </system.serviceModel>  
  <system.webServer>  
    <modules>  
      <remove name="ServiceModel"/>  
      <add name="ServiceModel"   
           preCondition="integratedMode,runtimeVersionv2.0"   
           type="System.ServiceModel.Activation.ServiceHttpModule, System.ServiceModel,Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
    </modules>  
    </system.webServer>  
```  
  
 Jeśli masz `aspNetCompatibilityEnabled` ustawioną `true`, skonfiguruj `System.ServiceModel.Activation.ServiceHttpHandlerFactory` pokazane na poniższy fragment konfiguracji.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />      
  </system.serviceModel>  
  <system.webServer>  
    <handlers>  
          <clear/>  
          <add name="TestAsyncHttpHandler"   
               path="*.svc"   
               verb="*"   
               type="System.ServiceModel.Activation.ServiceHttpHandlerFactory, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"           
               />  
    </handlers>      
  </system.webServer>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady usługi hostingu](http://msdn.microsoft.com/library/f703a3f6-0fba-418a-a92f-7ce75ccfa47e)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
