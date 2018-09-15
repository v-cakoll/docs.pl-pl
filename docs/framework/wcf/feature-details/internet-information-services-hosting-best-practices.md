---
title: Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 0ca5e20b846a1b10f5a52748ff06a4af958b2f4c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45658759"
---
# <a name="internet-information-services-hosting-best-practices"></a>Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych
W tym temacie opisano najlepsze rozwiązania dotyczące hostowania usług Windows Communication Foundation (WCF).  
  
## <a name="implementing-wcf-services-as-dlls"></a>Wdrażanie usługi WCF jako biblioteki dll  
 Implementowanie platformy WCF service jako bibliotekę DLL, która jest wdrażana do katalogu \bin aplikacji sieci Web umożliwia ponownego użycia usługi poza modelu aplikacji sieci Web, na przykład w środowisku testowym, który nie może mieć wdrożony Internet Information Services (IIS).  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>Hosty usług w aplikacjach hostowanych przez usługi IIS  
 Nie używaj imperatywne samodzielnego hostowania interfejsów API do tworzenia nowych hostach usługi tego nasłuchiwania na transportu sieciowego nieobsługiwane natywnie przez usługi IIS, środowisko hostingu (na przykład [!INCLUDE[iis601](../../../../includes/iis601-md.md)] do obsługi protokołu TCP usługi, ponieważ komunikację TCP nie jest natywnie obsługiwane w [!INCLUDE[iis601](../../../../includes/iis601-md.md)]). To podejście nie jest zalecane. Hosty usług utworzone obowiązkowo nie są znane w środowisku hostingu usług IIS. Punkt krytyczny jest, że przetwarzania wykonywane przez obowiązkowo utworzonej usługi nie jest uwzględniony przez usługi IIS podczas określania, czy hostingu pula aplikacji jest w stanie bezczynności. Wynik jest aplikacji, które mają takie hosty obowiązkowo utworzonej usługi IIS Środowisko hostingu agresywnie usuwa procesy hosta usług IIS.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>Identyfikatory URI i hostowanych przez usługi IIS punktów końcowych  
 Punkty końcowe usługi obsługiwane przez usługi IIS powinny być skonfigurowane przy użyciu względne jednolitych identyfikatorów zasobów (URI), nie bezwzględnych adresów. Gwarantuje to, że adres punktu końcowego mieści się w zestawie adresów identyfikatora URI, które należą do hostowania aplikacji i gwarantuje, że aktywacja oparta na komunikatach się stanie, zgodnie z oczekiwaniami.  
  
## <a name="state-management-and-process-recycling"></a>Zarządzanie stanem i odtwarzanie procesów  
 Środowisko hostingu usług IIS jest zoptymalizowany pod kątem usług, które nie obsługują stan lokalnego w pamięci. IIS odtwarza procesu hosta w odpowiedzi na szereg zdarzeń wewnętrznych i zewnętrznych, powodując dowolny stan volatile przechowywane wyłącznie w pamięci, aby zostać utracone. Usług hostowanych w usługach IIS należy przechowywać stanu zewnętrzne w stosunku do procesu (na przykład w bazie danych) lub w pamięci podręcznej, które mogą być łatwo ponownie utworzyć Jeśli aplikacja odtwarzanie zdarzeń występuje.  
  
