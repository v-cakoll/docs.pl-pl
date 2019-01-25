---
title: Instrukcje dotyczące konfigurowania katalogów wirtualnych
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: 0f32fd6d65db529ba1015dedd98f99efd7f408c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588115"
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="d0dc8-102">Instrukcje dotyczące konfigurowania katalogów wirtualnych</span><span class="sxs-lookup"><span data-stu-id="d0dc8-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="d0dc8-103">Przykłady Windows Communication Foundation (WCF) będą udostępniać wspólnego katalogu wirtualnego o nazwie servicemodelsamples, który jest zamapowany na %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-103">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0dc8-104">Dysk % SystemDrive % jest zwykle C: i D:, w zależności od lokalizacji dysku, na którym zainstalowano usługi Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="d0dc8-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="d0dc8-105">Możesz uruchamiać pliki Setupvroot.bat i Cleanupvroot.bat z [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) można utworzyć katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="d0dc8-106">Jeśli wolisz ręcznie utworzyć katalogu wirtualnego, należy użyć poniższych procedur.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="d0dc8-107">Procedury</span><span class="sxs-lookup"><span data-stu-id="d0dc8-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="d0dc8-108">Można utworzyć katalogu wirtualnego w usługach IIS 7.0 lub 7.5</span><span class="sxs-lookup"><span data-stu-id="d0dc8-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="d0dc8-109">Z **Start** menu, kliknij przycisk **Uruchom**, a następnie wpisz **inetmgr** aby otworzyć przystawkę MMC usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="d0dc8-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="d0dc8-110">W lewym okienku rozwiń węzeł z nazwą komputera, a następnie rozwiń **witryn** węzła.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3.  <span data-ttu-id="d0dc8-111">Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web**, a następnie wybierz pozycję **Add Application** otworzyć **okno Dodawanie aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4.  <span data-ttu-id="d0dc8-112">W oknie wpisz `servicemodelsamples` jako alias katalogu wirtualnego, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="d0dc8-113">Utwórz następujący katalog: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="d0dc8-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6.  <span data-ttu-id="d0dc8-114">Ustaw ścieżkę fizyczną na % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="d0dc8-115">Większość przykładów WCF skopiuj pliki wykonywalne usługi do tej lokalizacji podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7.  <span data-ttu-id="d0dc8-116">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-116">Click **OK**.</span></span> <span data-ttu-id="d0dc8-117">Aplikacja sieci Web został utworzony dla przykładów usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d0dc8-118">To zadanie można wykonać tylko raz, ponieważ jest używany przez wszystkie przykłady WCF servicemodelsamples tej samej aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-118">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d0dc8-119">Na potrzeby tej dokumentacji termin `virtual directory` jest synonimem `Web application`.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="d0dc8-120">Oprócz tworzenia katalogu wirtualnego, można również ustawić jej właściwości, aby umożliwić działanie usług WCF.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-120">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="d0dc8-121">Zobacz szczegóły poniżej.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="d0dc8-122">Można utworzyć katalogu wirtualnego w IIS 5.1 i 6.0</span><span class="sxs-lookup"><span data-stu-id="d0dc8-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="d0dc8-123">Otwórz okno wiersza polecenia i wpisz `start inetmgr` aby otworzyć przystawkę MMC usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="d0dc8-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="d0dc8-124">W lewym okienku rozwiń węzeł z nazwą komputera, a następnie rozwiń **witryn sieci Web** węzła.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3.  <span data-ttu-id="d0dc8-125">Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** i wybierz **nowe, katalog wirtualny** aby otworzyć Kreatora tworzenia katalogów wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4.  <span data-ttu-id="d0dc8-126">W kreatorze, wpisz `servicemodelsamples` jako alias katalogu wirtualnego, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="d0dc8-127">Ustaw ścieżkę na % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="d0dc8-128">Większość przykładów WCF skopiuj pliki wykonywalne usługi do tej lokalizacji podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-128">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6.  <span data-ttu-id="d0dc8-129">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-129">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="d0dc8-130">Domyślnie wybrane są następujące pola wyboru:</span><span class="sxs-lookup"><span data-stu-id="d0dc8-130">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="d0dc8-131">**Read**</span><span class="sxs-lookup"><span data-stu-id="d0dc8-131">**Read**</span></span>  
  
    -   <span data-ttu-id="d0dc8-132">**Uruchamianie skryptów (np. ASP)**</span><span class="sxs-lookup"><span data-stu-id="d0dc8-132">**Run scripts (such as ASP)**</span></span>  
  
