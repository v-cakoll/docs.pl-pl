---
title: Instrukcje dotyczące konfigurowania katalogów wirtualnych
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: 3ff578b69590071ef2135e777b3105e7c226563e
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806916"
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="aeeeb-102">Instrukcje dotyczące konfigurowania katalogów wirtualnych</span><span class="sxs-lookup"><span data-stu-id="aeeeb-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="aeeeb-103">Przykłady Windows Communication Foundation (WCF) będą udostępniać wspólnej katalog wirtualny o nazwie servicemodelsamples, który jest zamapowany na %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-103">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aeeeb-104">Dysk % SystemDrive % jest zwykle C: i D:, w zależności od lokalizacji dysku, na którym zainstalowano usługi Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="aeeeb-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="aeeeb-105">Możesz uruchamiać pliki Setupvroot.bat i Cleanupvroot.bat z [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) można utworzyć katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="aeeeb-106">Jeśli wolisz ręcznie utworzyć katalogu wirtualnego, należy użyć poniższych procedur.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="aeeeb-107">Procedury</span><span class="sxs-lookup"><span data-stu-id="aeeeb-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="aeeeb-108">Można utworzyć katalogu wirtualnego w usługach IIS 7.0 lub 7.5</span><span class="sxs-lookup"><span data-stu-id="aeeeb-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="aeeeb-109">Z **Start** menu, kliknij przycisk **Uruchom**, wpisz **inetmgr** do otwierania przystawki MMC usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="aeeeb-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="aeeeb-110">W okienku po lewej stronie rozwiń węzeł z nazwą komputera, a następnie rozwiń **witryny** węzła.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3.  <span data-ttu-id="aeeeb-111">Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web**, a następnie wybierz **Dodawanie aplikacji** otworzyć **okno Dodawanie aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4.  <span data-ttu-id="aeeeb-112">W oknie wpisz `servicemodelsamples` jako alias katalogu wirtualnego, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="aeeeb-113">Utworzyć następującego katalogu: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="aeeeb-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6.  <span data-ttu-id="aeeeb-114">Ustaw ścieżkę fizyczną % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="aeeeb-115">Większość przykładów WCF skopiuj pliki wykonywalne usługi do tej lokalizacji, podczas tworzenia.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7.  <span data-ttu-id="aeeeb-116">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-116">Click **OK**.</span></span> <span data-ttu-id="aeeeb-117">Aplikacja sieci Web został utworzony dla przykładów WCF.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aeeeb-118">To zadanie można wykonać tylko raz, ponieważ wszystkie przykłady WCF używają tego samego servicemodelsamples aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-118">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aeeeb-119">Na potrzeby tej dokumentacji termin `virtual directory` CGI `Web application`.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="aeeeb-120">Oprócz tworzenia katalogu wirtualnego, należy także ustawić jego właściwości, aby umożliwić działanie usług WCF.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-120">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="aeeeb-121">Aby uzyskać więcej informacji, zobacz poniżej.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="aeeeb-122">Można utworzyć katalogu wirtualnego w wersji 5.1 usług IIS lub 6.0</span><span class="sxs-lookup"><span data-stu-id="aeeeb-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="aeeeb-123">Otwórz okno wiersza polecenia i wpisz `start inetmgr` do otwierania przystawki MMC usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="aeeeb-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="aeeeb-124">W okienku po lewej stronie rozwiń węzeł z nazwą komputera, a następnie rozwiń **witryn sieci Web** węzła.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3.  <span data-ttu-id="aeeeb-125">Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** i wybierz **nowe, katalog wirtualny** aby otworzyć Kreatora tworzenia katalogów wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4.  <span data-ttu-id="aeeeb-126">W kreatorze wpisz `servicemodelsamples` jako alias katalogu wirtualnego, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="aeeeb-127">Ustaw ścieżkę na % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="aeeeb-128">Większość przykładów WCF skopiuj pliki wykonywalne usługi do tej lokalizacji, podczas tworzenia.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-128">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6.  <span data-ttu-id="aeeeb-129">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-129">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="aeeeb-130">Domyślnie wybrane są następujące pola wyboru:</span><span class="sxs-lookup"><span data-stu-id="aeeeb-130">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="aeeeb-131">**Odczyt**</span><span class="sxs-lookup"><span data-stu-id="aeeeb-131">**Read**</span></span>  
  
    -   <span data-ttu-id="aeeeb-132">**Uruchamianie skryptów (np.)**</span><span class="sxs-lookup"><span data-stu-id="aeeeb-132">**Run scripts (such as ASP)**</span></span>  
  
