---
title: "Uruchamianie przykładów programu Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3003c89b0cfcda9866c5b1accd154900bc650454
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="running-the-windows-communication-foundation-samples"></a>Uruchamianie przykładów programu Windows Communication Foundation
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Próbki mogą być uruchamiane w konfiguracji pojedynczego komputera lub między komputerami. Dostarczony, próbki są gotowe do uruchamiania na jednym komputerze. W konfiguracji między komputerami należy zmodyfikować ustawienia pliku konfiguracji na próbkę. Poniższe procedury dotyczą sposobu uruchamiania próbkę w tym samym komputerze lub między komputerami konfiguracje. Należy pamiętać, że zmiany w opisach usług hostowanych w Internet Information Services (IIS) i hostowanie Samoobsługowe próbek. Większość przykładów są hostowane w usługach IIS; Zapoznaj się z informacjami readme próbki ustalenie, jak jest obsługiwana.  
  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)], przykłady, które nie są obsługiwane w usługach IIS wymaga podwyższonego poziomu uprawnień, aby zarejestrować odbiornik przy użyciu składnika Http.sys. Użyj Httpcfg.exe, aby zarejestrować adresy nasłuchiwania usługi przy użyciu konta, które usługa jest uruchomiona w obszarze, lub uruchom usługi z wiersza polecenia z uprawnieniami administratora.  
  
> [!NOTE]
>  Tworzenie lub z dowolnym z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] próbek, pamiętaj, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Jeśli usługa jest obsługiwana przez usługi IIS, upewnij się, że masz dostęp usługi przy użyciu przeglądarki wprowadź następujący adres: http://localhost/servicemodelsamples/service.svc. Powinna być wyświetlana strona potwierdzenia w odpowiedzi. Jeśli nie zostanie wyświetlona strona potwierdzenia, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
2.  Jeśli usługa własnym jest obsługiwana, należy uruchomić Service.exe z \service\bin z folderu specyficzny dla języka. Działanie usługi jest wyświetlany w oknie konsoli usługi.  
  
3.  Uruchom Client.exe z \client\bin\\, z folderu specyficzny dla języka. Aktywność klienta jest wyświetlany w oknie konsoli klienta.  
  
4.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-machines"></a>Aby uruchomić przykład na komputerach  
  
1.  Jeśli usługa jest obsługiwana w usługach IIS:  
  
    1.  Na komputerze usługi należy utworzyć katalog wirtualny o nazwie ServiceModelSamples. Plik wsadowy dołączonego Setupvroot.bat [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) może służyć do tworzenia katalogu na dysku i katalog wirtualny.  
  
    2.  Skopiuj pliki programu usługi z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego ServiceModelSamples na komputerze usługi. Upewnij się, obejmują pliki w katalogu \bin.  
  
    3.  Aby uzyskać dostęp do usługi z komputera klienta przy użyciu przeglądarki testu.  
  
     Jeśli usługa jest samodzielnie hostowana:  
  
    1.  Na komputerze usługi należy utworzyć katalog do przechowywania plików usługi.  
  
    2.  Skopiuj pliki programu usługi z folderu \service\bin\ w folderze danego języka maszyną usługi.  
  
    3.  W pliku konfiguracji usługi Zmień wartość adresu definicji punktu końcowego do dopasowania nowy adres z usługą. Zamień wszystkie odwołania do "localhost" pełni kwalifikowanej nazwy domeny w adresie.  
  
    4.  Uruchom Service.exe z wiersza polecenia.  
  
2.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka, do komputera klienckiego.  
  
3.  Ustaw adres punktu końcowego.  
  
    1.  Jeśli usługa nie jest uruchomiona w ramach konta domeny, otwórz plik konfiguracji klienta i zmień wartość adresu definicji punktu końcowego do dopasowania nowy adres z usługą. Zamień wszystkie odwołania do "localhost" pełni kwalifikowanej nazwy domeny w adresie.  
  
    2.  Jeśli usługa jest uruchomiona w ramach konta domeny, należy ponownie wygenerować konfiguracji klienta, uruchamiając Svcutil.exe z usługą. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Uruchamianie Svcutil.exe, zobacz [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Użyj wygenerowanego pliku zamiast pliku konfiguracji w próbce. Wygenerowano plik konfiguracyjny zawiera informacje o dodatkowych tożsamości i zawiera wszystkie ustawienia niezbędne do połączenia z punktem końcowym usługi, nawet jeśli są one ustawienia domyślne. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]informacje o tożsamości, zobacz [uwierzytelnianie i tożsamość usługi](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), i [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).  
  
4.  Na komputerze klienckim należy uruchomić Client.exe z wiersza polecenia.  
  
### <a name="to-debug-a-service"></a>Aby debugować usługi  
  
1.  Tworzenie przy użyciu rozwiązania (klient i usługa) **kompilacji** menu lub CTRL + SHIFT + B.  
  
2.  Jeśli usługa jest obsługiwana w usługach IIS:  
  
    1.  Aktywowanie usługi, wprowadzając adres http://localhost/servicemodelsamples/service.svc przy użyciu przeglądarki.  
  
    2.  W rozwiązaniu, wybierz **debugowania** menu i **dołączyć do procesu** elementu menu.  
  
    3.  Wybierz **Pokaż procesy wszystkich użytkowników** pole wyboru.  
  
    4.  Wybierz proces roboczy hosta W3wp.exe debugowania (Wybierz ASPNet_wp.exe w systemie Windows XP).  
  
3.  Teraz można ustawić punktów przerwania w kodzie usługi i włączyć punkty przerwania w wyjątków.  
  
4.  Kliknij prawym przyciskiem myszy element projektu klienta, a następnie wybierz pozycję **debugowania**, **Start nowe wystąpienie**.  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
-   Jeśli usługa jest obsługiwana w usługach IIS ze względów bezpieczeństwa, Usuń katalog wirtualny definicji i uprawnienia w ramach kroków konfiguracji, po zakończeniu pracy z próbek.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
 [Uruchomione z próbek w grupie roboczej i na komputerach](http://msdn.microsoft.com/en-us/a451a525-e7ce-452d-9da9-620221260113)  
 [Porady dotyczące rozwiązywania problemów](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)
