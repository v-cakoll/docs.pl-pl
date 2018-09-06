---
title: Walidacja klienta
ms.date: 03/30/2017
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
ms.openlocfilehash: 3f8b5ec3f8652ef50bbda3456669f2abf456472b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740010"
---
# <a name="client-validation"></a>Walidacja klienta
Usługi często Publikowanie metadanych, aby włączyć automatyczne generowanie i konfigurowanie typów serwera proxy klienta. Jeśli usługa nie jest zaufany, aplikacje klienckie należy zweryfikować, że metadane odpowiada aplikacji klienta zasady dotyczące zabezpieczeń, transakcje, typ kontraktu usługi i tak dalej. W poniższym przykładzie pokazano, jak napisać klienta zachowanie punktu końcowego, która weryfikuje punktu końcowego usługi, aby upewnić się, że punkt końcowy usługi jest bezpieczny w użyciu.  
  
 Usługa udostępnia cztery punkty końcowe usługi. Pierwszy punkt końcowy korzysta z WSDualHttpBinding, drugi punkt końcowy korzysta z uwierzytelniania NTLM, trzeci punktu końcowego umożliwia przepływu transakcji, a czwarty punkt końcowy korzysta z uwierzytelniania opartego na certyfikatach.  
  
 Klient używa <xref:System.ServiceModel.Description.MetadataResolver> klasy do pobrania metadanych dla usługi. Klient wymusza zasady zabronienia powiązania dwukierunkowego, uwierzytelnianie NTLM i przepływem transakcji przy użyciu zachowanie sprawdzania poprawności. Dla każdego <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienia zaimportowane z metadanych usługi, aplikacja kliencka dodaje wystąpienie `InternetClientValidatorBehavior` zachowanie punktu końcowego do <xref:System.ServiceModel.Description.ServiceEndpoint> przed podjęciem próby nawiązać połączenie za pomocą klienta usługi Windows Communication Foundation (WCF) punkt końcowy. To zachowanie `Validate` metoda jest wykonywany przed dowolne operacje w usłudze są nazywane i wymusza zasady klienta, zgłaszając `InvalidOperationExceptions`.  
  
### <a name="to-build-the-sample"></a>Aby skompilować przykład  
  
1.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Otwórz wiersz polecenia programu Visual Studio z uprawnieniami administratora i uruchom Setup.bat jest z poziomu folderu instalacji przykładowej. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
2.  Uruchamianie aplikacji usługi z \service\bin\Debug.  
  
3.  Uruchom aplikację klienta z \client\bin\Debug. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
4.  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
5.  Usuń certyfikaty, uruchamiając Cleanup.bat, po zakończeniu dla próbki. Inne przykłady zabezpieczeń za pomocą tych samych certyfikatów.  
  
### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1.  Na serwerze, w wierszu polecenia programu Visual Studio, uruchomione z uprawnieniami administratora, wpisz `setup.bat service`. Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
2.  Na serwerze Przeprowadź edycję pliku App.config, aby odzwierciedlały nową nazwę certyfikatu. Oznacza to, zmień `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elementu, aby w pełni kwalifikowana nazwa domeny komputera.  
  
3.  Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.  
  
4.  Na komputerze klienckim, otwórz wiersz polecenia programu Visual Studio z uprawnieniami administratora i wpisz `setup.bat client`. Uruchamianie `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie Client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.  
  
5.  W pliku client.cs Zmień wartość adresu punktu końcowego MEX i `findValue` ustawienia domyślnego certyfikatu serwera do dopasowania nowy adres usługi. Można to zrobić, zastępując localhost w pełni kwalifikowana nazwa domeny serwera. Ponowna kompilacja.  
  
6.  Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
7.  Na komputerze klienckim należy uruchomić ImportServiceCert.bat w wierszu polecenia programu Visual Studio otwartych z uprawnieniami administratora. To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.  
  
8.  Na serwerze uruchom ImportClientCert.bat w wierszu polecenia programu Visual Studio otwartych z uprawnieniami administratora. To importuje certyfikat klienta z pliku Client.cer, do maszyny lokalnej - TrustedPeople magazynu.  
  
9. Na komputerze, usługi Skompiluj projekt usługi w programie Visual Studio i uruchom service.exe.  
  
10. Na komputerze klienckim, aby uruchomić client.exe.  
  
    1.  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
-   Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
    > [!NOTE]
    >  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach. Jeśli uruchamiasz przykłady WCF, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople przechowywania. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)
