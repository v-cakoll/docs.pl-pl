---
title: 'Instrukcje: Udostępnianie certyfikatów X.509 w architekturze WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 0917569b556c31413b715d75c83a96f3a4b015d7
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48579975"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="c0cd9-102">Instrukcje: Udostępnianie certyfikatów X.509 w architekturze WCF</span><span class="sxs-lookup"><span data-stu-id="c0cd9-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="c0cd9-103">Aby udostępnić certyfikat X.509 do programu Windows Communication Foundation (WCF), kod aplikacji należy określić nazwę magazynu certyfikatów i lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="c0cd9-104">W pewnych okolicznościach tożsamość procesu musi mieć dostęp do pliku, który zawiera klucz prywatny skojarzony z certyfikatem X.509.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="c0cd9-105">Aby uzyskać klucz prywatny skojarzony z certyfikatem X.509 w magazynie certyfikatów, WCF musi mieć uprawnienie, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="c0cd9-106">Domyślnie tylko właściciel i konto systemowe dostęp klucza prywatnego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="c0cd9-107">Aby Udostępnianie certyfikatów X.509 w architekturze WCF</span><span class="sxs-lookup"><span data-stu-id="c0cd9-107">To make X.509 certificates accessible to WCF</span></span>  
  
1.  <span data-ttu-id="c0cd9-108">Należy podać konto, które WCF działa dostęp do odczytu do pliku, który zawiera klucz prywatny skojarzony z certyfikatem X.509.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1.  <span data-ttu-id="c0cd9-109">Ustal, czy WCF wymaga dostęp do odczytu do klucza prywatnego dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="c0cd9-110">W poniższej tabeli przedstawiono, czy klucz prywatny musi być dostępny w przypadku korzystania z certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="c0cd9-111">Użyj certyfikatu X.509</span><span class="sxs-lookup"><span data-stu-id="c0cd9-111">X.509 certificate use</span></span>|<span data-ttu-id="c0cd9-112">klucz prywatny</span><span class="sxs-lookup"><span data-stu-id="c0cd9-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="c0cd9-113">Cyfrowego podpisywania wychodzących wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="c0cd9-114">Tak</span><span class="sxs-lookup"><span data-stu-id="c0cd9-114">Yes</span></span>|  
        |<span data-ttu-id="c0cd9-115">Sprawdzanie podpisu dla ruchu przychodzącego komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="c0cd9-116">Nie</span><span class="sxs-lookup"><span data-stu-id="c0cd9-116">No</span></span>|  
        |<span data-ttu-id="c0cd9-117">Szyfrowanie ruchu wychodzącego komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="c0cd9-118">Nie</span><span class="sxs-lookup"><span data-stu-id="c0cd9-118">No</span></span>|  
        |<span data-ttu-id="c0cd9-119">Odszyfrowywanie ruchu przychodzącego komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="c0cd9-120">Tak</span><span class="sxs-lookup"><span data-stu-id="c0cd9-120">Yes</span></span>|  
  
    2.  <span data-ttu-id="c0cd9-121">Określ lokalizację magazynu certyfikatów i nazwy, w którym przechowywany jest certyfikat.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="c0cd9-122">Magazyn certyfikatów, w którym przechowywany jest certyfikat jest określona w kodzie aplikacji lub w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="c0cd9-123">Na przykład w poniższym przykładzie określono, że certyfikat znajduje się w `CurrentUser` magazynie certyfikatów o nazwie `My`.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  <span data-ttu-id="c0cd9-124">Określić lokalizację klucza prywatnego dla certyfikatu na komputerze przy użyciu [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="c0cd9-125">[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) narzędzie wymaga nazwę magazynu certyfikatów, lokalizacja magazynu certyfikatów i coś, który unikatowo identyfikuje certyfikat.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="c0cd9-126">Narzędzie akceptuje nazwa podmiotu certyfikatu lub jego odcisk palca jako unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="c0cd9-127">Aby uzyskać więcej informacji dotyczących sposobu ustalenia odcisku palca certyfikatu, zobacz [porady: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="c0cd9-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="c0cd9-128">Poniższy przykład kodu wykorzystuje [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) narzędzie, aby określić lokalizację klucza prywatnego dla certyfikatu w `My` przechowywać w `CurrentUser` za pomocą odcisku palca `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  <span data-ttu-id="c0cd9-129">Określ konto, na której działają usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="c0cd9-130">W poniższej tabeli przedstawiono konto, na którym uruchomiono usługi WCF w danym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="c0cd9-131">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="c0cd9-131">Scenario</span></span>|<span data-ttu-id="c0cd9-132">Tożsamość procesu</span><span class="sxs-lookup"><span data-stu-id="c0cd9-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="c0cd9-133">Klient (Konsola lub aplikace WinForms).</span><span class="sxs-lookup"><span data-stu-id="c0cd9-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="c0cd9-134">Aktualnie zalogowany użytkownik.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="c0cd9-135">Usługa, która jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-135">Service that is self-hosted.</span></span>|<span data-ttu-id="c0cd9-136">Aktualnie zalogowany użytkownik.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="c0cd9-137">Usługa, która znajduje się w usługach IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) lub usług IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="c0cd9-137">Service that is hosted in IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) or IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span></span>|<span data-ttu-id="c0cd9-138">USŁUGA SIECIOWA</span><span class="sxs-lookup"><span data-stu-id="c0cd9-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="c0cd9-139">To znaczy usług hostowanych w usługach IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="c0cd9-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="c0cd9-140">W wartości clientauthtrustmode `<processModel>` elementu w pliku Machine.config.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="c0cd9-141">Domyślne konto to ASPNET.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-141">The default account is ASPNET.</span></span>|  
  
    5.  <span data-ttu-id="c0cd9-142">Przyznaj dostęp do odczytu do pliku, który zawiera klucz prywatny do konta, które WCF jest uruchamiany, za pomocą narzędzia takiego jak icacls.exe.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="c0cd9-143">Poniższy przykład kodu umożliwia edytowanie listy kontroli dostępu (DACL) określonego pliku do udzielania odczytu konta Usługa sieciowa (: R) dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="c0cd9-143">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```  
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="c0cd9-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0cd9-144">See Also</span></span>  
- [<span data-ttu-id="c0cd9-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="c0cd9-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)  
- [<span data-ttu-id="c0cd9-146">Instrukcje: pobieranie odcisku palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="c0cd9-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
- [<span data-ttu-id="c0cd9-147">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="c0cd9-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
