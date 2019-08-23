---
title: Instrukcje dotyczące konfigurowania katalogów wirtualnych
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: f755fadf6bef2bdd58fd31f3460a143b8f52eddf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966743"
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="cd4e6-102">Instrukcje dotyczące konfigurowania katalogów wirtualnych</span><span class="sxs-lookup"><span data-stu-id="cd4e6-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="cd4e6-103">Przykłady Windows Communication Foundation (WCF) są przeznaczone do udostępniania wspólnego katalogu wirtualnego o nazwie servicemodelsamples, który jest mapowany do folderu%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-103">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd4e6-104">Dysk% SystemDrive% jest zwykle C: lub D:, w zależności od lokalizacji dysku, w której zainstalowano Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="cd4e6-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="cd4e6-105">Pliki Setupvroot. bat i cleanupvroot. bat można uruchomić z [procedury konfiguracji jednorazowej dla przykładów Windows Communication Foundation,](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) aby utworzyć katalog wirtualny.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="cd4e6-106">Jeśli wolisz ręcznie utworzyć katalog wirtualny, Użyj poniższych procedur.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="cd4e6-107">Procedury</span><span class="sxs-lookup"><span data-stu-id="cd4e6-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="cd4e6-108">Aby utworzyć katalog wirtualny w usługach IIS 7,0 lub 7,5</span><span class="sxs-lookup"><span data-stu-id="cd4e6-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="cd4e6-109">W menu **Start** kliknij polecenie **Uruchom**, a następnie wpisz **inetmgr** , aby otworzyć przystawkę MMC Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="cd4e6-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="cd4e6-110">W lewym okienku rozwiń węzeł nazwą komputera, a następnie rozwiń węzeł **Lokacje** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3. <span data-ttu-id="cd4e6-111">Kliknij prawym przyciskiem myszy pozycję **Domyślna witryna sieci Web**, a następnie wybierz polecenie **Dodaj aplikację** , aby otworzyć **okno Dodawanie aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4. <span data-ttu-id="cd4e6-112">W oknie wpisz `servicemodelsamples` jako alias tworzonego katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="cd4e6-113">Utwórz następujący katalog:%SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="cd4e6-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6. <span data-ttu-id="cd4e6-114">Ustaw ścieżkę fizyczną na%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="cd4e6-115">Większość przykładów WCF kopiuje pliki wykonywalne usługi do tej lokalizacji po skompilowaniu.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7. <span data-ttu-id="cd4e6-116">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-116">Click **OK**.</span></span> <span data-ttu-id="cd4e6-117">Aplikacja sieci Web jest teraz utworzona dla przykładów WCF.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd4e6-118">To zadanie należy wykonać tylko raz, ponieważ wszystkie przykłady WCF używają tej samej aplikacji sieci Web servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-118">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd4e6-119">Na potrzeby tej dokumentacji termin `virtual directory` jest równoznaczny z. `Web application`</span><span class="sxs-lookup"><span data-stu-id="cd4e6-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="cd4e6-120">Oprócz tworzenia katalogu wirtualnego, należy również ustawić jego właściwości, aby umożliwić uruchamianie usług WCF.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-120">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="cd4e6-121">Aby uzyskać szczegółowe informacje, zobacz poniżej.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="cd4e6-122">Aby utworzyć katalog wirtualny w usługach IIS 5,1 lub 6,0</span><span class="sxs-lookup"><span data-stu-id="cd4e6-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="cd4e6-123">Otwórz okno wiersza polecenia i wpisz `start inetmgr` , aby otworzyć przystawkę MMC Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="cd4e6-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="cd4e6-124">W lewym okienku rozwiń węzeł nazwą komputera, a następnie rozwiń węzeł **witryny sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3. <span data-ttu-id="cd4e6-125">Kliknij prawym przyciskiem myszy pozycję **Domyślna witryna sieci Web** i wybierz pozycję **Nowy, katalog wirtualny,** aby otworzyć Kreatora tworzenia katalogów wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4. <span data-ttu-id="cd4e6-126">W Kreatorze wpisz `servicemodelsamples` jako alias tworzonego katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="cd4e6-127">Ustaw ścieżkę do%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="cd4e6-128">Większość przykładów WCF kopiuje pliki wykonywalne usługi do tej lokalizacji po skompilowaniu.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-128">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6. <span data-ttu-id="cd4e6-129">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-129">Click **Next**.</span></span>  
  
