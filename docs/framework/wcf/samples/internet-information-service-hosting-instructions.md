---
title: Instrukcje dotyczące hostowania internetowej usługi informacyjnej
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: f5aa276bc1178f3e7c61af7505fcf54df8b934e6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328962"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="2444c-102">Instrukcje dotyczące hostowania internetowej usługi informacyjnej</span><span class="sxs-lookup"><span data-stu-id="2444c-102">Internet Information Service Hosting Instructions</span></span>
<span data-ttu-id="2444c-103">Aby uruchomić przykłady, które są hostowane przez Internetowe usługi informacyjne (IIS), upewnij się, że usługi IIS został poprawnie zainstalowany i działa.</span><span class="sxs-lookup"><span data-stu-id="2444c-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="2444c-104">Aby zainstalować usługi IIS w wersji 7.5 w systemie Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="2444c-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="2444c-105">Z **Menedżera serwera**, wybierz opcję **ról.**</span><span class="sxs-lookup"><span data-stu-id="2444c-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="2444c-106">W obszarze **Podsumowanie ról**, kliknij przycisk **Dodaj role**.</span><span class="sxs-lookup"><span data-stu-id="2444c-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="2444c-107">Kliknij przycisk **dalej** do wyświetlenia **Wybieranie ról serwera** okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="2444c-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="2444c-108">Wybierz **serwera aplikacji** z **role** listy, a następnie kliknij przycisk **dalej** dwa razy, aby wyświetlić **Wybieranie usług ról** okno dialogowe Rola serwera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2444c-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="2444c-109">Wybierz **serwer sieci Web (IIS)** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="2444c-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="2444c-110">Jeśli zostanie wyświetlony monit, aby zainstalować dodatkowe usługi ról i funkcji, kliknij przycisk **Dodaj wymagane funkcje**.</span><span class="sxs-lookup"><span data-stu-id="2444c-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="2444c-111">Kliknij przycisk **dalej** dwa razy, aby wyświetlić **Wybieranie usług ról** okno dialogowe dla roli Serwer sieci Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="2444c-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="2444c-112">Rozwiń **narzędzia do zarządzania**, a następnie rozwiń węzeł **zgodność z narzędziami zarządzania usług IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="2444c-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="2444c-113">Wybierz **usług IIS 6 narzędzia obsługi skryptów**.</span><span class="sxs-lookup"><span data-stu-id="2444c-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="2444c-114">Jeśli zostanie wyświetlony monit, aby zainstalować dodatkowe usługi ról i funkcji, kliknij przycisk **Dodaj wymagane usługi ról**.</span><span class="sxs-lookup"><span data-stu-id="2444c-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="2444c-115">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="2444c-115">Click **Next**.</span></span>  
  
6. <span data-ttu-id="2444c-116">Podsumowanie wybrane opcje są poprawne, kliknij przycisk **zainstalować**.</span><span class="sxs-lookup"><span data-stu-id="2444c-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="2444c-117">Po zakończeniu instalacji kliknij przycisk **Zamknij**.</span><span class="sxs-lookup"><span data-stu-id="2444c-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="2444c-118">Aby zainstalować usługi IIS w wersji 7.5 Windows 7</span><span class="sxs-lookup"><span data-stu-id="2444c-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1. <span data-ttu-id="2444c-119">Kliknij przycisk **Start**, a następnie kliknij przycisk **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="2444c-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="2444c-120">Otwórz **programy** grupy.</span><span class="sxs-lookup"><span data-stu-id="2444c-120">Open the **Programs** group.</span></span>  
  
