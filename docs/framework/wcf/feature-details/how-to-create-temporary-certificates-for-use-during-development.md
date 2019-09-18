---
title: 'Instrukcje: tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: e2df35959f9821c65d694079aefa0ae6ba01897f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053297"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Instrukcje: tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania

Podczas tworzenia bezpiecznej usługi lub klienta przy użyciu programu Windows Communication Foundation (WCF) często konieczne jest podanie certyfikatu X. 509, który będzie używany jako poświadczenie. Certyfikat jest zwykle częścią łańcucha certyfikatów z urzędem głównym, które znajdują się w magazynie zaufanych głównych urzędów certyfikacji komputera. Łańcuch certyfikatów umożliwia określanie zakresu certyfikatów, w przypadku których zazwyczaj urząd główny pochodzi z organizacji lub jednostki biznesowej. Aby emulować ten czas podczas opracowywania, można utworzyć dwa certyfikaty spełniające wymagania dotyczące zabezpieczeń. Pierwszy to certyfikat z podpisem własnym, który znajduje się w magazynie zaufanych głównych urzędów certyfikacji, a drugi certyfikat jest tworzony od pierwszego i jest umieszczany w osobistym magazynie lokalizacji komputera lokalnego lub w osobistym magazynie Bieżąca lokalizacja użytkownika. W tym temacie przedstawiono procedurę tworzenia tych dwóch certyfikatów przy użyciu polecenia cmdlet programu PowerShell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) .

> [!IMPORTANT]
> Certyfikaty generowane przez polecenie cmdlet New-SelfSignedCertificate są udostępniane tylko do celów testowych. Podczas wdrażania usługi lub klienta upewnij się, że używasz odpowiedniego certyfikatu dostarczonego przez urząd certyfikacji. Może to być z serwera certyfikatów systemu Windows Server w organizacji lub innej firmy.
>
> Domyślnie polecenie cmdlet [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) tworzy certyfikaty z podpisem własnym i te certyfikaty są niezabezpieczone. Umieszczenie certyfikatów z podpisem własnym w magazynie zaufanych głównych urzędów certyfikacji pozwala utworzyć środowisko programistyczne, które bardziej przypomina środowisko wdrażania.

 Aby uzyskać więcej informacji na temat tworzenia i używania certyfikatów, zobacz [Praca z certyfikatami](working-with-certificates.md). Aby uzyskać więcej informacji na temat korzystania z certyfikatu jako poświadczenia, zobacz [Zabezpieczanie usług i klientów](securing-services-and-clients.md). Aby zapoznać się z samouczkiem dotyczącym korzystania z technologii Microsoft Authenticode, zobacz Omówienie [i samouczki Authenticode](https://go.microsoft.com/fwlink/?LinkId=88919).

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Aby utworzyć certyfikat głównego urzędu certyfikacji z podpisem własnym i wyeksportować klucz prywatny

Następujące polecenie tworzy certyfikat z podpisem własnym z nazwą podmiotu "RootCA" w magazynie osobistym bieżącego użytkownika.

```powershell
$rootcert = New-SelfSignedCertificate -CertStoreLocation Cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.19={text}CA=true") -KeyUsage CertSign,CrlSign,DigitalSignature
```

Musimy wyeksportować certyfikat do pliku PFX, aby można go było zaimportować do miejsca, w którym jest potrzebny w późniejszym kroku. W przypadku eksportowania certyfikatu z kluczem prywatnym do jego ochrony jest niezbędne hasło. Hasło jest `SecureString` zapisywane w i należy użyć polecenia cmdlet [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) do wyeksportowania certyfikatu ze skojarzonym kluczem prywatnym do pliku PFX. Zapiszemy również tylko certyfikat publiczny w pliku CRT przy użyciu polecenia cmdlet [Export-Certificate](/powershell/module/pkiclient/export-certificate) .

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Aby utworzyć nowy certyfikat podpisany przez certyfikat głównego urzędu certyfikacji

Następujące polecenie tworzy certyfikat podpisany przez `RootCA` obiekt z nazwą podmiotu "SignedByRootCA" przy użyciu klucza prywatnego wystawcy.

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

Podobnie Zapisz podpisany certyfikat z kluczem prywatnym w pliku PFX, a po prostu klucz publiczny w pliku CRT.

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Instalowanie certyfikatu w magazynie zaufanych głównych urzędów certyfikacji

Po utworzeniu certyfikatu z podpisem własnym można go zainstalować w magazynie zaufanych głównych urzędów certyfikacji. Wszystkie certyfikaty podpisane z certyfikatem w tym punkcie są zaufane przez komputer. Z tego powodu Usuń certyfikat ze sklepu, gdy tylko nie będą już potrzebne. Po usunięciu tego certyfikatu głównego urzędu wszystkie inne podpisane z nim certyfikaty staną się nieautoryzowane. Certyfikaty urzędu głównego są po prostu mechanizmem, w którym grupa certyfikatów może być w miarę potrzeb w zakresie. Na przykład w przypadku aplikacji równorzędnych zazwyczaj nie ma potrzeby dla urzędu głównego, ponieważ po prostu ufasz tożsamości indywidualnej za pomocą podanego certyfikatu.

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Aby zainstalować certyfikat z podpisem własnym w zaufanych głównych urzędach certyfikacji

1. Otwórz przystawkę Certyfikaty. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie certyfikatów z przystawką](how-to-view-certificates-with-the-mmc-snap-in.md)programu MMC.