8.  <span data-ttu-id="d0dc8-133">Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ** aby zakończyć działanie kreatora.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d0dc8-134">To zadanie muszą być wykonywane tylko raz, ponieważ wszystkie przykłady WCF używają tego samego servicemodelsamples katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-134">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="d0dc8-135">Aby ustawić właściwości dodatkowych katalogu wirtualnego w usługach IIS 7.0 lub 7.5</span><span class="sxs-lookup"><span data-stu-id="d0dc8-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="d0dc8-136">Kliknij węzeł servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="d0dc8-137">Wzdłuż dolnej części okna dwa widoki są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="d0dc8-138">Wybierz **widoku funkcji** Jeśli nie została jeszcze wybrana.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2.  <span data-ttu-id="d0dc8-139">Kliknij dwukrotnie pozycję **przeglądanie katalogów**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3.  <span data-ttu-id="d0dc8-140">W okienku akcji wybierz **Włącz** opcji.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="d0dc8-141">Dzięki temu można uzyskać dostępu do katalogu, w katalogu za pomocą programu Internet Explorer, która pomaga podczas debugowania usługi.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="d0dc8-142">Na koniec należy ustawić właściwości zabezpieczeń folderu servicemodelsamples, aby zezwalała na można uzyskać dostępu do innych osób.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="d0dc8-143">Zobacz szczegóły poniżej.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="d0dc8-144">Aby ustawić właściwości dodatkowych katalogu wirtualnego w usługach IIS 5.1 i 6.0</span><span class="sxs-lookup"><span data-stu-id="d0dc8-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="d0dc8-145">Kliknij prawym przyciskiem myszy węzeł servicemodelsamples, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="d0dc8-146">Domyślnie wybrane są następujące pola wyboru:</span><span class="sxs-lookup"><span data-stu-id="d0dc8-146">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="d0dc8-147">**Read**</span><span class="sxs-lookup"><span data-stu-id="d0dc8-147">**Read**</span></span>  
  
    -   <span data-ttu-id="d0dc8-148">**Rejestruj wizyty**</span><span class="sxs-lookup"><span data-stu-id="d0dc8-148">**Log visits**</span></span>  
  
    -   <span data-ttu-id="d0dc8-149">**Indeksuj ten zasób**</span><span class="sxs-lookup"><span data-stu-id="d0dc8-149">**Index this resource**</span></span>  
  
3.  <span data-ttu-id="d0dc8-150">Wybierz **przeglądanie katalogów** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="d0dc8-151">Dzięki temu można uzyskać dostępu do katalogu, w katalogu za pomocą programu Internet Explorer, która pomaga podczas debugowania usługi.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="d0dc8-152">Aby ustawić właściwości zabezpieczeń folderu w usługach IIS 7.0 lub 7.5</span><span class="sxs-lookup"><span data-stu-id="d0dc8-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="d0dc8-153">Przejdź do % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="d0dc8-154">Kliknij prawym przyciskiem myszy servicemodelsamples folder, a następnie kliknij przycisk **udziału** lub **udziału za pomocą**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3.  <span data-ttu-id="d0dc8-155">Kliknij strzałkę w dół po lewej stronie **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4.  <span data-ttu-id="d0dc8-156">Wybierz **znaleźć** wpisu.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-156">Select the **Find** entry.</span></span> <span data-ttu-id="d0dc8-157">**Wybieranie użytkowników lub grup** zostanie otwarte okno.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-157">The **Select Users or Groups** window opens.</span></span>  
  
