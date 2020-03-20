---
title: Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 3be9d4c81f891ad898099ba9041a09b16388b7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184718"
---
# <a name="internet-information-services-hosting-best-practices"></a>Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych
W tym temacie przedstawiono niektóre najlepsze rozwiązania dotyczące hostingu usług Windows Communication Foundation (WCF).  
  
## <a name="implementing-wcf-services-as-dlls"></a>Wdrażanie usług WCF jako bibliotek dll  
 Implementowanie usługi WCF jako biblioteki DLL, która jest wdrażana w katalogu \bin aplikacji sieci Web umożliwia ponowne użycie usługi poza modelem aplikacji sieci Web, na przykład w środowisku testowym, w które mogą nie mieć wdrożonych internetowych usług informacyjnych (IIS).  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>Hosty usług w aplikacjach hostowanych usługami IIS  
 Nie należy używać imperatywów interfejsów API hosta własnego do tworzenia nowych hostów usług, które nasłuchują na transportach sieciowych, które nie są natywnie obsługiwane przez środowisko hostingowe usług IIS (na przykład usługi IIS 6.0 do obsługi usług TCP, ponieważ komunikacja TCP nie jest obsługiwana natywnie w usługach IIS 6.0). Ta metoda nie jest zalecana. Hosty usługi utworzone zgodnie z wymogami nie są znane w środowisku hostingowym usług IIS. Punktem krytycznym jest to, że przetwarzanie wykonywane przez trwale utworzone usługi nie jest rozliczane przez usługi IIS, gdy określa, czy pula aplikacji hostingu jest bezczynna. W rezultacie aplikacje, które mają tak trwali utworzone hosty usług, mają środowisko hostingowe usług IIS, które agresywnie usuwa procesy hosta usług IIS.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>Punkty końcowe URI i punkty końcowe hostowane przez iIS  
 Punkty końcowe usługi hostowane przez usługi usług IIS powinny być konfigurowane przy użyciu względnych jednolitych identyfikatorów zasobów (URI), a nie adresów bezwzględnych. Gwarantuje to, że adres punktu końcowego mieści się w zestawie adresów identyfikatorów URI, które należą do aplikacji hostingowej i zapewnia, że aktywacja oparta na wiadomościach odbywa się zgodnie z oczekiwaniami.  
  
## <a name="state-management-and-process-recycling"></a>Zarządzanie państwem i recykling procesów  
 Środowisko hostingowe usług IIS jest zoptymalizowane pod kątem usług, które nie utrzymują stanu lokalnego w pamięci. Usługi IIS odtwarzają proces hosta w odpowiedzi na różne zdarzenia zewnętrzne i wewnętrzne, powodując utratę dowolnego stanu nietrwałego przechowywanego wyłącznie w pamięci. Usługi hostowane w usługach IIS powinny przechowywać ich stan zewnętrzny dla procesu (na przykład w bazie danych) lub w pamięci podręcznej, którą można łatwo odtworzyć, jeśli wystąpi zdarzenie odtworzenia aplikacji.  
  
