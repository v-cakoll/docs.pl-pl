---
title: 'Instrukcje: Wyświetlanie certyfikatów za pomocą przystawki programu MMC'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 69f79b64250ff46524e7b4720d13351774875a3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167508"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="b1a69-102">Instrukcje: Wyświetlanie certyfikatów za pomocą przystawki programu MMC</span><span class="sxs-lookup"><span data-stu-id="b1a69-102">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="b1a69-103">Podczas tworzenia bezpiecznego klienta lub usługę, można użyć [certyfikatu](working-with-certificates.md) jako poświadczenie.</span><span class="sxs-lookup"><span data-stu-id="b1a69-103">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="b1a69-104">Na przykład spotykanym typem poświadczeń jest certyfikat X.509, które są tworzone za pomocą <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="b1a69-104">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span> 

<span data-ttu-id="b1a69-105">Istnieją trzy różne typy magazynów certyfikatów, które można sprawdzić za pomocą programu Microsoft Management Console (MMC) w systemach Windows:</span><span class="sxs-lookup"><span data-stu-id="b1a69-105">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="b1a69-106">Komputer lokalny: Magazyn jest lokalne na urządzeniu i globalne dla wszystkich użytkowników na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="b1a69-106">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="b1a69-107">Bieżący użytkownik: Magazyn jest lokalny dla bieżącego konta użytkownika na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="b1a69-107">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="b1a69-108">Konto usługi: Magazyn jest lokalny dla określonej usługi na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="b1a69-108">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="b1a69-109">Wyświetlanie certyfikatów w przystawce programu MMC</span><span class="sxs-lookup"><span data-stu-id="b1a69-109">View certificates in the MMC snap-in</span></span> 

<span data-ttu-id="b1a69-110">Poniższa procedura pokazuje, jak sprawdzić magazynów na urządzeniu lokalnym, aby znaleźć odpowiedni certyfikat:</span><span class="sxs-lookup"><span data-stu-id="b1a69-110">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span> 
  
1. <span data-ttu-id="b1a69-111">Wybierz **Uruchom** z **Start** menu, a następnie wprowadź *mmc*.</span><span class="sxs-lookup"><span data-stu-id="b1a69-111">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span> 

    <span data-ttu-id="b1a69-112">Pojawi się programu MMC.</span><span class="sxs-lookup"><span data-stu-id="b1a69-112">The MMC appears.</span></span> 
  
2. <span data-ttu-id="b1a69-113">Z **pliku** menu, wybierz opcję **Dodawanie/Usuwanie przystawki**.</span><span class="sxs-lookup"><span data-stu-id="b1a69-113">From the **File** menu, select **Add/Remove Snap In**.</span></span> 
    
    <span data-ttu-id="b1a69-114">**Dodawanie lub usuwanie przystawek** zostanie wyświetlone okno.</span><span class="sxs-lookup"><span data-stu-id="b1a69-114">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="b1a69-115">Z **dostępne przystawki** wybierz **certyfikaty**, a następnie wybierz **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="b1a69-115">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Dodawanie przystawki certyfikatów](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="b1a69-117">W **certyfikatów w przystawce** wybierz **konto komputera**, a następnie wybierz pozycję **dalej**.</span><span class="sxs-lookup"><span data-stu-id="b1a69-117">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span> 
  
    <span data-ttu-id="b1a69-118">Opcjonalnie można wybrać **Moje konto użytkownika** dla bieżącego użytkownika lub **konto usługi** określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="b1a69-118">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="b1a69-119">Jeśli nie masz uprawnienia administratora dla danego urządzenia, mogą zarządzać certyfikatami, tylko w przypadku konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b1a69-119">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="b1a69-120">W **Wybieranie komputera** okna, pozostaw **komputera lokalnego** zaznaczone, a następnie wybierz pozycję **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="b1a69-120">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="b1a69-121">W **Dodawanie lub usuwanie przystawki** wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="b1a69-121">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Dodawanie przystawki certyfikatów](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="b1a69-123">Opcjonalne: Z **pliku** menu, wybierz opcję **Zapisz** lub **Zapisz jako** można zapisać pliku konsoli MMC w celu późniejszego użycia.</span><span class="sxs-lookup"><span data-stu-id="b1a69-123">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="b1a69-124">Zaznacz, aby wyświetlić certyfikaty w przystawce programu MMC **katalog główny konsoli** w okienku po lewej stronie, następnie rozwiń węzeł **certyfikaty (komputer lokalny)**.</span><span class="sxs-lookup"><span data-stu-id="b1a69-124">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="b1a69-125">Zostanie wyświetlona lista katalogów dla każdego typu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="b1a69-125">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="b1a69-126">Z każdego katalogu certyfikatu można wyświetlić, Eksportuj, importowanie i usunąć swoje certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="b1a69-126">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="b1a69-127">Wyświetlanie certyfikatów za pomocą narzędzia Menedżer certyfikatów</span><span class="sxs-lookup"><span data-stu-id="b1a69-127">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="b1a69-128">Można również wyświetlić, Eksportuj, importowanie i usunąć certyfikaty przy użyciu narzędzia Menedżer certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="b1a69-128">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="b1a69-129">Aby wyświetlić certyfikaty dla wybranego urządzenia lokalnego</span><span class="sxs-lookup"><span data-stu-id="b1a69-129">To view certificates for the local device</span></span>

1. <span data-ttu-id="b1a69-130">Wybierz **Uruchom** z **Start** menu, a następnie wprowadź *certlm.msc*.</span><span class="sxs-lookup"><span data-stu-id="b1a69-130">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span> 

    <span data-ttu-id="b1a69-131">Zostanie wyświetlone narzędzie Menedżer certyfikatów dla wybranego urządzenia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="b1a69-131">The Certificate Manager tool for the local device appears.</span></span> 
  
2. <span data-ttu-id="b1a69-132">Aby wyświetlić certyfikaty, w obszarze **certyfikaty — komputer lokalny** w lewym okienku rozwiń węzeł katalogu dla typu certyfikatu, którą chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="b1a69-132">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="b1a69-133">Aby wyświetlić certyfikaty dla bieżącego użytkownika</span><span class="sxs-lookup"><span data-stu-id="b1a69-133">To view certificates for the current user</span></span>

1. <span data-ttu-id="b1a69-134">Wybierz **Uruchom** z **Start** menu, a następnie wprowadź *certmgr.msc*.</span><span class="sxs-lookup"><span data-stu-id="b1a69-134">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span> 

    <span data-ttu-id="b1a69-135">Zostanie wyświetlone narzędzie Menedżer certyfikatów dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b1a69-135">The Certificate Manager tool for the current user appears.</span></span> 
  
2. <span data-ttu-id="b1a69-136">Aby wyświetlić certyfikaty, w obszarze **Certyfikaty — bieżący użytkownik** w lewym okienku rozwiń węzeł katalogu dla typu certyfikatu, którą chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="b1a69-136">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1a69-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1a69-137">See also</span></span>

- [<span data-ttu-id="b1a69-138">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="b1a69-138">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="b1a69-139">Instrukcje: Tworzenie certyfikatów tymczasowych do użytku w trakcie opracowywania</span><span class="sxs-lookup"><span data-stu-id="b1a69-139">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="b1a69-140">Instrukcje: Pobieranie odcisku palca certyfikatu</span><span class="sxs-lookup"><span data-stu-id="b1a69-140">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