5.  <span data-ttu-id="d0dc8-158">Kliknij przycisk **zaawansowane**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-158">Click **Advanced**.</span></span>  
  
6.  <span data-ttu-id="d0dc8-159">Kliknij przycisk **lokalizacje**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-159">Click **Locations**.</span></span> <span data-ttu-id="d0dc8-160">**Lokalizacje** jest teraz otwarte okno.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-160">The **Locations** window is now open.</span></span>  
  
7.  <span data-ttu-id="d0dc8-161">Zaznacz wpis dla komputera, używana.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="d0dc8-162">Należy wybrać komputer lokalny i nie wpis dla jak domeny, do których należą.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="d0dc8-163">Po wybraniu komputera, kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-163">After you have selected the computer, click **OK**.</span></span>  
  
8.  <span data-ttu-id="d0dc8-164">Kliknij przycisk **Znajdź teraz**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-164">Click **Find Now**.</span></span> <span data-ttu-id="d0dc8-165">Spowoduje to wypełnienie wyników wyszukiwania za pomocą obiektów skojarzonych z komputerem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="d0dc8-166">Znajdź **IIS_IUSRS** wpis **Name (nazwa wyróżniająca względną)** kolumny.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="d0dc8-167">Wybierz odpowiedni wpis, a następnie kliknij przycisk **OK** Zamknij wyszukiwanie okno wyników.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="d0dc8-168">Kliknij przycisk **OK** zamknąć **Wybieranie użytkowników lub grup** okna.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="d0dc8-169">Kliknij przycisk **udziału** aby utrwalić zmiany.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="d0dc8-170">Po zakończeniu zmiany, co pozwala na udostępnianie kliknij **gotowe** zamknąć **udostępniania plików** okna.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="d0dc8-171">Do ustawiania właściwości zabezpieczeń folderu usługi IIS 5.1 i 6.0</span><span class="sxs-lookup"><span data-stu-id="d0dc8-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="d0dc8-172">Przejdź do % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="d0dc8-173">Kliknij prawym przyciskiem myszy **servicemodelsamples** folder, a następnie kliknij przycisk **udostępnianie i zabezpieczenia.**</span><span class="sxs-lookup"><span data-stu-id="d0dc8-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3.  <span data-ttu-id="d0dc8-174">Kliknij przycisk **zabezpieczeń** kartę.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-174">Click the **Security** tab.</span></span>  
  
