---
title: "Kompilowanie przykładów programu Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26a47e6ea0d93d81275d7b3b87c88d0d3ab595df
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="building-the-windows-communication-foundation-samples"></a>Kompilowanie przykładów programu Windows Communication Foundation
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Próbki mogą być tworzone przy użyciu programu Visual Studio 2010 lub **msbuild** polecenie w wierszu polecenia. Zarówno procedury opisane w tym temacie.  
  
> [!NOTE]
>  Tworzenie lub z dowolnym z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] próbek, upewnij się, mogły być wykonane [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-build-the-sample-using-a-command-prompt"></a>Aby samodzielnie tworzyć przykładowy przy użyciu wiersza polecenia  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersz z uprawnieniami administratora polecenia i przejdź do podkatalogu specyficzne dla języka w obszarze na lokalizację katalogu, w którym zainstalowano próbki.  
  
2.  Typ `msbuild` w wierszu polecenia. Pliki programu klienta są przeznaczone do client\bin i pliki programu usługi są przeznaczone do service\bin. Jeśli usługa jest obsługiwana przez Internet Information Services (IIS), pliki programu usługi są również kopiowane do katalogu servicemodelsamples i jej podkatalog \bin.  
  
> [!NOTE]
>  Należy ustawić listy ACL na %systemdrive%\inetpub\wwwroot udzielenia modyfikowania uprawnień do konta, na którym są uruchomione. W przeciwnym razie niektóre po kompilacji zdarzenia błędów. Alternatywnie można pozostawić listy kontroli dostępu i uruchom SDK wiersz polecenia jako administrator.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Aby samodzielnie tworzyć przykładowy przy użyciu programu Visual Studio  
  
1.  Jeśli używasz [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 lub Windows Server 2008 R2, a także program [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], należy uruchomić [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] z podwyższonym poziomem uprawnień. Aby to zrobić, kliknij prawym przyciskiem myszy ikonę w Start menu, a następnie kliknij przycisk **Uruchom jako administrator**.  
  
2.  Z **pliku** w menu [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], kliknij przycisk **Otwórz**, następnie kliknij przycisk **projektu/rozwiązania**. Przejdź do podkatalogu specyficzne dla języka w katalogu, w którym zainstalowano próbki, a następnie kliknij dwukrotnie ikonę pliku SLN, aby otworzyć rozwiązanie w [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
3.  W **kompilacji** menu, wybierz opcję **Kompiluj ponownie rozwiązanie**. Pliki programu klienta są przeznaczone do client\bin i pliki programu usługi są przeznaczone do service\bin. Jeśli usługa jest obsługiwana w usługach IIS, pliki programu usługi są również kopiowane do katalogu servicemodelsamples i jej podkatalog \bin.  
  
> [!NOTE]
>  Należy ustawić listy ACL na %systemdrive%\inetpub\wwwroot udzielenia modyfikowania uprawnień do konta, na którym są uruchomione. W przeciwnym razie niektóre po kompilacji zdarzenia błędów. Alternatywnie można pozostawić listy kontroli dostępu i uruchom wiersz polecenia zestawu SDK lub Visual Studio jako administrator. Niektóre akcje programu Visual Studio (takich jak dołączanie debugera do procesu roboczego ASP.Net) wymagają również uprawnienia administracyjne.  
  
## <a name="setup-batch-files-and-scripts"></a>Pliki wsadowe Instalatora i skryptów  
 Pliki wsadowe Setup.exe i Cleanup.exe i skrypty powinien zostać uruchomiony z wiersza polecenia programu Visual Studio. Kilka zestawu w górę i oczyszczania plików wykonywanie zadań, które wymagają uprawnień administratora i powinna być uruchamiana z uprawnieniami administratora.  
  
## <a name="important-security-information-about-metadata-endpoints"></a>Ważne informacje dotyczące zabezpieczeń dotyczące punkty końcowe metadanych  
 Aby zapobiec przypadkowe ujawnienie metadanych usługi potencjalnie poufnych, konfigurację domyślną dla [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usług wyłącza Publikowanie metadanych. To zachowanie jest domyślnie bezpieczne, ale również zaimportować narzędzia (na przykład Svcutil.exe) oznacza, że metadane nie można użyć do generowania kodu klienta wymaganych do wywołania tej usługi, chyba że jawnie włączone jest zachowanie podczas publikowania metadanych usługi w konfiguracji. Aby eksperymentowanie z próbek łatwiejsze, prawie wszystkie próbki ujawniać punkt końcowy publikowania metadanych niezabezpieczona. Takie punkty końcowe są potencjalnie dostępne dla anonimowych użytkowników nieuwierzytelnionych i należy uważać przed wdrożeniem takich punktów końcowych w celu zapewnienia publicznie ujawniająca metadanych usługi odpowiednie. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Publikowanie metadanych usługi, zobacz [zachowanie podczas publikowania metadanych](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md) próbki. Zobacz [punktu końcowego metadanych niestandardowy bezpieczny](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) przykładowa przykładowe zabezpieczanie punktu końcowego metadanych.  
  
## <a name="exception-handling"></a>Obsługa wyjątków  
 Ogólnie rzecz biorąc, te przykłady nie obejmują obsługi wyjątków, aby zachować koncentruje się na temat próbki kodu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Obsługa wyjątków, zobacz [oczekiwane wyjątki](../../../../docs/framework/wcf/samples/expected-exceptions.md) próbki.  
  
## <a name="regenerating-clients-and-configuration-with-svcutil"></a>Trwa ponowne generowanie klientów i konfiguracji z narzędzia Svcutil  
 Można użyć [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można ponownie wygenerować kod klienta i konfiguracji dla większości próbek. Niektóre przykłady wymagają konfiguracji ręcznie edytowane. Na przykład jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla przykładu, który używa poświadczeń certyfikatu klienta, muszą ręcznie określić poświadczenia, wcześniej skonfigurowany. Niektóre przykłady użycia określonych opcji Svcutil.exe wpływ na wygenerowany kod, te opcje są określone w tematy szczególnych próbek.  
  
#### <a name="to-regenerate-the-client-and-configuration-files"></a>Można ponownie wygenerować pliki klienta i konfiguracji  
  
1.  Otwórz wiersz polecenia z zestawu SDK i przejdź do podkatalogu specyficzne dla języka w obszarze na lokalizację katalogu, w którym zainstalowano próbki.  
  
2.  Jeśli usługa jest typem hostowanych w sieci Web, użyj następującego polecenia.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     Jeśli usługa jest samodzielnie hostowana wpisz następujące polecenie.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     Zastąp http://localhost:8000/ServiceModelSamples/service.svc/mex adres punktu końcowego mex samodzielnie hostowana usługa.  
  
     Aby wygenerować klienta w typie Visual Basic, użyj następującego polecenia.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
     Jeśli usługa jest siebie typu, użyj następującego polecenia.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
    > [!NOTE]
    >  Aby pominąć generowanie konfiguracji klienta dodać **/noconfig** opcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md)  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