> [!NOTE]
> Protokoły WCF używa dla niezawodności warstwy wiadomości i zabezpieczeń użyć stanu nietrwałe w pamięci. WCF niezawodne sesje i sesje zabezpieczeń może zakończyć się nieoczekiwanie z powodu odtwarzania aplikacji. Aplikacje hostowane przez usługi IIS, które korzystają z tych protokołów, powinny zależeć od czegoś innego niż klucz sesji dostarczony przez WCF do korelowania stanu warstwy aplikacji (na przykład konstruowania warstwy aplikacji lub niestandardowego nagłówka korelacji) lub wyłączyć Recykling procesów usług IIS dla hosta aplikacji.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Optymalizacja wydajności w scenariuszach warstwy środkowej  
 Aby uzyskać optymalną wydajność w *scenariuszu warstwy środkowej*— usługa, która wywołuje inne usługi w odpowiedzi na wiadomości przychodzące — smówić wystąpienie klienta usługi WCF do usługi zdalnej raz i użyć go ponownie w wielu żądaniach przychodzących. Tworzenie wystąpienia klientów usług WCF jest kosztowną operacją w stosunku do wykonywania wywołania usługi w istniejącym wystąpieniu klienta, a scenariusze warstwy środkowej generują wyraźny wzrost wydajności przez buforowanie klientów zdalnych w żądaniach. Klienci usługi WCF są bezpieczne dla wątków, więc nie jest konieczne synchronizowanie dostępu do klienta w wielu wątkach.  
  
 Scenariusze warstwy środkowej również produkować wzrost wydajności przy użyciu asynchronicznych interfejsów API generowanych przez `svcutil /a` opcję. Opcja `/a` powoduje, że [Narzędzie narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generuje `BeginXXX/EndXXX` metody dla każdej operacji usługi, co umożliwia potencjalnie długotrwałe wywołania usług zdalnych w wątkach w tle.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>WCF w scenariuszach multi-homed lub multi-named  
 Usługi WCF można wdrożyć wewnątrz farmy sieci Web usług IIS, gdzie `http://www.contoso.com`zestaw komputerów ma wspólną nazwę zewnętrzną (na przykład), ale są indywidualnie adresowane przez różne nazwy hostów (na przykład `http://www.contoso.com` mogą kierować ruch do dwóch różnych maszyn o nazwie `http://machine1.internal.contoso.com` i `http://machine2.internal.contoso.com`). Ten scenariusz wdrażania jest w pełni obsługiwany przez WCF, ale wymaga specjalnej konfiguracji witryny sieci Web usług WCF usługi WCF usługi WCF do wyświetlania poprawne (zewnętrzne) nazwa hosta w metadanych usługi (Język opisu usług sieci Web).  
  
 Aby upewnić się, że w generowanych przez metadane usługi WCF jest wyświetlana poprawna nazwa hosta, skonfiguruj domyślną tożsamość witryny sieci Web usług IIS obsługującej usługi WCF w celu użycia jawnej nazwy hosta. Na przykład komputery znajdujące się `www.contoso.com` wewnątrz farmy powinny używać powiązania lokacji usług IIS *:80:www.contoso.com dla protokołu HTTP i \*:443:www.contoso.com dla protokołu HTTPS.  
  
 Powiązania witryny sieci Web usług IIS można skonfigurować przy użyciu przystawki Programu Microsoft Management Console (MMC) usług IIS.  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Pule aplikacji uruchomione w różnych kontekstach użytkownika zastępują zestawy z innych kont w folderze tymczasowym  
 Aby upewnić się, że pule aplikacji działających w różnych kontekstach użytkownika nie mogą zastępować zestawów z innych kont w folderze plików ASP.NET tymczasowych, należy użyć różnych tożsamości i folderów tymczasowych dla różnych aplikacji. Na przykład jeśli masz dwie aplikacje wirtualne /Application1 i / Application2, można utworzyć dwie pule aplikacji, A i B, z dwóch różnych tożsamości. Pula aplikacji A można uruchomić w ramach jednej tożsamości użytkownika (user1), podczas gdy pula aplikacji B można uruchomić w ramach innej tożsamości użytkownika (user2) i skonfigurować /Application1 do używania A i /Application2 do korzystania z B.  
  
 W witrynie Web.config folder tymczasowy \< system.web/compilation/@tempFolder można skonfigurować przy użyciu>. Dla /Application1 może to być "c:\tempForUser1", a dla application2 może to być "c:\tempForUser2". Udziel odpowiednich uprawnień do zapisu do tych folderów dla dwóch tożsamości.  
  
 Następnie użytkownik2 nie może zmienić folderu generowania kodu dla /application2 (w obszarze c:\tempForUser1).  
  
## <a name="enabling-asynchronous-processing"></a>Włączanie przetwarzania asynchronii  
 Domyślnie wiadomości wysyłane do usługi WCF hostowane w ramach usług IIS 6.0 i wcześniejszych są przetwarzane w sposób synchroniczne. ASP.NET wywołania do WCF na własny wątek (ASP.NET wątku roboczego) i WCF używa innego wątku do przetwarzania żądania. WCF przytrzymuje na wątku roboczym ASP.NET, dopóki nie zakończy przetwarzania. Prowadzi to do synchroniczowego przetwarzania żądań. Przetwarzanie żądań asynchronicznie umożliwia większą skalowalność, ponieważ zmniejsza liczbę wątków wymaganych do przetworzenia żądania — WCF nie trzyma się wątku ASP.NET podczas przetwarzania żądania. Użycie zachowania asynchroniiowego nie jest zalecane dla komputerów z usługami IIS 6.0, ponieważ nie ma możliwości ograniczania przychodzących żądań, które otwierają serwer na ataki *typu "odmowa usługi"* (DOS). Począwszy od iis 7.0, wprowadzono równoczesne `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`przepustnicy żądania: . Dzięki tej nowej przepustnicy można bezpiecznie korzystać z przetwarzania asynchronicznie.  Domyślnie w serwisach IIS 7.0 jest rejestrowany program obsługi asynchronicznego i moduł. Jeśli ta opcja została wyłączona, można ręcznie włączyć asynchroniczne przetwarzanie żądań w pliku Web.config aplikacji. Używane ustawienia zależą od `aspNetCompatibilityEnabled` ustawienia. Jeśli ustawiono `aspNetCompatibilityEnabled` `false`, `System.ServiceModel.Activation.ServiceHttpModule` skonfigurować, jak pokazano w poniższym fragmentie konfiguracji.  
  
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
  
 Jeśli ustawiono `aspNetCompatibilityEnabled` `true`, `System.ServiceModel.Activation.ServiceHttpHandlerFactory` skonfigurować, jak pokazano w poniższym urywek konfiguracji.  
  
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

- [Przykłady hostingu usług](../samples/hosting.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
