---
title: Wdrażanie usługi WCF hostowanej przez Internetowe usługi informacyjne
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 67f6877546951bd92b235218f10f6ccc7011ef5c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463856"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Wdrażanie usługi WCF hostowanej przez Internetowe usługi informacyjne

Tworzenie i wdrażanie usługi Windows Communication Foundation (WCF), która jest hostowana w internetowych usługach informacyjnych (IIS) składa się z następujących zadań:

- Upewnij się, że usługi IIS, ASP.NET, WCF i składnik aktywacji WCF są poprawnie zainstalowane i zarejestrowane.

- Utwórz nową aplikację usług IIS lub ponownie użyć istniejącej aplikacji ASP.NET.

- Utwórz plik .svc dla usługi WCF.

- Wdrażanie implementacji usługi w aplikacji usług IIS.

- Konfigurowanie usługi WCF.

Aby uzyskać szczegółowe informacje na temat tworzenia usługi WCF hostowane przez usługi usług IIS, zobacz [Jak: Hostowanie usługi WCF w usługach IIS](how-to-host-a-wcf-service-in-iis.md).

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Upewnij się, że iIS, ASP.NET i WCF są poprawnie zainstalowane i zarejestrowane

WCF, IIS i ASP.NET muszą być zainstalowane dla usług WCF hostowanych usług usług IIS do poprawnego działania. Procedury instalowania WCF (jako część programu .NET Framework), ASP.NET i IIS różnią się w zależności od systemu operacyjnego. Aby uzyskać więcej informacji na temat instalowania WCF i programu .NET Framework, zobacz [Instalowanie programu .NET Framework dla deweloperów](../../install/guide-for-developers.md). Aby zainstalować usługi IIS w systemie Windows 10, otwórz **okno Programy i funkcje** w **Panelu sterowania,** a następnie wybierz pozycję **Włącz lub wyłącz funkcje systemu Windows**. W **obszarze Funkcje systemu Windows**wybierz pozycję Internetowe usługi **informacyjne,** a następnie wybierz przycisk **OK**.

![Funkcje systemu Windows z wyróżnionymi iis](./media/windows-features-iis.png)

Instrukcje dotyczące instalowania usług IIS w innych systemach operacyjnych można znaleźć na [stronie Zainstaluj usługi IIS w systemie Windows Vista i Windows 7](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7) oraz [Zainstaluj usługi IIS 8.5 w systemie Windows Server 2012 R2](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2).

Proces instalacji programu .NET Framework automatycznie rejestruje WCF w usługach IIS, jeśli usługe IIS są już obecne na komputerze. Jeśli usługi IIS są instalowane po platformie .NET Framework, wymagany jest dodatkowy krok do zarejestrowania WCF w urzędzie IIS i ASP.NET. Można to zrobić w następujący sposób, w zależności od systemu operacyjnego:

- Windows 7 i Windows Server 2003: Aby zarejestrować usługę IIS, użyj narzędzia [ServiceModel Registration Tool (ServiceModelReg.exe).](../../../../docs/framework/wcf/servicemodelreg-exe.md) Aby użyć tego narzędzia, wpisz **servicemodelreg.exe /i /x** w [wierszu polecenia dewelopera dla programu Visual Studio](../../tools/developer-command-prompt-for-vs.md).

- Windows 7: Na koniec należy sprawdzić, czy ASP.NET jest skonfigurowany do używania programu .NET Framework w wersji 4 lub nowszej. Można to zrobić, uruchamiając narzędzie ASPNET_Regiis `–i` z opcją. Aby uzyskać więcej informacji, zobacz [ASP.NET narzędzia rejestracji iis](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)).

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Tworzenie nowej aplikacji usług IIS lub ponowne używanie istniejącej aplikacji ASP.NET

Usługi WCF hostowane przez usługi IIS muszą znajdować się wewnątrz aplikacji usług IIS. Można utworzyć nową aplikację usług IIS do obsługi usług WCF wyłącznie. Alternatywnie można wdrożyć usługę WCF w istniejącej aplikacji, która jest już hostuje zawartość ASP.NET 2.0 (na przykład strony .aspx i usługi sieci Web ASP.NET [ASMX]). Aby uzyskać więcej informacji na temat tych opcji, zobacz sekcje "Hosting WCF Side-by-Side with ASP.NET" i "Hosting WCF Services in ASP.NET Compatibility Mode" w [WCF Services and ASP.NET](wcf-services-and-aspnet.md).

