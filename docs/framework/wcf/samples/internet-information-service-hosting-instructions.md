---
title: Instrukcje dotyczące hostowania internetowej usługi informacyjnej
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 226b47bfd90dc4cffb0a364a804016043cc25d02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929111"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="2d428-102">Instrukcje dotyczące hostowania internetowej usługi informacyjnej</span><span class="sxs-lookup"><span data-stu-id="2d428-102">Internet Information Service Hosting Instructions</span></span>
<span data-ttu-id="2d428-103">Aby uruchomić przykłady, które są hostowane przez Internet Information Services (IIS), należy upewnić się, że usługi IIS są prawidłowo zainstalowane i uruchomione.</span><span class="sxs-lookup"><span data-stu-id="2d428-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="2d428-104">Aby zainstalować usługi IIS w wersji 7,5 w systemie Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="2d428-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="2d428-105">W obszarze **Menedżer serwera**wybierz pozycję **role.**</span><span class="sxs-lookup"><span data-stu-id="2d428-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="2d428-106">W obszarze **Podsumowanie ról**kliknij pozycję **Dodaj role**.</span><span class="sxs-lookup"><span data-stu-id="2d428-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="2d428-107">Kliknij przycisk **dalej** , aby wyświetlić okno dialogowe **Wybieranie ról serwera** .</span><span class="sxs-lookup"><span data-stu-id="2d428-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="2d428-108">Wybierz pozycję **serwer aplikacji** z listy **role** , a następnie kliknij przycisk **dalej** dwa razy, aby wyświetlić okno dialogowe **Wybieranie usług ról** dla roli serwera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2d428-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="2d428-109">Zaznacz pole wyboru **serwer sieci Web (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="2d428-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="2d428-110">Jeśli zostanie wyświetlony monit o zainstalowanie dodatkowych usług ról i funkcji, kliknij przycisk **Dodaj wymagane funkcje**.</span><span class="sxs-lookup"><span data-stu-id="2d428-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="2d428-111">Kliknij dwukrotnie przycisk **dalej** , aby wyświetlić okno dialogowe **Wybieranie usług ról** dla roli Serwer sieci Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="2d428-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="2d428-112">Rozwiń węzeł **Narzędzia do zarządzania**, a następnie rozwiń pozycję Zgodność z zarządzaniem **usługami IIS**w wersji 6.</span><span class="sxs-lookup"><span data-stu-id="2d428-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="2d428-113">Wybierz pozycję **Narzędzia obsługi skryptów w usługach IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="2d428-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="2d428-114">Jeśli zostanie wyświetlony monit o zainstalowanie dodatkowych usług ról i funkcji, kliknij przycisk **Dodaj wymagane usługi ról**.</span><span class="sxs-lookup"><span data-stu-id="2d428-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="2d428-115">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="2d428-115">Click **Next**.</span></span>  
  
6. <span data-ttu-id="2d428-116">Jeśli podsumowanie wybranych opcji jest poprawne, kliknij przycisk **Instaluj**.</span><span class="sxs-lookup"><span data-stu-id="2d428-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="2d428-117">Po zakończeniu instalacji kliknij przycisk **Zamknij**.</span><span class="sxs-lookup"><span data-stu-id="2d428-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="2d428-118">Aby zainstalować usługi IIS w wersji 7,5 w systemie Windows 7</span><span class="sxs-lookup"><span data-stu-id="2d428-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1. <span data-ttu-id="2d428-119">Kliknij przycisk **Start**, a następnie kliknij pozycję **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="2d428-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="2d428-120">Otwórz grupę **programy** .</span><span class="sxs-lookup"><span data-stu-id="2d428-120">Open the **Programs** group.</span></span>  
  
