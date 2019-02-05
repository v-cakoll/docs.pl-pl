---
title: 'Instrukcje: Tworzenie certyfikatów tymczasowych do użytku w trakcie opracowywania'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: 609b142c5dd1cac92acf0f1c0a62d17a9b5c957e
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738633"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Instrukcje: Tworzenie certyfikatów tymczasowych do użytku w trakcie opracowywania

Podczas tworzenia bezpiecznego usługi lub klienta przy użyciu usługi Windows Communication Foundation (WCF), często jest konieczne dostarczanie certyfikatu X.509, który ma być używany jako poświadczenia. Certyfikat jest zazwyczaj w łańcuchu certyfikatów za pomocą głównego urzędu znaleziono w magazynie zaufanych głównych urzędów certyfikacji komputera. Posiadanie łańcuch certyfikatów umożliwia określania zakresu zestawu certyfikatów, w których zwykle głównego urzędu certyfikacji jest od swojej organizacji lub jednostki biznesowej. Aby emulować to w czasie programowania, można utworzyć dwa certyfikaty do spełnienia wymagań dotyczących zabezpieczeń. Pierwsza to certyfikat z podpisem własnym, który jest umieszczony w magazynie zaufanych głównych urzędów certyfikacji i drugiego certyfikatu jest tworzony z pierwszego i znajduje się w magazynie osobistym lokalizacji komputera lokalnego lub w magazynie osobistym Bieżąca lokalizacja użytkownika. W tym temacie przedstawiono kroki umożliwiające utworzenie tych dwóch certyfikatów przy użyciu programu Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) polecenia cmdlet.

