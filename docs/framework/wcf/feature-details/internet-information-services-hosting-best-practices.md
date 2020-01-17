---
title: Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 092e6ab675cf807db44c2085f8b0e7bbf67d7b28
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211914"
---
# <a name="internet-information-services-hosting-best-practices"></a>Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych
W tym temacie opisano najlepsze rozwiązania dotyczące hostingu usług Windows Communication Foundation (WCF).  
  
## <a name="implementing-wcf-services-as-dlls"></a>Implementowanie usług WCF jako bibliotek DLL  
 Wdrożenie usługi WCF jako biblioteki DLL wdrożonej w katalogu \Bin aplikacji sieci Web umożliwia ponowne użycie usługi poza modelem aplikacji sieci Web, na przykład w środowisku testowym, które może nie mieć wdrożonych Internet Information Services (IIS).  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>Hosty usług w aplikacjach hostowanych przez usługi IIS  
 Nie należy używać autonomicznych interfejsów API, aby utworzyć nowe hosty usług, które nasłuchują na transportach sieciowych, które nie są natywnie obsługiwane przez środowisko hostingu usług IIS (na przykład usługi IIS 6,0 do hostowania usług TCP, ponieważ komunikacja TCP nie jest natywnie obsługiwana w usługach IIS 6,0). Ta metoda nie jest zalecana. Hosty usługi tworzone w sposób nieznane są w środowisku hostingu usług IIS. Punkt krytyczny polega na tym, że przetwarzanie wykonywane przez usługi, które zostały utworzone w sposób nieużywany, nie jest uwzględniane przez usługi IIS podczas określania, czy pula aplikacji hostingu jest bezczynna. W efekcie aplikacje, które mają takie same utworzone hosty usług, mają środowisko hostingu usług IIS, które w sposób agresywny usuwa procesy hosta usług IIS.  
  
## <a name="uris-and-iis-hosted-endpoints"></a>Identyfikatory URI i punkty końcowe hostowane w usługach IIS  
 Punkty końcowe dla usługi hostowanej przez usługi IIS powinny być skonfigurowane przy użyciu względnych identyfikatorów zasobów (URI), a nie adresów bezwzględnych. Gwarantuje to, że adres punktu końcowego znajduje się w zestawie adresów URI należących do aplikacji hostingowej i zapewnia, że Aktywacja oparta na komunikatach będzie wykonywana zgodnie z oczekiwaniami.  
  
## <a name="state-management-and-process-recycling"></a>Zarządzanie stanami i odtwarzanie procesów  
 Środowisko hostingu usług IIS jest zoptymalizowane pod kątem usług, które nie obsługują stanu lokalnego w pamięci. Program IIS odtwarza proces hosta w odpowiedzi na różnorodne zdarzenia zewnętrzne i wewnętrzne, powodując utratę wszelkich nietrwałych Stanów przechowywanych wyłącznie w pamięci. Usługi hostowane w usługach IIS powinny przechowywać ich stan zewnętrzny względem procesu (na przykład w bazie danych) lub w pamięci podręcznej w pamięci, która może być łatwo tworzona w przypadku wystąpienia zdarzenia odtwarzania aplikacji.  
  