8.  <span data-ttu-id="aeeeb-133">Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ** aby zakończyć pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aeeeb-134">To zadanie należy wykonać tylko raz, ponieważ przykłady WCF używają tego samego servicemodelsamples katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-134">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="aeeeb-135">Aby ustawić właściwości dodatkowe katalogu wirtualnego w usługach IIS 7.0 lub 7.5</span><span class="sxs-lookup"><span data-stu-id="aeeeb-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="aeeeb-136">Kliknij węzeł servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="aeeeb-137">Wzdłuż dolnej części okna wyświetlane są dwa widoki.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="aeeeb-138">Wybierz **widoku funkcji** Jeśli nie została jeszcze wybrana.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2.  <span data-ttu-id="aeeeb-139">Kliknij dwukrotnie pozycję **przeglądanie katalogów**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3.  <span data-ttu-id="aeeeb-140">W okienku Akcje, wybierz **włączyć** opcji.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="aeeeb-141">Dzięki temu można uzyskać dostępu do katalogu katalogu przy użyciu programu Internet Explorer, która pomaga w przypadku debugowania usługi.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="aeeeb-142">Ponadto należy ustawić właściwości zabezpieczeń folderu servicemodelsamples, aby zezwolić na dostęp do innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="aeeeb-143">Aby uzyskać więcej informacji, zobacz poniżej.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="aeeeb-144">Aby ustawić właściwości dodatkowe katalogu wirtualnego w wersji 5.1 usług IIS lub 6.0</span><span class="sxs-lookup"><span data-stu-id="aeeeb-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="aeeeb-145">Kliknij prawym przyciskiem myszy węzeł servicemodelsamples, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="aeeeb-146">Domyślnie wybrane są następujące pola wyboru:</span><span class="sxs-lookup"><span data-stu-id="aeeeb-146">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="aeeeb-147">**Odczyt**</span><span class="sxs-lookup"><span data-stu-id="aeeeb-147">**Read**</span></span>  
  
    -   <span data-ttu-id="aeeeb-148">**Odwiedza dziennika**</span><span class="sxs-lookup"><span data-stu-id="aeeeb-148">**Log visits**</span></span>  
  
    -   <span data-ttu-id="aeeeb-149">**Tego zasobu**</span><span class="sxs-lookup"><span data-stu-id="aeeeb-149">**Index this resource**</span></span>  
  
3.  <span data-ttu-id="aeeeb-150">Wybierz **przeglądanie katalogów** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="aeeeb-151">Dzięki temu można uzyskać dostępu do katalogu katalogu przy użyciu programu Internet Explorer, która pomaga w przypadku debugowania usługi.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="aeeeb-152">Aby ustawić właściwości zabezpieczeń folderu w usługach IIS 7.0 lub 7.5</span><span class="sxs-lookup"><span data-stu-id="aeeeb-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="aeeeb-153">Przejdź do % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="aeeeb-154">Kliknij prawym przyciskiem myszy servicemodelsamples folder, a następnie kliknij przycisk **udziału** lub **udziału z**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3.  <span data-ttu-id="aeeeb-155">Kliknij strzałkę w dół do lewej strony **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4.  <span data-ttu-id="aeeeb-156">Wybierz **znaleźć** wpisu.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-156">Select the **Find** entry.</span></span> <span data-ttu-id="aeeeb-157">**Wybieranie użytkowników lub grup** zostanie otwarte okno.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-157">The **Select Users or Groups** window opens.</span></span>  
  
