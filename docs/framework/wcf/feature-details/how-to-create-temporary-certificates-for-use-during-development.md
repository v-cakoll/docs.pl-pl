---
title: 'Instrukcje: Tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: ca495c23b30144013b8efe22b7bf6f3cf38b16cd
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591701"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="bcd63-102">Instrukcje: Tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania</span><span class="sxs-lookup"><span data-stu-id="bcd63-102">How to: Create Temporary Certificates for Use During Development</span></span>
<span data-ttu-id="bcd63-103">Podczas tworzenia bezpiecznego usługi lub klienta przy użyciu usługi Windows Communication Foundation (WCF), często jest konieczne dostarczanie certyfikatu X.509, który ma być używany jako poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="bcd63-103">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="bcd63-104">Certyfikat jest zazwyczaj w łańcuchu certyfikatów za pomocą głównego urzędu znaleziono w magazynie zaufanych głównych urzędów certyfikacji komputera.</span><span class="sxs-lookup"><span data-stu-id="bcd63-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="bcd63-105">Posiadanie łańcuch certyfikatów umożliwia określania zakresu zestawu certyfikatów, w których zwykle głównego urzędu certyfikacji jest od swojej organizacji lub jednostki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="bcd63-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="bcd63-106">Aby emulować to w czasie programowania, można utworzyć dwa certyfikaty do spełnienia wymagań dotyczących zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bcd63-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="bcd63-107">Pierwsza to certyfikat z podpisem własnym, który jest umieszczony w magazynie zaufanych głównych urzędów certyfikacji i drugiego certyfikatu jest tworzony z pierwszego i znajduje się w magazynie osobistym lokalizacji komputera lokalnego lub w magazynie osobistym Bieżąca lokalizacja użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bcd63-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="bcd63-108">W tym temacie przedstawiono kroki umożliwiające utworzenie tych dwóch certyfikatów przy użyciu programu Powershell [New-SelfSignedCertificate)](https://docs.microsoft.com/en-us/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bcd63-108">This topic walks through the steps to create these two certificates using the Powershell [New-SelfSignedCertificate)](https://docs.microsoft.com/en-us/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps) cmdlet.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bcd63-109">Polecenie cmdlet New-SelfSignedCertificate generuje certyfikaty znajdują się tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="bcd63-109">The certificates that the New-SelfSignedCertificate cmdlet generates are provided for testing purposes only.</span></span> <span data-ttu-id="bcd63-110">Podczas wdrażania usługi lub klienta, należy użyć odpowiedni certyfikat, dostarczone przez urząd certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="bcd63-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="bcd63-111">Może to mieć długość od serwera certyfikatów systemu Windows Server w Twojej organizacji lub innej.</span><span class="sxs-lookup"><span data-stu-id="bcd63-111">This could either be from a Windows Server certificate server in your organization or a third party.</span></span>  
>   
>  <span data-ttu-id="bcd63-112">Domyślnie [New-SelfSignedCertificate](https://docs.microsoft.com/en-us/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps) polecenie cmdlet tworzy certyfikaty, które są z podpisem własnym, a te certyfikaty są niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="bcd63-112">By default, the [New-SelfSignedCertificate](https://docs.microsoft.com/en-us/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps) cmdlet creates certificates that are self-signed and these certificates are insecure.</span></span> <span data-ttu-id="bcd63-113">Umieszczenie certyfikatów z podpisem własnym w zaufanych głównych urzędów certyfikacji magazynu pozwala na tworzenie środowisko programistyczne, które symuluje bardziej ścisłe środowiska wdrażania.</span><span class="sxs-lookup"><span data-stu-id="bcd63-113">Placing the self-signed certificates in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>  
  
 <span data-ttu-id="bcd63-114">Aby uzyskać więcej informacji na temat tworzenia i używania certyfikatów, zobacz [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="bcd63-114">For more information about creating and using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="bcd63-115">Aby uzyskać więcej informacji na temat za pomocą certyfikatu jako poświadczenia zobacz [zabezpieczania usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="bcd63-115">For more information about using a certificate as a credential, see [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="bcd63-116">Aby zapoznać się z samouczkiem dotyczącym przy użyciu technologii Authenticode firmy Microsoft, zobacz [Authenticode omówienia i samouczki](https://go.microsoft.com/fwlink/?LinkId=88919).</span><span class="sxs-lookup"><span data-stu-id="bcd63-116">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://go.microsoft.com/fwlink/?LinkId=88919).</span></span>  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="bcd63-117">Aby utworzyć certyfikat z urzędu głównego z podpisem własnym i wyeksportować klucz prywatny</span><span class="sxs-lookup"><span data-stu-id="bcd63-117">To create a self-signed root authority certificate and export the private key</span></span>  
  
<span data-ttu-id="bcd63-118">Następujące polecenie tworzy certyfikat z podpisem własnym z nazwą podmiotu "RootCA" w magazynie osobistym bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bcd63-118">The following command creates a self-signed certificate with a subject name of "RootCA" in the Current User Personal store.</span></span> 
```
PS $rootCert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("1.3.6.1.4.1.311.21.10={text}1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2")
```
<span data-ttu-id="bcd63-119">Potrzebujemy wyeksportować certyfikat do pliku PFX, tak aby można było importować do miejsca w późniejszym kroku, w których jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="bcd63-119">We need to export the certificate to a PFX file so that it can be imported to where it's needed in a later step.</span></span> <span data-ttu-id="bcd63-120">Podczas eksportowania certyfikatu z kluczem prywatnym, aby chronić go wymaga hasła.</span><span class="sxs-lookup"><span data-stu-id="bcd63-120">When exporting a certificate with the private key, a password is needed to protect it.</span></span> <span data-ttu-id="bcd63-121">Firma Microsoft Zapisz hasło w `SecureString` i użyj [Export-PfxCertificate](https://docs.microsoft.com/en-us/powershell/module/pkiclient/export-pfxcertificate?view=win10-ps) polecenia cmdlet, aby wyeksportować certyfikat z skojarzony klucz prywatny do pliku PFX.</span><span class="sxs-lookup"><span data-stu-id="bcd63-121">We save the password in a `SecureString` and use the [Export-PfxCertificate](https://docs.microsoft.com/en-us/powershell/module/pkiclient/export-pfxcertificate?view=win10-ps) cmdlet to export the certificate with the associated private key to a PFX file.</span></span> <span data-ttu-id="bcd63-122">Oszczędzamy również po prostu certyfikatu publicznego do pliku CRT przy użyciu [eksportu certyfikatu](https://docs.microsoft.com/en-us/powershell/module/pkiclient/export-certificate?view=win10-ps) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bcd63-122">We also save just the public certificate into a CRT file using the [Export-Certificate](https://docs.microsoft.com/en-us/powershell/module/pkiclient/export-certificate?view=win10-ps) cmdlet.</span></span>
```
PS [System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
PS [String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
PS Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
PS Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="bcd63-123">Aby utworzyć nowy certyfikat podpisany przez certyfikat głównego urzędu certyfikacji</span><span class="sxs-lookup"><span data-stu-id="bcd63-123">To create a new certificate signed by a root authority certificate</span></span>  
  
<span data-ttu-id="bcd63-124">Następujące polecenie tworzy certyfikat z podpisem `RootCA` z nazwą podmiotu "SignedByRootCA" przy użyciu klucza prywatnego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="bcd63-124">The following command creates a certificate signed by the `RootCA` with a subject name of "SignedByRootCA" using the private key of the issuer.</span></span>
```
PS $testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert 
```
<span data-ttu-id="bcd63-125">Podobnie oszczędzamy certyfikatu z podpisem z kluczem prywatnym do pliku PFX i tylko klucz publiczny do pliku CRT.</span><span class="sxs-lookup"><span data-stu-id="bcd63-125">Similarly, we save the signed certificate with private key into a PFX file and just the public key into a CRT file.</span></span>
```
PS [String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
PS Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword 
PS Export-Certificate -Cert $testCertPath -FilePath testcert.crt        
```
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="bcd63-126">Instalowanie certyfikatu w zaufanych Store urzędów certyfikacji, który jest głównym</span><span class="sxs-lookup"><span data-stu-id="bcd63-126">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>  
 <span data-ttu-id="bcd63-127">Po utworzeniu certyfikatu z podpisem własnym można zainstalować go w magazynie zaufanych głównych urzędów certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="bcd63-127">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="bcd63-128">Wszystkie certyfikaty, które są podpisane za pomocą certyfikatu, w tym momencie są zaufane przez komputer.</span><span class="sxs-lookup"><span data-stu-id="bcd63-128">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="bcd63-129">Z tego powodu Usuń certyfikat z magazynu, jak tylko nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="bcd63-129">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="bcd63-130">Jeśli usuniesz ten certyfikat głównego urzędu certyfikacji, wszystkie certyfikaty, którzy zalogowali się z nią stają się nieautoryzowanych.</span><span class="sxs-lookup"><span data-stu-id="bcd63-130">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="bcd63-131">Certyfikaty z głównego to po prostu mechanizm zgodnie z którą grupą certyfikatów można zmniejszyć zakres gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="bcd63-131">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="bcd63-132">Na przykład w aplikacji peer-to-peer, zwykle nie ma potrzeby dla głównego urzędu ponieważ tożsamość osoby ufasz po prostu przez podany certyfikat.</span><span class="sxs-lookup"><span data-stu-id="bcd63-132">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="bcd63-133">Aby zainstalować certyfikat z podpisem własnym w zaufanych głównych urzędów certyfikacji</span><span class="sxs-lookup"><span data-stu-id="bcd63-133">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>  
  
1.  <span data-ttu-id="bcd63-134">Otwórz przystawkę certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="bcd63-134">Open the certificate snap-in.</span></span> <span data-ttu-id="bcd63-135">Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie certyfikatów za pomocą przystawki programu MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="bcd63-135">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2.  <span data-ttu-id="bcd63-136">Otwórz folder z certyfikatem, albo **komputera lokalnego** lub **bieżącego użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="bcd63-136">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>  
  
3.  <span data-ttu-id="bcd63-137">Otwórz **zaufane główne urzędy certyfikacji** folderu.</span><span class="sxs-lookup"><span data-stu-id="bcd63-137">Open the **Trusted Root Certification Authorities** folder.</span></span>  
  
4.  <span data-ttu-id="bcd63-138">Kliknij prawym przyciskiem myszy **certyfikaty** folder i kliknij przycisk **wszystkie zadania**, następnie kliknij przycisk **importu**.</span><span class="sxs-lookup"><span data-stu-id="bcd63-138">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>  
  
5.  <span data-ttu-id="bcd63-139">Postępuj zgodnie z wyświetlanymi na ekranie kreatora instrukcjami, aby zaimportować TempCa.cer do magazynu.</span><span class="sxs-lookup"><span data-stu-id="bcd63-139">Follow the on-screen wizard instructions to import the TempCa.cer into the store.</span></span>  
  
## <a name="using-certificates-with-wcf"></a><span data-ttu-id="bcd63-140">Używanie certyfikatów z programem WCF</span><span class="sxs-lookup"><span data-stu-id="bcd63-140">Using Certificates With WCF</span></span>  
 <span data-ttu-id="bcd63-141">Po skonfigurowaniu certyfikatów tymczasowych można ich użyć do opracowywania rozwiązań usługi WCF, które określają certyfikaty jako typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="bcd63-141">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="bcd63-142">Na przykład następującej konfiguracji XML określa zabezpieczenia komunikatów i certyfikatu jako typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="bcd63-142">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="bcd63-143">Aby określić certyfikat jako typu poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="bcd63-143">To specify a certificate as the client credential type</span></span>  
  
-   <span data-ttu-id="bcd63-144">W pliku konfiguracji usługi umożliwia ustawianie trybu zabezpieczeń do wiadomości i typu poświadczeń klienta do certyfikatu następujący kod XML.</span><span class="sxs-lookup"><span data-stu-id="bcd63-144">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>  
  
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
  
 <span data-ttu-id="bcd63-145">W pliku konfiguracji dla klienta użyj następujący kod XML, aby określić, czy certyfikat został znaleziony w magazynie użytkownika i można znaleźć, przeszukując pola SubjectName dla wartości "CohoWinery."</span><span class="sxs-lookup"><span data-stu-id="bcd63-145">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>  
  
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
  
 <span data-ttu-id="bcd63-146">Aby uzyskać więcej informacji na temat korzystania z certyfikatów w programie WCF zobacz [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="bcd63-146">For more information about using certificates in WCF, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bcd63-147">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="bcd63-147">.NET Framework Security</span></span>  
 <span data-ttu-id="bcd63-148">Pamiętaj usunąć wszystkie certyfikaty urzędu głównego tymczasowe z **zaufane główne urzędy certyfikacji** i **osobistych** foldery, klikając prawym przyciskiem myszy certyfikat, a następnie klikając  **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="bcd63-148">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcd63-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bcd63-149">See Also</span></span>  
 [<span data-ttu-id="bcd63-150">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="bcd63-150">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="bcd63-151">Instrukcje: wyświetlanie certyfikatów w przystawce programu MMC</span><span class="sxs-lookup"><span data-stu-id="bcd63-151">How to: View Certificates with the MMC Snap-in</span></span>](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [<span data-ttu-id="bcd63-152">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="bcd63-152">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
