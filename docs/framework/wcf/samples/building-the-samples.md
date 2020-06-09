---
title: Kompilowanie przykładów programu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: 53599b3b1827651b48df9921bb59a679a36ee39c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592622"
---
# <a name="building-the-windows-communication-foundation-samples"></a>Kompilowanie przykładów programu Windows Communication Foundation

Przykłady Windows Communication Foundation (WCF) można skompilować przy użyciu środowiska IDE programu Visual Studio lub za pomocą polecenia **MSBuild** z wiersza polecenia. Obie procedury opisano w tym temacie.

> [!NOTE]
> Przed skompilowaniem lub uruchomieniem dowolnego z przykładów programu WCF upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

## <a name="to-build-the-sample-using-a-command-prompt"></a>Aby skompilować przykład za pomocą wiersza polecenia

1. Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio i przejdź do podkatalogu specyficznego dla języka w lokalizacji katalogu, w której zainstalowano przykład.

2. Wpisz `msbuild` w wierszu polecenia. Pliki programu klienckiego są kompilowane do *client\bin* , a pliki programu usługi są kompilowane do *service\bin*. Jeśli usługa jest hostowana przez Internet Information Services (IIS), pliki programu usługi są również kopiowane do katalogu *servicemodelsamples* i jego podkatalogu *\Bin* .

> [!NOTE]
> Należy ustawić listy ACL w *%SYSTEMDRIVE%\Inetpub\Wwwroot* , aby przyznać uprawnienia do modyfikowania na koncie, w ramach którego jest uruchomiony. W przeciwnym razie niektóre zdarzenia post nie powiodą się. Alternatywnie można pozostawić listy kontroli dostępu i uruchomić wiersz polecenia zestawu SDK jako administrator.

## <a name="to-build-the-sample-using-visual-studio"></a>Aby skompilować przykład za pomocą programu Visual Studio

1. W menu **plik** w programie Visual Studio wybierz pozycję **Otwórz**  >  **projekt/rozwiązanie**. Przejdź do podkatalogu specyficznego dla języka w katalogu, w którym zainstalowano przykład, a następnie kliknij dwukrotnie ikonę pliku. sln, aby otworzyć rozwiązanie w programie Visual Studio.

1. Z menu **kompilacja** wybierz opcję **Kompiluj ponownie rozwiązanie**.

   Pliki programu klienckiego są kompilowane do client\bin, a pliki programu usługi są kompilowane do service\bin. Jeśli usługa jest hostowana w usługach IIS, pliki programu usługi są również kopiowane do katalogu *servicemodelsamples* i jego podkatalogu *\Bin* .

> [!NOTE]
> Należy ustawić listy ACL w%systemdrive%\Inetpub\Wwwroot, aby przyznać uprawnienia do modyfikowania na koncie, w ramach którego jest uruchomiony. W przeciwnym razie niektóre zdarzenia post nie powiodą się. Alternatywnie można pozostawić listy kontroli dostępu i uruchomić wiersz polecenia zestawu SDK lub program Visual Studio jako administrator. Niektóre akcje programu Visual Studio (takie jak dołączenie debugera do procesu roboczego ASP.Net) wymagają również uprawnień administracyjnych.

## <a name="setup-batch-files-and-scripts"></a>Konfigurowanie plików i skryptów wsadowych
 Pliki i skrypty wsadowe Setup. exe i Cleanup. exe powinny być uruchamiane z wiersz polecenia dla deweloperów dla programu Visual Studio. Kilka konfiguracji i oczyszczania plików wykonuje zadania, które wymagają uprawnień administracyjnych i powinny być uruchamiane z uprawnieniami administratora.

## <a name="important-security-information-about-metadata-endpoints"></a>Ważne informacje o zabezpieczeniach punktów końcowych metadanych
 Aby zapobiec przypadkowemu ujawnieniu potencjalnie poufnych metadanych usługi, konfiguracja domyślna dla usług Windows Communication Foundation (WCF) wyłącza Publikowanie metadanych. To zachowanie jest domyślnie bezpieczne, ale oznacza to, że nie można użyć narzędzia do importowania metadanych (takiego jak Svcutil. exe) w celu wygenerowania kodu klienta wymaganego do wywołania usługi, chyba że zachowanie publikowania metadanych usługi jest jawnie włączone w konfiguracji. Aby ułatwić eksperymentowanie z przykładami, prawie wszystkie przykłady uwidaczniają niezabezpieczony punkt końcowy publikowania metadanych. Takie punkty końcowe są potencjalnie dostępne dla anonimowych użytkowników nieuwierzytelnionych i należy zachować ostrożność przed wdrożeniem takich punktów końcowych, aby upewnić się, że można publicznie odzamknąć metadane usługi. Aby uzyskać więcej informacji na temat publikowania metadanych usługi, zobacz przykład [zachowania publikowania metadanych](metadata-publishing-behavior.md) . Zapoznaj się z przykładem [niestandardowego bezpiecznego punktu końcowego metadanych](custom-secure-metadata-endpoint.md) w celu uzyskania przykładowego zabezpieczenia punktu końcowego metadanych.

## <a name="exception-handling"></a>Obsługa wyjątków
 Ogólnie mówiąc, te próbki nie obejmują obsługi wyjątków, aby zachować kod skoncentrowany na temacie przykładu. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz przykład [oczekiwanych wyjątków](expected-exceptions.md) .

## <a name="regenerating-clients-and-configuration-with-svcutil"></a>Ponowne generowanie klientów i konfiguracji za pomocą Svcutil
 Aby wygenerować kod i konfigurację klienta większości przykładów, można użyć [Narzędzia do przesyłania metadanych (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) . Niektóre przykłady wymagają ręcznej edycji konfiguracji. Jeśli na przykład używasz programu Svcutil. exe, aby ponownie wygenerować konfigurację dla przykładu, który używa poświadczeń certyfikatu klienta, musisz ręcznie określić wcześniej skonfigurowane poświadczenia. Niektóre przykłady używają określonych opcji Svcutil. exe, aby wpływać na wygenerowany kod, te opcje są określone w określonych przykładowych tematach.

### <a name="to-regenerate-the-client-and-configuration-files"></a>Aby ponownie wygenerować pliki klienta i konfiguracji

1. Otwórz wiersz polecenia zestawu SDK i przejdź do podkatalogu specyficznego dla języka w lokalizacji katalogu, w której zainstalowano przykład.

2. Jeśli usługa jest typem hostowanym w sieci Web, użyj następującego polecenia.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Jeśli usługa jest typem własnym, wpisz następujące polecenie.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Zamień `http://localhost:8000/ServiceModelSamples/service.svc/mex` na adres punktu końcowego MEX usługi samodzielnej.

     Aby wygenerować klienta w typie Visual Basic, użyj następującego polecenia.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     Jeśli usługa jest typem własnym, użyj następującego polecenia.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > Aby pominąć generowanie konfiguracji klienta, Dodaj opcję **/noconfig** .

## <a name="see-also"></a>Zobacz też

- [Uruchamianie przykładów programu Windows Communication Foundation](running-the-samples.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
