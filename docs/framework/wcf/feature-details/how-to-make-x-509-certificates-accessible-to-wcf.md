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
ms.openlocfilehash: 7f24966f06730e62ea7a8967c3930f05ca78f50e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347082"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="9dfe6-102">Instrukcje: Udostępnianie certyfikatów X.509 w architekturze WCF</span><span class="sxs-lookup"><span data-stu-id="9dfe6-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="9dfe6-103">Aby udostępnić certyfikat X. 509 dla Windows Communication Foundation (WCF), kod aplikacji musi określać nazwę i lokalizację magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="9dfe6-104">W pewnych okolicznościach tożsamość procesu musi mieć dostęp do pliku, który zawiera klucz prywatny skojarzony z certyfikatem X. 509.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="9dfe6-105">Aby uzyskać klucz prywatny skojarzony z certyfikatem X. 509 w magazynie certyfikatów, WCF musi mieć odpowiednie uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="9dfe6-106">Domyślnie tylko właściciel i konto systemowe mogą uzyskać dostęp do klucza prywatnego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="9dfe6-107">Aby udostępnić certyfikaty X. 509 dla usługi WCF</span><span class="sxs-lookup"><span data-stu-id="9dfe6-107">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="9dfe6-108">Podaj konto, na którym działa funkcja WCF z dostępem do odczytu do pliku, który zawiera klucz prywatny skojarzony z certyfikatem X. 509.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="9dfe6-109">Ustal, czy funkcja WCF wymaga dostępu do odczytu do klucza prywatnego dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="9dfe6-110">W poniższej tabeli przedstawiono informacje o tym, czy klucz prywatny musi być dostępny podczas korzystania z certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="9dfe6-111">Użycie certyfikatu X. 509</span><span class="sxs-lookup"><span data-stu-id="9dfe6-111">X.509 certificate use</span></span>|<span data-ttu-id="9dfe6-112">Klucz prywatny</span><span class="sxs-lookup"><span data-stu-id="9dfe6-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="9dfe6-113">Cyfrowe podpisywanie wychodzącego komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="9dfe6-114">Tak</span><span class="sxs-lookup"><span data-stu-id="9dfe6-114">Yes</span></span>|  
        |<span data-ttu-id="9dfe6-115">Weryfikowanie podpisu przychodzącego komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="9dfe6-116">Nie</span><span class="sxs-lookup"><span data-stu-id="9dfe6-116">No</span></span>|  
        |<span data-ttu-id="9dfe6-117">Szyfrowanie wychodzącego komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="9dfe6-118">Nie</span><span class="sxs-lookup"><span data-stu-id="9dfe6-118">No</span></span>|  
        |<span data-ttu-id="9dfe6-119">Odszyfrowywanie przychodzącego komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="9dfe6-120">Tak</span><span class="sxs-lookup"><span data-stu-id="9dfe6-120">Yes</span></span>|  
  
    2. <span data-ttu-id="9dfe6-121">Określ lokalizację i nazwę magazynu certyfikatów, w którym przechowywany jest certyfikat.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="9dfe6-122">Magazyn certyfikatów, w którym jest przechowywany certyfikat, jest określany w kodzie aplikacji lub w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="9dfe6-123">Na przykład poniższy przykład określa, że certyfikat znajduje się w `CurrentUser` magazyn certyfikatów o nazwie `My`.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="9dfe6-124">Określ, gdzie klucz prywatny certyfikatu znajduje się na komputerze przy użyciu narzędzia [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) .</span><span class="sxs-lookup"><span data-stu-id="9dfe6-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="9dfe6-125">Narzędzie [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) wymaga nazwy magazynu certyfikatów, lokalizacji magazynu certyfikatów i elementu, który jednoznacznie identyfikuje certyfikat.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="9dfe6-126">Narzędzie akceptuje nazwę podmiotu lub odcisk palca certyfikatu jako unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="9dfe6-127">Aby uzyskać więcej informacji na temat sposobu ustalania odcisku palca certyfikatu, zobacz [How to: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="9dfe6-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="9dfe6-128">Poniższy przykład kodu używa narzędzia [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) do określenia lokalizacji klucza prywatnego certyfikatu w magazynie `My` w `CurrentUser` z odciskiem palca `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="9dfe6-129">Określ konto, w ramach którego działa usługa WCF.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="9dfe6-130">W poniższej tabeli przedstawiono szczegółowe informacje na temat konta, pod którym działa usługa WCF w danym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="9dfe6-131">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="9dfe6-131">Scenario</span></span>|<span data-ttu-id="9dfe6-132">Tożsamość procesu</span><span class="sxs-lookup"><span data-stu-id="9dfe6-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="9dfe6-133">Klient (Aplikacja konsolowa lub WinForms).</span><span class="sxs-lookup"><span data-stu-id="9dfe6-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="9dfe6-134">Aktualnie zalogowany użytkownik.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="9dfe6-135">Usługa, która jest samodzielna.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-135">Service that is self-hosted.</span></span>|<span data-ttu-id="9dfe6-136">Aktualnie zalogowany użytkownik.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="9dfe6-137">Usługa hostowana w usługach IIS 6,0 (Windows Server 2003) lub IIS 7,0 (Windows Vista).</span><span class="sxs-lookup"><span data-stu-id="9dfe6-137">Service that is hosted in IIS 6.0 (Windows Server 2003) or IIS 7.0 (Windows Vista).</span></span>|<span data-ttu-id="9dfe6-138">USŁUGA SIECIOWA</span><span class="sxs-lookup"><span data-stu-id="9dfe6-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="9dfe6-139">Usługa hostowana w usługach IIS 5. X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="9dfe6-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="9dfe6-140">Kontrolowane przez element `<processModel>` w pliku Machine. config.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="9dfe6-141">Domyślne konto to ASPNET.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-141">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="9dfe6-142">Przyznaj uprawnienia do odczytu pliku, który zawiera klucz prywatny do konta, w ramach którego działa usługa WCF, przy użyciu narzędzia, takiego jak icacls. exe.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="9dfe6-143">Poniższy przykład kodu umożliwia edycję poufnej listy kontroli dostępu (DACL) dla określonego pliku, aby przyznać kontu usługi sieciowej odczytywanie (: R) dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="9dfe6-143">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console 
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="9dfe6-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9dfe6-144">See also</span></span>

- [<span data-ttu-id="9dfe6-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="9dfe6-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [<span data-ttu-id="9dfe6-146">Instrukcje: pobieranie odcisku palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="9dfe6-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="9dfe6-147">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="9dfe6-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
