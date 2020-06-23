---
title: 'Instrukcje: Wyświetlanie certyfikatów w przystawce programu MMC'
description: Bezpieczny klient lub usługa WCF mogą używać certyfikatu jako poświadczenia. Dowiedz się więcej na temat typów magazynów certyfikatów, które można sprawdzić za pomocą wtyczki programu MMC.
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: e63034e48ae836f67f89b454829f7196c94610cd
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246678"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="4d10b-104">Instrukcje: Wyświetlanie certyfikatów w przystawce programu MMC</span><span class="sxs-lookup"><span data-stu-id="4d10b-104">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="4d10b-105">Podczas tworzenia bezpiecznego klienta lub usługi można użyć [certyfikatu](working-with-certificates.md) jako poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="4d10b-105">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="4d10b-106">Typowym typem poświadczeń jest na przykład certyfikat X. 509, który tworzysz przy użyciu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="4d10b-106">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="4d10b-107">Istnieją trzy różne typy magazynów certyfikatów, które można przeanalizować za pomocą programu Microsoft Management Console (MMC) w systemach Windows:</span><span class="sxs-lookup"><span data-stu-id="4d10b-107">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="4d10b-108">Komputer lokalny: Magazyn jest lokalny dla urządzenia i globalny dla wszystkich użytkowników na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="4d10b-108">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="4d10b-109">Bieżący użytkownik: Magazyn jest lokalny dla bieżącego konta użytkownika na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="4d10b-109">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="4d10b-110">Konto usługi: Magazyn jest lokalny dla określonej usługi na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="4d10b-110">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="4d10b-111">Wyświetlanie certyfikatów w przystawce programu MMC</span><span class="sxs-lookup"><span data-stu-id="4d10b-111">View certificates in the MMC snap-in</span></span>

<span data-ttu-id="4d10b-112">Poniższa procedura przedstawia sposób badania magazynów na urządzeniu lokalnym w celu znalezienia odpowiedniego certyfikatu:</span><span class="sxs-lookup"><span data-stu-id="4d10b-112">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span>
  
1. <span data-ttu-id="4d10b-113">Z menu **Start** wybierz polecenie **Uruchom** , a następnie wprowadź *MMC*.</span><span class="sxs-lookup"><span data-stu-id="4d10b-113">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span>

    <span data-ttu-id="4d10b-114">Zostanie wyświetlony program MMC.</span><span class="sxs-lookup"><span data-stu-id="4d10b-114">The MMC appears.</span></span>
  
2. <span data-ttu-id="4d10b-115">Z menu **plik** wybierz pozycję **Dodaj/Usuń przystawkę**.</span><span class="sxs-lookup"><span data-stu-id="4d10b-115">From the **File** menu, select **Add/Remove Snap In**.</span></span>

    <span data-ttu-id="4d10b-116">Zostanie wyświetlone okno **Dodawanie lub usuwanie przystawek** .</span><span class="sxs-lookup"><span data-stu-id="4d10b-116">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="4d10b-117">Z listy **Dostępne przystawki** wybierz pozycję **Certyfikaty**, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="4d10b-117">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Dodaj przystawkę certyfikatów](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="4d10b-119">W oknie **Przystawka certyfikatów** wybierz pozycję **konto komputera**, a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="4d10b-119">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span>
  
    <span data-ttu-id="4d10b-120">Opcjonalnie możesz wybrać **konto użytkownika** dla bieżącego użytkownika lub **usługi** dla określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="4d10b-120">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4d10b-121">Jeśli nie jesteś administratorem urządzenia, możesz zarządzać certyfikatami tylko dla Twojego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4d10b-121">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="4d10b-122">W oknie **Wybieranie komputera** pozostaw wybraną opcję **komputer lokalny** , a następnie wybierz pozycję **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="4d10b-122">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="4d10b-123">W oknie **Dodawanie lub usuwanie przystawki** wybierz pozycję **OK**.</span><span class="sxs-lookup"><span data-stu-id="4d10b-123">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Dodaj przystawkę certyfikatów](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="4d10b-125">Opcjonalne: z menu **plik** wybierz polecenie **Zapisz** lub **Zapisz jako** , aby zapisać plik konsoli programu MMC do późniejszego użycia.</span><span class="sxs-lookup"><span data-stu-id="4d10b-125">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="4d10b-126">Aby wyświetlić certyfikaty w przystawce programu MMC, w okienku po lewej stronie wybierz pozycję **katalog główny konsoli** , a następnie rozwiń węzeł **Certyfikaty (komputer lokalny)**.</span><span class="sxs-lookup"><span data-stu-id="4d10b-126">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="4d10b-127">Zostanie wyświetlona lista katalogów dla każdego typu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="4d10b-127">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="4d10b-128">W każdym katalogu certyfikatów można wyświetlać, eksportować, importować i usuwać jego certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="4d10b-128">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="4d10b-129">Wyświetlanie certyfikatów za pomocą narzędzia Menedżer certyfikatów</span><span class="sxs-lookup"><span data-stu-id="4d10b-129">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="4d10b-130">Można również wyświetlać, eksportować, importować i usuwać certyfikaty przy użyciu narzędzia Menedżer certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="4d10b-130">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="4d10b-131">Aby wyświetlić certyfikaty dla urządzenia lokalnego</span><span class="sxs-lookup"><span data-stu-id="4d10b-131">To view certificates for the local device</span></span>

1. <span data-ttu-id="4d10b-132">Z menu **Start** wybierz polecenie **Uruchom** , a następnie wprowadź *certlm. msc*.</span><span class="sxs-lookup"><span data-stu-id="4d10b-132">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span>

    <span data-ttu-id="4d10b-133">Zostanie wyświetlone narzędzie Menedżer certyfikatów dla urządzenia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="4d10b-133">The Certificate Manager tool for the local device appears.</span></span>
  
2. <span data-ttu-id="4d10b-134">Aby wyświetlić certyfikaty, w obszarze **Certyfikaty — komputer lokalny** w okienku po lewej stronie rozwiń katalog dla typu certyfikatu, który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="4d10b-134">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="4d10b-135">Aby wyświetlić certyfikaty dla bieżącego użytkownika</span><span class="sxs-lookup"><span data-stu-id="4d10b-135">To view certificates for the current user</span></span>

1. <span data-ttu-id="4d10b-136">Z menu **Start** wybierz polecenie **Uruchom** , a następnie wprowadź *certmgr. msc*.</span><span class="sxs-lookup"><span data-stu-id="4d10b-136">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span>

    <span data-ttu-id="4d10b-137">Zostanie wyświetlone narzędzie Menedżer certyfikatów dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4d10b-137">The Certificate Manager tool for the current user appears.</span></span>
  
2. <span data-ttu-id="4d10b-138">Aby wyświetlić certyfikaty, w obszarze **Certyfikaty — bieżący użytkownik** w lewym okienku rozwiń katalog dla typu certyfikatu, który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="4d10b-138">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d10b-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d10b-139">See also</span></span>

- [<span data-ttu-id="4d10b-140">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="4d10b-140">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="4d10b-141">Instrukcje: Tworzenie certyfikatów tymczasowych do użycia podczas opracowywania</span><span class="sxs-lookup"><span data-stu-id="4d10b-141">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="4d10b-142">Instrukcje: Pobieranie odcisku palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="4d10b-142">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
