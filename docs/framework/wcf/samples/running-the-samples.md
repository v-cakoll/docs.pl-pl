---
title: Uruchamianie przykładów programu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: df984f2464084948cdaa51dab96554de9400911f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965498"
---
# <a name="running-the-windows-communication-foundation-samples"></a>Uruchamianie przykładów programu Windows Communication Foundation
Przykłady Windows Communication Foundation (WCF) można uruchamiać w konfiguracjach na jednym lub wielu komputerach. Jak przedstawiono, przykłady są gotowe do uruchomienia na pojedynczym komputerze. W konfiguracji między maszynami należy zmodyfikować ustawienia przykładowego pliku konfiguracji. W poniższych procedurach opisano sposób uruchamiania przykładu w konfiguracjach tego samego komputera i wielu maszyn. Należy zauważyć, że istnieją różne kroki dotyczące usług hostowanych w Internet Information Services (IIS) i własnych przykładowych. Większość przykładów jest hostowana w usługach IIS. Zobacz informacje dotyczące przykładowego pliku Readme, aby określić, w jaki sposób jest hostowany.  
  
 W [!INCLUDE[wv](../../../../includes/wv-md.md)]systemie przykłady, które nie są hostowane w usługach IIS, wymagają podwyższonego poziomu uprawnień do zarejestrowania odbiornika przy użyciu protokołu HTTP. sys. Użyj HttpCfg. exe, aby zarejestrować adresy nasłuchujące usługi przy użyciu konta, w ramach którego usługa jest uruchomiona, lub uruchomić usługę z wiersza polecenia z uprawnieniami administratora.  
  
> [!NOTE]
> Przed skompilowaniem lub uruchomieniem dowolnego z przykładów programu WCF upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze  
  
1. Jeśli usługa jest hostowana przez usługi IIS, upewnij się, że możesz uzyskać dostęp do usługi przy użyciu przeglądarki, wprowadzając następujący `http://localhost/servicemodelsamples/service.svc`adres:. W odpowiedzi powinna zostać wyświetlona strona potwierdzenia. Jeśli strona potwierdzenia nie jest wyświetlana, zobacz [wskazówki dotyczące rozwiązywania problemów z](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))przykładami WCF.  
  
2. Jeśli usługa jest samodzielna, uruchom program Service. exe z \service\bin, z poziomu folderu specyficznego dla języka. Działanie usługi jest wyświetlane w oknie konsoli usługi.  
  
3. Uruchom program Client. exe z\\\client\bin, z poziomu folderu specyficznego dla języka. Aktywność klienta jest wyświetlana w oknie konsoli klienta.  
  
4. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Aby uruchomić przykład na wielu maszynach  
  
1. Jeśli usługa jest hostowana w usługach IIS:  
  
    1. Na maszynie usługi Utwórz katalog wirtualny o nazwie ServiceModelSamples. Plik wsadowy Setupvroot. bat dołączony do [procedury konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) można użyć do utworzenia katalogu dysku i katalogu wirtualnego.  
  
    2. Skopiuj pliki programu usługi z%SystemDrive%\Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego ServiceModelSamples na maszynie usługi. Upewnij się, że pliki zostały uwzględnione w katalogu \Bin.  
  
    3. Sprawdź, czy możesz uzyskać dostęp do usługi z komputera klienckiego za pomocą przeglądarki.  
  
     Jeśli usługa jest samoobsługowa:  
  
    1. Na maszynie usługi Utwórz katalog do przechowywania plików usługi.  
  
    2. Skopiuj pliki programu Service Files z folderu \service\bin\, w obszarze folder specyficzny dla języka, do maszyny usługi.  
  
    3. W pliku konfiguracji usługi Zmień wartość adresu definicji punktu końcowego, aby odpowiadała nowemu adresowi usługi. Zastąp wszystkie odwołania do "localhost" z w pełni kwalifikowaną nazwą domeny w adresie.  
  
    4. Uruchom polecenie Service. exe z wiersza polecenia.  
  
2. Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputera klienckiego.  
  
3. Ustaw adres punktu końcowego.  
  
    1. Jeśli usługa nie jest uruchomiona na koncie domeny, należy otworzyć plik konfiguracji klienta i zmienić wartość adresu definicji punktu końcowego, aby odpowiadała nowemu adresowi usługi. Zastąp wszystkie odwołania do "localhost" z w pełni kwalifikowaną nazwą domeny w adresie.  
  
    2. Jeśli usługa jest uruchomiona w ramach konta domeny, należy ponownie wygenerować konfigurację klienta, uruchamiając program Svcutil. exe w usłudze. Aby uzyskać więcej informacji na temat uruchamiania programu Svcutil. exe, zobacz [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Użyj wygenerowanego pliku zamiast pliku konfiguracji w przykładzie. Wygenerowany plik konfiguracji zawiera dodatkowe informacje o tożsamości i zawiera wszystkie ustawienia niezbędne do nawiązania połączenia z punktem końcowym usługi, mimo że są to ustawienia domyślne. Aby uzyskać więcej informacji na temat informacji o tożsamościach, zobacz [tożsamość usługi i uwierzytelnianie](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)oraz [ \<> tożsamości](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).  
  
4. Na komputerze klienckim uruchom program Client. exe z wiersza polecenia.  
  
### <a name="to-debug-a-service"></a>Aby debugować usługę  
  
1. Skompiluj rozwiązanie (zarówno klient, jak i usługa) przy użyciu menu **kompilacja** lub Ctrl + Shift + B.  
  
2. Jeśli usługa jest hostowana w usługach IIS:  
  
    1. Aktywuj usługę przy użyciu przeglądarki, wprowadzając adres `http://localhost/servicemodelsamples/service.svc`.  
  
    2. W rozwiązaniu wybierz menu **Debuguj** i element menu **Dołącz do procesu** .  
  
    3. Zaznacz pole wyboru **Pokaż procesy wszystkich użytkowników** .  
  
    4. Wybierz proces roboczy hosta w3wp. exe do debugowania (wybierz polecenie ASPNet_wp. exe w systemie Windows XP).  
  
3. Teraz można ustawić punkty przerwania w kodzie usługi i włączyć punkty przerwania na wyjątkach.  
  
4. Kliknij prawym przyciskiem myszy element projektu klienta i wybierz polecenie **Debuguj**, **Uruchom nowe wystąpienie**.  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
- Jeśli usługa jest hostowana w usługach IIS ze względów bezpieczeństwa, usuń definicję katalogu wirtualnego i uprawnienia przyznane w procedurach instalacji po zakończeniu pracy z przykładami.  
  
## <a name="see-also"></a>Zobacz także

- [Kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)
- [Wskazówki dotyczące rozwiązywania problemów z przykładami WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))