> [!IMPORTANT]
> Polecenie cmdlet New-SelfSignedCertificate generuje certyfikaty znajdują się tylko do celów testowych. Podczas wdrażania usługi lub klienta, należy użyć odpowiedni certyfikat, dostarczone przez urząd certyfikacji. Może to mieć długość od serwera certyfikatów systemu Windows Server w Twojej organizacji lub innej.
>
> Domyślnie [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) polecenie cmdlet tworzy certyfikaty, które są z podpisem własnym, a te certyfikaty są niebezpieczne. Umieszczenie certyfikatów z podpisem własnym w zaufanych głównych urzędów certyfikacji magazynu pozwala na tworzenie środowisko programistyczne, które symuluje bardziej ścisłe środowiska wdrażania.

 Aby uzyskać więcej informacji na temat tworzenia i używania certyfikatów, zobacz [Working with Certificates](working-with-certificates.md). Aby uzyskać więcej informacji na temat za pomocą certyfikatu jako poświadczenia zobacz [zabezpieczania usług i klientów](securing-services-and-clients.md). Aby zapoznać się z samouczkiem dotyczącym przy użyciu technologii Authenticode firmy Microsoft, zobacz [Authenticode omówienia i samouczki](https://go.microsoft.com/fwlink/?LinkId=88919).

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Aby utworzyć certyfikat z urzędu głównego z podpisem własnym i wyeksportować klucz prywatny

Następujące polecenie tworzy certyfikat z podpisem własnym z nazwą podmiotu "RootCA" w magazynie osobistym bieżącego użytkownika.

```powershell
PS $rootCert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("1.3.6.1.4.1.311.21.10={text}1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2")
```

Potrzebujemy wyeksportować certyfikat do pliku PFX, tak aby można było importować do miejsca w późniejszym kroku, w których jest wymagane. Podczas eksportowania certyfikatu z kluczem prywatnym, aby chronić go wymaga hasła. Firma Microsoft Zapisz hasło w `SecureString` i użyj [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) polecenia cmdlet, aby wyeksportować certyfikat z skojarzony klucz prywatny do pliku PFX. Oszczędzamy również po prostu certyfikatu publicznego do pliku CRT przy użyciu [eksportu certyfikatu](/powershell/module/pkiclient/export-certificate) polecenia cmdlet.

```powershell
PS [System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
PS [String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
PS Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
PS Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Aby utworzyć nowy certyfikat podpisany przez certyfikat głównego urzędu certyfikacji

Następujące polecenie tworzy certyfikat z podpisem `RootCA` z nazwą podmiotu "SignedByRootCA" przy użyciu klucza prywatnego wystawcy.

```powershell
PS $testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

Podobnie oszczędzamy certyfikatu z podpisem z kluczem prywatnym do pliku PFX i tylko klucz publiczny do pliku CRT.

```powershell
PS [String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
PS Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
PS Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Instalowanie certyfikatu w zaufanych Store urzędów certyfikacji, który jest głównym

Po utworzeniu certyfikatu z podpisem własnym można zainstalować go w magazynie zaufanych głównych urzędów certyfikacji. Wszystkie certyfikaty, które są podpisane za pomocą certyfikatu, w tym momencie są zaufane przez komputer. Z tego powodu Usuń certyfikat z magazynu, jak tylko nie są już potrzebne. Jeśli usuniesz ten certyfikat głównego urzędu certyfikacji, wszystkie certyfikaty, którzy zalogowali się z nią stają się nieautoryzowanych. Certyfikaty z głównego to po prostu mechanizm zgodnie z którą grupą certyfikatów można zmniejszyć zakres gdy jest to konieczne. Na przykład w aplikacji peer-to-peer, zwykle nie ma potrzeby dla głównego urzędu ponieważ tożsamość osoby ufasz po prostu przez podany certyfikat.

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Aby zainstalować certyfikat z podpisem własnym w zaufanych głównych urzędów certyfikacji

1. Otwórz przystawkę certyfikatu. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie certyfikatów za pomocą przystawki programu MMC](how-to-view-certificates-with-the-mmc-snap-in.md).

2. Otwórz folder z certyfikatem, albo **komputera lokalnego** lub **bieżącego użytkownika**.

3. Otwórz **zaufane główne urzędy certyfikacji** folderu.

4. Kliknij prawym przyciskiem myszy **certyfikaty** folder i kliknij przycisk **wszystkie zadania**, następnie kliknij przycisk **importu**.

5. Postępuj zgodnie z wyświetlanymi na ekranie kreatora instrukcjami, aby zaimportować RootCA.pfx do magazynu.

## <a name="using-certificates-with-wcf"></a>Za pomocą certyfikatów przy użyciu programu WCF

Po skonfigurowaniu certyfikatów tymczasowych można ich użyć do opracowywania rozwiązań usługi WCF, które określają certyfikaty jako typu poświadczeń klienta. Na przykład następującej konfiguracji XML określa zabezpieczenia komunikatów i certyfikatu jako typu poświadczeń klienta.

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>Aby określić certyfikat jako typu poświadczeń klienta

- W pliku konfiguracji usługi umożliwia ustawianie trybu zabezpieczeń do wiadomości i typu poświadczeń klienta do certyfikatu następujący kod XML.

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

W pliku konfiguracji dla klienta użyj następujący kod XML, aby określić, czy certyfikat został znaleziony w magazynie użytkownika i można znaleźć, przeszukując pola SubjectName dla wartości "CohoWinery."

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

Aby uzyskać więcej informacji na temat korzystania z certyfikatów w programie WCF zobacz [Working with Certificates](working-with-certificates.md).

## <a name="net-framework-security"></a>zabezpieczenia .NET Framework

Pamiętaj usunąć wszystkie certyfikaty urzędu głównego tymczasowe z **zaufane główne urzędy certyfikacji** i **osobistych** foldery, klikając prawym przyciskiem myszy certyfikat, a następnie klikając  **Usuń**.

## <a name="see-also"></a>Zobacz także

- [Praca z certyfikatami](working-with-certificates.md)
- [Instrukcje: Wyświetlanie certyfikatów za pomocą przystawki programu MMC](how-to-view-certificates-with-the-mmc-snap-in.md)
- [Zabezpieczanie usług i klientów](securing-services-and-clients.md)