7. <span data-ttu-id="cd4e6-130">Domyślnie są zaznaczone następujące pola wyboru:</span><span class="sxs-lookup"><span data-stu-id="cd4e6-130">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="cd4e6-131">**Read**</span><span class="sxs-lookup"><span data-stu-id="cd4e6-131">**Read**</span></span>  
  
    - <span data-ttu-id="cd4e6-132">**Uruchamianie skryptów (takich jak ASP)**</span><span class="sxs-lookup"><span data-stu-id="cd4e6-132">**Run scripts (such as ASP)**</span></span>  
  
8. <span data-ttu-id="cd4e6-133">Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ** , aby zakończyć pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd4e6-134">To zadanie należy wykonać tylko raz, ponieważ wszystkie przykłady WCF używają tego samego katalogu wirtualnego ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-134">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="cd4e6-135">Aby ustawić dodatkowe właściwości katalogu wirtualnego w usługach IIS 7,0 lub 7,5</span><span class="sxs-lookup"><span data-stu-id="cd4e6-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="cd4e6-136">Kliknij węzeł servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="cd4e6-137">W dolnej części okna wyświetlane są dwa widoki.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="cd4e6-138">Wybierz pozycję **funkcje widok** , jeśli nie została jeszcze wybrana.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2. <span data-ttu-id="cd4e6-139">Kliknij dwukrotnie wpis do **przeglądania katalogów**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3. <span data-ttu-id="cd4e6-140">W okienku Akcje wybierz opcję **Włącz** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="cd4e6-141">Dzięki temu można uzyskać dostęp do katalogu katalogu przy użyciu programu Internet Explorer, który ułatwia debugowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="cd4e6-142">Na koniec należy ustawić właściwości zabezpieczeń folderu servicemodelsamples, aby umożliwić dostęp innym osobom.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="cd4e6-143">Aby uzyskać szczegółowe informacje, zobacz poniżej.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="cd4e6-144">Aby ustawić dodatkowe właściwości katalogu wirtualnego w usługach IIS 5,1 lub 6,0</span><span class="sxs-lookup"><span data-stu-id="cd4e6-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="cd4e6-145">Kliknij prawym przyciskiem myszy węzeł servicemodelsamples, a następnie kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="cd4e6-146">Domyślnie są zaznaczone następujące pola wyboru:</span><span class="sxs-lookup"><span data-stu-id="cd4e6-146">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="cd4e6-147">**Read**</span><span class="sxs-lookup"><span data-stu-id="cd4e6-147">**Read**</span></span>  
  
    - <span data-ttu-id="cd4e6-148">**Wizyty w dzienniku**</span><span class="sxs-lookup"><span data-stu-id="cd4e6-148">**Log visits**</span></span>  
  
    - <span data-ttu-id="cd4e6-149">**Indeksuj ten zasób**</span><span class="sxs-lookup"><span data-stu-id="cd4e6-149">**Index this resource**</span></span>  
  
3. <span data-ttu-id="cd4e6-150">Zaznacz pole wyboru **Przeglądanie katalogów** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="cd4e6-151">Dzięki temu można uzyskać dostęp do katalogu katalogu przy użyciu programu Internet Explorer, który ułatwia debugowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="cd4e6-152">Aby ustawić właściwości zabezpieczeń folderu w usługach IIS 7,0 lub 7,5</span><span class="sxs-lookup"><span data-stu-id="cd4e6-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="cd4e6-153">Przejdź do%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="cd4e6-154">Kliknij prawym przyciskiem myszy folder servicemodelsamples, a następnie kliknij pozycję **Udostępnij** lub **Udostępnij**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3. <span data-ttu-id="cd4e6-155">Kliknij strzałkę w dół znajdującą się po lewej stronie przycisku **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4. <span data-ttu-id="cd4e6-156">Wybierz pozycję **Znajdź** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-156">Select the **Find** entry.</span></span> <span data-ttu-id="cd4e6-157">Zostanie otwarte okno **Wybieranie użytkowników lub grup** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-157">The **Select Users or Groups** window opens.</span></span>  
  