3. <span data-ttu-id="2d428-121">W obszarze **programy i funkcje**kliknij pozycję **Włącz lub wyłącz funkcje systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="2d428-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="2d428-122">Zostanie wyświetlone okno dialogowe **Kontrola konta użytkownika** .</span><span class="sxs-lookup"><span data-stu-id="2d428-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="2d428-123">Kliknij przycisk **Kontynuuj**.</span><span class="sxs-lookup"><span data-stu-id="2d428-123">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="2d428-124">Zostanie wyświetlone okno dialogowe **funkcje systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="2d428-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="2d428-125">Rozwiń element oznaczony **Internet Information Services**.</span><span class="sxs-lookup"><span data-stu-id="2d428-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="2d428-126">Rozwiń element oznaczony **World Wide Web Services**.</span><span class="sxs-lookup"><span data-stu-id="2d428-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="2d428-127">Rozwiń element zatytułowany **Programowanie aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="2d428-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="2d428-128">Upewnij się, że wybrano następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="2d428-128">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="2d428-129">**Rozszerzalność platformy .NET**</span><span class="sxs-lookup"><span data-stu-id="2d428-129">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="2d428-130">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="2d428-130">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="2d428-131">**Rozszerzenia ISAPI**</span><span class="sxs-lookup"><span data-stu-id="2d428-131">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="2d428-132">**Filtry ISAPI**</span><span class="sxs-lookup"><span data-stu-id="2d428-132">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="2d428-133">W obszarze elementu **World Wide Web usługach**rozwiń węzeł **wspólne funkcje http**.</span><span class="sxs-lookup"><span data-stu-id="2d428-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="2d428-134">Upewnij się, że jest zaznaczona **Zawartość statyczna** .</span><span class="sxs-lookup"><span data-stu-id="2d428-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="2d428-135">W obszarze elementu **World Wide Web usługach**rozwiń węzeł **zabezpieczenia**.</span><span class="sxs-lookup"><span data-stu-id="2d428-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="2d428-136">Upewnij się, że wybrano **uwierzytelnianie systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="2d428-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="2d428-137">W katalogu **Internet Information Services** rozwiń element **Narzędzia do zarządzania siecią Web**, a następnie wybierz pozycję **Konsola zarządzania usługami IIS**.</span><span class="sxs-lookup"><span data-stu-id="2d428-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="2d428-138">Rozwiń element o nazwie **zgodność z usługami IIS 6**, a następnie wybierz pozycję **Narzędzia do obsługi skryptów w usługach IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="2d428-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="2d428-139">W katalogu **Internet Information Services** rozwiń element z etykietą **Microsoft .NET Framework 3.5.1**, a następnie wybierz pozycję **Windows Communication Foundation Aktywacja HTTP**.</span><span class="sxs-lookup"><span data-stu-id="2d428-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="2d428-140">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2d428-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="2d428-141">Aby zainstalować usługi IIS w wersji 7,0 w systemie Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="2d428-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1. <span data-ttu-id="2d428-142">W obszarze **Menedżer serwera**wybierz pozycję **role**.</span><span class="sxs-lookup"><span data-stu-id="2d428-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="2d428-143">W obszarze **Podsumowanie ról**kliknij pozycję **Dodaj role**.</span><span class="sxs-lookup"><span data-stu-id="2d428-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="2d428-144">Kliknij przycisk **dalej** , aby wyświetlić okno dialogowe **Wybieranie ról serwera** .</span><span class="sxs-lookup"><span data-stu-id="2d428-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="2d428-145">Wybierz pozycję **serwer aplikacji** z listy **role** , a następnie kliknij przycisk **dalej** dwa razy, aby wyświetlić okno dialogowe **Wybieranie usług ról** dla roli serwera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2d428-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="2d428-146">Zaznacz pole wyboru **serwer sieci Web (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="2d428-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="2d428-147">Jeśli zostanie wyświetlony monit o zainstalowanie dodatkowych usług ról i funkcji, kliknij przycisk **Dodaj wymagane funkcje**.</span><span class="sxs-lookup"><span data-stu-id="2d428-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="2d428-148">Kliknij dwukrotnie przycisk **dalej** , aby wyświetlić okno dialogowe **Wybieranie usług ról** dla roli Serwer sieci Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="2d428-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="2d428-149">Rozwiń węzeł **Narzędzia do zarządzania**, a następnie rozwiń pozycję Zgodność z zarządzaniem **usługami IIS**w wersji 6.</span><span class="sxs-lookup"><span data-stu-id="2d428-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="2d428-150">Wybierz pozycję **Narzędzia obsługi skryptów w usługach IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="2d428-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="2d428-151">Jeśli zostanie wyświetlony monit o zainstalowanie dodatkowych usług ról i funkcji, kliknij przycisk **Dodaj wymagane usługi ról**.</span><span class="sxs-lookup"><span data-stu-id="2d428-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="2d428-152">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="2d428-152">Click **Next**.</span></span>  
  
