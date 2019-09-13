---
title: Wdrażanie usługi WCF hostowanej przez Internetowe usługi informacyjne
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 95c56f767bbe8dce44ea742de00c65c357bd1378
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895111"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Wdrażanie usługi WCF hostowanej przez Internetowe usługi informacyjne

Tworzenie i wdrażanie usługi Windows Communication Foundation (WCF), która jest hostowana w usłudze Internet Information Services (IIS), składa się z następujących zadań:

- Upewnij się, że program IIS, ASP.NET, WCF i składnik aktywacji WCF są prawidłowo zainstalowane i zarejestrowane.

- Utwórz nową aplikację usług IIS lub ponownie Użyj istniejącej aplikacji ASP.NET.

- Utwórz plik SVC dla usługi WCF.

- Wdróż implementację usługi w aplikacji usług IIS.

- Skonfiguruj usługę WCF.

Szczegółowy przewodnik dotyczący tworzenia usługi WCF hostowanej przez usługi IIS znajduje się [w temacie How to: Hostowanie usługi WCF w usługach](how-to-host-a-wcf-service-in-iis.md)IIS.

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Upewnij się, że usługi IIS, ASP.NET i WCF są poprawnie zainstalowane i zarejestrowane

Do poprawnego działania usług WCF hostowanych przez usługi IIS należy zainstalować usługi WCF, IIS i ASP.NET. Procedury instalacji WCF (w ramach .NET Framework), ASP.NET i IIS różnią się w zależności od używanego systemu operacyjnego. Aby uzyskać więcej informacji na temat instalowania programu WCF i .NET Framework, zobacz [instalowanie .NET Framework dla deweloperów](../../install/guide-for-developers.md). Aby zainstalować usługi IIS w systemie Windows 10, Otwórz aplet **programy i funkcje** w **Panelu sterowania** , a następnie wybierz opcję **Włącz lub wyłącz funkcje systemu Windows**. W obszarze **funkcje systemu Windows**wybierz pozycję **Internet Information Services** a następnie wybierz przycisk **OK**.

![Funkcje systemu Windows z wyróżnionymi usługami IIS](media/windows-features-iis.png)

Instrukcje dotyczące instalowania usług IIS w innych systemach operacyjnych znajdują się w [tematach Instalowanie usług IIS w systemach Windows Vista i Windows 7](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7) oraz [instalowanie usług IIS 8,5 w systemie Windows Server 2012 R2](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2).

Proces instalacji .NET Framework automatycznie rejestruje funkcję WCF z usługami IIS, jeśli usługi IIS znajdują się już na komputerze. Jeśli usługi IIS są zainstalowane po .NET Framework, do zarejestrowania WCF w usługach IIS i ASP.NET jest wymagany dodatkowy krok. Można to zrobić w następujący sposób, w zależności od używanego systemu operacyjnego:

- Windows 7 i Windows Server 2003: Użyj narzędzia do [rejestracji ServiceModel (ServiceModelReg. exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) w celu zarejestrowania WCF w usługach IIS. Aby użyć tego narzędzia, wpisz **ServiceModelReg. exe/i/x** w [wiersz polecenia dla deweloperów dla programu Visual Studio](../../tools/developer-command-prompt-for-vs.md).

- Windows 7: Na koniec należy sprawdzić, czy ASP.NET jest skonfigurowany do używania .NET Framework w wersji 4 lub nowszej. W tym celu należy uruchomić narzędzie Aspnet_regiis z `–i` opcją. Aby uzyskać więcej informacji, zobacz [ASP.NET narzędzia rejestracji usług IIS](https://go.microsoft.com/fwlink/?LinkId=201186).

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Tworzenie nowej aplikacji usług IIS lub ponowne używanie istniejącej aplikacji ASP.NET

Usługi WCF hostowane przez usługi IIS muszą znajdować się wewnątrz aplikacji usług IIS. Można utworzyć nową aplikację IIS do hostowania wyłącznie usług WCF. Alternatywnie można wdrożyć usługę WCF w istniejącej aplikacji, która już udostępnia zawartość ASP.NET 2,0 (na przykład strony. aspx i usługi sieci Web ASP.NET [ASMX]). Aby uzyskać więcej informacji na temat tych opcji, zobacz sekcję "Hosting programu WCF obok siebie" i "hosting usług WCF w trybie zgodności ASP.NET" w sekcjach [usługi WCF i ASP.NET](wcf-services-and-aspnet.md).

Należy pamiętać, że program IIS 6,0 i jego nowsze wersje okresowo ponownie uruchamiają izolowaną aplikację programistyczną zorientowaną na obiekt. Wartość domyślna to 1740 minut. Maksymalna obsługiwana wartość to 71 582 minut. To ponowne uruchomienie można wyłączyć. Aby uzyskać więcej informacji na temat tej właściwości, zobacz [PeriodicRestartTime](https://go.microsoft.com/fwlink/?LinkId=109968).

## <a name="create-an-svc-file-for-the-wcf-service"></a>Tworzenie pliku SVC dla usługi WCF

Usługi WCF hostowane w usługach IIS są reprezentowane jako specjalne pliki zawartości (pliki SVC) wewnątrz aplikacji usług IIS. Ten model jest podobny do sposobu, w jaki strony ASMX są reprezentowane w aplikacji usług IIS jako pliki. asmx. Plik SVC zawiera dyrektywę przetwarzania specyficzną dla programu WCF ([\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)), która umożliwia infrastrukturze hostingu WCF aktywowanie usług hostowanych w odpowiedzi na komunikaty przychodzące. Najbardziej typowa Składnia pliku SVC znajduje się w poniższej instrukcji.

`<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>`

Składa się z [ \@dyrektywy ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) i jednego atrybutu, `Service`. Wartość `Service` atrybutu jest nazwą typu środowiska uruchomieniowego języka wspólnego (CLR) dla implementacji usługi. Użycie tej dyrektywy jest zasadniczo równoważne z tworzeniem hosta usługi przy użyciu następującego kodu.

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

Można również wykonać dodatkową konfigurację hostingu, taką jak tworzenie listy adresów podstawowych dla usługi. Możesz również użyć niestandardowej <xref:System.ServiceModel.Activation.ServiceHostFactory> do rozbudowania dyrektywy do użycia z niestandardowymi rozwiązaniami hostingu. Aplikacje usług IIS obsługujące usługi WCF nie są odpowiedzialne za zarządzanie tworzeniem i okresem <xref:System.ServiceModel.ServiceHost> istnienia wystąpień. Zarządzana infrastruktura hostingu WCF tworzy wymagane <xref:System.ServiceModel.ServiceHost> wystąpienie dynamicznie, gdy zostanie odebrane pierwsze żądanie dla pliku SVC. Wystąpienie nie jest wyłączane, dopóki nie zostanie zamknięte jawnie przez kod lub podczas odtwarzania aplikacji.

Aby uzyskać więcej informacji na temat składni plików SVC, zobacz [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Wdrażanie implementacji usługi w aplikacji usług IIS

Usługi WCF hostowane w usługach IIS używają tego samego dynamicznego modelu kompilacji, co ASP.NET 2,0. Podobnie jak w przypadku ASP.NET, można wdrożyć kod implementacji dla usług WCF hostowanych przez usługi IIS na kilka sposobów w różnych lokalizacjach w następujący sposób:

- Jako prekompilowany plik DLL znajdujący się w globalnej pamięci podręcznej zestawów (GAC) lub w katalogu \Bin aplikacji. Wstępnie skompilowane pliki binarne nie są aktualizowane do momentu wdrożenia nowej wersji biblioteki klas.

- Jako Nieskompilowane pliki źródłowe znajdują się w katalogu \App_Code aplikacji. Pliki źródłowe znajdujące się w tym katalogu są dynamicznie wymagane podczas przetwarzania pierwszego żądania aplikacji. Wszelkie zmiany w plikach w katalogu \App_Code powodują, że cała aplikacja zostanie odtworzona i ponownie skompilowana po odebraniu następnego żądania.

- Jako Nieskompilowany kod umieszczony bezpośrednio w pliku SVC. Kod implementacji może być również umieszczony w pliku SVC usługi po \@dyrektywie ServiceHost. Wszelkie zmiany w kodzie wbudowanym powodują, że aplikacja zostanie odtworzona i ponownie skompilowana po odebraniu następnego żądania.

Aby uzyskać więcej informacji na temat modelu kompilacji ASP.NET 2,0, zobacz [Omówienie kompilacji ASP.NET](https://go.microsoft.com/fwlink/?LinkId=94773).

## <a name="configure-the-wcf-service"></a>Konfigurowanie usługi WCF

Hostowane w usługach IIS usługi WCF przechowują konfigurację w pliku Web. config aplikacji. Usługi hostowane przez usługi IIS używają tych samych elementów konfiguracji i składni jako usług WCF hostowanych poza usługami IIS. Jednak następujące ograniczenia są unikatowe dla środowiska hostingu usług IIS:

- Adresy podstawowe dla usług hostowanych przez usługi IIS.

- Aplikacje obsługujące usługi WCF spoza usług IIS mogą kontrolować adres podstawowy usług, które są hosty, przekazując zestaw identyfikatorów URI adresów bazowych do <xref:System.ServiceModel.ServiceHost> konstruktora lub [ \<dostarczając > element hosta](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) w usłudze skonfigurować. Usługi hostowane w usługach IIS nie mają możliwości kontrolowania adresu podstawowego; adres podstawowy usługi hostowanej przez usługi IIS jest adresem pliku SVC.

### <a name="endpoint-addresses-for-iis-hosted-services"></a>Adresy punktów końcowych dla usług hostowanych przez usługi IIS

W przypadku hostowania w usługach IIS adresy punktów końcowych są zawsze uznawane za odnoszące się do adresu pliku SVC, który reprezentuje usługę. Na przykład jeśli adres podstawowy usługi WCF ma `http://localhost/Application1/MyService.svc` następującą konfigurację punktu końcowego:

```xml
<endpoint address="anotherEndpoint" .../>
```

Zapewnia to punkt końcowy, który można połączyć o `http://localhost/Application1/MyService.svc/anotherEndpoint`.

Analogicznie, element konfiguracji punktu końcowego, który używa pustego ciągu jako adresu względnego, zapewnia punkt `http://localhost/Application1/MyService.svc`końcowy, który jest dostępny pod adresem podstawowym.

```xml
<endpoint address="" ... />
```

Należy zawsze używać względnych adresów punktów końcowych dla punktów końcowych usług hostowanych przez usługi IIS. Dostarczenie w pełni kwalifikowanego adresu punktu końcowego (na przykład `http://localhost/MyService.svc`) może prowadzić do błędów w wdrożeniu usługi, jeśli adres punktu końcowego nie wskazuje aplikacji usług IIS, która hostuje punkt końcowy. Używanie względnych adresów punktów końcowych dla usług hostowanych pozwala uniknąć potencjalnych konfliktów.

### <a name="available-transports"></a>Dostępne transporty

Usługi WCF hostowane w usługach IIS 5,1 i IIS 6,0 są ograniczone do korzystania z komunikacji opartej na protokole HTTP. Na tych platformach usług IIS skonfigurowanie usługi hostowanej do korzystania z powiązania inne niż HTTP powoduje wystąpienie błędu podczas aktywacji usługi. W przypadku usług IIS 7,0 obsługiwane transporty obejmują protokoły HTTP, net. TCP, net. pipe, net. MSMQ i MSMQ. formatname w celu zapewnienia zgodności z poprzednimi wersjami z istniejącymi aplikacjami MSMQ.

### <a name="http-transport-security"></a>Zabezpieczenia transportu HTTP

Usługi WCF hostowane przez usługi IIS mogą korzystać z zabezpieczeń transportu HTTP (na przykład schematów uwierzytelniania HTTPS i HTTP, takich jak podstawowe, szyfrowane i zintegrowane uwierzytelnianie systemu Windows), o ile katalog wirtualny usług IIS zawierający usługę obsługuje te funkcje Ustawienia. Ustawienia zabezpieczeń transportu HTTP dla powiązania hostowanego punktu końcowego muszą być zgodne z ustawieniami zabezpieczeń transportu w katalogu wirtualnym usług IIS, który go zawiera.

Na przykład punkt końcowy programu WCF skonfigurowany do korzystania z uwierzytelniania szyfrowanego protokołu HTTP musi znajdować się w katalogu wirtualnym usług IIS, który jest również skonfigurowany do zezwalania na uwierzytelnianie szyfrowane protokołu HTTP. Niedopasowane kombinacje ustawień usług IIS i ustawień punktu końcowego WCF powodują wystąpienie błędu podczas aktywacji usługi.

## <a name="see-also"></a>Zobacz także

- [Hostowanie przez Internetowe usługi informacyjne](hosting-in-internet-information-services.md)
- [Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych](internet-information-services-hosting-best-practices.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://go.microsoft.com/fwlink/?LinkId=201276)