3. <span data-ttu-id="2444c-121">W obszarze **programy i funkcje**, kliknij przycisk **Włącz lub wyłącz funkcje Windows**.</span><span class="sxs-lookup"><span data-stu-id="2444c-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="2444c-122">**Kontrola konta użytkownika** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="2444c-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="2444c-123">Kliknij przycisk **Kontynuuj**.</span><span class="sxs-lookup"><span data-stu-id="2444c-123">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="2444c-124">**Funkcji Windows** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="2444c-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="2444c-125">Rozwiń element etykietami **Internetowe usługi informacyjne**.</span><span class="sxs-lookup"><span data-stu-id="2444c-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="2444c-126">Rozwiń element etykietami **usługi World Wide Web**.</span><span class="sxs-lookup"><span data-stu-id="2444c-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="2444c-127">Rozwiń element etykietami **funkcje tworzenia aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="2444c-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="2444c-128">Upewnij się, że wybrane są następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="2444c-128">Make sure the following items are selected:</span></span>  
  
    1.  **<span data-ttu-id="2444c-129">Rozszerzalność architektury .NET</span><span class="sxs-lookup"><span data-stu-id="2444c-129">.NET Extensibility</span></span>**  
  
    2.  **<span data-ttu-id="2444c-130">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2444c-130">ASP.NET</span></span>**  
  
    3.  **<span data-ttu-id="2444c-131">ISAPI Extensions</span><span class="sxs-lookup"><span data-stu-id="2444c-131">ISAPI Extensions</span></span>**  
  
    4.  **<span data-ttu-id="2444c-132">Filtry ISAPI</span><span class="sxs-lookup"><span data-stu-id="2444c-132">ISAPI Filters</span></span>**  
  
9. <span data-ttu-id="2444c-133">W obszarze elementu etykietą **usługi World Wide Web**, rozwiń węzeł **wspólne funkcje Http**.</span><span class="sxs-lookup"><span data-stu-id="2444c-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="2444c-134">Upewnij się, że **zawartość statyczna** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="2444c-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="2444c-135">W obszarze elementu etykietą **usługi World Wide Web**, rozwiń węzeł **zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="2444c-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="2444c-136">Upewnij się, że **uwierzytelniania Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="2444c-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="2444c-137">W obszarze **Internetowe usługi informacyjne** katalogu, rozwiń element etykietami **narzędzia zarządzania siecią Web**, a następnie wybierz pozycję **Konsola zarządzania usługami IIS**.</span><span class="sxs-lookup"><span data-stu-id="2444c-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="2444c-138">Rozwiń element etykietami **zgodność z narzędziami zarządzania usług IIS 6**, a następnie wybierz pozycję **narzędzia obsługi skryptów w usługach IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="2444c-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="2444c-139">W obszarze **Internetowe usługi informacyjne** katalogu, rozwiń element etykietami **Microsoft .NET Framework 3.5.1**, a następnie wybierz pozycję **Windows Communication Foundation Http aktywacji**.</span><span class="sxs-lookup"><span data-stu-id="2444c-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="2444c-140">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2444c-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="2444c-141">Aby zainstalować usługi IIS w wersji 7.0 w systemie Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="2444c-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1. <span data-ttu-id="2444c-142">Z **Menedżera serwera**, wybierz opcję **role**.</span><span class="sxs-lookup"><span data-stu-id="2444c-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="2444c-143">W obszarze **Podsumowanie ról**, kliknij przycisk **Dodaj role**.</span><span class="sxs-lookup"><span data-stu-id="2444c-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="2444c-144">Kliknij przycisk **dalej** do wyświetlenia **Wybieranie ról serwera** okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="2444c-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="2444c-145">Wybierz **serwera aplikacji** z **role** listy, a następnie kliknij przycisk **dalej** dwa razy, aby wyświetlić **Wybieranie usług ról** okno dialogowe Rola serwera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2444c-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="2444c-146">Wybierz **serwer sieci Web (IIS)** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="2444c-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="2444c-147">Jeśli zostanie wyświetlony monit, aby zainstalować dodatkowe usługi ról i funkcji, kliknij przycisk **Dodaj wymagane funkcje**.</span><span class="sxs-lookup"><span data-stu-id="2444c-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="2444c-148">Kliknij przycisk **dalej** dwa razy, aby wyświetlić **Wybieranie usług ról** okno dialogowe dla roli Serwer sieci Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="2444c-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="2444c-149">Rozwiń **narzędzia do zarządzania**, a następnie rozwiń węzeł **zgodność z narzędziami zarządzania usług IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="2444c-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="2444c-150">Wybierz **usług IIS 6 narzędzia obsługi skryptów**.</span><span class="sxs-lookup"><span data-stu-id="2444c-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="2444c-151">Jeśli zostanie wyświetlony monit, aby zainstalować dodatkowe usługi ról i funkcji, kliknij przycisk **Dodaj wymagane usługi ról**.</span><span class="sxs-lookup"><span data-stu-id="2444c-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="2444c-152">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="2444c-152">Click **Next**.</span></span>  
  
