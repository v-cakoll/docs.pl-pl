---
title: Zabezpieczenia powiązania niestandardowego
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
ms.openlocfilehash: 56c3ed4be894a265635c747373e0b79599ce129d
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221703"
---
# <a name="custom-binding-security"></a>Zabezpieczenia powiązania niestandardowego
Niniejszy przykład pokazuje sposób konfigurowania zabezpieczeń przy użyciu niestandardowego powiązania. Widoczny jest sposób użyć niestandardowego powiązania, aby włączyć zabezpieczenia na poziomie komunikatu wraz z bezpiecznym transportem. Jest to przydatne, gdy bezpiecznym transportem jest wymagana do przesyłania komunikatów między klientem a usługą i jednocześnie komunikaty muszą być bezpieczne na poziomie komunikatu. Ta konfiguracja nie jest obsługiwana przez powiązania dostarczane przez system.

 W tym przykładzie składa się z konsoli klienta programu (EXE) i program konsoli usługi (EXE). Usługa implementuje kontraktu dwukierunkowego. Kontrakt jest definiowany przez `ICalculatorDuplex` interfejs, który udostępnia operacje matematyczne (dodawania, odejmowania, mnożenia i dzielenia). `ICalculatorDuplex` Interfejs umożliwia klientowi do wykonywania operacji matematycznych obliczania wyniku uruchomionych w sesji. Niezależnie od siebie, usługa może zwrócić wyniki na `ICalculatorDuplexCallback` interfejsu. Kontrakt dupleksowy wymaga elementu session, ponieważ kontekst muszą być ustalane do skorelowania zestaw komunikatów przesyłanych między klientem a usługą. Powiązanie niestandardowe zdefiniowano obsługującego komunikację dupleksową, która jest bezpieczna.

> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.

 Konfiguracja usługi definiuje niestandardowego powiązania, który obsługuje następujące funkcje:

-   Komunikację TCP chronionych z użyciem protokołu TLS/SSL.

-   Zabezpieczenia komunikatów Windows.

 Konfiguracja powiązania niestandardowego pozwala bezpiecznym transportem, jednocześnie umożliwiając zabezpieczenia na poziomie komunikatu. Określanie kolejności elementów wiązania jest ważny w celu definiowania niestandardowego powiązania, ponieważ każdy z nich reprezentuje warstwę w stosie kanału (zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md)). Powiązania niestandardowego jest zdefiniowany w plikach konfiguracji usługi i klienta, jak pokazano w poniższym Przykładowa konfiguracja.

```xml
<bindings>
  <!-- Configure a custom binding. -->
  <customBinding>
    <binding name="Binding1">
      <security authenticationMode="SecureConversation"
                 requireSecurityContextCancellation="true">
      </security>
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>
      <sslStreamSecurity requireClientCertificate="false"/>
      <tcpTransport/>
    </binding>
  </customBinding>
</bindings>
```

 Niestandardowego powiązania z certyfikatem usługi do uwierzytelniania usługi na poziomie transportu i do ochrony komunikatów podczas transmisji między klientem a usługą. Jest to osiągane przez `sslStreamSecurity` element powiązania. Certyfikat usługi jest skonfigurowany za pomocą zachowanie usługi, jak pokazano w poniższym Przykładowa konfiguracja.

```xml
<behaviors>
    <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
        <serviceMetadata />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>
        </serviceCredentials>
    </behavior>
    </serviceBehaviors>
</behaviors>
```

 Ponadto niestandardowego powiązania za pomocą zabezpieczeń wiadomości typ poświadczeń Windows — jest to domyślny typ poświadczeń. Jest to osiągane przez `security` element powiązania. Zarówno klient, jak i usługi są uwierzytelniane przy użyciu zabezpieczeń na poziomie komunikatu, jeśli mechanizm uwierzytelniania Kerberos jest dostępna. Dzieje się tak, jeśli na przykład jest uruchamiany w środowisku usługi Active Directory. Jeśli mechanizm uwierzytelniania Kerberos jest niedostępny, zostanie użyte uwierzytelnianie NTLM. NTLM uwierzytelnia klienta do usługi, ale nie uwierzytelnia usługi do klienta. `security` Element powiązania jest skonfigurowany do używania `SecureConversation``authenticationType`, co powoduje, że w przypadku tworzenia sesji zabezpieczeń zarówno klient, jak i usługi. Jest to wymagane do włączenia usługi kontraktu dwukierunkowego do pracy.

 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.

