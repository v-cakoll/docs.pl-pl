---
title: Kompilowanie przykładów programu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: 46f4015c00916a5cab932e8fd2539c7c86588a30
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264652"
---
# <a name="building-the-windows-communication-foundation-samples"></a>Kompilowanie przykładów programu Windows Communication Foundation

Mogą być wbudowane przykładów Windows Communication Foundation (WCF), za pomocą środowiska IDE programu Visual Studio lub **msbuild** polecenie w wierszu polecenia. Obie procedury są opisane w tym temacie.

> [!NOTE]
> Przed przystąpieniem do tworzenia lub z dowolnym przykłady WCF, upewnij się, kiedy została wykonana [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

## <a name="to-build-the-sample-using-a-command-prompt"></a>Aby skompilować przykład za pomocą wiersza polecenia

1.  Otwórz wiersz polecenia dla deweloperów programu Visual Studio i przejdź do podkatalogu specyficzny dla języka, w lokalizacji katalogu, w której zainstalowany próbki.

2.  Typ `msbuild` w wierszu polecenia. Pliki programu klienta zostały opracowane w celu *client\bin* i plików programu usługi zostały opracowane w celu *service\bin*. Jeśli usługa jest obsługiwana przez Internetowe usługi informacyjne (IIS), plików programu usługi są również kopiowane do *servicemodelsamples* katalogu i jego *\bin* podkatalogu.

> [!NOTE]
> Listy ACL należy ustawić na *%systemdrive%\inetpub\wwwroot* udzielenia modyfikowania uprawnień do konta, w którym są uruchomione. W przeciwnym razie niektóre po awarii zdarzeń kompilacji. Alternatywnie można pozostawić listy ACL, i uruchom wiersz polecenia zestawu SDK jako administrator.

## <a name="to-build-the-sample-using-visual-studio"></a>Aby skompilować przykład za pomocą programu Visual Studio

1. Z **pliku** menu w programie Visual Studio, wybierz **Otwórz** > **projekt/rozwiązanie**. Przejdź do podkatalogu specyficzny dla języka w katalogu, w którym zainstalowano próbki, a następnie kliknij dwukrotnie ikonę pliku .sln, aby otworzyć rozwiązanie w programie Visual Studio.

1. Z **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.

   Pliki programu klienta zostały opracowane w celu client\bin i plików programu usługi zostały opracowane w celu service\bin. Jeśli usługa jest hostowana w usługach IIS, pliki programów service również są kopiowane do *servicemodelsamples* katalogu i jego *\bin* podkatalogu.

> [!NOTE]
> Musisz ustawić list ACL %systemdrive%\inetpub\wwwroot udzielenia modyfikowania uprawnień do konta, w którym są uruchomione. W przeciwnym razie niektóre po awarii zdarzeń kompilacji. Alternatywnie można pozostawić listy ACL, i uruchom wiersz polecenia zestawu SDK lub programu Visual Studio jako administrator. Niektóre akcje programu Visual Studio (na przykład dołączanie debugera do procesu roboczego ASP.Net) również wymagają uprawnień administratora.

## <a name="setup-batch-files-and-scripts"></a>Pliki wsadowe Instalatora i skryptów
 Setup.exe i Cleanup.exe pliki wsadowe i skryptów można uruchamiać z wiersza polecenia dla deweloperów programu Visual Studio. Kilka zestawu w górę i oczyszczania plików wykonywania zadań, które wymagają uprawnień administratora i powinien zostać uruchomiony z uprawnieniami administratora.

## <a name="important-security-information-about-metadata-endpoints"></a>Ważne informacje dotyczące zabezpieczeń dotyczące punktów końcowych metadanych
 Aby zapobiegać niezamierzonym ujawnieniem metadanych usługi potencjalnie poufnych, konfigurację domyślną dla usług Windows Communication Foundation (WCF) powoduje wyłączenie publikowania metadanych. To zachowanie jest domyślnie bezpieczny, ale również zaimportować narzędzia (takie jak Svcutil.exe) oznacza, że metadane nie można użyć do wygenerowania kodu klienta wymaganych do wywołania tej usługi, chyba że jawnie włączone jest zachowanie publikowania metadanych usługi w konfiguracji. Aby upewnić się, eksperymentowania z przykładów łatwiejsze, prawie wszystkie przykłady uwidocznić punkt końcowy publikowania metadanych niezabezpieczona. Takie punkty końcowe są potencjalnie dostępne dla anonimowe, nieuwierzytelnione konsumentów i należy uważać, przed wdrożeniem tych punktów końcowych w celu zapewnienia publicznie ujawniająca metadanych usługi odpowiednie. Aby uzyskać więcej informacji na temat publikowania metadanych usługi, zobacz [zachowanie publikowania metadanych](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md) próbki. Zobacz [niestandardowy bezpieczny punkt końcowy metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) przykładowe przykład zabezpieczenia punktu końcowego metadanych.

## <a name="exception-handling"></a>Obsługa wyjątków
 Ogólnie rzecz biorąc te przykłady nie obejmują obsługi wyjątków, aby zachować zgodność kodu koncentruje się na ten temat próbki. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [oczekiwane wyjątki](../../../../docs/framework/wcf/samples/expected-exceptions.md) próbki.

## <a name="regenerating-clients-and-configuration-with-svcutil"></a>Trwa ponowne generowanie klientów i konfiguracji za pomocą narzędzia Svcutil
 Możesz użyć [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ponownego generowania kodu klienta i konfiguracji dla większości próbek. Niektóre przykłady wymagają konfiguracji ręcznie edytowane. Na przykład w przypadku używasz Svcutil.exe ponownego generowania konfiguracji dla przykładu, który używa poświadczeń certyfikatu klienta muszą ręcznie określić poświadczeń wcześniej skonfigurowane. Przykłady wpływa na kod wygenerowany przy użyciu określonych opcji Svcutil.exe, te opcje są określone w tematach określonych przykładowe.

### <a name="to-regenerate-the-client-and-configuration-files"></a>Aby ponownie wygenerować pliki klienta i konfiguracji

1.  Otwórz wiersz polecenia z zestawu SDK i przejdź do podkatalogu specyficzny dla języka, w lokalizacji katalogu, w której zainstalowany próbki.

2.  Jeśli usługa jest typem hostowanych w sieci Web, użyj następującego polecenia.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Jeśli usługa jest Self-Hosted wpisz następujące polecenie.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Zastąp http://localhost:8000/ServiceModelSamples/service.svc/mex przy użyciu adresu punktu końcowego mex samodzielnie hostowanej usługi.

     Aby wygenerować klienta w typie języka Visual Basic, użyj następującego polecenia.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     Jeśli usługa jest typem Self-Hosted, użyj następującego polecenia.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > Aby pominąć generowanie konfiguracji klienta należy dodać **/noconfig** opcji.

## <a name="see-also"></a>Zobacz też

- [Uruchamianie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
