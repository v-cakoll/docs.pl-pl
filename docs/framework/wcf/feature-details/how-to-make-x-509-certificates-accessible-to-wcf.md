---
title: "Instrukcje: Udostępnianie certyfikatów X.509 w architekturze WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e03a38e2a93dd866bc3da65527d5410b09009e00
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="882ef-102">Instrukcje: Udostępnianie certyfikatów X.509 w architekturze WCF</span><span class="sxs-lookup"><span data-stu-id="882ef-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="882ef-103">Aby udostępnić certyfikat X.509 do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], kod aplikacji należy określić nazwę magazynu certyfikatów i lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="882ef-103">To make an X.509 certificate accessible to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], application code must specify the certificate store name and location.</span></span> <span data-ttu-id="882ef-104">W pewnych okolicznościach tożsamość procesu musi mieć dostęp do pliku, który zawiera klucz prywatny skojarzony z certyfikatem X.509.</span><span class="sxs-lookup"><span data-stu-id="882ef-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="882ef-105">Aby uzyskać klucz prywatny skojarzony z certyfikatem X.509 w magazynie certyfikatów [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] musi mieć uprawnienia, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="882ef-105">To obtain the private key associated with an X.509 certificate in a certificate store, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] must have permission to do so.</span></span> <span data-ttu-id="882ef-106">Domyślnie tylko właściciel i konta System można uzyskać dostępu do klucza prywatnego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="882ef-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="882ef-107">Aby Udostępnianie certyfikatów X.509 w architekturze WCF</span><span class="sxs-lookup"><span data-stu-id="882ef-107">To make X.509 certificates accessible to WCF</span></span>  
  
1.  <span data-ttu-id="882ef-108">Nadaj kontu, pod którym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] działa dostęp do odczytu do pliku, który zawiera klucz prywatny skojarzony z certyfikatem X.509.</span><span class="sxs-lookup"><span data-stu-id="882ef-108">Give the account under which [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1.  <span data-ttu-id="882ef-109">Określić, czy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wymaga dostępu do odczytu do klucza prywatnego dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="882ef-109">Determine whether [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="882ef-110">Poniższa tabela zawiera szczegóły, czy klucz prywatny musi być dostępny w przypadku używania certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="882ef-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="882ef-111">Użyj certyfikatu X.509</span><span class="sxs-lookup"><span data-stu-id="882ef-111">X.509 certificate use</span></span>|<span data-ttu-id="882ef-112">klucz prywatny</span><span class="sxs-lookup"><span data-stu-id="882ef-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="882ef-113">Cyfrowego podpisywania wychodzących wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="882ef-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="882ef-114">Tak</span><span class="sxs-lookup"><span data-stu-id="882ef-114">Yes</span></span>|  
        |<span data-ttu-id="882ef-115">Sprawdzanie podpisu dla ruchu przychodzącego komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="882ef-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="882ef-116">Nie</span><span class="sxs-lookup"><span data-stu-id="882ef-116">No</span></span>|  
        |<span data-ttu-id="882ef-117">Szyfrowanie wiadomości wychodzącej protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="882ef-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="882ef-118">Nie</span><span class="sxs-lookup"><span data-stu-id="882ef-118">No</span></span>|  
        |<span data-ttu-id="882ef-119">Odszyfrowywanie przychodzącego komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="882ef-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="882ef-120">Tak</span><span class="sxs-lookup"><span data-stu-id="882ef-120">Yes</span></span>|  
  
    2.  <span data-ttu-id="882ef-121">Ustal lokalizacja magazynu certyfikatów i nazwy, w którym przechowywany jest certyfikat.</span><span class="sxs-lookup"><span data-stu-id="882ef-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="882ef-122">Magazyn certyfikatów, w którym znajduje się certyfikat jest określona w kodzie aplikacji lub w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="882ef-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="882ef-123">Na przykład w poniższym przykładzie określa, że certyfikat znajduje się w `CurrentUser` magazynie certyfikatów o nazwie `My`.</span><span class="sxs-lookup"><span data-stu-id="882ef-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  <span data-ttu-id="882ef-124">Określić lokalizację klucza prywatnego dla certyfikatu na komputerze przy użyciu [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="882ef-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="882ef-125">[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) narzędzie wymaga nazwę magazynu certyfikatów, lokalizacja magazynu certyfikatów i coś, który unikatowo identyfikuje certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="882ef-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="882ef-126">Narzędzie akceptuje nazwa podmiotu certyfikatu lub jego odcisk palca jako unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="882ef-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="882ef-127">jak ustalić odcisk palca certyfikatu, zobacz temat [porady: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="882ef-127"> how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="882ef-128">Poniższy przykład kodu wykorzystuje [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) narzędzia, aby określić lokalizację klucza prywatnego dla certyfikatu w `My` przechowywać w `CurrentUser` z odciskiem palca `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span><span class="sxs-lookup"><span data-stu-id="882ef-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  <span data-ttu-id="882ef-129">Określić konto który [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="882ef-129">Determine the account that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running under.</span></span>  
  
         <span data-ttu-id="882ef-130">W poniższej tabeli przedstawiono konto, na którym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest uruchomiona w danym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="882ef-130">The following table details the account under which [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="882ef-131">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="882ef-131">Scenario</span></span>|<span data-ttu-id="882ef-132">Tożsamość procesu</span><span class="sxs-lookup"><span data-stu-id="882ef-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="882ef-133">Klient (konsoli lub aplikacja WinForms).</span><span class="sxs-lookup"><span data-stu-id="882ef-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="882ef-134">Aktualnie zalogowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="882ef-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="882ef-135">Usługa, która jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="882ef-135">Service that is self-hosted.</span></span>|<span data-ttu-id="882ef-136">Aktualnie zalogowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="882ef-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="882ef-137">Usługa, która znajduje się w usługach IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) lub usług IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="882ef-137">Service that is hosted in IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) or IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span></span>|<span data-ttu-id="882ef-138">USŁUGA SIECIOWA</span><span class="sxs-lookup"><span data-stu-id="882ef-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="882ef-139">Oznacza to usługi hostowanej w usługach IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="882ef-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="882ef-140">Steruje `<processModel>` elementu w pliku Machine.config.</span><span class="sxs-lookup"><span data-stu-id="882ef-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="882ef-141">Domyślne konto jest ASPNET.</span><span class="sxs-lookup"><span data-stu-id="882ef-141">The default account is ASPNET.</span></span>|  
  
    5.  <span data-ttu-id="882ef-142">Dostęp do pliku, który zawiera klucz prywatny, aby konto który [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] działa w ramach, przy użyciu narzędzia, takiego jak cacls.exe.</span><span class="sxs-lookup"><span data-stu-id="882ef-142">Grant read access to the file that contains the private key to the account that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running under, using a tool such as cacls.exe.</span></span>  
  
         <span data-ttu-id="882ef-143">Poniższy kod przykładowy edycji (/ E) listy kontroli dostępu (ACL) dla określonego pliku udzielić (/ G) odczytu konto Usługa sieciowa (: R) dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="882ef-143">The following code example edits (/E) the access control list (ACL) for the specified file to grant (/G) the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```  
        cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="882ef-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="882ef-144">See Also</span></span>  
 [<span data-ttu-id="882ef-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="882ef-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)  
 [<span data-ttu-id="882ef-146">Porady: Pobieranie odcisku palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="882ef-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
 [<span data-ttu-id="882ef-147">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="882ef-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
