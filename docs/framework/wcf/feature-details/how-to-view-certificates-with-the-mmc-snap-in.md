---
title: "Instrukcje: Wyświetlanie certyfikatów w przystawce programu MMC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 43925a301d4f0d2ca1a852912255be49dd330ae5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="51214-102">Instrukcje: Wyświetlanie certyfikatów w przystawce programu MMC</span><span class="sxs-lookup"><span data-stu-id="51214-102">How to: View Certificates with the MMC Snap-in</span></span>
<span data-ttu-id="51214-103">Typowe typ poświadczeń jest certyfikat X.509.</span><span class="sxs-lookup"><span data-stu-id="51214-103">A common type of credential is the X.509 certificate.</span></span> <span data-ttu-id="51214-104">Podczas tworzenia bezpiecznych usług lub klientów, można określić, można użyć certyfikatu jako poświadczeń klienta lub usługi przy użyciu metod, takich jak <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="51214-104">When creating secure services or clients, you can specify a certificate be used as the client or service credential by using methods such as the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="51214-105">Metoda wymaga różnych parametrów, takich jak magazyn, gdy certyfikat jest przechowywany i wartości używana podczas wyszukiwania certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="51214-105">The method requires various parameters, such as the store where the certificate is stored and a value to use when searching for the certificate.</span></span> <span data-ttu-id="51214-106">W poniższej procedurze przedstawiono sposób badania w magazynie na komputerze można znaleźć odpowiedniego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="51214-106">The following procedure demonstrates how to examine the stores on a computer to find an appropriate certificate.</span></span> <span data-ttu-id="51214-107">Na przykład wyszukiwanie odcisk palca certyfikatu, zobacz [porady: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="51214-107">For an example of finding the certificate thumbprint, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="51214-108">Aby wyświetlić certyfikaty w przystawce programu MMC</span><span class="sxs-lookup"><span data-stu-id="51214-108">To view certificates in the MMC snap-in</span></span>  
  
1.  <span data-ttu-id="51214-109">Otwórz okno wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="51214-109">Open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="51214-110">Typ `mmc` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="51214-110">Type `mmc` and press the ENTER key.</span></span> <span data-ttu-id="51214-111">Należy pamiętać, że aby wyświetlić certyfikaty w magazynie komputera lokalnego, musi należeć do roli administratora.</span><span class="sxs-lookup"><span data-stu-id="51214-111">Note that to view certificates in the local machine store, you must be in the Administrator role.</span></span>  
  
3.  <span data-ttu-id="51214-112">Na **pliku** menu, kliknij przycisk **przystawka Dodaj lub usuń**.</span><span class="sxs-lookup"><span data-stu-id="51214-112">On the **File** menu, click **Add/Remove Snap In**.</span></span>  
  
4.  <span data-ttu-id="51214-113">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="51214-113">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="51214-114">W **Dodawanie przystawki autonomicznej** okno dialogowe, wybierz opcję **certyfikaty**.</span><span class="sxs-lookup"><span data-stu-id="51214-114">In the **Add Standalone Snap-in** dialog box, select **Certificates**.</span></span>  
  
6.  <span data-ttu-id="51214-115">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="51214-115">Click **Add**.</span></span>  
  
7.  <span data-ttu-id="51214-116">W **certyfikatów przystawki** okno dialogowe, wybierz opcję **konto komputera** i kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="51214-116">In the **Certificates snap-in** dialog box, select **Computer account** and click **Next**.</span></span> <span data-ttu-id="51214-117">Opcjonalnie można wybrać **Moje konto** lub **konto usługi**.</span><span class="sxs-lookup"><span data-stu-id="51214-117">Optionally, you can select **My User account** or **Service account**.</span></span> <span data-ttu-id="51214-118">Jeśli nie jesteś administratorem komputera, mogą zarządzać certyfikatami tylko dla tego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="51214-118">If you are not an administrator of the computer, you can manage certificates only for your user account.</span></span>  
  
8.  <span data-ttu-id="51214-119">W **Wybieranie komputera** okno dialogowe, kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="51214-119">In the **Select Computer** dialog box, click **Finish**.</span></span>  
  
9. <span data-ttu-id="51214-120">W **Dodawanie przystawki autonomicznej** okno dialogowe, kliknij przycisk **Zamknij**.</span><span class="sxs-lookup"><span data-stu-id="51214-120">In the **Add Standalone Snap-in** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="51214-121">Na **Dodaj/Usuń przystawkę** okno dialogowe, kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="51214-121">On the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="51214-122">W **katalog główny konsoli** okna, kliknij przycisk **certyfikaty (komputer lokalny)** Aby wyświetlić certyfikat są przechowywane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="51214-122">In the **Console Root** window, click **Certificates (Local Computer)** to view the certificate stores for the computer.</span></span>  
  
12. <span data-ttu-id="51214-123">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="51214-123">Optional.</span></span> <span data-ttu-id="51214-124">Aby wyświetlić certyfikaty dla konta, powtórz kroki od 3 do 6.</span><span class="sxs-lookup"><span data-stu-id="51214-124">To view certificates for your account, repeat steps 3 to 6.</span></span> <span data-ttu-id="51214-125">W kroku 7, zamiast zaznaczania **konto komputera**, kliknij przycisk **Moje konto** i powtórz kroki od 8 do 10.</span><span class="sxs-lookup"><span data-stu-id="51214-125">In step 7, instead of selecting **Computer account**, click **My User account** and repeat steps 8 to 10.</span></span>  
  
13. <span data-ttu-id="51214-126">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="51214-126">Optional.</span></span> <span data-ttu-id="51214-127">Na **pliku** menu, kliknij przycisk **zapisać** lub **Zapisz jako**.</span><span class="sxs-lookup"><span data-stu-id="51214-127">On the **File** menu, click **Save** or **Save As**.</span></span> <span data-ttu-id="51214-128">Zapisz plik konsoli do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="51214-128">Save the console file for later reuse.</span></span>  
  
## <a name="viewing-certificates-with-internet-explorer"></a><span data-ttu-id="51214-129">Wyświetlanie certyfikatów w programie Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="51214-129">Viewing Certificates with Internet Explorer</span></span>  
 <span data-ttu-id="51214-130">Można również wyświetlić, eksportowanie, importowania i usunąć certyfikaty w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="51214-130">You can also view, export, import, and delete certificates by using Internet Explorer.</span></span>  
  
#### <a name="to-view-certificates-with-internet-explorer"></a><span data-ttu-id="51214-131">Aby wyświetlić certyfikaty z programem Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="51214-131">To view certificates with Internet Explorer</span></span>  
  
1.  <span data-ttu-id="51214-132">W programie Internet Explorer, kliknij przycisk **narzędzia**, następnie kliknij przycisk **Opcje internetowe** do wyświetlenia **Opcje internetowe** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="51214-132">In Internet Explorer, click **Tools**, then click **Internet Options** to display the **Internet Options** dialog box.</span></span>  
  
2.  <span data-ttu-id="51214-133">Kliknij przycisk **zawartości** kartę.</span><span class="sxs-lookup"><span data-stu-id="51214-133">Click the **Content** tab.</span></span>  
  
3.  <span data-ttu-id="51214-134">W obszarze **certyfikaty**, kliknij przycisk **certyfikaty**.</span><span class="sxs-lookup"><span data-stu-id="51214-134">Under **Certificates**, click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="51214-135">Aby wyświetlić szczegóły każdego certyfikatu, zaznacz certyfikat i kliknij **widoku**.</span><span class="sxs-lookup"><span data-stu-id="51214-135">To view details of any certificate, select the certificate and click **View**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51214-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51214-136">See Also</span></span>  
 [<span data-ttu-id="51214-137">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="51214-137">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="51214-138">Porady: Tworzenie certyfikatów tymczasowych do użytku w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="51214-138">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [<span data-ttu-id="51214-139">Porady: Pobieranie odcisku palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="51214-139">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