6. <span data-ttu-id="2444c-153">Podsumowanie wybrane opcje są poprawne, kliknij przycisk **zainstalować**.</span><span class="sxs-lookup"><span data-stu-id="2444c-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="2444c-154">Po zakończeniu instalacji kliknij przycisk **Zamknij**.</span><span class="sxs-lookup"><span data-stu-id="2444c-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="2444c-155">Aby zainstalować usługi IIS w wersji 7.0 w systemie Windows Vista</span><span class="sxs-lookup"><span data-stu-id="2444c-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1. <span data-ttu-id="2444c-156">Kliknij przycisk Start, a następnie kliknij Panel sterowania.</span><span class="sxs-lookup"><span data-stu-id="2444c-156">Click Start, and then click Control Panel.</span></span>  
  
2. <span data-ttu-id="2444c-157">Wybierz **programy** grupy.</span><span class="sxs-lookup"><span data-stu-id="2444c-157">Select the **Programs** group.</span></span>  
  
3. <span data-ttu-id="2444c-158">W obszarze **programy i funkcje**, kliknij przycisk **Włącz lub wyłącz funkcje Windows**.</span><span class="sxs-lookup"><span data-stu-id="2444c-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="2444c-159">**Kontrola konta użytkownika** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="2444c-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="2444c-160">Kliknij przycisk **Kontynuuj**.</span><span class="sxs-lookup"><span data-stu-id="2444c-160">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="2444c-161">**Funkcji Windows** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="2444c-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="2444c-162">Rozwiń element etykietami **Internetowe usługi informacyjne**.</span><span class="sxs-lookup"><span data-stu-id="2444c-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="2444c-163">Rozwiń element etykietami **usługi World Wide Web**.</span><span class="sxs-lookup"><span data-stu-id="2444c-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="2444c-164">Rozwiń element etykietami **funkcje tworzenia aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="2444c-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="2444c-165">Upewnij się, że wybrane są następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="2444c-165">Make sure the following items are selected:</span></span>  
  
    1.  **<span data-ttu-id="2444c-166">Rozszerzalność architektury .NET</span><span class="sxs-lookup"><span data-stu-id="2444c-166">.NET Extensibility</span></span>**  
  
    2.  **<span data-ttu-id="2444c-167">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2444c-167">ASP.NET</span></span>**  
  
    3.  **<span data-ttu-id="2444c-168">ISAPI Extensions</span><span class="sxs-lookup"><span data-stu-id="2444c-168">ISAPI Extensions</span></span>**  
  
    4.  **<span data-ttu-id="2444c-169">Filtry ISAPI</span><span class="sxs-lookup"><span data-stu-id="2444c-169">ISAPI Filters</span></span>**  
  