6. <span data-ttu-id="2d428-153">Jeśli podsumowanie wybranych opcji jest poprawne, kliknij przycisk **Instaluj**.</span><span class="sxs-lookup"><span data-stu-id="2d428-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="2d428-154">Po zakończeniu instalacji kliknij przycisk **Zamknij**.</span><span class="sxs-lookup"><span data-stu-id="2d428-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="2d428-155">Aby zainstalować usługi IIS w wersji 7,0 w systemie Windows Vista</span><span class="sxs-lookup"><span data-stu-id="2d428-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1. <span data-ttu-id="2d428-156">Kliknij przycisk Start, a następnie kliknij pozycję Panel sterowania.</span><span class="sxs-lookup"><span data-stu-id="2d428-156">Click Start, and then click Control Panel.</span></span>  
  
2. <span data-ttu-id="2d428-157">Wybierz grupę **programy** .</span><span class="sxs-lookup"><span data-stu-id="2d428-157">Select the **Programs** group.</span></span>  
  
3. <span data-ttu-id="2d428-158">W obszarze **programy i funkcje**kliknij pozycję **Włącz lub wyłącz funkcje systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="2d428-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="2d428-159">Zostanie wyświetlone okno dialogowe **Kontrola konta użytkownika** .</span><span class="sxs-lookup"><span data-stu-id="2d428-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="2d428-160">Kliknij przycisk **Kontynuuj**.</span><span class="sxs-lookup"><span data-stu-id="2d428-160">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="2d428-161">Zostanie wyświetlone okno dialogowe **funkcje systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="2d428-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="2d428-162">Rozwiń element oznaczony **Internet Information Services**.</span><span class="sxs-lookup"><span data-stu-id="2d428-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="2d428-163">Rozwiń element oznaczony **World Wide Web Services**.</span><span class="sxs-lookup"><span data-stu-id="2d428-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="2d428-164">Rozwiń element zatytułowany **Programowanie aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="2d428-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="2d428-165">Upewnij się, że wybrano następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="2d428-165">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="2d428-166">**Rozszerzalność platformy .NET**</span><span class="sxs-lookup"><span data-stu-id="2d428-166">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="2d428-167">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="2d428-167">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="2d428-168">**Rozszerzenia ISAPI**</span><span class="sxs-lookup"><span data-stu-id="2d428-168">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="2d428-169">**Filtry ISAPI**</span><span class="sxs-lookup"><span data-stu-id="2d428-169">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="2d428-170">Rozwiń element zatytułowany **Narzędzia do zarządzania siecią Web**, a następnie wybierz pozycję **Konsola zarządzania usługami IIS**.</span><span class="sxs-lookup"><span data-stu-id="2d428-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="2d428-171">W obszarze elementu **World Wide Web usługach**rozwiń węzeł **wspólne funkcje http**.</span><span class="sxs-lookup"><span data-stu-id="2d428-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="2d428-172">Upewnij się, że jest zaznaczona **Zawartość statyczna** .</span><span class="sxs-lookup"><span data-stu-id="2d428-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="2d428-173">W obszarze elementu **World Wide Web usługach**rozwiń węzeł **zabezpieczenia**.</span><span class="sxs-lookup"><span data-stu-id="2d428-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="2d428-174">Upewnij się, że wybrano **uwierzytelnianie systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="2d428-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="2d428-175">Rozwiń element o nazwie **zgodność z usługami IIS 6**, a następnie wybierz pozycję **Narzędzia do obsługi skryptów w usługach IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="2d428-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="2d428-176">Rozwiń element oznaczony **Microsoft .NET Framework 3,0**, a następnie wybierz pozycję **Windows Communication Foundation Aktywacja HTTP**.</span><span class="sxs-lookup"><span data-stu-id="2d428-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="2d428-177">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2d428-177">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="2d428-178">Aby zainstalować usługi IIS w wersji 6,0 w systemie Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="2d428-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1. <span data-ttu-id="2d428-179">W obszarze **Zarządzanie serwerem**, kliknij przycisk **Dodaj lub Usuń rolę**, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2d428-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2. <span data-ttu-id="2d428-180">Wybierz pozycję **serwer aplikacji (IIS, ASP.NET)** z listy **rola serwera** , a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2d428-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="2d428-181">Zaznacz pole wyboru **włącz ASP.NET** , a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2d428-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="2d428-182">Jeśli podsumowanie wybranych opcji jest poprawne, kliknij przycisk Dalej.</span><span class="sxs-lookup"><span data-stu-id="2d428-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="2d428-183">Aby zainstalować usługi IIS w wersji 5,1 w systemie Windows XP z zainstalowanym dodatkiem Service Pack 2 i Service Pack 3</span><span class="sxs-lookup"><span data-stu-id="2d428-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1. <span data-ttu-id="2d428-184">W panelu sterowania kliknij pozycję **Dodaj lub usuń programy**.</span><span class="sxs-lookup"><span data-stu-id="2d428-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2. <span data-ttu-id="2d428-185">W oknie dialogowym **Dodawanie lub usuwanie programów** kliknij pozycję **Dodaj/Usuń składniki systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="2d428-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3. <span data-ttu-id="2d428-186">W **Kreatorze składników systemu Windows**zaznacz pole wyboru **Internet Information Services (IIS)** , a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2d428-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="2d428-187">Jeśli zostanie wyświetlone okno dialogowe **wymagające plików** , włóż dysk instalacyjny systemu operacyjnego, przejdź do folderu i386, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2d428-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="2d428-188">Po zakończeniu instalacji kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="2d428-188">When installation completes, click **Finish**.</span></span>  
  
