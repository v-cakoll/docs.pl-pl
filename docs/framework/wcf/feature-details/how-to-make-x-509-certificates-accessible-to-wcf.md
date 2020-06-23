---
title: 'Instrukcje: Udostępnianie certyfikatów X.509 w architekturze WCF'
description: Dowiedz się, jak udostępnić certyfikat X. 509 dla programu WCF. Kod aplikacji musi określać nazwę i lokalizację magazynu certyfikatów. Mogą istnieć inne wymagania.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 5cc1118640bcf1262d88cb8cdb39939ae315cae3
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246873"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="06d4f-105">Instrukcje: Udostępnianie certyfikatów X.509 w architekturze WCF</span><span class="sxs-lookup"><span data-stu-id="06d4f-105">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="06d4f-106">Aby udostępnić certyfikat X. 509 dla Windows Communication Foundation (WCF), kod aplikacji musi określać nazwę i lokalizację magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="06d4f-106">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="06d4f-107">W pewnych okolicznościach tożsamość procesu musi mieć dostęp do pliku, który zawiera klucz prywatny skojarzony z certyfikatem X. 509.</span><span class="sxs-lookup"><span data-stu-id="06d4f-107">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="06d4f-108">Aby uzyskać klucz prywatny skojarzony z certyfikatem X. 509 w magazynie certyfikatów, WCF musi mieć odpowiednie uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="06d4f-108">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="06d4f-109">Domyślnie tylko właściciel i konto systemowe mogą uzyskać dostęp do klucza prywatnego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="06d4f-109">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="06d4f-110">Aby udostępnić certyfikaty X. 509 dla usługi WCF</span><span class="sxs-lookup"><span data-stu-id="06d4f-110">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="06d4f-111">Podaj konto, na którym działa funkcja WCF z dostępem do odczytu do pliku, który zawiera klucz prywatny skojarzony z certyfikatem X. 509.</span><span class="sxs-lookup"><span data-stu-id="06d4f-111">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="06d4f-112">Ustal, czy funkcja WCF wymaga dostępu do odczytu do klucza prywatnego dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="06d4f-112">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="06d4f-113">W poniższej tabeli przedstawiono informacje o tym, czy klucz prywatny musi być dostępny podczas korzystania z certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="06d4f-113">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="06d4f-114">Użycie certyfikatu X. 509</span><span class="sxs-lookup"><span data-stu-id="06d4f-114">X.509 certificate use</span></span>|<span data-ttu-id="06d4f-115">Klucz prywatny</span><span class="sxs-lookup"><span data-stu-id="06d4f-115">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="06d4f-116">Cyfrowe podpisywanie wychodzącego komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="06d4f-116">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="06d4f-117">Tak</span><span class="sxs-lookup"><span data-stu-id="06d4f-117">Yes</span></span>|  
        |<span data-ttu-id="06d4f-118">Weryfikowanie podpisu przychodzącego komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="06d4f-118">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="06d4f-119">Nie</span><span class="sxs-lookup"><span data-stu-id="06d4f-119">No</span></span>|  
        |<span data-ttu-id="06d4f-120">Szyfrowanie wychodzącego komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="06d4f-120">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="06d4f-121">Nie</span><span class="sxs-lookup"><span data-stu-id="06d4f-121">No</span></span>|  
        |<span data-ttu-id="06d4f-122">Odszyfrowywanie przychodzącego komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="06d4f-122">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="06d4f-123">Tak</span><span class="sxs-lookup"><span data-stu-id="06d4f-123">Yes</span></span>|  
  
    2. <span data-ttu-id="06d4f-124">Określ lokalizację i nazwę magazynu certyfikatów, w którym przechowywany jest certyfikat.</span><span class="sxs-lookup"><span data-stu-id="06d4f-124">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="06d4f-125">Magazyn certyfikatów, w którym jest przechowywany certyfikat, jest określany w kodzie aplikacji lub w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="06d4f-125">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="06d4f-126">Na przykład poniższy przykład określa, że certyfikat znajduje się w `CurrentUser` magazynie certyfikatów o nazwie `My` .</span><span class="sxs-lookup"><span data-stu-id="06d4f-126">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="06d4f-127">Określ, gdzie klucz prywatny certyfikatu znajduje się na komputerze przy użyciu narzędzia [FindPrivateKey](../samples/findprivatekey.md) .</span><span class="sxs-lookup"><span data-stu-id="06d4f-127">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="06d4f-128">Narzędzie [FindPrivateKey](../samples/findprivatekey.md) wymaga nazwy magazynu certyfikatów, lokalizacji magazynu certyfikatów i elementu, który jednoznacznie identyfikuje certyfikat.</span><span class="sxs-lookup"><span data-stu-id="06d4f-128">The [FindPrivateKey](../samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="06d4f-129">Narzędzie akceptuje nazwę podmiotu lub odcisk palca certyfikatu jako unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="06d4f-129">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="06d4f-130">Aby uzyskać więcej informacji na temat sposobu ustalania odcisku palca certyfikatu, zobacz [How to: Pobieranie odcisku palca certyfikatu](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="06d4f-130">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="06d4f-131">Poniższy przykład kodu używa narzędzia [FindPrivateKey](../samples/findprivatekey.md) do określenia lokalizacji klucza prywatnego certyfikatu w `My` magazynie przy `CurrentUser` użyciu odcisku palca `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d` .</span><span class="sxs-lookup"><span data-stu-id="06d4f-131">The following code example uses the [FindPrivateKey](../samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="06d4f-132">Określ konto, w ramach którego działa usługa WCF.</span><span class="sxs-lookup"><span data-stu-id="06d4f-132">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="06d4f-133">W poniższej tabeli przedstawiono szczegółowe informacje na temat konta, pod którym działa usługa WCF w danym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="06d4f-133">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="06d4f-134">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="06d4f-134">Scenario</span></span>|<span data-ttu-id="06d4f-135">Tożsamość procesu</span><span class="sxs-lookup"><span data-stu-id="06d4f-135">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="06d4f-136">Klient (Aplikacja konsolowa lub WinForms).</span><span class="sxs-lookup"><span data-stu-id="06d4f-136">Client (console or WinForms application).</span></span>|<span data-ttu-id="06d4f-137">Aktualnie zalogowany użytkownik.</span><span class="sxs-lookup"><span data-stu-id="06d4f-137">Currently logged in user.</span></span>|  
        |<span data-ttu-id="06d4f-138">Usługa, która jest samodzielna.</span><span class="sxs-lookup"><span data-stu-id="06d4f-138">Service that is self-hosted.</span></span>|<span data-ttu-id="06d4f-139">Aktualnie zalogowany użytkownik.</span><span class="sxs-lookup"><span data-stu-id="06d4f-139">Currently logged in user.</span></span>|  
        |<span data-ttu-id="06d4f-140">Usługa hostowana w usługach IIS 6,0 (Windows Server 2003) lub IIS 7,0 (Windows Vista).</span><span class="sxs-lookup"><span data-stu-id="06d4f-140">Service that is hosted in IIS 6.0 (Windows Server 2003) or IIS 7.0 (Windows Vista).</span></span>|<span data-ttu-id="06d4f-141">USŁUGA SIECIOWA</span><span class="sxs-lookup"><span data-stu-id="06d4f-141">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="06d4f-142">Usługa hostowana w usługach IIS 5. X (Windows XP).</span><span class="sxs-lookup"><span data-stu-id="06d4f-142">Service that is hosted in IIS 5.X (Windows XP).</span></span>|<span data-ttu-id="06d4f-143">Kontrolowane przez `<processModel>` element w pliku Machine.config.</span><span class="sxs-lookup"><span data-stu-id="06d4f-143">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="06d4f-144">Domyślne konto to ASPNET.</span><span class="sxs-lookup"><span data-stu-id="06d4f-144">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="06d4f-145">Przyznaj uprawnienia do odczytu pliku, który zawiera klucz prywatny do konta, w ramach którego działa usługa WCF, przy użyciu narzędzia takiego jak icacls.exe.</span><span class="sxs-lookup"><span data-stu-id="06d4f-145">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="06d4f-146">Poniższy przykład kodu umożliwia edycję poufnej listy kontroli dostępu (DACL) dla określonego pliku, aby przyznać kontu usługi sieciowej odczytywanie (: R) dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="06d4f-146">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="06d4f-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06d4f-147">See also</span></span>

- [<span data-ttu-id="06d4f-148">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="06d4f-148">FindPrivateKey</span></span>](../samples/findprivatekey.md)
- [<span data-ttu-id="06d4f-149">Instrukcje: pobieranie odcisku palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="06d4f-149">How to: Retrieve the Thumbprint of a Certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="06d4f-150">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="06d4f-150">Working with Certificates</span></span>](working-with-certificates.md)