5.  <span data-ttu-id="aeeeb-158">Kliknij przycisk **zaawansowane**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-158">Click **Advanced**.</span></span>  
  
6.  <span data-ttu-id="aeeeb-159">Kliknij przycisk **lokalizacje**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-159">Click **Locations**.</span></span> <span data-ttu-id="aeeeb-160">**Lokalizacje** okno jest już otwarty.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-160">The **Locations** window is now open.</span></span>  
  
7.  <span data-ttu-id="aeeeb-161">Zaznacz wpis dla używanego komputera.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="aeeeb-162">Należy wybrać komputer lokalny i nie wpis dla wszystkich domen lub sieci wyświetlanych na liście.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="aeeeb-163">Po wybraniu komputera, kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-163">After you have selected the computer, click **OK**.</span></span>  
  
8.  <span data-ttu-id="aeeeb-164">Kliknij przycisk **Znajdź teraz**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-164">Click **Find Now**.</span></span> <span data-ttu-id="aeeeb-165">Spowoduje to wypełnienie wyniki wyszukiwania z obiektów skojarzonych z komputerem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="aeeeb-166">Znajdź **IIS_IUSRS** wpis w **Name (nazwa wyróżniająca względną)** kolumny.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="aeeeb-167">Wybierz ten wpis i kliknij przycisk **OK** okno wyników aby zamknąć wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="aeeeb-168">Kliknij przycisk **OK** zamknąć **Wybieranie użytkowników lub grup** okna.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="aeeeb-169">Kliknij przycisk **udziału** aby utrwalić zmiany.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="aeeeb-170">Po zakończeniu wprowadzania zmian, aby włączyć udostępnianie, kliknij przycisk **gotowe** zamknąć **udostępniania plików** okna.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="aeeeb-171">Aby ustawić właściwości zabezpieczeń folderu w wersji 5.1 usług IIS lub 6.0</span><span class="sxs-lookup"><span data-stu-id="aeeeb-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="aeeeb-172">Przejdź do % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="aeeeb-173">Kliknij prawym przyciskiem myszy **servicemodelsamples** folder, a następnie kliknij przycisk **udostępnianie i zabezpieczenia.**</span><span class="sxs-lookup"><span data-stu-id="aeeeb-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3.  <span data-ttu-id="aeeeb-174">Kliknij przycisk **zabezpieczeń** kartę.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-174">Click the **Security** tab.</span></span>  
  