6. <span data-ttu-id="2d428-189">Zamknij okno dialogowe **Dodaj lub usuń programy** , a następnie zamknij **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="2d428-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="2d428-190">Aby zweryfikować instalację usług IIS i ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2d428-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1. <span data-ttu-id="2d428-191">Zapisz plik HTML znaleziony na końcu tego tematu w katalogu głównym \InetPub\wwwroot i nadaj mu nazwę default. aspx.</span><span class="sxs-lookup"><span data-stu-id="2d428-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2. <span data-ttu-id="2d428-192">Otwórz okno przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="2d428-192">Open a browser window.</span></span>  
  
3. <span data-ttu-id="2d428-193">Wpisz `http://localhost/Default.aspx` w polu adres, a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="2d428-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4. <span data-ttu-id="2d428-194">Zostanie wyświetlona strona sieci Web z tekstem "Hello world".</span><span class="sxs-lookup"><span data-stu-id="2d428-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d428-195">Za każdym razem, gdy instalujesz nową wersję .NET Framework, należy ponownie zarejestrować program aspnet_isapi jako rozszerzenie usługi sieci Web dla usług IIS.</span><span class="sxs-lookup"><span data-stu-id="2d428-195">Each time you install a new version of the .NET Framework, you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="2d428-196">Aby to zrobić, wydaj `aspnet_regiis –I –enable` polecenie.</span><span class="sxs-lookup"><span data-stu-id="2d428-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="2d428-197">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="2d428-197">Sample Code</span></span>  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