> [!NOTE]
> Protokoły są używane przez usługi WCF do niezawodności warstwy komunikatów i zabezpieczeń używają nietrwałego stanu w pamięci. Niezawodne sesje i sesje zabezpieczeń programu WCF mogą zostać nieoczekiwanie przerwane z powodu odtworzenia aplikacji. Aplikacje hostowane przez usługi IIS, które używają tych protokołów, powinny być zależne od czegoś innego niż klucz sesji dostarczony przez funkcję WCF w celu skorelowania stanu warstwy aplikacji (na przykład konstruowania warstwy aplikacji lub niestandardowego nagłówka korelacji) lub wyłączenia Odtwarzanie procesów programu IIS dla aplikacji hostowanej.  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>Optymalizacja wydajności w scenariuszach warstwy środkowej  
 W celu uzyskania optymalnej wydajności w *scenariuszu warstwy środkowej*— usługi, która wywołuje do innych usług w odpowiedzi na komunikaty przychodzące — Tworzenie wystąpienia klienta usługi WCF w usłudze zdalnej raz i ponowne używanie jej w wielu żądaniach przychodzących. Tworzenie wystąpień klientów usługi WCF jest kosztowną operacją względną dla tworzenia wywołania usługi na istniejącym wystąpieniu klienta, a scenariusze warstwy środkowej dają różne zyski wydajności przez buforowanie klientów zdalnych między żądaniami. Klienci usługi WCF są bezpieczne wątkowo, dlatego nie trzeba synchronizować dostępu do klienta w wielu wątkach.  
  
 Scenariusze dotyczące warstwy środkowej powodują również wzrost wydajności przy użyciu asynchronicznych interfejsów API generowanych przez opcję `svcutil /a`. Opcja `/a` powoduje, że [Narzędzie metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generuje metody `BeginXXX/EndXXX` dla każdej operacji usługi, co umożliwia wykonywanie długotrwałych wywołań usług zdalnych w wątkach w tle.  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>WCF w scenariuszach wieloadresowych lub wielonazwanych  
 Można wdrażać usługi WCF w kolektywie serwerów sieci Web usług IIS, w których zestaw komputerów współużytkuje wspólną nazwę zewnętrzną (taką jak `http://www.contoso.com`), ale są indywidualnie adresowane przez różne nazwy hostów (na przykład `http://www.contoso.com` może kierować ruch do dwóch różnych maszyn o nazwach `http://machine1.internal.contoso.com` i `http://machine2.internal.contoso.com`). Ten scenariusz wdrażania jest w pełni obsługiwany przez funkcję WCF, ale wymaga specjalnej konfiguracji witryny sieci Web usług IIS, która hostuje usługi WCF w celu wyświetlenia poprawnej (zewnętrznej) nazwy hosta w metadanych usługi (Web Services Description Language).  
  
 Aby upewnić się, że w programie WCF metadanych usługi jest wyświetlana poprawna nazwa hosta, Skonfiguruj domyślną tożsamość witryny sieci Web usług IIS, która hostuje usługi WCF do używania jawnej nazwy hosta. Na przykład komputery znajdujące się wewnątrz farmy `www.contoso.com` powinny używać powiązania witryny IIS *: 80: www. contoso. com dla protokołów HTTP i \*: 443: www. contoso. com dla protokołu HTTPS.  
  
 Powiązania witryny sieci Web usług IIS można skonfigurować za pomocą przystawki MMC programu IIS.  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>Pule aplikacji działające w różnych kontekstach użytkownika zastępują zestawy z innych kont w folderze tymczasowym  
 Aby zapewnić, że pule aplikacji działające w różnych kontekstach użytkownika nie mogą zastąpić zestawów z innych kont w folderze tymczasowych plików ASP.NET, Użyj różnych tożsamości i folderów tymczasowych dla różnych aplikacji. Na przykład jeśli masz dwie aplikacje wirtualne/Application1 i/Application2, możesz utworzyć dwie pule aplikacji, a i B, z dwoma różnymi tożsamościami. Pula aplikacji A może działać w ramach jednej tożsamości użytkownika (Użytkownik1), podczas gdy pula aplikacji B może działać w ramach innej tożsamości użytkownika (b), i skonfigurować/Application1 do używania a i/Application2 do korzystania z tej opcji.  
  
 W pliku Web. config można skonfigurować folder tymczasowy przy użyciu \<system.web/compilation/@tempFolder>. Dla/Application1 może być "c:\tempForUser1" i dla application2, może to być "c:\tempForUser2". Przyznaj odpowiednie uprawnienia do zapisu dla tych folderów dla dwóch tożsamości.  
  
 Następnie nie można zmienić folderu generacji kodu dla/application2 (w obszarze c:\tempForUser1).  
  
## <a name="enabling-asynchronous-processing"></a>Włączanie przetwarzania asynchronicznego  
 Domyślnie komunikaty wysyłane do usługi WCF hostowanej w usługach IIS 6,0 i wcześniejszych są przetwarzane synchronicznie. ASP.NET wywołuje do programu WCF we własnym wątku (wątek roboczy ASP.NET) i WCF używa innego wątku do przetworzenia żądania. Program WCF jest przechowywany w wątku roboczym ASP.NET, dopóki jego przetwarzanie nie zostanie zakończone. Prowadzi to do synchronicznego przetwarzania żądań. Przetwarzanie żądań asynchronicznie zapewnia lepszą skalowalność, ponieważ zmniejsza liczbę wątków wymaganych do przetworzenia żądania — WCF nie znajduje się w wątku ASP.NET podczas przetwarzania żądania. Używanie zachowań asynchronicznych nie jest zalecane w przypadku maszyn z usługami IIS 6,0, ponieważ nie ma możliwości ograniczania żądań przychodzących, które otwierają serwer na ataki *typu "odmowa usługi"* (DOS). Począwszy od usług IIS 7,0 wprowadzono współbieżne ograniczenie żądania: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`. Przy użyciu tego nowego ograniczenia można bezpiecznie używać przetwarzania asynchronicznego.  Domyślnie w usługach IIS 7,0 zarejestrowano asynchroniczną procedurę obsługi i moduł. Jeśli ta funkcja została wyłączona, można ręcznie włączyć asynchroniczne przetwarzanie żądań w pliku Web. config aplikacji. Ustawienia, które są używane, zależą od ustawienia `aspNetCompatibilityEnabled`. Jeśli masz `aspNetCompatibilityEnabled` ustawiony na `false`, skonfiguruj `System.ServiceModel.Activation.ServiceHttpModule` jak pokazano w poniższym fragmencie kodu.  
  
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
  
 Jeśli masz `aspNetCompatibilityEnabled` ustawiony na `true`, skonfiguruj `System.ServiceModel.Activation.ServiceHttpHandlerFactory` jak pokazano w poniższym fragmencie kodu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Przykłady hostingu usług](../samples/hosting.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
