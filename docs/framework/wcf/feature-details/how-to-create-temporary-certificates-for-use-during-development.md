---
title: 'Instrukcje: Tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: 9e01ccb29ad017a2657ab08b54d7f01ef4564481
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964539"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="84f97-102">Instrukcje: Tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania</span><span class="sxs-lookup"><span data-stu-id="84f97-102">How to: Create Temporary Certificates for Use During Development</span></span>

<span data-ttu-id="84f97-103">Podczas tworzenia bezpiecznej usługi lub klienta przy użyciu programu Windows Communication Foundation (WCF) często konieczne jest podanie certyfikatu X. 509, który będzie używany jako poświadczenie.</span><span class="sxs-lookup"><span data-stu-id="84f97-103">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="84f97-104">Certyfikat jest zwykle częścią łańcucha certyfikatów z urzędem głównym, które znajdują się w magazynie zaufanych głównych urzędów certyfikacji komputera.</span><span class="sxs-lookup"><span data-stu-id="84f97-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="84f97-105">Łańcuch certyfikatów umożliwia określanie zakresu certyfikatów, w przypadku których zazwyczaj urząd główny pochodzi z organizacji lub jednostki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="84f97-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="84f97-106">Aby emulować ten czas podczas opracowywania, można utworzyć dwa certyfikaty spełniające wymagania dotyczące zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="84f97-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="84f97-107">Pierwszy to certyfikat z podpisem własnym, który znajduje się w magazynie zaufanych głównych urzędów certyfikacji, a drugi certyfikat jest tworzony od pierwszego i jest umieszczany w osobistym magazynie lokalizacji komputera lokalnego lub w osobistym magazynie Bieżąca lokalizacja użytkownika.</span><span class="sxs-lookup"><span data-stu-id="84f97-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="84f97-108">W tym temacie przedstawiono procedurę tworzenia tych dwóch certyfikatów przy użyciu polecenia cmdlet programu PowerShell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) .</span><span class="sxs-lookup"><span data-stu-id="84f97-108">This topic walks through the steps to create these two certificates using the Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84f97-109">Certyfikaty generowane przez polecenie cmdlet New-SelfSignedCertificate są udostępniane tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="84f97-109">The certificates that the New-SelfSignedCertificate cmdlet generates are provided for testing purposes only.</span></span> <span data-ttu-id="84f97-110">Podczas wdrażania usługi lub klienta upewnij się, że używasz odpowiedniego certyfikatu dostarczonego przez urząd certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="84f97-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="84f97-111">Może to być z serwera certyfikatów systemu Windows Server w organizacji lub innej firmy.</span><span class="sxs-lookup"><span data-stu-id="84f97-111">This could either be from a Windows Server certificate server in your organization or a third party.</span></span>
>
> <span data-ttu-id="84f97-112">Domyślnie polecenie cmdlet [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) tworzy certyfikaty z podpisem własnym i te certyfikaty są niezabezpieczone.</span><span class="sxs-lookup"><span data-stu-id="84f97-112">By default, the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet creates certificates that are self-signed and these certificates are insecure.</span></span> <span data-ttu-id="84f97-113">Umieszczenie certyfikatów z podpisem własnym w magazynie zaufanych głównych urzędów certyfikacji pozwala utworzyć środowisko programistyczne, które bardziej przypomina środowisko wdrażania.</span><span class="sxs-lookup"><span data-stu-id="84f97-113">Placing the self-signed certificates in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>

 <span data-ttu-id="84f97-114">Aby uzyskać więcej informacji na temat tworzenia i używania certyfikatów, zobacz [Praca z certyfikatami](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="84f97-114">For more information about creating and using certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="84f97-115">Aby uzyskać więcej informacji na temat korzystania z certyfikatu jako poświadczenia, zobacz [Zabezpieczanie usług i klientów](securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="84f97-115">For more information about using a certificate as a credential, see [Securing Services and Clients](securing-services-and-clients.md).</span></span> <span data-ttu-id="84f97-116">Aby zapoznać się z samouczkiem dotyczącym korzystania z technologii Microsoft Authenticode, zobacz Omówienie [i samouczki Authenticode](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="84f97-116">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85)).</span></span>

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="84f97-117">Aby utworzyć certyfikat głównego urzędu certyfikacji z podpisem własnym i wyeksportować klucz prywatny</span><span class="sxs-lookup"><span data-stu-id="84f97-117">To create a self-signed root authority certificate and export the private key</span></span>

<span data-ttu-id="84f97-118">Następujące polecenie tworzy certyfikat z podpisem własnym z nazwą podmiotu "RootCA" w magazynie osobistym bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="84f97-118">The following command creates a self-signed certificate with a subject name of "RootCA" in the Current User Personal store.</span></span>

```powershell
$rootcert = New-SelfSignedCertificate -CertStoreLocation Cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.19={text}CA=true") -KeyUsage CertSign,CrlSign,DigitalSignature
```

<span data-ttu-id="84f97-119">Musimy wyeksportować certyfikat do pliku PFX, aby można go było zaimportować do miejsca, w którym jest potrzebny w późniejszym kroku.</span><span class="sxs-lookup"><span data-stu-id="84f97-119">We need to export the certificate to a PFX file so that it can be imported to where it's needed in a later step.</span></span> <span data-ttu-id="84f97-120">W przypadku eksportowania certyfikatu z kluczem prywatnym do jego ochrony jest niezbędne hasło.</span><span class="sxs-lookup"><span data-stu-id="84f97-120">When exporting a certificate with the private key, a password is needed to protect it.</span></span> <span data-ttu-id="84f97-121">Zapiszemy hasło w `SecureString` i użyj polecenia cmdlet [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) , aby wyeksportować certyfikat ze skojarzonym kluczem prywatnym do pliku PFX.</span><span class="sxs-lookup"><span data-stu-id="84f97-121">We save the password in a `SecureString` and use the [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet to export the certificate with the associated private key to a PFX file.</span></span> <span data-ttu-id="84f97-122">Zapiszemy również tylko certyfikat publiczny w pliku CRT przy użyciu polecenia cmdlet [Export-Certificate](/powershell/module/pkiclient/export-certificate) .</span><span class="sxs-lookup"><span data-stu-id="84f97-122">We also save just the public certificate into a CRT file using the [Export-Certificate](/powershell/module/pkiclient/export-certificate) cmdlet.</span></span>

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="84f97-123">Aby utworzyć nowy certyfikat podpisany przez certyfikat głównego urzędu certyfikacji</span><span class="sxs-lookup"><span data-stu-id="84f97-123">To create a new certificate signed by a root authority certificate</span></span>

<span data-ttu-id="84f97-124">Następujące polecenie tworzy certyfikat podpisany przez `RootCA` z nazwą podmiotu "SignedByRootCA" przy użyciu klucza prywatnego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="84f97-124">The following command creates a certificate signed by the `RootCA` with a subject name of "SignedByRootCA" using the private key of the issuer.</span></span>

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

<span data-ttu-id="84f97-125">Podobnie Zapisz podpisany certyfikat z kluczem prywatnym w pliku PFX, a po prostu klucz publiczny w pliku CRT.</span><span class="sxs-lookup"><span data-stu-id="84f97-125">Similarly, we save the signed certificate with private key into a PFX file and just the public key into a CRT file.</span></span>

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="84f97-126">Instalowanie certyfikatu w magazynie zaufanych głównych urzędów certyfikacji</span><span class="sxs-lookup"><span data-stu-id="84f97-126">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>

<span data-ttu-id="84f97-127">Po utworzeniu certyfikatu z podpisem własnym można go zainstalować w magazynie zaufanych głównych urzędów certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="84f97-127">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="84f97-128">Wszystkie certyfikaty podpisane z certyfikatem w tym punkcie są zaufane przez komputer.</span><span class="sxs-lookup"><span data-stu-id="84f97-128">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="84f97-129">Z tego powodu Usuń certyfikat ze sklepu, gdy tylko nie będą już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="84f97-129">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="84f97-130">Po usunięciu tego certyfikatu głównego urzędu wszystkie inne podpisane z nim certyfikaty staną się nieautoryzowane.</span><span class="sxs-lookup"><span data-stu-id="84f97-130">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="84f97-131">Certyfikaty urzędu głównego są po prostu mechanizmem, w którym grupa certyfikatów może być w miarę potrzeb w zakresie.</span><span class="sxs-lookup"><span data-stu-id="84f97-131">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="84f97-132">Na przykład w przypadku aplikacji równorzędnych zazwyczaj nie ma potrzeby dla urzędu głównego, ponieważ po prostu ufasz tożsamości indywidualnej za pomocą podanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="84f97-132">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="84f97-133">Aby zainstalować certyfikat z podpisem własnym w zaufanych głównych urzędach certyfikacji</span><span class="sxs-lookup"><span data-stu-id="84f97-133">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>

1. <span data-ttu-id="84f97-134">Otwórz przystawkę Certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="84f97-134">Open the certificate snap-in.</span></span> <span data-ttu-id="84f97-135">Aby uzyskać więcej informacji, zobacz [How to: View Certificates za pomocą przystawki MMC](how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="84f97-135">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

2. <span data-ttu-id="84f97-136">Otwórz folder do przechowywania certyfikatu, **komputera lokalnego** lub **bieżącego użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="84f97-136">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>

3. <span data-ttu-id="84f97-137">Otwórz folder **Zaufane główne** urzędy certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="84f97-137">Open the **Trusted Root Certification Authorities** folder.</span></span>

4. <span data-ttu-id="84f97-138">Kliknij prawym przyciskiem myszy folder **Certyfikaty** , a następnie kliknij pozycję **wszystkie zadania**, a następnie kliknij pozycję **Importuj**.</span><span class="sxs-lookup"><span data-stu-id="84f97-138">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>

5. <span data-ttu-id="84f97-139">Postępuj zgodnie z instrukcjami kreatora wyświetlanymi na ekranie, aby zaimportować plik RootCA. pfx do magazynu.</span><span class="sxs-lookup"><span data-stu-id="84f97-139">Follow the on-screen wizard instructions to import the RootCA.pfx into the store.</span></span>

## <a name="using-certificates-with-wcf"></a><span data-ttu-id="84f97-140">Korzystanie z certyfikatów w programie WCF</span><span class="sxs-lookup"><span data-stu-id="84f97-140">Using certificates With WCF</span></span>

<span data-ttu-id="84f97-141">Po skonfigurowaniu certyfikatów tymczasowych można użyć ich do opracowania rozwiązań WCF, które określają certyfikaty jako typ poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="84f97-141">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="84f97-142">Na przykład następująca konfiguracja XML określa zabezpieczenia komunikatów i certyfikat jako typ poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="84f97-142">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="84f97-143">Aby określić certyfikat jako typ poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="84f97-143">To specify a certificate as the client credential type</span></span>

1. <span data-ttu-id="84f97-144">W pliku konfiguracji usługi Użyj poniższego kodu XML, aby ustawić tryb zabezpieczeń na komunikat, a poświadczenia klienta typ certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="84f97-144">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>

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

2. <span data-ttu-id="84f97-145">W pliku konfiguracji klienta Użyj następującego kodu XML, aby określić, że certyfikat znajduje się w magazynie użytkownika, i można go znaleźć, wyszukując pole SubjectName dla wartości "CohoWinery".</span><span class="sxs-lookup"><span data-stu-id="84f97-145">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>

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

<span data-ttu-id="84f97-146">Aby uzyskać więcej informacji o używaniu certyfikatów w programie WCF, zobacz [Praca z certyfikatami](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="84f97-146">For more information about using certificates in WCF, see [Working with Certificates](working-with-certificates.md).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="84f97-147">zabezpieczenia .NET Framework</span><span class="sxs-lookup"><span data-stu-id="84f97-147">.NET Framework security</span></span>

<span data-ttu-id="84f97-148">Pamiętaj o usunięciu wszelkich tymczasowych certyfikatów głównych urzędów **certyfikacji z zaufanych głównych źródeł certyfikatów** i folderów **osobistych** , klikając prawym przyciskiem myszy certyfikat, a następnie klikając polecenie **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="84f97-148">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>

## <a name="see-also"></a><span data-ttu-id="84f97-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84f97-149">See also</span></span>

- [<span data-ttu-id="84f97-150">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="84f97-150">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="84f97-151">Instrukcje: wyświetlanie certyfikatów w przystawce programu MMC</span><span class="sxs-lookup"><span data-stu-id="84f97-151">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="84f97-152">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="84f97-152">Securing Services and Clients</span></span>](securing-services-and-clients.md)