```
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

 Po uruchomieniu przykładu, zobacz komunikaty zwracane do klienta na interfejs wywołania zwrotnego wysyłane z usługi. Jest wyświetlany wynik każdego pośrednich następuje całe równanie po ukończeniu wszystkich operacji. Naciśnij klawisz ENTER, aby zamknąć klienta.

 Dołączony plik Setup.bat umożliwia konfigurowanie klienta i serwera przy użyciu certyfikatu odpowiednie usługi uruchamianie hostowanej aplikacji, która wymaga zabezpieczeń oparte na certyfikatach. Ten plik wsadowy muszą zostać zmodyfikowane, działają na różnych komputerach lub działać w przypadku innych obsługiwanych.

 Poniżej zawiera krótkie omówienie różnych sekcji plików wsadowych, które dotyczą tego przykładu tak, aby ich można modyfikować, aby uruchomić w prawidłowej konfiguracji:

-   Tworzenie certyfikatu serwera.

     Następujące wiersze z pliku Setup.bat jest utworzenie certyfikatu serwera, który ma być używany. `%SERVER_NAME%` Zmienna Określa nazwę serwera. Zmieniać tej zmiennej do określenia nazwy serwera. Ten plik wsadowy wartością domyślną jest nazwa serwera, na hoście lokalnym.

     Certyfikat jest przechowywany w magazynie CurrentUser usług hostowanych w sieci Web.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.

     Przechowywać następujące wiersze w Setup.bat jest kopiowanie plików certyfikatu serwera do klienta zaufanych osób. Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2010 wiersz polecenia. Wymaga to, że zmienna środowiskowa MSSDK odwołują się do katalogu, w którym jest zainstalowany zestaw SDK. Ta zmienna środowiskowa jest automatycznie ustawiana w ramach programu Visual Studio 2010 wiersz polecenia.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze

1.  Otwórz wiersz polecenia dewelopera dla okna programu Visual Studio z uprawnieniami administratora i uruchom Setup.bat jest z poziomu folderu instalacji przykładowej. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.

    > [!NOTE]
    >  Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2012 wiersz polecenia. Ustaw w Visual Studio 2012 Command Prompt punkty do katalogu, który zawiera pliki wykonywalne wymagane przez skrypt Setup.bat jest zmiennej środowiskowej PATH.  
  
2.  Uruchom Service.exe z \service\bin.  
  
3.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
4.  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1.  Na komputerze usługi:  
  
    1.  Utwórz katalog wirtualny o nazwie servicemodelsamples na komputerze usługi.  
  
    2.  Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, skopiuj pliki w podkatalogu \bin.  
  
    3.  Skopiuj pliki Setup.bat i Cleanup.bat komputer usługi.  
  
    4.  Uruchom następujące polecenie w wierszu polecenia dewelopera dla programu Visual Studio otwartych z uprawnieniami administratora: `Setup.bat service`. Spowoduje to utworzenie certyfikatu usługi o nazwie podmiotu, pasujące do nazwy komputera, na którym uruchomiono plik wsadowy na.  
  
        > [!NOTE]
        >  Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2010 wiersz polecenia. Wymaga to, że zmiennej środowiskowej path odwołują się do katalogu, w którym jest zainstalowany zestaw SDK. Ta zmienna środowiskowa jest automatycznie ustawiana w ramach programu Visual Studio 2010 wiersz polecenia.

    5.  Zmiana [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) wewnątrz pliku Service.exe.config, aby odzwierciedlić nazwę podmiotu certyfikatu, wygenerowany w poprzednim kroku.

    6.  Uruchom Service.exe z poziomu wiersza polecenia.

2.  Na komputerze klienckim:

    1.  Skopiuj pliki programu klienta z folderu \client\bin\ na komputerze klienckim. Również skopiować plik Cleanup.bat.

    2.  Uruchom Cleanup.bat, aby usunąć wszelkie stare certyfikaty z poprzednich przykładów.

    3.  Eksportowanie certyfikatu usługi otworzyć wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administracyjnymi, a następnie uruchamiając następujące polecenie na komputerze usługi (Zastąp `%SERVER_NAME%` z w pełni kwalifikowaną nazwę komputera, na którym Usługa jest uruchomiona):

        ```
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4.  Skopiuj %SERVER_NAME%.cer komputer kliencki (Zastąp nazwa_serwera % z w pełni kwalifikowaną nazwę komputera, na którym jest uruchomiona usługa).

    5.  Zaimportuj certyfikat usługi otworzyć wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administracyjnymi, a następnie uruchamiając następujące polecenie na komputerze klienckim (Zastąp % nazwa_serwera % z w pełni kwalifikowaną nazwę komputera, na którym Usługa jest uruchomiona):

        ```
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

         Kroki nie są konieczne, jeśli certyfikat został wystawiony przez zaufanego wystawcy c, d i e.

    6.  Zmodyfikuj plik App.config klienta w następujący sposób:

        ```xml
        <client>
            <endpoint name="default"
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"
                binding="customBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"
        behaviorConfiguration="CalculatorClientBehavior" />
        </client>
        ```

    7.  Jeśli usługa jest uruchomiona w ramach konta innego niż Usługa sieciowa lub konta System lokalny w środowisku domeny, może być konieczne zmodyfikowanie tożsamość punktu końcowego dla punktu końcowego usługi w pliku App.config klienta można ustawić odpowiednie nazwy UPN lub nazwy SPN na podstawie na koncie, które jest używane do uruchamiania usługi. Aby uzyskać więcej informacji o tożsamości punktu końcowego, zobacz [uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) tematu.

    8.  Uruchom Client.exe z poziomu wiersza polecenia.

### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki

-   Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.

## <a name="see-also"></a>Zobacz też
