---
title: 'Instrukcje: Wyświetlanie certyfikatów w przystawce programu MMC'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 72fd6a1be2f33e1bfeb08fd43f3436627ee842e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521585"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="8d878-102">Instrukcje: Wyświetlanie certyfikatów w przystawce programu MMC</span><span class="sxs-lookup"><span data-stu-id="8d878-102">How to: View Certificates with the MMC Snap-in</span></span>
<span data-ttu-id="8d878-103">Spotykanym typem poświadczeń jest to certyfikat X.509.</span><span class="sxs-lookup"><span data-stu-id="8d878-103">A common type of credential is the X.509 certificate.</span></span> <span data-ttu-id="8d878-104">Podczas tworzenia bezpiecznych usług lub klientów, można określić, można użyć certyfikatu jako poświadczeń klienta lub usługi przy użyciu metod, takich jak <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8d878-104">When creating secure services or clients, you can specify a certificate be used as the client or service credential by using methods such as the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="8d878-105">Metoda wymaga różnych parametrów, takich jak magazyn, gdy certyfikat jest przechowywany i wartości do użycia podczas wyszukiwania certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="8d878-105">The method requires various parameters, such as the store where the certificate is stored and a value to use when searching for the certificate.</span></span> <span data-ttu-id="8d878-106">Poniższa procedura pokazuje, jak sprawdzić magazynów na komputerze, aby znaleźć odpowiedni certyfikat.</span><span class="sxs-lookup"><span data-stu-id="8d878-106">The following procedure demonstrates how to examine the stores on a computer to find an appropriate certificate.</span></span> <span data-ttu-id="8d878-107">Na przykład znajdowania odcisk palca certyfikatu, zobacz [jak: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="8d878-107">For an example of finding the certificate thumbprint, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="8d878-108">Aby wyświetlić certyfikaty w przystawce programu MMC</span><span class="sxs-lookup"><span data-stu-id="8d878-108">To view certificates in the MMC snap-in</span></span>  
  
1.  <span data-ttu-id="8d878-109">Otwórz okno wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="8d878-109">Open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="8d878-110">Typ `mmc` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="8d878-110">Type `mmc` and press the ENTER key.</span></span> <span data-ttu-id="8d878-111">Należy pamiętać, że aby wyświetlić certyfikaty w magazynie komputera lokalnego, musisz mieć rolę administratora.</span><span class="sxs-lookup"><span data-stu-id="8d878-111">Note that to view certificates in the local machine store, you must be in the Administrator role.</span></span>  
  
3.  <span data-ttu-id="8d878-112">Na **pliku** menu, kliknij przycisk **Dodawanie/Usuwanie przystawki**.</span><span class="sxs-lookup"><span data-stu-id="8d878-112">On the **File** menu, click **Add/Remove Snap In**.</span></span>  
  
4.  <span data-ttu-id="8d878-113">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="8d878-113">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="8d878-114">W **Dodawanie przystawki autonomicznej** okno dialogowe, wybierz opcję **certyfikaty**.</span><span class="sxs-lookup"><span data-stu-id="8d878-114">In the **Add Standalone Snap-in** dialog box, select **Certificates**.</span></span>  
  
6.  <span data-ttu-id="8d878-115">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="8d878-115">Click **Add**.</span></span>  
  
7.  <span data-ttu-id="8d878-116">W **certyfikatów w przystawce** okno dialogowe, wybierz opcję **konto komputera** i kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="8d878-116">In the **Certificates snap-in** dialog box, select **Computer account** and click **Next**.</span></span> <span data-ttu-id="8d878-117">Opcjonalnie można wybrać **Moje konto** lub **konto usługi**.</span><span class="sxs-lookup"><span data-stu-id="8d878-117">Optionally, you can select **My User account** or **Service account**.</span></span> <span data-ttu-id="8d878-118">Jeśli nie jesteś administratorem komputera, można zarządzać certyfikaty tylko dla tego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8d878-118">If you are not an administrator of the computer, you can manage certificates only for your user account.</span></span>  
  
