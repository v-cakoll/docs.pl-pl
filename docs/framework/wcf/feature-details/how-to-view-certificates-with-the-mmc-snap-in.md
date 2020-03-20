---
title: 'Jak: Wyświetlanie certyfikatów przy przystawce PROGRAMU MMC'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 35048c24e838c513909fae8bedcba287001f5cef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184785"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="5fca6-102">Jak: Wyświetlanie certyfikatów przy przystawce PROGRAMU MMC</span><span class="sxs-lookup"><span data-stu-id="5fca6-102">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="5fca6-103">Podczas tworzenia bezpiecznego klienta lub usługi, można użyć [certyfikatu](working-with-certificates.md) jako poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="5fca6-103">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="5fca6-104">Na przykład typowym typem poświadczeń jest certyfikat X.509, który można utworzyć za <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> pomocą metody.</span><span class="sxs-lookup"><span data-stu-id="5fca6-104">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="5fca6-105">Istnieją trzy różne typy magazynów certyfikatów, które można sprawdzić za pomocą programu Microsoft Management Console (MMC) w systemach Windows:</span><span class="sxs-lookup"><span data-stu-id="5fca6-105">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="5fca6-106">Komputer lokalny: magazyn jest lokalny dla urządzenia i globalny dla wszystkich użytkowników na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="5fca6-106">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="5fca6-107">Bieżący użytkownik: Sklep jest lokalny dla bieżącego konta użytkownika na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="5fca6-107">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="5fca6-108">Konto usługi: sklep jest lokalny dla określonej usługi na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="5fca6-108">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="5fca6-109">Wyświetlanie certyfikatów w przystawce programu MMC</span><span class="sxs-lookup"><span data-stu-id="5fca6-109">View certificates in the MMC snap-in</span></span>

<span data-ttu-id="5fca6-110">Poniższa procedura pokazuje, jak sprawdzić sklepy na urządzeniu lokalnym, aby znaleźć odpowiedni certyfikat:</span><span class="sxs-lookup"><span data-stu-id="5fca6-110">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span>
  
1. <span data-ttu-id="5fca6-111">Wybierz **polecenie Uruchom** z menu **Start,** a następnie wprowadź *mmc*.</span><span class="sxs-lookup"><span data-stu-id="5fca6-111">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span>

    <span data-ttu-id="5fca6-112">Pojawi się program MMC.</span><span class="sxs-lookup"><span data-stu-id="5fca6-112">The MMC appears.</span></span>
  
2. <span data-ttu-id="5fca6-113">Z menu **Plik** wybierz polecenie **Dodaj/Usuń przyciąganie .**</span><span class="sxs-lookup"><span data-stu-id="5fca6-113">From the **File** menu, select **Add/Remove Snap In**.</span></span>

    <span data-ttu-id="5fca6-114">Zostanie **wyświetlenie** okna Dodaj lub Usuń przystawki.</span><span class="sxs-lookup"><span data-stu-id="5fca6-114">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="5fca6-115">Z listy **Dostępne przystawki** wybierz pozycję **Certyfikaty**, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="5fca6-115">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Dodawanie przystawki certyfikatu](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="5fca6-117">W oknie **przystawki Certyfikaty** wybierz pozycję **Konto komputera**, a następnie wybierz pozycję **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="5fca6-117">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span>
  
    <span data-ttu-id="5fca6-118">Opcjonalnie można wybrać **moje konto użytkownika** dla bieżącego użytkownika lub konto **usługi** dla określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="5fca6-118">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5fca6-119">Jeśli nie jesteś administratorem urządzenia, możesz zarządzać certyfikatami tylko dla swojego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5fca6-119">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="5fca6-120">W oknie **Wybierz komputer** pozostaw zaznaczoną pozycję **Komputer lokalny,** a następnie wybierz pozycję **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="5fca6-120">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="5fca6-121">W oknie **Dodawanie lub usuwanie przyciągania** wybierz pozycję **OK**.</span><span class="sxs-lookup"><span data-stu-id="5fca6-121">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Dodawanie przystawki certyfikatu](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="5fca6-123">Opcjonalnie: z menu **Plik** wybierz polecenie **Zapisz** lub **Zapisz jako,** aby zapisać plik konsoli programu MMC do późniejszego użycia.</span><span class="sxs-lookup"><span data-stu-id="5fca6-123">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="5fca6-124">Aby wyświetlić certyfikaty w przystawce programu MMC, wybierz pozycję **Katalog główny konsoli** w lewym okienku, a następnie rozwiń pozycję **Certyfikaty (komputer lokalny).**</span><span class="sxs-lookup"><span data-stu-id="5fca6-124">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="5fca6-125">Pojawi się lista katalogów dla każdego typu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="5fca6-125">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="5fca6-126">Z każdego katalogu certyfikatów można wyświetlać, eksportować, importować i usuwać jego certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="5fca6-126">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="5fca6-127">Wyświetlanie certyfikatów za pomocą narzędzia Menedżer certyfikatów</span><span class="sxs-lookup"><span data-stu-id="5fca6-127">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="5fca6-128">Certyfikaty można również wyświetlać, eksportować, importować i usuwać za pomocą narzędzia Menedżer certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="5fca6-128">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="5fca6-129">Aby wyświetlić certyfikaty dla urządzenia lokalnego</span><span class="sxs-lookup"><span data-stu-id="5fca6-129">To view certificates for the local device</span></span>

1. <span data-ttu-id="5fca6-130">Wybierz **polecenie Uruchom** z menu **Start,** a następnie wprowadź *plik certlm.msc*.</span><span class="sxs-lookup"><span data-stu-id="5fca6-130">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span>

    <span data-ttu-id="5fca6-131">Zostanie wyświetlone narzędzie Menedżer certyfikatów dla urządzenia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="5fca6-131">The Certificate Manager tool for the local device appears.</span></span>
  
2. <span data-ttu-id="5fca6-132">Aby wyświetlić certyfikaty, w obszarze **Certyfikaty — Komputer lokalny** w lewym okienku rozwiń katalog typu certyfikatu, który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="5fca6-132">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="5fca6-133">Aby wyświetlić certyfikaty dla bieżącego użytkownika</span><span class="sxs-lookup"><span data-stu-id="5fca6-133">To view certificates for the current user</span></span>

1. <span data-ttu-id="5fca6-134">Wybierz **polecenie Uruchom** z menu **Start,** a następnie wprowadź plik *certmgr.msc*.</span><span class="sxs-lookup"><span data-stu-id="5fca6-134">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span>

    <span data-ttu-id="5fca6-135">Pojawi się narzędzie Menedżer certyfikatów dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5fca6-135">The Certificate Manager tool for the current user appears.</span></span>
  
2. <span data-ttu-id="5fca6-136">Aby wyświetlić certyfikaty, w obszarze **Certyfikaty — bieżący użytkownik** w lewym okienku rozwiń katalog dla typu certyfikatu, który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="5fca6-136">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="5fca6-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5fca6-137">See also</span></span>

- [<span data-ttu-id="5fca6-138">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="5fca6-138">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="5fca6-139">Jak: Tworzenie tymczasowych certyfikatów do użycia podczas tworzenia</span><span class="sxs-lookup"><span data-stu-id="5fca6-139">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="5fca6-140">Jak: Pobieranie odcisku palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="5fca6-140">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
