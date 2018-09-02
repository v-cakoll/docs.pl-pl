---
title: Uruchamianie przykładów programu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: d6fc93af217bfc282ce7030973be32baf7d864cd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425778"
---
# <a name="running-the-windows-communication-foundation-samples"></a>Uruchamianie przykładów programu Windows Communication Foundation
Przykłady Windows Communication Foundation (WCF) mogą być uruchamiane w konfiguracji pojedynczego komputera lub między komputerami. Dostarczony, próbki są gotowe do uruchamiania na jednym komputerze. W konfiguracji między komputerami jest niezbędnej do modyfikacji ustawień pliku konfiguracji w próbce. Poniższe procedury dotyczą sposobu uruchamiania przykładu w tym samym komputerze, jak i między komputerami konfiguracji. Należy pamiętać, że istnieją różnice w krokach dla usług hostowanych w Internet Information Services (IIS) i samodzielnie hostowanej próbek. Większość przykładów są hostowane w usługach IIS; Zapoznaj się z informacjami readme próbki, aby określić, jak jest hostowana.  
  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)], przykłady, które nie są hostowane w usługach IIS wymaga podwyższonego poziomu uprawnień, aby zarejestrować odbiornik w pliku Http.sys. Umożliwia zarejestrowanie service nasłuchiwania adresów konto, na którym jest uruchomiona w ramach Httpcfg.exe, lub uruchom usługi z poziomu wiersza polecenia z uprawnieniami administratora.  
  
> [!NOTE]
>  Przed przystąpieniem do tworzenia lub z dowolnym przykłady WCF, upewnij się, kiedy została wykonana [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Jeśli usługa jest hostowana przez usługi IIS, upewnij się, czy można uzyskać dostęp do usługi, za pomocą przeglądarki, wpisując następujący adres: http://localhost/servicemodelsamples/service.svc. Strona potwierdzenia powinna być wyświetlana w odpowiedzi. Jeśli nie zostanie wyświetlona strona potwierdzenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
2.  Jeśli usługa jest samodzielnie hostowana, uruchom Service.exe \service\bin jest dostępna z folderu specyficzny dla języka. Działania usługi będzie wyświetlany w oknie konsoli usługi.  
  
3.  Uruchom Client.exe z \client\bin\\, jest dostępna z folderu specyficzny dla języka. Aktywność klienta jest wyświetlany w oknie konsoli klienta.  
  
4.  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-machines"></a>Do uruchomienia przykładu na komputerach  
  
1.  Jeśli usługa jest hostowana w usługach IIS:  
  
    1.  Na komputerze usługi należy utworzyć katalog wirtualny o nazwie ServiceModelSamples. Plik wsadowy dołączone Setupvroot.bat [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) może służyć do tworzenia katalogu na dysku i katalogu wirtualnego.  
  
    2.  Skopiuj pliki programu usługi z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples ServiceModelSamples katalogu wirtualnego na maszynie usługi. Upewnij się, obejmują pliki w katalogu \bin.  
  
    3.  Test, aby uzyskać dostęp do usługi z komputera klienckiego za pomocą przeglądarki.  
  
     Jeśli usługa jest samodzielnie hostowana:  
  
    1.  Na komputerze usługi należy utworzyć katalog do przechowywania plików usługi.  
  
    2.  Skopiuj pliki programu usługi z folderu \service\bin\ w folderze specyficzny dla języka maszyną usługi.  
  
    3.  W pliku konfiguracji usługi Zmień wartość adresu definicji punktu końcowego, aby dopasować nowy adres usługi. Zastąp wszystkie odwołania do "localhost" w pełni kwalifikowaną nazwę domeny w adresie.  
  
    4.  Uruchom Service.exe z poziomu wiersza polecenia.  
  
2.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.  
  
3.  Ustaw adres punktu końcowego.  
  
    1.  Jeśli usługa nie jest uruchomiona w ramach konta domeny, otwórz plik konfiguracji klienta, a następnie zmień wartość adresu definicji punktu końcowego, aby dopasować nowy adres usługi. Zastąp wszystkie odwołania do "localhost" w pełni kwalifikowaną nazwę domeny w adresie.  
  
    2.  Jeśli usługa jest uruchomiona w ramach konta domeny, należy ponownie wygenerować konfiguracji klienta, uruchamiając Svcutil.exe korzystająca z usługi. Aby uzyskać więcej informacji na temat uruchamiania Svcutil.exe, zobacz [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Użyj wygenerowanego pliku zamiast pliku konfiguracji w próbce. Wygenerowano plik konfiguracyjny zawiera informacje o dodatkowych tożsamości i zawiera wszystkie ustawienia wymagane do połączenia z punktu końcowego usługi, nawet jeśli są one ustawienia domyślne. Aby uzyskać więcej informacji o tożsamości, zobacz [uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), i [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).  
  
4.  Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia.  
  
### <a name="to-debug-a-service"></a>Aby debugować usługę  
  
1.  Rozwiązanie (klient i usługa), przy użyciu kompilacji **kompilacji** menu lub klawiszy CTRL + SHIFT + B.  
  
2.  Jeśli usługa jest hostowana w usługach IIS:  
  
    1.  Aktywuj usługę za pomocą przeglądarki, wprowadzając adres http://localhost/servicemodelsamples/service.svc.  
  
    2.  W rozwiązaniu, wybierz **debugowania** menu i **dołączyć do procesu** elementu menu.  
  
    3.  Wybierz **Pokaż procesy wszystkich użytkowników** pole wyboru.  
  
    4.  Wybierz host proces roboczy W3wp.exe do debugowania (Wybierz ASPNet_wp.exe Windows XP).  
  
3.  Możesz teraz ustawiać punkty przerwania w kodzie usługi i Włącz punkty przerwania przy wyjątkach.  
  
4.  Kliknij prawym przyciskiem myszy element projektu klienta, a następnie wybierz **debugowania**, **Uruchom nowe wystąpienie**.  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
-   Jeśli usługa jest hostowana w usługach IIS na potrzeby zabezpieczeń, należy usunąć z definicji katalogu wirtualnego i uprawnienia udzielone w ramach kroków konfiguracji, po zakończeniu pracy z próbek.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
 [Uruchamianie przykładów programu, w grupie roboczej, a na maszynach](https://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113)  
 [Wskazówki dotyczące rozwiązywania problemów](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)