Należy zauważyć, że usługi IIS 6.0 i nowsze wersje okresowo ponownie uruchamiają izolowane aplikacje programowania obiektowego. Wartość domyślna to 1740 minut. Maksymalna obsługiwana wartość wynosi 71 582 minut. To ponowne uruchomienie można wyłączyć. Aby uzyskać więcej informacji na temat tej właściwości, zobacz [PeriodicRestartTime](https://docs.microsoft.com/previous-versions/iis/6.0-sdk/ms525914(v=vs.90)).

## <a name="create-an-svc-file-for-the-wcf-service"></a>Tworzenie pliku .svc dla usługi WCF

Usługi WCF hostowane w usługach IIS są reprezentowane jako pliki zawartości specjalnej (pliki svc) wewnątrz aplikacji usług IIS. Ten model jest podobny do sposobu, w jaki strony ASMX są reprezentowane wewnątrz aplikacji IIS jako pliki asmx. Plik .svc zawiera dyrektywę przetwarzania specyficzne dla WCF[\@(ServiceHost),](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)która umożliwia infrastrukturze hostingowej WCF aktywować hostowane usługi w odpowiedzi na przychodzące wiadomości. Najczęstszą składnią pliku .svc jest następująca instrukcja.

`<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>`

Składa się z [ \@dyrektywy ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) i `Service`jednego atrybutu, . Wartość atrybutu `Service` jest nazwą typu środowiska wykonawczego języka wspólnego (CLR) implementacji usługi. Za pomocą tej dyrektywy jest zasadniczo równoważne tworzenie hosta usługi przy użyciu następującego kodu.

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

Można również wykonać dodatkową konfigurację hostingu, taką jak tworzenie listy adresów podstawowych dla usługi. Można również użyć <xref:System.ServiceModel.Activation.ServiceHostFactory> niestandardowego rozszerzenia dyrektywy do użytku z niestandardowymi rozwiązaniami hostingowymi. Aplikacje usług IIS, które hostują usługi WCF <xref:System.ServiceModel.ServiceHost> nie są odpowiedzialne za zarządzanie tworzeniem i okresem istnienia wystąpień. Zarządzana infrastruktura hostingowa WCF tworzy niezbędne <xref:System.ServiceModel.ServiceHost> wystąpienie dynamicznie po odebraniu pierwszego żądania dla pliku .svc. Wystąpienie nie jest zwalniany, dopóki nie zostanie jawnie zamknięte przez kod lub gdy aplikacja jest odtwomia.

Aby uzyskać więcej informacji na temat składni plików .svc, zobacz [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Wdrażanie implementacji usługi w aplikacji usług IIS

Usługi WCF hostowane w usługach IIS używają tego samego modelu kompilacji dynamicznej, co ASP.NET 2.0. Podobnie jak w przypadku ASP.NET, można wdrożyć kod implementacji usług WCF hostowanych usług usług IIS na kilka sposobów w różnych lokalizacjach, w następujący sposób:

- Jako wstępnie skompilowany plik dll znajdujący się w globalnej pamięci podręcznej zestawów (GAC) lub w katalogu \bin aplikacji. Wstępnie skompilowane pliki binarne nie są aktualizowane, dopóki nie zostanie wdrożona nowa wersja biblioteki klas.

- Jako nieskompilowane pliki źródłowe znajdujące się w katalogu \App_Code aplikacji. Pliki źródłowe znajdujące się w tym katalogu są dynamicznie wymagane podczas przetwarzania pierwszego żądania aplikacji. Wszelkie zmiany w plikach w katalogu \App_Code powodują, że cała aplikacja zostanie poddana recyklingowi i ponownie skompilowana po odebraniu następnego żądania.

- Jako nieskompilowany kod umieszczony bezpośrednio w pliku .svc. Kod implementacji może również znajdować się w ybliwę \@w pliku .svc usługi, po servicehost dyrektywy. Wszelkie zmiany w kodzie wbudowanym powodują, że aplikacja ma zostać odtworzena i ponownie skompilowana po otrzymaniu następnego żądania.

Aby uzyskać więcej informacji na temat ASP.NET modelu kompilacji 2.0, zobacz [ASP.NET Przegląd kompilacji](https://docs.microsoft.com/previous-versions/aspnet/ms178466(v=vs.100)).

## <a name="configure-the-wcf-service"></a>Konfigurowanie usługi WCF

Usługi WCF hostowane przez usługi IIS przechowują swoją konfigurację w plikach Web.config aplikacji. Usługi hostowane przez usługi IIS używają tych samych elementów konfiguracji i składni, co usługi WCF hostowane poza usługami IIS. Jednak następujące ograniczenia są unikatowe dla środowiska hostingowego usługi IIS:

- Adresy podstawowe usług hostowanych usług IIS.

- Aplikacje obsługujące usługi WCF poza usługami IIS mogą kontrolować adres podstawowy usług, które <xref:System.ServiceModel.ServiceHost> hostują, przekazując zestaw identyfikatorów URI adresu podstawowego do konstruktora lub udostępniając element [ \<>hosta](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) w konfiguracji usługi. Usługi hostowane w usługach IIS nie mają możliwości kontrolowania swojego adresu podstawowego; adresem podstawowym usługi hostowanego przez usługi IIS jest adres pliku .svc.

### <a name="endpoint-addresses-for-iis-hosted-services"></a>Adresy punktów końcowych usług hostowanych usług IIS

Gdy są hostowane w usługach IIS, adresy punktów końcowych są zawsze uważane za względem adresu pliku .svc reprezentującego usługę. Na przykład jeśli adres podstawowy usługi WCF ma `http://localhost/Application1/MyService.svc` następującą konfigurację punktu końcowego:

```xml
<endpoint address="anotherEndpoint" />
```

Zapewnia to punkt końcowy, do `http://localhost/Application1/MyService.svc/anotherEndpoint`którego można osiągnąć w programie .

Podobnie element konfiguracji punktu końcowego, który używa pustego ciągu jako względnego `http://localhost/Application1/MyService.svc`adresu zapewnia punkt końcowy osiągalny w , który jest adresem podstawowym.

```xml
<endpoint address="" />
```

Dla punktów końcowych usługi hostowanych usługami IIS należy zawsze używać względnych adresów końcowych punktów końcowych usługi hostowanych przez usługi. Podanie w pełni kwalifikowanego adresu punktu `http://localhost/MyService.svc`końcowego (na przykład ) może prowadzić do błędów we wdrażaniu usługi, jeśli adres punktu końcowego nie wskazuje aplikacji usług IIS, która obsługuje usługę ujawniającą punkt końcowy. Przy użyciu względnych adresów punktów końcowych dla usług hostowanych pozwala uniknąć tych potencjalnych konfliktów.

### <a name="available-transports"></a>Dostępne transporty

Usługi WCF hostowane w usługach IIS 5.1 i IIS 6.0 są ograniczone do korzystania z komunikacji opartej na protok lubeli HTTP. Na tych platformach usług IIS skonfigurowanie usługi hosta w celu użycia powiązania innego niż HTTP powoduje błąd podczas aktywacji usługi. W przypadku programów IIS 7.0 obsługiwane transporty obejmują protokoły HTTP, Net.TCP, Net.Pipe, Net.MSMQ i msmq.formatname dla wstecznej zgodności z istniejącymi aplikacjami usługi MSMQ.

### <a name="http-transport-security"></a>Zabezpieczenia transportu HTTP

Usługi WCF hostowane przez usługi IIS mogą korzystać z zabezpieczeń transportu HTTP (na przykład schematów uwierzytelniania HTTPS i HTTP, takich jak podstawowe, digest i zintegrowane uwierzytelnianie systemu Windows), o ile katalog wirtualny usług IIS zawierający usługę obsługuje te ustawienia. Ustawienia zabezpieczeń transportu HTTP w powiązaniu hostowanego punktu końcowego muszą być zgodne z ustawieniami zabezpieczeń transportu w katalogu wirtualnym usług IIS, który go zawiera.

Na przykład punkt końcowy WCF skonfigurowany do używania uwierzytelniania szyfrowanego HTTP musi znajdować się w katalogu wirtualnym usług IIS, który jest również skonfigurowany do zezwalania na uwierzytelnianie szyfrowane HTTP. Niedopasowane kombinacje ustawień usług IIS i ustawień punktu końcowego WCF powodują błąd podczas aktywacji usługi.

## <a name="see-also"></a>Zobacz też

- [Hostowanie przez Internetowe usługi informacyjne](hosting-in-internet-information-services.md)
- [Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych](internet-information-services-hosting-best-practices.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
