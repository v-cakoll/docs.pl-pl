---
title: Zabezpieczenia wiązania niestandardowego
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
ms.openlocfilehash: eb575594cec9ea714578bc104344acc14b00e9df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592466"
---
# <a name="custom-binding-security"></a>Zabezpieczenia wiązania niestandardowego

Ten przykład pokazuje, jak skonfigurować zabezpieczenia przy użyciu niestandardowego powiązania. Pokazuje, jak użyć niestandardowego powiązania, aby włączyć zabezpieczenia na poziomie wiadomości razem z bezpiecznym transportem. Jest to przydatne, gdy do przesyłania komunikatów między klientem i usługą jest wymagany bezpieczny transport, a jednocześnie komunikaty muszą być bezpieczne na poziomie wiadomości. Ta konfiguracja nie jest obsługiwana przez powiązania dostarczone przez system.

Ten przykład składa się z programu Konsola klienta (EXE) i programu Service Console (EXE). Usługa implementuje kontrakt dupleksowy. Kontrakt jest definiowany przez `ICalculatorDuplex` interfejs, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie). `ICalculatorDuplex`Interfejs umożliwia klientowi wykonywanie operacji matematycznych, co pozwala obliczyć wynik działania w ramach sesji. Niezależnie od tego, czy usługa może zwracać wyniki w `ICalculatorDuplexCallback` interfejsie. Kontrakt dupleksowy wymaga sesji, ponieważ należy ustanowić kontekst w celu skorelowania zestawu komunikatów wysyłanych między klientem a usługą. Zdefiniowane jest niestandardowe powiązanie, które obsługuje komunikację dupleksową i jest bezpieczne.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Konfiguracja usługi definiuje niestandardowe powiązanie, które obsługuje następujące elementy:

- Komunikacja TCP zabezpieczona przy użyciu protokołu TLS/SSL.

- Zabezpieczenia komunikatów systemu Windows.

Konfiguracja powiązania niestandardowego umożliwia bezpieczne transport przez jednoczesne włączenie zabezpieczeń na poziomie wiadomości. Kolejność elementów powiązania jest istotna dla definiowania niestandardowego powiązania, ponieważ każdy reprezentuje warstwę w stosie kanału (zobacz [powiązania niestandardowe](../extending/custom-bindings.md)). Niestandardowe powiązanie jest zdefiniowane w plikach konfiguracji usługi i klienta, jak pokazano w poniższej konfiguracji przykładowej.

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

Niestandardowe powiązanie używa certyfikatu usługi do uwierzytelniania usługi na poziomie transportu oraz do ochrony komunikatów podczas przesyłania między klientem i usługą. Jest to realizowane przez `sslStreamSecurity` element Binding. Certyfikat usługi jest konfigurowany przy użyciu zachowania usługi, jak pokazano w poniższej konfiguracji przykładowej.

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

Ponadto niestandardowe powiązanie używa zabezpieczeń komunikatów z typem poświadczeń systemu Windows — jest to domyślny typ poświadczeń. Jest to realizowane przez `security` element Binding. Klient i usługa są uwierzytelniani przy użyciu zabezpieczeń na poziomie wiadomości, jeśli jest dostępny mechanizm uwierzytelniania Kerberos. Dzieje się tak, jeśli przykład jest uruchamiany w środowisku Active Directoryowym. Jeśli mechanizm uwierzytelniania Kerberos jest niedostępny, jest używane uwierzytelnianie NTLM. Protokół NTLM uwierzytelnia klienta w usłudze, ale nie uwierzytelnia usługi dla klienta. `security`Element Binding jest skonfigurowany do użycia `SecureConversation` `authenticationType` , co powoduje utworzenie sesji zabezpieczeń zarówno na kliencie, jak i w usłudze. Jest to wymagane, aby umożliwić pracę kontraktu dupleksowego usługi.

Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

