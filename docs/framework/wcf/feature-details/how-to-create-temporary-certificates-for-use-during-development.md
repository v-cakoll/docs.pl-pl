---
title: 'Instrukcje: Tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f5a096fd6e052fc744af5cee1ab0d322e1daafe6
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="0c62e-102">Instrukcje: Tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania</span><span class="sxs-lookup"><span data-stu-id="0c62e-102">How to: Create Temporary Certificates for Use During Development</span></span>
<span data-ttu-id="0c62e-103">Podczas tworzenia bezpiecznego usługi lub klienta przy użyciu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], jest często przekazać certyfikat X.509 mają być używane jako poświadczenie.</span><span class="sxs-lookup"><span data-stu-id="0c62e-103">When developing a secure service or client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="0c62e-104">Certyfikat jest zwykle częścią łańcucha certyfikatów przy użyciu głównego urzędu został znaleziony w magazynie zaufanych głównych urzędów certyfikacji komputera.</span><span class="sxs-lookup"><span data-stu-id="0c62e-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="0c62e-105">Posiadanie łańcuch certyfikatów umożliwia określania zakresu zestawu certyfikatów, w których zwykle głównego urzędu certyfikacji jest od swojej organizacji lub jednostki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="0c62e-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="0c62e-106">Aby emulować to w czasie tworzenia, możesz utworzyć dwa certyfikaty by spełnić ich wymagań zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0c62e-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="0c62e-107">Pierwsza to certyfikatu z podpisem własnym, który jest umieszczony w magazynie zaufanych głównych urzędów certyfikacji i drugiego certyfikatu jest tworzona na podstawie pierwszego i znajduje się w magazynie osobistym lokalizacji komputera lokalnego lub w magazynie osobistym Bieżąca lokalizacja użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0c62e-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="0c62e-108">W tym temacie przedstawiono kroki, aby utworzyć tych dwóch certyfikatów przy użyciu [narzędzie tworzenia certyfikatów (MakeCert.exe)](http://go.microsoft.com/fwlink/?LinkId=248185), które są dostarczane przez [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="0c62e-108">This topic walks through the steps to create these two certificates using the [Certificate Creation Tool (MakeCert.exe)](http://go.microsoft.com/fwlink/?LinkId=248185), which is provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0c62e-109">Narzędzie do tworzenia certyfikacji generuje certyfikaty są udostępniane tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="0c62e-109">The certificates the Certification Creation tool generates are provided for testing purposes only.</span></span> <span data-ttu-id="0c62e-110">Podczas wdrażania usługi lub klienta, należy użyć odpowiedni certyfikat dostarczony przez urząd certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="0c62e-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="0c62e-111">Może to być albo z [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certyfikatów serwera w organizacji lub innych firm.</span><span class="sxs-lookup"><span data-stu-id="0c62e-111">This could either be from a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certificate server in your organization or a third party.</span></span>  
>   
>  <span data-ttu-id="0c62e-112">Domyślnie [Makecert.exe (narzędzie tworzenia certyfikatów)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) tworzy certyfikaty, których główny urząd certyfikacji jest nazywany "Agencji głównego **."**</span><span class="sxs-lookup"><span data-stu-id="0c62e-112">By default, the [Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) creates certificates whose root authority is called "Root Agency **."**</span></span> <span data-ttu-id="0c62e-113">Ponieważ agencję"główny" nie ma w magazynie zaufanych głównych urzędów certyfikacji, dzięki temu te certyfikaty niezabezpieczonych.</span><span class="sxs-lookup"><span data-stu-id="0c62e-113">Because the "Root Agency" is not in the Trusted Root Certification Authorities store, this makes these certificates insecure.</span></span> <span data-ttu-id="0c62e-114">Tworzenie certyfikatu z podpisem własnym, który znajduje się w zaufanych głównych urzędów certyfikacji magazynu umożliwia utworzenie Środowisko deweloperskie, która symuluje dokładniejsze środowiska wdrażania.</span><span class="sxs-lookup"><span data-stu-id="0c62e-114">Creating a self-signed certificate that is placed in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>  
  
 <span data-ttu-id="0c62e-115">Aby uzyskać więcej informacji na temat tworzenia i używania certyfikatów, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="0c62e-115">For more information about creating and using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="0c62e-116">Aby uzyskać więcej informacji o używaniu certyfikatu jako poświadczeń, zobacz [zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="0c62e-116">For more information about using a certificate as a credential, see [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="0c62e-117">Samouczek dotyczący przy użyciu technologii Microsoft Authenticode, zobacz [Authenticode omówienia i samouczki](http://go.microsoft.com/fwlink/?LinkId=88919).</span><span class="sxs-lookup"><span data-stu-id="0c62e-117">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](http://go.microsoft.com/fwlink/?LinkId=88919).</span></span>  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="0c62e-118">Utwórz samopodpisany certyfikat głównego urzędu certyfikacji i eksportowanie klucza prywatnego</span><span class="sxs-lookup"><span data-stu-id="0c62e-118">To create a self-signed root authority certificate and export the private key</span></span>  
  
1.  <span data-ttu-id="0c62e-119">Za pomocą narzędzia MakeCert.exe z następujących parametrów:</span><span class="sxs-lookup"><span data-stu-id="0c62e-119">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="0c62e-120">`-n` `subjectName`.</span><span class="sxs-lookup"><span data-stu-id="0c62e-120">`-n` `subjectName`.</span></span> <span data-ttu-id="0c62e-121">Określa nazwę podmiotu.</span><span class="sxs-lookup"><span data-stu-id="0c62e-121">Specifies the subject name.</span></span> <span data-ttu-id="0c62e-122">Konwencji jest przed nazwą podmiotu "CN =" dla "Nazwa pospolita".</span><span class="sxs-lookup"><span data-stu-id="0c62e-122">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    2.  <span data-ttu-id="0c62e-123">`-r`.</span><span class="sxs-lookup"><span data-stu-id="0c62e-123">`-r`.</span></span> <span data-ttu-id="0c62e-124">Określa, że certyfikat będzie podpisem.</span><span class="sxs-lookup"><span data-stu-id="0c62e-124">Specifies that the certificate will be self-signed.</span></span>  
  
    3.  <span data-ttu-id="0c62e-125">`-sv` `privateKeyFile`.</span><span class="sxs-lookup"><span data-stu-id="0c62e-125">`-sv` `privateKeyFile`.</span></span> <span data-ttu-id="0c62e-126">Określa plik, który zawiera kontener klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="0c62e-126">Specifies the file that contains the private key container.</span></span>  
  
     <span data-ttu-id="0c62e-127">Na przykład następujące polecenie tworzy certyfikat z podpisem własnym z nazwą podmiotu "CN = TempCA."</span><span class="sxs-lookup"><span data-stu-id="0c62e-127">For example, the following command creates a self-signed certificate with a subject name of "CN=TempCA."</span></span>  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     <span data-ttu-id="0c62e-128">Pojawi się monit o podanie hasła do ochrony klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="0c62e-128">You will be prompted to provide a password to protect the private key.</span></span> <span data-ttu-id="0c62e-129">To hasło jest wymagane, gdy Tworzenie certyfikatu podpisanego przez ten certyfikat główny.</span><span class="sxs-lookup"><span data-stu-id="0c62e-129">This password is required when creating a certificate signed by this root certificate.</span></span>  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="0c62e-130">Aby utworzyć nowy certyfikat podpisany przez certyfikat głównego urzędu certyfikacji</span><span class="sxs-lookup"><span data-stu-id="0c62e-130">To create a new certificate signed by a root authority certificate</span></span>  
  
1.  <span data-ttu-id="0c62e-131">Za pomocą narzędzia MakeCert.exe z następujących parametrów:</span><span class="sxs-lookup"><span data-stu-id="0c62e-131">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="0c62e-132">`-sk` `subjectKey`.</span><span class="sxs-lookup"><span data-stu-id="0c62e-132">`-sk` `subjectKey`.</span></span> <span data-ttu-id="0c62e-133">Lokalizacja kontenera klucza podmiotu, który zawiera klucz prywatny.</span><span class="sxs-lookup"><span data-stu-id="0c62e-133">The location of the subject's key container that holds the private key.</span></span> <span data-ttu-id="0c62e-134">Jeśli kontener kluczy nie istnieje, zostanie utworzony jeden.</span><span class="sxs-lookup"><span data-stu-id="0c62e-134">If a key container does not exist, one is created.</span></span> <span data-ttu-id="0c62e-135">Jeśli żadna z opcji -sk lub - sv jest używana, kontener klucza o nazwie JoeSoft zostanie utworzony domyślnie.</span><span class="sxs-lookup"><span data-stu-id="0c62e-135">If neither of the -sk or -sv options is used, a key container called JoeSoft is created by default.</span></span>  
  
    2.  <span data-ttu-id="0c62e-136">`-n` `subjectName`.</span><span class="sxs-lookup"><span data-stu-id="0c62e-136">`-n` `subjectName`.</span></span> <span data-ttu-id="0c62e-137">Określa nazwę podmiotu.</span><span class="sxs-lookup"><span data-stu-id="0c62e-137">Specifies the subject name.</span></span> <span data-ttu-id="0c62e-138">Konwencji jest przed nazwą podmiotu "CN =" dla "Nazwa pospolita".</span><span class="sxs-lookup"><span data-stu-id="0c62e-138">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    3.  <span data-ttu-id="0c62e-139">`-iv` `issuerKeyFile`.</span><span class="sxs-lookup"><span data-stu-id="0c62e-139">`-iv` `issuerKeyFile`.</span></span> <span data-ttu-id="0c62e-140">Określa plik klucza prywatnego przez wystawcę.</span><span class="sxs-lookup"><span data-stu-id="0c62e-140">Specifies the issuer's private key file.</span></span>  
  
    4.  <span data-ttu-id="0c62e-141">`-ic` `issuerCertFile`.</span><span class="sxs-lookup"><span data-stu-id="0c62e-141">`-ic` `issuerCertFile`.</span></span> <span data-ttu-id="0c62e-142">Określa lokalizację wystawcy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="0c62e-142">Specifies the location of the issuer's certificate.</span></span>  
  
     <span data-ttu-id="0c62e-143">Na przykład następujące polecenie tworzy certyfikat z podpisem `TempCA` certyfikat głównego urzędu certyfikacji z nazwą podmiotu `"CN=SignedByCA"` przy użyciu klucza prywatnego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="0c62e-143">For example, the following command creates a certificate signed by the `TempCA` root authority certificate with a subject name of `"CN=SignedByCA"` using the private key of the issuer.</span></span>  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="0c62e-144">Instalowanie certyfikatu w magazynie zaufanych urzędów certyfikacji głównego</span><span class="sxs-lookup"><span data-stu-id="0c62e-144">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>  
 <span data-ttu-id="0c62e-145">Po utworzeniu certyfikatu z podpisem własnym można zainstalować go w magazynie zaufanych głównych urzędów certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="0c62e-145">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="0c62e-146">Wszystkie certyfikaty, które są podpisane przy użyciu certyfikatu w tym momencie są zaufane przez komputer.</span><span class="sxs-lookup"><span data-stu-id="0c62e-146">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="0c62e-147">Z tego powodu należy usunąć certyfikat z magazynu jak nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="0c62e-147">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="0c62e-148">Jeśli usuniesz ten certyfikat głównego urzędu certyfikacji, wszystkie certyfikaty, które podpisane z nim stają się nieautoryzowane.</span><span class="sxs-lookup"><span data-stu-id="0c62e-148">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="0c62e-149">Certyfikaty urzędu głównego są po prostu mechanizm zgodnie z którymi grupy certyfikatów można ograniczyć zakres niezbędne.</span><span class="sxs-lookup"><span data-stu-id="0c62e-149">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="0c62e-150">Na przykład w aplikacji peer-to-peer, nie ma zwykle nie jest konieczne urząd główny ponieważ tożsamość osoby po prostu zaufania przez podany certyfikat.</span><span class="sxs-lookup"><span data-stu-id="0c62e-150">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="0c62e-151">Aby zainstalować certyfikat z podpisem własnym w zaufane główne urzędy certyfikacji</span><span class="sxs-lookup"><span data-stu-id="0c62e-151">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>  
  
1.  <span data-ttu-id="0c62e-152">Otwórz przystawkę certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="0c62e-152">Open the certificate snap-in.</span></span> <span data-ttu-id="0c62e-153">Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie certyfikatów w przystawce MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="0c62e-153">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2.  <span data-ttu-id="0c62e-154">Otwórz folder z certyfikatem, albo **komputera lokalnego** lub **bieżącego użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="0c62e-154">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>  
  
3.  <span data-ttu-id="0c62e-155">Otwórz **zaufane główne urzędy certyfikacji** folderu.</span><span class="sxs-lookup"><span data-stu-id="0c62e-155">Open the **Trusted Root Certification Authorities** folder.</span></span>  
  
4.  <span data-ttu-id="0c62e-156">Kliknij prawym przyciskiem myszy **certyfikaty** folder i kliknij przycisk **wszystkie zadania**, następnie kliknij przycisk **importu**.</span><span class="sxs-lookup"><span data-stu-id="0c62e-156">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>  
  
5.  <span data-ttu-id="0c62e-157">Postępuj zgodnie z wyświetlanymi na ekranie kreatora instrukcjami, aby zaimportować TempCa.cer magazynu.</span><span class="sxs-lookup"><span data-stu-id="0c62e-157">Follow the on-screen wizard instructions to import the TempCa.cer into the store.</span></span>  
  
## <a name="using-certificates-with-wcf"></a><span data-ttu-id="0c62e-158">Za pomocą certyfikatów z programem WCF</span><span class="sxs-lookup"><span data-stu-id="0c62e-158">Using Certificates With WCF</span></span>  
 <span data-ttu-id="0c62e-159">Po skonfigurowaniu certyfikatów tymczasowych można używać ich do opracowywania rozwiązań WCF, które określają certyfikatów jako typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="0c62e-159">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="0c62e-160">Na przykład następująca konfiguracja XML określa zabezpieczeń komunikatów i certyfikatu jako typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="0c62e-160">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="0c62e-161">Aby określić certyfikat jako typu poświadczeń klienta</span><span class="sxs-lookup"><span data-stu-id="0c62e-161">To specify a certificate as the client credential type</span></span>  
  
-   <span data-ttu-id="0c62e-162">W pliku konfiguracji dla usługi użyj następujący kod XML, aby ustawić trybu zabezpieczeń do wiadomości i typu poświadczeń klienta do certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="0c62e-162">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>  
  
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
  
 <span data-ttu-id="0c62e-163">W pliku konfiguracji dla klienta użyj następującego kodu XML, aby określić certyfikat został znaleziony w magazynie użytkownika czy można znaleźć, wyszukując pole SubjectName dla wartości "CohoWinery."</span><span class="sxs-lookup"><span data-stu-id="0c62e-163">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>  
  
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
  
 <span data-ttu-id="0c62e-164">Aby uzyskać więcej informacji o używaniu certyfikatów w programie WCF, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="0c62e-164">For more information about using certificates in WCF, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0c62e-165">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="0c62e-165">.NET Framework Security</span></span>  
 <span data-ttu-id="0c62e-166">Pamiętaj usunąć wszystkie certyfikaty urzędu tymczasowego katalogu głównego z **zaufane główne urzędy certyfikacji** i **osobistych** folderów przez kliknięcie prawym przyciskiem myszy certyfikat, a następnie klikając polecenie  **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="0c62e-166">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c62e-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c62e-167">See Also</span></span>  
 [<span data-ttu-id="0c62e-168">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="0c62e-168">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="0c62e-169">Instrukcje: wyświetlanie certyfikatów w przystawce programu MMC</span><span class="sxs-lookup"><span data-stu-id="0c62e-169">How to: View Certificates with the MMC Snap-in</span></span>](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [<span data-ttu-id="0c62e-170">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="0c62e-170">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