4.  <span data-ttu-id="aeeeb-175">Jeśli korzystasz z usług IIS 6.0, w **nazwy grup lub użytkowników** zaznacz pole wyboru czy **konta gościa Internet** ma na liście.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="aeeeb-176">Jeśli nie ma na liście:</span><span class="sxs-lookup"><span data-stu-id="aeeeb-176">If it is not listed:</span></span>  
  
    1.  <span data-ttu-id="aeeeb-177">Kliknij przycisk **Start** , a następnie kliknij przycisk **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="aeeeb-178">Jeśli nie widzisz **kont użytkowników** ikony, kliknij przycisk **Przełącz do widoku kategorii**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3.  <span data-ttu-id="aeeeb-179">Kliknij przycisk **kont użytkowników** ikony.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-179">Click the **User Accounts** icon.</span></span>  
  
    4.  <span data-ttu-id="aeeeb-180">W obszarze "lub wybierz ikonę Panelu sterowania," kliknij **kont użytkowników**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5.  <span data-ttu-id="aeeeb-181">W **kont użytkowników** okno dialogowe, kliknij przycisk **zaawansowane** kartę.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6.  <span data-ttu-id="aeeeb-182">Kliknij przycisk **zaawansowane**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-182">Click **Advanced**.</span></span>  
  
    7.  <span data-ttu-id="aeeeb-183">W **lokalnych użytkowników i grup** okno dialogowe, kliknij, aby rozwinąć **użytkowników** folderu.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8.  <span data-ttu-id="aeeeb-184">W prawym okienku kliknij dwukrotnie **konta gościa Internet**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="aeeeb-185">W **właściwości** okno dialogowe, kopiowania nazwę używane jako konto gościa Internet.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="aeeeb-186">Domyślnie nazwa rozpoczyna się od "USR_", po której następuje nazwa komputera.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="aeeeb-187">Zamknij okno dialogowe **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="aeeeb-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="aeeeb-188">Zamknij **lokalnych użytkowników i grup** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="aeeeb-189">Zamknij **kont użytkowników** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="aeeeb-190">Zamknij innych **kont użytkowników** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="aeeeb-191">W **servicemodelsamples właściwości** na okna dialogowego **zabezpieczeń** , kliknij pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="aeeeb-192">Wpisz nazwę komputera, a następnie ukośnik odwrotny, a następnie wklej nazwę konta użytkownika, Internet, na przykład myMachineName\\InternetGuestAccountName %</span><span class="sxs-lookup"><span data-stu-id="aeeeb-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="aeeeb-193">Kliknij przycisk **Sprawdź nazwy** można zweryfikować operacji dodawania.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="aeeeb-194">Jeśli jest on prawidłowy, nazwa jest wielkimi literami i podkreślony.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5.  <span data-ttu-id="aeeeb-195">Dla usług IIS 6.0, również sprawdzić, czy Usługa sieciowa ma na liście **nazwy grup lub użytkowników** pole.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="aeeeb-196">Jeśli usługa sieciowa nie ma na liście:</span><span class="sxs-lookup"><span data-stu-id="aeeeb-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1.  <span data-ttu-id="aeeeb-197">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-197">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="aeeeb-198">W **Wybieranie użytkowników lub grup** okno dialogowe, wpisz nazwę komputera, a następnie ukośnik odwrotny.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3.  <span data-ttu-id="aeeeb-199">Typ **usługi** po ukośniku odwrotnym (bez spacji).</span><span class="sxs-lookup"><span data-stu-id="aeeeb-199">Type **service** after the backslash (no space).</span></span>  
  
    4.  <span data-ttu-id="aeeeb-200">Kliknij przycisk **Sprawdź nazwy**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-200">Click **Check names**.</span></span>  
  
    5.  <span data-ttu-id="aeeeb-201">W przypadku odnalezienia wielu nazw wybierz **usługi SIECIOWEJ** i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6.  <span data-ttu-id="aeeeb-202">Kliknij przycisk **OK** zamknąć **Wybieranie użytkowników lub grup** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6.  <span data-ttu-id="aeeeb-203">Jeśli używasz systemu Windows XP z dodatkiem SP2 z wersji 5.1 usług IIS, sprawdź, czy zarówno konta gościa Internet i ASPNET są wymieniony w **nazwy grup lub użytkowników** pole.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="aeeeb-204">Należy pamiętać, że użytkownik ASPNET może należeć do wbudowanych **użytkowników** grupy zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="aeeeb-205">Jeśli tak, jeśli następnie **użytkowników** grupy znajduje się w oknie dialogowym, ale nie trzeba go dodać jako osobny element do listy dozwolonych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="aeeeb-206">Aby sprawdzić, czy ASPNET jest częścią **użytkowników** grupy zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="aeeeb-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1.  <span data-ttu-id="aeeeb-207">Na **Start** menu, kliknij przycisk **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="aeeeb-208">Kliknij przycisk **kont użytkowników** ikony.</span><span class="sxs-lookup"><span data-stu-id="aeeeb-208">Click the **User Accounts** icon.</span></span>  
  
    3.  <span data-ttu-id="aeeeb-209">W **grupy** kolumny, sprawdź, czy wartość **ASPNET** jest "Użytkownicy".</span><span class="sxs-lookup"><span data-stu-id="aeeeb-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeeeb-210">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aeeeb-210">See Also</span></span>  
 [<span data-ttu-id="aeeeb-211">Instrukcje dotyczące hostowania internetowej usługi informacyjnej</span><span class="sxs-lookup"><span data-stu-id="aeeeb-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