5. <span data-ttu-id="cd4e6-158">Kliknij przycisk **zaawansowane**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-158">Click **Advanced**.</span></span>  
  
6. <span data-ttu-id="cd4e6-159">Kliknij pozycję **lokalizacje**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-159">Click **Locations**.</span></span> <span data-ttu-id="cd4e6-160">Okno **lokalizacje** jest teraz otwarte.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-160">The **Locations** window is now open.</span></span>  
  
7. <span data-ttu-id="cd4e6-161">Wybierz wpis dla używanego komputera.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="cd4e6-162">Ważne jest, aby wybrać komputer lokalny, a nie wpis dla dowolnych domen lub sieci, które są wymienione na liście.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="cd4e6-163">Po wybraniu komputera kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-163">After you have selected the computer, click **OK**.</span></span>  
  
8. <span data-ttu-id="cd4e6-164">Kliknij przycisk **Znajdź teraz**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-164">Click **Find Now**.</span></span> <span data-ttu-id="cd4e6-165">Spowoduje to wypełnienie wyników wyszukiwania za pomocą obiektów skojarzonych z komputerem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="cd4e6-166">Znajdź wpis **IIS_IUSRS** w kolumnie **Nazwa (względna nazwa wyróżniająca)** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="cd4e6-167">Wybierz ten wpis, a następnie kliknij przycisk **OK** , aby zamknąć okno wyników wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="cd4e6-168">Kliknij przycisk **OK** , aby zamknąć okno **Wybieranie użytkowników lub grup** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="cd4e6-169">Kliknij przycisk **Udostępnij** , aby zachować zmiany.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="cd4e6-170">Po zakończeniu wprowadzania zmian w celu włączenia udostępniania kliknij przycisk **gotowe** , aby zamknąć okno **udostępnianie plików** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="cd4e6-171">Aby ustawić właściwości zabezpieczeń folderu w usługach IIS 5,1 lub 6,0</span><span class="sxs-lookup"><span data-stu-id="cd4e6-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="cd4e6-172">Przejdź do%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="cd4e6-173">Kliknij prawym przyciskiem myszy folder **servicemodelsamples** , a następnie kliknij pozycję **udostępnianie i zabezpieczenia.**</span><span class="sxs-lookup"><span data-stu-id="cd4e6-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3. <span data-ttu-id="cd4e6-174">Kliknij kartę **zabezpieczenia** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-174">Click the **Security** tab.</span></span>  
  
