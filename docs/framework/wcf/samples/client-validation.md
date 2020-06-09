---
title: Walidacja klienta
ms.date: 03/30/2017
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
ms.openlocfilehash: dce11ec2e3ef552c0c53e1faf89a12bc13b66ae0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585327"
---
# <a name="client-validation"></a>Walidacja klienta
Usługi często publikują metadane, aby umożliwić automatyczne generowanie i Konfigurowanie typów serwerów proxy klienta. Gdy usługa nie jest zaufana, aplikacje klienckie powinny sprawdzić, czy metadane są zgodne z zasadami aplikacji klienta dotyczącymi zabezpieczeń, transakcji, typu kontraktu usługi i tak dalej. Poniższy przykład pokazuje, jak napisać zachowanie punktu końcowego klienta, które sprawdza poprawność punktu końcowego usługi, aby upewnić się, że punkt końcowy usługi jest bezpieczny do użycia.  
  
 Usługa udostępnia cztery punkty końcowe usługi. Pierwszy punkt końcowy używa WSDualHttpBinding, drugi punkt końcowy używa uwierzytelniania NTLM, trzeci punkt końcowy włącza przepływ transakcji, a czwarty punkt końcowy używa uwierzytelniania opartego na certyfikatach.  
  
 Klient używa <xref:System.ServiceModel.Description.MetadataResolver> klasy do pobierania metadanych dla usługi. Klient wymusza zasady uniemożliwiające powiązania dupleksowe, uwierzytelnianie NTLM i przepływ transakcji przy użyciu sprawdzania poprawności. Dla każdego <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienia zaimportowanego z metadanych usługi aplikacja kliencka dodaje wystąpienie `InternetClientValidatorBehavior` zachowania punktu końcowego do programu <xref:System.ServiceModel.Description.ServiceEndpoint> przed podjęciem próby użycia klienta Windows Communication Foundation (WCF) do nawiązania połączenia z punktem końcowym. `Validate`Metoda zachowania jest uruchamiana przed wywołaniem jakiejkolwiek operacji w usłudze i wymusza zasady klienta przez wyrzucanie `InvalidOperationExceptions` .  
  
### <a name="to-build-the-sample"></a>Aby skompilować przykład  
  
1. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1. Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administratora i uruchom setup. bat z przykładowego folderu instalacji. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.  
  
2. Uruchom aplikację usługi z \service\bin\Debug.  
  
3. Uruchom aplikację kliencką z \client\bin\Debug. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
4. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
5. Usuń certyfikaty, uruchamiając Oczyść. bat po zakończeniu korzystania z przykładu. Inne przykłady zabezpieczeń używają tych samych certyfikatów.  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na wielu komputerach  
  
1. Na serwerze programu w wiersz polecenia dla deweloperów dla programu Visual Studio Uruchom polecenie z uprawnieniami administratora, wpisz `setup.bat service` . Uruchomienie `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service. cer.  
  
2. Na serwerze Edytuj plik App. config, aby odzwierciedlić nową nazwę certyfikatu. Oznacza to, że należy zmienić `findValue` atrybut w [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elemencie na w pełni kwalifikowaną nazwę domeny komputera.  
  
3. Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
4. Na kliencie Otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administratora i wpisz `setup.bat client` . Uruchomienie `setup.bat` z `client` argumentem tworzy certyfikat klienta o nazwie Client.com i eksportuje certyfikat klienta do pliku o nazwie Client. cer.  
  
5. W pliku client.cs Zmień wartość adresu punktu końcowego MEX oraz na `findValue` ustawienie domyślnego certyfikatu serwera tak, aby odpowiadał nowemu adresowi usługi. Można to zrobić, zastępując localhost nazwą domeny, w której jest w pełni kwalifikowana. Odtworzyć.  
  
6. Skopiuj plik. cer programu Client z katalogu Client do katalogu usługi na serwerze programu.  
  
7. Na kliencie Uruchom program ImportServiceCert. bat w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.  
  
8. Na serwerze programu Uruchom program ImportClientCert. bat w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Spowoduje to zaimportowanie certyfikatu klienta z pliku. cer klienta do magazynu LocalMachine-TrustedPeople.  
  
9. Na komputerze usługi Skompiluj projekt usługi w programie Visual Studio i uruchom polecenie Service. exe.  
  
10. Na komputerze klienckim uruchom program Client. exe.  
  
    1. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
- Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.  
  
    > [!NOTE]
    > Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między komputerami. W przypadku uruchamiania przykładów WCF, które używają certyfikatów między komputerami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .  
  
## <a name="see-also"></a>Zobacz też

- [Używanie metadanych](../feature-details/using-metadata.md)