8.  <span data-ttu-id="8d878-119">W **Wybieranie komputera** okno dialogowe, kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="8d878-119">In the **Select Computer** dialog box, click **Finish**.</span></span>  
  
9. <span data-ttu-id="8d878-120">W **Dodawanie przystawki autonomicznej** okno dialogowe, kliknij przycisk **Zamknij**.</span><span class="sxs-lookup"><span data-stu-id="8d878-120">In the **Add Standalone Snap-in** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="8d878-121">Na **Dodaj/Usuń przystawkę** okno dialogowe, kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8d878-121">On the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="8d878-122">W **katalog główny konsoli** okna, kliknij przycisk **certyfikaty (komputer lokalny)** Aby wyświetlić certyfikat są przechowywane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8d878-122">In the **Console Root** window, click **Certificates (Local Computer)** to view the certificate stores for the computer.</span></span>  
  
12. <span data-ttu-id="8d878-123">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8d878-123">Optional.</span></span> <span data-ttu-id="8d878-124">Aby wyświetlić certyfikaty dla konta, powtórz kroki od 3 do 6.</span><span class="sxs-lookup"><span data-stu-id="8d878-124">To view certificates for your account, repeat steps 3 to 6.</span></span> <span data-ttu-id="8d878-125">W kroku 7, zamiast zaznaczania **konto komputera**, kliknij przycisk **Moje konto** i powtórz kroki od 8 do 10.</span><span class="sxs-lookup"><span data-stu-id="8d878-125">In step 7, instead of selecting **Computer account**, click **My User account** and repeat steps 8 to 10.</span></span>  
  
13. <span data-ttu-id="8d878-126">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8d878-126">Optional.</span></span> <span data-ttu-id="8d878-127">Na **pliku** menu, kliknij przycisk **Zapisz** lub **Zapisz jako**.</span><span class="sxs-lookup"><span data-stu-id="8d878-127">On the **File** menu, click **Save** or **Save As**.</span></span> <span data-ttu-id="8d878-128">Zapisz plik konsoli do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="8d878-128">Save the console file for later reuse.</span></span>  
  
## <a name="viewing-certificates-with-internet-explorer"></a><span data-ttu-id="8d878-129">Wyświetlanie certyfikatów w programie Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="8d878-129">Viewing Certificates with Internet Explorer</span></span>  
 <span data-ttu-id="8d878-130">Można również wyświetlić, eksportować, importowanie i usunąć certyfikaty w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8d878-130">You can also view, export, import, and delete certificates by using Internet Explorer.</span></span>  
  
#### <a name="to-view-certificates-with-internet-explorer"></a><span data-ttu-id="8d878-131">Aby wyświetlić certyfikaty z programem Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="8d878-131">To view certificates with Internet Explorer</span></span>  
  
1.  <span data-ttu-id="8d878-132">W programie Internet Explorer kliknij **narzędzia**, następnie kliknij przycisk **Opcje internetowe** do wyświetlenia **Opcje internetowe** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="8d878-132">In Internet Explorer, click **Tools**, then click **Internet Options** to display the **Internet Options** dialog box.</span></span>  
  
2.  <span data-ttu-id="8d878-133">Kliknij przycisk **zawartości** kartę.</span><span class="sxs-lookup"><span data-stu-id="8d878-133">Click the **Content** tab.</span></span>  
  
3.  <span data-ttu-id="8d878-134">W obszarze **certyfikaty**, kliknij przycisk **certyfikaty**.</span><span class="sxs-lookup"><span data-stu-id="8d878-134">Under **Certificates**, click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="8d878-135">Aby wyświetlić szczegóły każdego certyfikatu, wybierz certyfikat i kliknij **widoku**.</span><span class="sxs-lookup"><span data-stu-id="8d878-135">To view details of any certificate, select the certificate and click **View**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d878-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d878-136">See also</span></span>
- [<span data-ttu-id="8d878-137">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="8d878-137">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="8d878-138">Instrukcje: Tworzenie certyfikatów tymczasowych do użytku w trakcie opracowywania</span><span class="sxs-lookup"><span data-stu-id="8d878-138">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="8d878-139">Instrukcje: Pobieranie odcisku palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="8d878-139">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
