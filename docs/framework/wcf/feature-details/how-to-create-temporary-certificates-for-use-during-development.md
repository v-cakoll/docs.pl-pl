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
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="c78c7-102">Instrukcje: Tworzenie certyfikatów tymczasowych do użytku w trakcie opracowywania</span><span class="sxs-lookup"><span data-stu-id="c78c7-102">How to: Create Temporary Certificates for Use During Development</span></span>

<span data-ttu-id="c78c7-103">Podczas tworzenia bezpiecznego usługi lub klienta przy użyciu usługi Windows Communication Foundation (WCF), często jest konieczne dostarczanie certyfikatu X.509, który ma być używany jako poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="c78c7-103">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="c78c7-104">Certyfikat jest zazwyczaj w łańcuchu certyfikatów za pomocą głównego urzędu znaleziono w magazynie zaufanych głównych urzędów certyfikacji komputera.</span><span class="sxs-lookup"><span data-stu-id="c78c7-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="c78c7-105">Posiadanie łańcuch certyfikatów umożliwia określania zakresu zestawu certyfikatów, w których zwykle głównego urzędu certyfikacji jest od swojej organizacji lub jednostki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="c78c7-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="c78c7-106">Aby emulować to w czasie programowania, można utworzyć dwa certyfikaty do spełnienia wymagań dotyczących zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c78c7-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="c78c7-107">Pierwsza to certyfikat z podpisem własnym, który jest umieszczony w magazynie zaufanych głównych urzędów certyfikacji i drugiego certyfikatu jest tworzony z pierwszego i znajduje się w magazynie osobistym lokalizacji komputera lokalnego lub w magazynie osobistym Bieżąca lokalizacja użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c78c7-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="c78c7-108">W tym temacie przedstawiono kroki umożliwiające utworzenie tych dwóch certyfikatów przy użyciu programu Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c78c7-108">This topic walks through the steps to create these two certificates using the Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c78c7-109">Polecenie cmdlet New-SelfSignedCertificate generuje certyfikaty znajdują się tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="c78c7-109">The certificates that the New-SelfSignedCertificate cmdlet generates are provided for testing purposes only.</span></span> <span data-ttu-id="c78c7-110">Podczas wdrażania usługi lub klienta, należy użyć odpowiedni certyfikat, dostarczone przez urząd certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="c78c7-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="c78c7-111">Może to mieć długość od serwera certyfikatów systemu Windows Server w Twojej organizacji lub innej.</span><span class="sxs-lookup"><span data-stu-id="c78c7-111">This could either be from a Windows Server certificate server in your organization or a third party.</span></span>
>
> <span data-ttu-id="c78c7-112">Domyślnie [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) polecenie cmdlet tworzy certyfikaty, które są z podpisem własnym, a te certyfikaty są niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="c78c7-112">By default, the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet creates certificates that are self-signed and these certificates are insecure.</span></span> <span data-ttu-id="c78c7-113">Umieszczenie certyfikatów z podpisem własnym w zaufanych głównych urzędów certyfikacji magazynu pozwala na tworzenie środowisko programistyczne, które symuluje bardziej ścisłe środowiska wdrażania.</span><span class="sxs-lookup"><span data-stu-id="c78c7-113">Placing the self-signed certificates in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>

 <span data-ttu-id="c78c7-114">Aby uzyskać więcej informacji na temat tworzenia i używania certyfikatów, zobacz [Working with Certificates](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="c78c7-114">For more information about creating and using certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="c78c7-115">Aby uzyskać więcej informacji na temat za pomocą certyfikatu jako poświadczenia zobacz [zabezpieczania usług i klientów](securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="c78c7-115">For more information about using a certificate as a credential, see [Securing Services and Clients](securing-services-and-clients.md).</span></span> <span data-ttu-id="c78c7-116">Aby zapoznać się z samouczkiem dotyczącym przy użyciu technologii Authenticode firmy Microsoft, zobacz [Authenticode omówienia i samouczki](https://go.microsoft.com/fwlink/?LinkId=88919).</span><span class="sxs-lookup"><span data-stu-id="c78c7-116">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://go.microsoft.com/fwlink/?LinkId=88919).</span></span>

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="c78c7-117">Aby utworzyć certyfikat z urzędu głównego z podpisem własnym i wyeksportować klucz prywatny</span><span class="sxs-lookup"><span data-stu-id="c78c7-117">To create a self-signed root authority certificate and export the private key</span></span>

<span data-ttu-id="c78c7-118">Następujące polecenie tworzy certyfikat z podpisem własnym z nazwą podmiotu "RootCA" w magazynie osobistym bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c78c7-118">The following command creates a self-signed certificate with a subject name of "RootCA" in the Current User Personal store.</span></span>

```powershell
PS $rootCert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("1.3.6.1.4.1.311.21.10={text}1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2")
```

<span data-ttu-id="c78c7-119">Potrzebujemy wyeksportować certyfikat do pliku PFX, tak aby można było importować do miejsca w późniejszym kroku, w których jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="c78c7-119">We need to export the certificate to a PFX file so that it can be imported to where it's needed in a later step.</span></span> <span data-ttu-id="c78c7-120">Podczas eksportowania certyfikatu z kluczem prywatnym, aby chronić go wymaga hasła.</span><span class="sxs-lookup"><span data-stu-id="c78c7-120">When exporting a certificate with the private key, a password is needed to protect it.</span></span> <span data-ttu-id="c78c7-121">Firma Microsoft Zapisz hasło w `SecureString` i użyj [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) polecenia cmdlet, aby wyeksportować certyfikat z skojarzony klucz prywatny do pliku PFX.</span><span class="sxs-lookup"><span data-stu-id="c78c7-121">We save the password in a `SecureString` and use the [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet to export the certificate with the associated private key to a PFX file.</span></span> <span data-ttu-id="c78c7-122">Oszczędzamy również po prostu certyfikatu publicznego do pliku CRT przy użyciu [eksportu certyfikatu](/powershell/module/pkiclient/export-certificate) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c78c7-122">We also save just the public certificate into a CRT file using the [Export-Certificate](/powershell/module/pkiclient/export-certificate) cmdlet.</span></span>

```powershell
PS [System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
PS [String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
PS Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
PS Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="c78c7-123">Aby utworzyć nowy certyfikat podpisany przez certyfikat głównego urzędu certyfikacji</span><span class="sxs-lookup"><span data-stu-id="c78c7-123">To create a new certificate signed by a root authority certificate</span></span>

<span data-ttu-id="c78c7-124">Następujące polecenie tworzy certyfikat z podpisem `RootCA` z nazwą podmiotu "SignedByRootCA" przy użyciu klucza prywatnego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="c78c7-124">The following command creates a certificate signed by the `RootCA` with a subject name of "SignedByRootCA" using the private key of the issuer.</span></span>

```powershell
PS $testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

<span data-ttu-id="c78c7-125">Podobnie oszczędzamy certyfikatu z podpisem z kluczem prywatnym do pliku PFX i tylko klucz publiczny do pliku CRT.</span><span class="sxs-lookup"><span data-stu-id="c78c7-125">Similarly, we save the signed certificate with private key into a PFX file and just the public key into a CRT file.</span></span>

```powershell
PS [String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
PS Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
PS Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="c78c7-126">Instalowanie certyfikatu w zaufanych Store urzędów certyfikacji, który jest głównym</span><span class="sxs-lookup"><span data-stu-id="c78c7-126">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>

<span data-ttu-id="c78c7-127">Po utworzeniu certyfikatu z podpisem własnym można zainstalować go w magazynie zaufanych głównych urzędów certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="c78c7-127">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="c78c7-128">Wszystkie certyfikaty, które są podpisane za pomocą certyfikatu, w tym momencie są zaufane przez komputer.</span><span class="sxs-lookup"><span data-stu-id="c78c7-128">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="c78c7-129">Z tego powodu Usuń certyfikat z magazynu, jak tylko nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="c78c7-129">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="c78c7-130">Jeśli usuniesz ten certyfikat głównego urzędu certyfikacji, wszystkie certyfikaty, którzy zalogowali się z nią stają się nieautoryzowanych.</span><span class="sxs-lookup"><span data-stu-id="c78c7-130">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="c78c7-131">Certyfikaty z głównego to po prostu mechanizm zgodnie z którą grupą certyfikatów można zmniejszyć zakres gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="c78c7-131">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="c78c7-132">Na przykład w aplikacji peer-to-peer, zwykle nie ma potrzeby dla głównego urzędu ponieważ tożsamość osoby ufasz po prostu przez podany certyfikat.</span><span class="sxs-lookup"><span data-stu-id="c78c7-132">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="c78c7-133">Aby zainstalować certyfikat z podpisem własnym w zaufanych głównych urzędów certyfikacji</span><span class="sxs-lookup"><span data-stu-id="c78c7-133">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>

1. <span data-ttu-id="c78c7-134">Otwórz przystawkę certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="c78c7-134">Open the certificate snap-in.</span></span> <span data-ttu-id="c78c7-135">Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie certyfikatów za pomocą przystawki programu MMC](how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="c78c7-135">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

2. <span data-ttu-id="c78c7-136">Otwórz folder z certyfikatem, albo **komputera lokalnego** lub **bieżącego użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="c78c7-136">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>

3. <span data-ttu-id="c78c7-137">Otwórz **zaufane główne urzędy certyfikacji** folderu.</span><span class="sxs-lookup"><span data-stu-id="c78c7-137">Open the **Trusted Root Certification Authorities** folder.</span></span>

4. <span data-ttu-id="c78c7-138">Kliknij prawym przyciskiem myszy **certyfikaty** folder i kliknij przycisk **wszystkie zadania**, następnie kliknij przycisk **importu**.</span><span class="sxs-lookup"><span data-stu-id="c78c7-138">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>

5. <span data-ttu-id="c78c7-139">Postępuj zgodnie z wyświetlanymi na ekranie kreatora instrukcjami, aby zaimportować RootCA.pfx do magazynu.</span><span class="sxs-lookup"><span data-stu-id="c78c7-139">Follow the on-screen wizard instructions to import the RootCA.pfx into the store.</span></span>

## <a name="using-certificates-with-wcf"></a><span data-ttu-id="c78c7-140">Za pomocą certyfikatów przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="c78c7-140">Using certificates With WCF</span></span>

<span data-ttu-id="c78c7-141">Po skonfigurowaniu certyfikatów tymczasowych można ich użyć do opracowywania rozwiązań usługi WCF, które określają certyfikaty jako typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="c78c7-141">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="c78c7-142">Na przykład następującej konfiguracji XML określa zabezpieczenia komunikatów i certyfikatu jako typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="c78c7-142">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="c78c7-143">Aby określić certyfikat jako typu poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="c78c7-143">To specify a certificate as the client credential type</span></span>

- <span data-ttu-id="c78c7-144">W pliku konfiguracji usługi umożliwia ustawianie trybu zabezpieczeń do wiadomości i typu poświadczeń klienta do certyfikatu następujący kod XML.</span><span class="sxs-lookup"><span data-stu-id="c78c7-144">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>

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

<span data-ttu-id="c78c7-145">W pliku konfiguracji dla klienta użyj następujący kod XML, aby określić, czy certyfikat został znaleziony w magazynie użytkownika i można znaleźć, przeszukując pola SubjectName dla wartości "CohoWinery."</span><span class="sxs-lookup"><span data-stu-id="c78c7-145">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>

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

<span data-ttu-id="c78c7-146">Aby uzyskać więcej informacji na temat korzystania z certyfikatów w programie WCF zobacz [Working with Certificates](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="c78c7-146">For more information about using certificates in WCF, see [Working with Certificates](working-with-certificates.md).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="c78c7-147">zabezpieczenia .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c78c7-147">.NET Framework security</span></span>

<span data-ttu-id="c78c7-148">Pamiętaj usunąć wszystkie certyfikaty urzędu głównego tymczasowe z **zaufane główne urzędy certyfikacji** i **osobistych** foldery, klikając prawym przyciskiem myszy certyfikat, a następnie klikając  **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="c78c7-148">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>

## <a name="see-also"></a><span data-ttu-id="c78c7-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c78c7-149">See also</span></span>

- [<span data-ttu-id="c78c7-150">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="c78c7-150">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="c78c7-151">Instrukcje: Wyświetlanie certyfikatów za pomocą przystawki programu MMC</span><span class="sxs-lookup"><span data-stu-id="c78c7-151">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="c78c7-152">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="c78c7-152">Securing Services and Clients</span></span>](securing-services-and-clients.md)