4.  <span data-ttu-id="d0dc8-175">Jeśli używasz usług IIS 6.0 w **nazwy grupy lub użytkownika** zaznacz pole wyboru czy **konta gościa Internet** znajduje się na liście.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="d0dc8-176">Jeśli nie ma na liście:</span><span class="sxs-lookup"><span data-stu-id="d0dc8-176">If it is not listed:</span></span>  
  
    1.  <span data-ttu-id="d0dc8-177">Kliknij przycisk **Start** a następnie kliknij przycisk **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="d0dc8-178">Jeśli nie widzisz **kont użytkowników** ikonę, kliknij przycisk **Przełącz do widoku kategorii**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3.  <span data-ttu-id="d0dc8-179">Kliknij przycisk **kont użytkowników** ikony.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-179">Click the **User Accounts** icon.</span></span>  
  
    4.  <span data-ttu-id="d0dc8-180">W obszarze "lub wybierz ikonę Panelu sterowania" kliknij **kont użytkowników**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5.  <span data-ttu-id="d0dc8-181">W **kont użytkowników** okno dialogowe, kliknij przycisk **zaawansowane** kartę.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6.  <span data-ttu-id="d0dc8-182">Kliknij przycisk **zaawansowane**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-182">Click **Advanced**.</span></span>  
  
    7.  <span data-ttu-id="d0dc8-183">W **lokalnych użytkowników i grup** okno dialogowe, kliknij, aby rozwinąć **użytkowników** folderu.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8.  <span data-ttu-id="d0dc8-184">W okienku po prawej stronie, kliknij dwukrotnie **konta gościa Internet**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="d0dc8-185">W **właściwości** okno dialogowe, kopia nazwa używana jako konto gościa internetowego.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="d0dc8-186">Domyślnie nazwa zaczyna się od "USR_", po której następuje nazwa komputera.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="d0dc8-187">Zamknij okno dialogowe **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="d0dc8-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="d0dc8-188">Zamknij **lokalnych użytkowników i grup** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="d0dc8-189">Zamknij **kont użytkowników** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="d0dc8-190">Zamknij innych **kont użytkowników** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="d0dc8-191">W **servicemodelsamples właściwości** dialogowym **zabezpieczeń** kliknij pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="d0dc8-192">Wpisz nazwę komputera, a następnie ukośnik odwrotny, a następnie wklej nazwę konta użytkownika Internet, na przykład myMachineName\\InternetGuestAccountName %</span><span class="sxs-lookup"><span data-stu-id="d0dc8-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="d0dc8-193">Kliknij przycisk **Sprawdź nazwy** do sprawdzenia poprawności operacji dodawania.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="d0dc8-194">Jeśli jest on prawidłowy, nazwa jest wpisany tylko wielkimi literami i jest podkreślony.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5.  <span data-ttu-id="d0dc8-195">Dla usług IIS 6.0 również Sprawdź, czy Usługa sieciowa znajduje się w **nazwy grupy lub użytkownika** pole.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="d0dc8-196">Jeśli usługa sieciowa nie ma na liście:</span><span class="sxs-lookup"><span data-stu-id="d0dc8-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1.  <span data-ttu-id="d0dc8-197">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-197">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="d0dc8-198">W **Wybieranie użytkowników lub grup** okno dialogowe, wpisz nazwę komputera, a następnie znakiem ukośnika odwrotnego.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3.  <span data-ttu-id="d0dc8-199">Typ **usługi** po ukośniku odwrotnym (bez spacji).</span><span class="sxs-lookup"><span data-stu-id="d0dc8-199">Type **service** after the backslash (no space).</span></span>  
  
    4.  <span data-ttu-id="d0dc8-200">Kliknij przycisk **Sprawdź nazwy**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-200">Click **Check names**.</span></span>  
  
    5.  <span data-ttu-id="d0dc8-201">Jeśli zostaną znalezione wiele nazw, zaznacz **Usługa sieciowa** i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6.  <span data-ttu-id="d0dc8-202">Kliknij przycisk **OK** zamknąć **Wybieranie użytkowników lub grup** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6.  <span data-ttu-id="d0dc8-203">Jeśli usługi IIS 5.1 za pomocą Windows XP z dodatkiem SP2, sprawdź, liście zarówno konta gościa Internet, jak i ASPNET **nazwy grupy lub użytkownika** pole.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="d0dc8-204">Należy pamiętać, że użytkownik ASPNET może być członkiem wbudowanej **użytkowników** grupy zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="d0dc8-205">Jeśli tak, a w przypadku **użytkowników** grupy znajduje się w oknie dialogowym, nie trzeba go dodać jako osobny element do listy dozwolonych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="d0dc8-206">Aby sprawdzić, czy ASPNET jest częścią **użytkowników** grupy zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="d0dc8-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1.  <span data-ttu-id="d0dc8-207">Na **Start** menu, kliknij przycisk **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="d0dc8-208">Kliknij przycisk **kont użytkowników** ikony.</span><span class="sxs-lookup"><span data-stu-id="d0dc8-208">Click the **User Accounts** icon.</span></span>  
  
    3.  <span data-ttu-id="d0dc8-209">W **grupy** kolumny, sprawdź, czy wartość **ASPNET** jest "Użytkownicy".</span><span class="sxs-lookup"><span data-stu-id="d0dc8-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0dc8-210">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0dc8-210">See also</span></span>
- [<span data-ttu-id="d0dc8-211">Instrukcje dotyczące hostowania internetowej usługi informacyjnej</span><span class="sxs-lookup"><span data-stu-id="d0dc8-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