2. Otwórz folder do przechowywania certyfikatu, **komputera lokalnego** lub **bieżącego użytkownika**.

3. Otwórz folder **Zaufane główne** urzędy certyfikacji.

4. Kliknij prawym przyciskiem myszy folder **Certyfikaty** , a następnie kliknij pozycję **wszystkie zadania**, a następnie kliknij pozycję **Importuj**.

5. Postępuj zgodnie z instrukcjami kreatora wyświetlanymi na ekranie, aby zaimportować plik RootCA. pfx do magazynu.

## <a name="using-certificates-with-wcf"></a>Korzystanie z certyfikatów w programie WCF

Po skonfigurowaniu certyfikatów tymczasowych można użyć ich do opracowania rozwiązań WCF, które określają certyfikaty jako typ poświadczeń klienta. Na przykład następująca konfiguracja XML określa zabezpieczenia komunikatów i certyfikat jako typ poświadczeń klienta.

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>Aby określić certyfikat jako typ poświadczeń klienta

1. W pliku konfiguracji usługi Użyj poniższego kodu XML, aby ustawić tryb zabezpieczeń na komunikat, a poświadczenia klienta typ certyfikatu.

    ```xml
    <bindings>
      <wsHttpBinding>
        <binding name="CertificateForClient">
          <security>
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    ```

2. W pliku konfiguracji klienta Użyj następującego kodu XML, aby określić, że certyfikat znajduje się w magazynie użytkownika, i można go znaleźć, wyszukując pole SubjectName dla wartości "CohoWinery".

    ```xml
    <behaviors>
      <endpointBehaviors>
        <behavior name="CertForClient">
          <clientCredentials>
            <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>
    ```

Aby uzyskać więcej informacji o używaniu certyfikatów w programie WCF, zobacz [Praca z certyfikatami](working-with-certificates.md).

## <a name="net-framework-security"></a>zabezpieczenia .NET Framework

Pamiętaj o usunięciu wszelkich tymczasowych certyfikatów głównych urzędów **certyfikacji z zaufanych głównych źródeł certyfikatów** i folderów **osobistych** , klikając prawym przyciskiem myszy certyfikat, a następnie klikając polecenie **Usuń**.

## <a name="see-also"></a>Zobacz także

- [Praca z certyfikatami](working-with-certificates.md)
- [Instrukcje: Wyświetlanie certyfikatów z przystawką programu MMC](how-to-view-certificates-with-the-mmc-snap-in.md)
- [Zabezpieczanie usług i klientów](securing-services-and-clients.md)