4. <span data-ttu-id="cd4e6-175">Jeśli używasz usług IIS 6,0, w polu **nazwy grupy lub użytkownika** Sprawdź, czy na liście znajdują się **konta gościa internetowego** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="cd4e6-176">Jeśli nie ma go na liście:</span><span class="sxs-lookup"><span data-stu-id="cd4e6-176">If it is not listed:</span></span>  
  
    1. <span data-ttu-id="cd4e6-177">Kliknij przycisk **Start** , a następnie kliknij pozycję **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="cd4e6-178">Jeśli nie widzisz ikony **konta użytkowników** , kliknij przycisk **Przełącz do widoku kategorii**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3. <span data-ttu-id="cd4e6-179">Kliknij ikonę **konta użytkowników** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-179">Click the **User Accounts** icon.</span></span>  
  
    4. <span data-ttu-id="cd4e6-180">W obszarze "lub wybierz ikonę panelu sterowania" kliknij pozycję **konta użytkowników**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5. <span data-ttu-id="cd4e6-181">W oknie dialogowym **konta użytkowników** kliknij kartę **Zaawansowane** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6. <span data-ttu-id="cd4e6-182">Kliknij przycisk **zaawansowane**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-182">Click **Advanced**.</span></span>  
  
    7. <span data-ttu-id="cd4e6-183">W oknie dialogowym **lokalni użytkownicy i grupy** kliknij, aby rozwinąć folder **Users (Użytkownicy** ).</span><span class="sxs-lookup"><span data-stu-id="cd4e6-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8. <span data-ttu-id="cd4e6-184">W prawym okienku kliknij dwukrotnie pozycję **konto gościa internetowego**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="cd4e6-185">W oknie dialogowym **Właściwości** skopiuj nazwę używaną jako konto gościa internetowego.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="cd4e6-186">Domyślnie nazwa rozpoczyna się od ciągu "USR_", po którym następuje nazwa komputera.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="cd4e6-187">Zamknij okno dialogowe **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="cd4e6-188">Zamknij okno dialogowe **Użytkownicy i grupy lokalne** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="cd4e6-189">Zamknij okno dialogowe **konta użytkowników** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="cd4e6-190">Zamknij okno dialogowe inne **konta użytkowników** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="cd4e6-191">W oknie dialogowym **Właściwości servicemodelsamples** na karcie **zabezpieczenia** kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="cd4e6-192">Wpisz nazwę komputera, a następnie ukośnik odwrotny, a następnie wklej nazwę konta użytkownika internetowego, na przykład MojKomputer\\% InternetGuestAccountName%</span><span class="sxs-lookup"><span data-stu-id="cd4e6-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="cd4e6-193">Kliknij przycisk **Sprawdź nazwy** , aby zweryfikować dodanie.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="cd4e6-194">Jeśli jest to prawidłowe, nazwa jest w Wielkiej litery i jest podkreślona.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5. <span data-ttu-id="cd4e6-195">W przypadku usług IIS 6,0 Sprawdź, czy usługa sieciowa znajduje się w polu **nazwy grupy lub użytkownika** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="cd4e6-196">Jeśli usługa sieciowa nie jest wymieniona na liście:</span><span class="sxs-lookup"><span data-stu-id="cd4e6-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1. <span data-ttu-id="cd4e6-197">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-197">Click **Add**.</span></span>  
  
    2. <span data-ttu-id="cd4e6-198">W oknie dialogowym **Wybieranie użytkowników lub grup** wpisz nazwę komputera, a następnie ukośnik odwrotny.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3. <span data-ttu-id="cd4e6-199">Wpisz **usługę** po ukośniku odwrotnym (bez spacji).</span><span class="sxs-lookup"><span data-stu-id="cd4e6-199">Type **service** after the backslash (no space).</span></span>  
  
    4. <span data-ttu-id="cd4e6-200">Kliknij przycisk **Sprawdź nazwy**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-200">Click **Check names**.</span></span>  
  
    5. <span data-ttu-id="cd4e6-201">Jeśli zostanie znalezionych wiele nazw, wybierz pozycję **Usługa sieciowa** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6. <span data-ttu-id="cd4e6-202">Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Wybieranie użytkowników lub grup** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6. <span data-ttu-id="cd4e6-203">Jeśli używasz systemu Windows XP z dodatkiem SP2 z usługami IIS 5,1, sprawdź, czy w polu **nazwy grupy lub użytkownika** są wyświetlane zarówno konto gościa internetowego, jak i ASPNET.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="cd4e6-204">Należy pamiętać, że użytkownik ASPNET może być członkiem wbudowanej grupy zabezpieczeń **Użytkownicy** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="cd4e6-205">Jeśli tak, to jeśli w oknie dialogowym zostanie wyświetlona Grupa **Użytkownicy** , nie musisz dodawać jej jako osobnego elementu do listy dozwolonych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="cd4e6-206">Aby sprawdzić, czy ASPNET jest częścią grupy zabezpieczeń **Użytkownicy** :</span><span class="sxs-lookup"><span data-stu-id="cd4e6-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1. <span data-ttu-id="cd4e6-207">W menu **Start** kliknij pozycję **Panel sterowania**.</span><span class="sxs-lookup"><span data-stu-id="cd4e6-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="cd4e6-208">Kliknij ikonę **konta użytkowników** .</span><span class="sxs-lookup"><span data-stu-id="cd4e6-208">Click the **User Accounts** icon.</span></span>  
  
    3. <span data-ttu-id="cd4e6-209">W kolumnie **Grupa** Sprawdź, czy wartość **ASPNET** to "Users".</span><span class="sxs-lookup"><span data-stu-id="cd4e6-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd4e6-210">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd4e6-210">See also</span></span>

- [<span data-ttu-id="cd4e6-211">Instrukcje dotyczące hostowania internetowej usługi informacyjnej</span><span class="sxs-lookup"><span data-stu-id="cd4e6-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