> [!NOTE]
>  Użyj protokołów używana WCF dla komunikatu warstwy niezawodności i skutecznych zabezpieczeniach volatile stanu w pamięci. Sesje niezawodnej usługi WCF i sesje zabezpieczeń może zakończyć nieoczekiwanie z powodu odtwarzanie aplikacji. Aplikacje hostowane w usługach IIS, wchodzące użytkowania tych protokołów albo zależy od coś innego niż klucz sesji dostarczone do usługi WCF do korelacji stan warstwy aplikacji (na przykład, konstrukcja warstwy aplikacji lub nagłówek niestandardowej korelacji) lub wyłączanie Odtwarzanie dla aplikacji hostowanych procesów usług IIS.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Optymalizacja wydajności w scenariuszach warstwy środkowej  
 Aby uzyskać optymalną wydajność w *scenariusza warstwy środkowej*— usługi, który wywołuje się z innymi usługami w odpowiedzi na komunikaty przychodzące — raz wystąpienia klienta usługi WCF do zdalnej usługi i użyć go ponownie w wielu przychodzące żądania. Wystąpienia klientów usługi WCF jest kosztowną operacją względem co wywołanie w istniejącym wystąpieniu klienta usługi i scenariusze warstwy środkowej okazuje wzrost wydajności distinct, buforując klientów zdalnych żądań. Klienci usługi WCF są odporne na wątki, więc nie jest konieczne do synchronizowania dostępu do klienta przez wiele wątków.  
  
 Scenariusze warstwy środkowej utworzyć również zwiększenie wydajności przy użyciu asynchronicznych interfejsów API generowanych przez `svcutil /a` opcji. `/a` Opcji powoduje, że [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania `BeginXXX/EndXXX` metod dla każdej operacji usługi, co pozwala potencjalnie długotrwałych wywołań usługi zdalnej ma zostać wykonane na wątków w tle.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>Usługi WCF w scenariuszach wieloadresowych lub wielu nazwane  
 Można wdrożyć usługi WCF w ramach farmy sieci Web usług IIS, w której zestaw komputerów używają tej samej nazwy zewnętrzne (takie jak http://www.contoso.com) , ale indywidualnie są rozwiązywane przez różne nazwy hostów (na przykład http://www.contoso.com może kierować ruch do dwóch różnych komputerach o nazwie http://machine1.internal.contoso.com i http://machine2.internal.contoso.com). Ten scenariusz wdrażania jest w pełni obsługiwany przez architekturę WCF, ale wymaga specjalnej konfiguracji witryny sieci Web usług IIS, hostowanie usługi WCF, aby wyświetlić poprawną nazwę hosta (zewnętrzne) w metadanych usługi (Web Services Description Language).  
  
 Aby upewnić się, że poprawna nazwa hosta jest wyświetlana w metadanych usługi WCF generuje, konfigurowanie tożsamości domyślnej witryny sieci Web usług IIS, który jest hostem usług WCF do użycia jawnej nazwy hosta. Na przykład komputery, które znajdują się wewnątrz farmy www.contoso.com powinien używać powiązanie witryny usług IIS *:80:www.contoso.com dla protokołu HTTP i \*: 443:www.contoso.com dla protokołu HTTPS.  
  
 Powiązania witryny sieci Web usług IIS można skonfigurować za pomocą przystawki usług IIS programu Microsoft Management Console (MMC).  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Pule aplikacji uruchomionych w różnych kontekstów użytkownika zastąpić zestawów z innych kont w folderze tymczasowym  
 Aby upewnić się, że pule aplikacji uruchomionych w różnych kontekstów użytkownika nie może zastąpić zestawów z innych kont w pliku tymczasowym [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pliki w folderze, użyj różnych tożsamości i folderów tymczasowych dla różnych aplikacji. Na przykład, jeśli masz dwa /Application1 aplikacji wirtualnych i / Aplikacja2, możesz utworzyć dwie pule aplikacji, A i B, z dwóch różnych tożsamości. Pula aplikacji A można uruchamiana tożsamości w ramach jednego użytkownika (Użytkownik1), podczas gdy można uruchomić puli aplikacji B inną tożsamość użytkownika (Użytkownik2) i skonfigurować /Application1 używaj i /Application2, aby użyć B.  
  
 W pliku Web.config, można skonfigurować za pomocą folderu tymczasowego \< system.web/compilation/@tempFolder>. Dla /Application1 może być "c:\tempForUser1", a dla Aplikacja2 może być "c:\tempForUser2". Przyznawanie odpowiednich uprawnień do zapisu do tych folderów dla dwóch tożsamości.  
  
 Następnie Użytkownik2 nie można zmienić folder generowania kodu dla /application2 (w obszarze c:\tempForUser1).  
  
## <a name="enabling-asynchronous-processing"></a>Włączanie przetwarzania asynchronicznego  
 Domyślnie komunikaty wysyłane do usługi WCF hostowanej w ramach usług IIS 6.0 i starsze są przetwarzane w sposób synchroniczne. ASP.NET wywołania do usługi WCF w jego własnym wątku (wątek procesu roboczego ASP.NET) i WCF używa innego wątku przetwarzania żądania. WCF przechowuje na wątku roboczego ASP.NET, dopóki nie ukończy przetwarzanie. Prowadzi to do synchronicznego przetwarzania żądania. Asynchronicznego przetwarzania żądań umożliwia zwiększenie skalowalności, ponieważ zmniejsza liczbę wątków, wymaganych do przetworzenia żądania — WCF nie posiada w wątku ASP.NET podczas przetwarzania żądania. Korzystanie z zachowanie asynchroniczne nie jest zalecane dla maszyn z systemem usług IIS 6.0, ponieważ nie istnieje żaden sposób ograniczania żądań przychodzących, które otwierają serwerze *"odmowa usługi"* ataków (DOS). Począwszy od usług IIS 7.0, ograniczania żądań współbieżnych wprowadzono: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`. Za pomocą tego nowego ograniczenia jest bezpieczny w użyciu przetwarzania asynchronicznego.  Domyślnie w usługach IIS 7.0 obsługi asynchronicznego i moduł są rejestrowane. Jeśli ta funkcja została wyłączona, można ręcznie włączyć asynchronicznego przetwarzania żądań w pliku Web.config aplikacji. Ustawienia używane są zależne od Twojego `aspNetCompatibilityEnabled` ustawienie. Jeśli masz `aspNetCompatibilityEnabled` równa `false`, skonfiguruj `System.ServiceModel.Activation.ServiceHttpModule` jak pokazano w poniższym fragmencie kodu konfiguracji.  
  
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
  
 Jeśli masz `aspNetCompatibilityEnabled` równa `true`, skonfiguruj `System.ServiceModel.Activation.ServiceHttpHandlerFactory` jak pokazano w poniższym fragmencie kodu konfiguracji.  
  
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
 [Przykłady usługi hostingu](https://msdn.microsoft.com/library/f703a3f6-0fba-418a-a92f-7ce75ccfa47e)  
 [Windows Server AppFabric funkcje hostingu](https://go.microsoft.com/fwlink/?LinkId=201276)