```console
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

Po uruchomieniu przykładu komunikaty zwrócone do klienta są wyświetlane w interfejsie wywołania zwrotnego wysyłanego z usługi. Zostanie wyświetlony każdy wynik pośredni, po którym następuje całe równanie po zakończeniu wszystkich operacji. Naciśnij klawisz ENTER, aby zamknąć klienta.

Dołączony plik Setup. bat umożliwia skonfigurowanie klienta i serwera przy użyciu odpowiedniego certyfikatu usługi do uruchamiania hostowanej aplikacji, która wymaga zabezpieczeń opartych na certyfikatach. Ten plik wsadowy należy zmodyfikować, aby mógł działać na różnych komputerach lub działać w nieobsługiwanym przypadku.

Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, które mają zastosowanie do tego przykładu, aby można je było modyfikować do uruchamiania w odpowiedniej konfiguracji:

- Tworzenie certyfikatu serwera.

  Poniższe wiersze z pliku Setup. bat umożliwiają utworzenie certyfikatu serwera, który ma być używany. `%SERVER_NAME%`Zmienna określa nazwę serwera. Zmień tę zmienną, aby określić własną nazwę serwera. Ten plik wsadowy domyślnie Nazwa serwera to localhost.

  Certyfikat jest przechowywany w magazynie CurrentUser dla usług hostowanych w sieci Web.

  ```bat
  echo ************
  echo Server cert setup starting
  echo %SERVER_NAME%
  echo ************
  echo making server cert
  echo ************
  makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
  ```

- Instalowanie certyfikatu serwera w zaufanym magazynie certyfikatów klienta.

  Poniższe wiersze w pliku Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta. Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.

  ```console
  certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
  ```

  > [!NOTE]
  > Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2010. Wymaga, aby zmienna środowiskowa MSSDK wskazywała katalog, w którym zainstalowano zestaw SDK. Ta zmienna środowiskowa jest ustawiana automatycznie w wierszu polecenia programu Visual Studio 2010.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze

1. Otwórz okno wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administratora i uruchom setup. bat z przykładowego folderu instalacyjnego. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.

    > [!NOTE]
    > Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012. Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat.

2. Uruchom usługę Service. exe z \service\bin.

3. Uruchamianie programu Client. exe z \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.

4. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na wielu komputerach

1. Na komputerze usługi:

    1. Utwórz katalog wirtualny o nazwie servicemodelsamples na komputerze usługi.

    2. Skopiuj pliki programu usługi z \Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, że pliki zostały skopiowane do podkatalogu \Bin.

    3. Skopiuj pliki Setup. bat i Oczyść. bat do komputera usługi.

    4. Uruchom następujące polecenie w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora: `Setup.bat service` . Spowoduje to utworzenie certyfikatu usługi z nazwą podmiotu zgodną z nazwą komputera, na którym uruchomiono plik wsadowy.

        > [!NOTE]
        > Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2010. Wymaga, aby zmienna środowiskowa Path wskazywała katalog, w którym zainstalowano zestaw SDK. Ta zmienna środowiskowa jest ustawiana automatycznie w wierszu polecenia programu Visual Studio 2010.

    5. Zmień [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) wewnątrz pliku Service. exe. config, aby odzwierciedlał nazwę podmiotu certyfikatu wygenerowanego w poprzednim kroku.

    6. Uruchom polecenie Service. exe z wiersza polecenia.

2. Na komputerze klienckim:

    1. Skopiuj pliki programu klienckiego z folderu \client\bin\ na komputer kliencki. Skopiuj również plik Cleanup. bat.

    2. Uruchom Oczyść. bat, aby usunąć wszystkie stare certyfikaty z poprzednich przykładów.

    3. Wyeksportuj certyfikat usługi, otwierając wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administracyjnymi, a następnie uruchamiając następujące polecenie na komputerze usługi ( `%SERVER_NAME%` należy zastąpić w pełni kwalifikowaną nazwą komputera, na którym uruchomiona jest usługa):

        ```console
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4. Skopiuj% SERVER_NAME%. cer do komputera klienckiego (Zastępuje% SERVER_NAME% za pomocą w pełni kwalifikowanej nazwy komputera, na którym jest uruchomiona usługa).

    5. Zaimportuj certyfikat usługi, otwierając wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administracyjnymi, a następnie uruchamiając następujące polecenie na komputerze klienckim (zamiennie% SERVER_NAME% z w pełni kwalifikowaną nazwą komputera, na którym uruchomiona jest usługa):

        ```console
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

        Kroki c, d i e nie są konieczne, jeśli certyfikat jest wystawiony przez zaufanego wystawcy.

    6. Zmodyfikuj plik App. config klienta w następujący sposób:

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

    7. Jeśli usługa jest uruchomiona w ramach konta innego niż konto NetworkService lub LocalSystem w środowisku domeny, może być konieczne zmodyfikowanie tożsamości punktu końcowego dla punktu końcowego usługi w pliku App. config klienta, aby ustawić odpowiednią nazwę UPN lub nazwę SPN na podstawie konta, które jest używane do uruchamiania usługi. Aby uzyskać więcej informacji na temat tożsamości punktów końcowych, zobacz temat [tożsamość usługi i uwierzytelnianie](../feature-details/service-identity-and-authentication.md) .

    8. Uruchom plik Client. exe z wiersza polecenia.

### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie

- Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.
