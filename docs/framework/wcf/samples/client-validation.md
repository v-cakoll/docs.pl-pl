---
title: Walidacja klienta
ms.date: 03/30/2017
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
ms.openlocfilehash: 6e34ca8e1bb14f610e363c02eaeb94b7fa5e27c7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808289"
---
# <a name="client-validation"></a>Walidacja klienta
Usługi często Publikowanie metadanych, aby włączyć automatyczne generowanie i konfigurowanie typów serwera proxy klienta. Jeśli usługa nie jest zaufany, aplikacje klienckie należy zweryfikować, że metadane odpowiada aplikacji klienckiej zasad dotyczących zabezpieczeń, transakcje, typ kontraktu usługi i tak dalej. W poniższym przykładzie pokazano, jak napisać klienta zachowania punktu końcowego, która weryfikuje punktu końcowego usługi, aby upewnić się, że tego punktu końcowego usługi jest bezpiecznie korzystać.  
  
 Usługa udostępnia cztery punkty końcowe usługi. Pierwszym punktem końcowym używa WSDualHttpBinding, drugiego punktu końcowego jest używane uwierzytelnianie NTLM, trzeci punktu końcowego umożliwia przepływu transakcji, a czwarta punkt końcowy korzysta z uwierzytelniania opartego na certyfikatach.  
  
 Klient używa <xref:System.ServiceModel.Description.MetadataResolver> klasy do pobierania metadanych dla usługi. Klient wymusza zasady zabronienia dwustronnego wiązań, uwierzytelnianie NTLM i za pomocą zachowania sprawdzania poprawności przepływu transakcji. Dla każdego <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienia zaimportowane z metadanych usługi, aplikacja kliencka dodaje wystąpienie `InternetClientValidatorBehavior` zachowania punktu końcowego do <xref:System.ServiceModel.Description.ServiceEndpoint> przed podjęciem próby nawiązania połączenia za pomocą klienta usługi Windows Communication Foundation (WCF) punkt końcowy. To zachowanie `Validate` metody jest uruchamiany przed są nazywane żadnych operacji w usłudze i wymusza zasady klienta przez zgłaszanie `InvalidOperationExceptions`.  
  
### <a name="to-build-the-sample"></a>Aby samodzielnie tworzyć przykładowy  
  
1.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Otwórz wiersz polecenia programu Visual Studio z uprawnieniami administratora i uruchom pliku Setup.bat z folderu instalacyjnego próbki. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
2.  Uruchom aplikację usługi z \service\bin\Debug.  
  
3.  Uruchom aplikację klienta z \client\bin\Debug. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
4.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
5.  Usuń certyfikaty, uruchamiając Cleanup.bat po zakończeniu z próbką. Inne przykłady zabezpieczeń za pomocą tego samego certyfikatów.  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na komputerach  
  
1.  Na serwerze, w wierszu polecenia programu Visual Studio uruchomione z uprawnieniami administratora, wpisz `setup.bat service`. Uruchomiona `setup.bat` z `service` argument tworzy certyfikat usługi z domeny w pełni kwalifikowaną nazwę komputera i wyeksportuj certyfikat usługi do pliku o nazwie Service.cer.  
  
2.  Na serwerze edytowanie pliku App.config, aby odzwierciedlić nową nazwę certyfikatu. Oznacza to, zmień `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elementu, aby w pełni kwalifikowaną nazwą domeny komputera.  
  
3.  Skopiuj plik Service.cer z katalogu usług do katalogu klienta na komputerze klienckim.  
  
4.  Na komputerze klienckim, otwórz wiersz polecenia programu Visual Studio z uprawnieniami administratora i wpisz `setup.bat client`. Uruchomiona `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie Client.com i wyeksportuj certyfikat klienta do pliku o nazwie Client.cer.  
  
5.  W pliku client.cs Zmień wartość adresu punktu końcowego MEX i `findValue` ustawienia domyślnego certyfikatu serwera do dopasowania nowy adres z usługą. Aby to zrobić, zastępując localhost w pełni kwalifikowaną nazwą domeny serwera. Skompiluj ponownie.  
  
6.  Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
7.  Na komputerze klienckim należy uruchomić ImportServiceCert.bat w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora. Certyfikat usługi to importuje z pliku Service.cer do CurrentUser - TrustedPeople magazynu.  
  
8.  Na serwerze należy uruchomić ImportClientCert.bat w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora. Certyfikat klienta to importuje z pliku Client.cer do LocalMachine - TrustedPeople magazynu.  
  
9. Na komputerze, usługi Skompiluj projekt usługi w programie Visual Studio i uruchom service.exe.  
  
10. Uruchom client.exe na komputerze klienckim.  
  
    1.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
-   Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.  
  
    > [!NOTE]
    >  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania na komputerach w przykładzie. Po uruchomieniu przykłady WCF, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople przechowywania. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)