9. <span data-ttu-id="2444c-170">Rozwiń element etykietami **narzędzia zarządzania siecią Web**, a następnie wybierz pozycję **Konsola zarządzania usługami IIS**.</span><span class="sxs-lookup"><span data-stu-id="2444c-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="2444c-171">W obszarze elementu etykietą **usługi World Wide Web**, rozwiń węzeł **wspólne funkcje Http**.</span><span class="sxs-lookup"><span data-stu-id="2444c-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="2444c-172">Upewnij się, że **zawartość statyczna** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="2444c-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="2444c-173">W obszarze elementu etykietą **usługi World Wide Web**, rozwiń węzeł **zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="2444c-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="2444c-174">Upewnij się, że **uwierzytelniania Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="2444c-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="2444c-175">Rozwiń element etykietami **zgodność z narzędziami zarządzania usług IIS 6**, a następnie wybierz pozycję **narzędzia obsługi skryptów w usługach IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="2444c-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="2444c-176">Rozwiń element etykietami **Microsoft .NET Framework 3.0**, a następnie wybierz pozycję **Aktywacja Http programu Windows Communication Foundation**.</span><span class="sxs-lookup"><span data-stu-id="2444c-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="2444c-177">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2444c-177">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="2444c-178">Aby zainstalować usługi IIS w wersji 6.0 w systemie Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="2444c-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1. <span data-ttu-id="2444c-179">Z **Zarządzanie serwerem**, kliknij przycisk **apletu Dodaj lub Usuń rolę**, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2444c-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2. <span data-ttu-id="2444c-180">Wybierz **serwer aplikacji (usługi IIS, ASP.NET)** z **roli serwera** listy, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2444c-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="2444c-181">Wybierz **Włącz ASP.NET** pole wyboru, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2444c-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="2444c-182">Jeśli podsumowanie wybrane opcje są poprawne, kliknij przycisk Dalej.</span><span class="sxs-lookup"><span data-stu-id="2444c-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="2444c-183">Aby zainstalować usługi IIS w wersji 5.1 w systemie Windows XP z dodatkiem Service Pack 2 i dodatkiem Service Pack 3 zainstalowany</span><span class="sxs-lookup"><span data-stu-id="2444c-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1. <span data-ttu-id="2444c-184">W Panelu sterowania kliknij **apletu Dodaj lub usuń programy**.</span><span class="sxs-lookup"><span data-stu-id="2444c-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2. <span data-ttu-id="2444c-185">W **apletu Dodaj lub usuń programy** okno dialogowe, kliknij przycisk **Dodaj/Usuń składniki Windows**.</span><span class="sxs-lookup"><span data-stu-id="2444c-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3. <span data-ttu-id="2444c-186">W **Kreatora składników Windows**, wybierz opcję **Internet Information Services (IIS)** pole wyboru, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2444c-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="2444c-187">Jeśli **pliki potrzebne** zostanie wyświetlone okno dialogowe, włóż dysk instalacyjny systemu operacyjnego, przejdź do folderu i386, a następnie kliknij **OK**.</span><span class="sxs-lookup"><span data-stu-id="2444c-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="2444c-188">Po zakończeniu instalacji kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="2444c-188">When installation completes, click **Finish**.</span></span>  
  
6. <span data-ttu-id="2444c-189">Zamknij **apletu Dodaj lub usuń programy** okno dialogowe, a następnie Zamknij **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="2444c-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="2444c-190">Aby sprawdzić poprawność instalacji usług IIS i platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2444c-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1. <span data-ttu-id="2444c-191">Zapisz ten plik HTML znajdującą się na końcu tego tematu w katalogu głównym \InetPub\wwwroot i nadaj jej nazwę na Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="2444c-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2. <span data-ttu-id="2444c-192">Otwórz okno przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="2444c-192">Open a browser window.</span></span>  
  
3. <span data-ttu-id="2444c-193">Typ `http://localhost/Default.aspx` w polu adresu, a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="2444c-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4. <span data-ttu-id="2444c-194">Strony sieci Web z tekstu "Hello World" powinna zostać wyświetlona.</span><span class="sxs-lookup"><span data-stu-id="2444c-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2444c-195">Każdorazowo Zainstaluj nową wersję [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], należy ponownie zarejestrować Biblioteka aspnet_isapi jako rozszerzenie usługi sieci Web dla usług IIS.</span><span class="sxs-lookup"><span data-stu-id="2444c-195">Each time you install a new version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="2444c-196">Aby to zrobić, należy wydać `aspnet_regiis –I –enable` polecenia.</span><span class="sxs-lookup"><span data-stu-id="2444c-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="2444c-197">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="2444c-197">Sample Code</span></span>  
  
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
