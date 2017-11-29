---
title: "Instrukcje dotyczące konfigurowania katalogów wirtualnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
caps.latest.revision: "36"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b727f391abfeb1112de1b6cde3ceb564d3860974
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="5378f-102">Instrukcje dotyczące konfigurowania katalogów wirtualnych</span><span class="sxs-lookup"><span data-stu-id="5378f-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="5378f-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Będą udostępniać wspólnej katalog wirtualny o nazwie servicemodelsamples, który jest zamapowany na %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder próbek.</span><span class="sxs-lookup"><span data-stu-id="5378f-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5378f-104">Dysk % SystemDrive % jest zwykle C: i D:, w zależności od lokalizacji dysku, na którym zainstalowano usługi Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="5378f-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="5378f-105">Możesz uruchamiać pliki Setupvroot.bat i Cleanupvroot.bat z [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) można utworzyć katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="5378f-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="5378f-106">Jeśli wolisz ręcznie utworzyć katalogu wirtualnego, należy użyć poniższych procedur.</span><span class="sxs-lookup"><span data-stu-id="5378f-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="5378f-107">Procedury</span><span class="sxs-lookup"><span data-stu-id="5378f-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="5378f-108">Można utworzyć katalogu wirtualnego w usługach IIS 7.0 lub 7.5</span><span class="sxs-lookup"><span data-stu-id="5378f-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="5378f-109">Z **Start** menu, kliknij przycisk **Uruchom**, wpisz **inetmgr** do otwierania przystawki MMC usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="5378f-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="5378f-110">W okienku po lewej stronie rozwiń węzeł z nazwą komputera, a następnie rozwiń **witryny** węzła.</span><span class="sxs-lookup"><span data-stu-id="5378f-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3.  <span data-ttu-id="5378f-111">Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web**, a następnie wybierz **Dodawanie aplikacji** otworzyć **okno Dodawanie aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="5378f-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4.  <span data-ttu-id="5378f-112">W oknie wpisz `servicemodelsamples` jako alias katalogu wirtualnego, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="5378f-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="5378f-113">Utworzyć następującego katalogu: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="5378f-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6.  <span data-ttu-id="5378f-114">Ustaw ścieżkę fizyczną % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="5378f-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="5378f-115">Większość przykładów WCF skopiuj pliki wykonywalne usługi do tej lokalizacji, podczas tworzenia.</span><span class="sxs-lookup"><span data-stu-id="5378f-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7.  <span data-ttu-id="5378f-116">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="5378f-116">Click **OK**.</span></span> <span data-ttu-id="5378f-117">Aplikacja sieci Web został utworzony dla przykładów WCF.</span><span class="sxs-lookup"><span data-stu-id="5378f-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5378f-118">To zadanie należy wykonać tylko raz, ponieważ wszystkie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przykłady użycia servicemodelsamples tej samej aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5378f-118">This task must be performed only once, because all of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5378f-119">Na potrzeby tej dokumentacji termin `virtual directory` CGI `Web application`.</span><span class="sxs-lookup"><span data-stu-id="5378f-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="5378f-120">Oprócz tworzenia katalogu wirtualnego, należy także ustawić jej właściwości w celu włączenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] działanie usług.</span><span class="sxs-lookup"><span data-stu-id="5378f-120">In addition to creating the virtual directory, you must also set its properties to enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to run.</span></span> <span data-ttu-id="5378f-121">Aby uzyskać więcej informacji, zobacz poniżej.</span><span class="sxs-lookup"><span data-stu-id="5378f-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="5378f-122">Można utworzyć katalogu wirtualnego w wersji 5.1 usług IIS lub 6.0</span><span class="sxs-lookup"><span data-stu-id="5378f-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="5378f-123">Otwórz okno wiersza polecenia i wpisz `start inetmgr` do otwierania przystawki MMC usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="5378f-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="5378f-124">W okienku po lewej stronie rozwiń węzeł z nazwą komputera, a następnie rozwiń **witryn sieci Web** węzła.</span><span class="sxs-lookup"><span data-stu-id="5378f-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3.  <span data-ttu-id="5378f-125">Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** i wybierz **nowe, katalog wirtualny** aby otworzyć Kreatora tworzenia katalogów wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="5378f-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4.  <span data-ttu-id="5378f-126">W kreatorze wpisz `servicemodelsamples` jako alias katalogu wirtualnego, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="5378f-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="5378f-127">Ustaw ścieżkę na % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="5378f-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="5378f-128">Większość [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przykłady skopiuj pliki wykonywalne usługi do tej lokalizacji, podczas tworzenia.</span><span class="sxs-lookup"><span data-stu-id="5378f-128">Most of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples copy service executable files to this location when built.</span></span>  
  
6.  <span data-ttu-id="5378f-129">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="5378f-129">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="5378f-130">Domyślnie wybrane są następujące pola wyboru:</span><span class="sxs-lookup"><span data-stu-id="5378f-130">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="5378f-131">**Odczyt**</span><span class="sxs-lookup"><span data-stu-id="5378f-131">**Read**</span></span>  
  
    -   <span data-ttu-id="5378f-132">**Uruchamianie skryptów (np.)**</span><span class="sxs-lookup"><span data-stu-id="5378f-132">**Run scripts (such as ASP)**</span></span>  
  
8.  <span data-ttu-id="5378f-133">Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ** aby zakończyć pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="5378f-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5378f-134">To zadanie należy wykonać tylko raz. ponieważ wszystkie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przykłady użyć tego samego servicemodelsamples katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="5378f-134">This task must be performed only once because all of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="5378f-135">Aby ustawić właściwości dodatkowe katalogu wirtualnego w usługach IIS 7.0 lub 7.5</span><span class="sxs-lookup"><span data-stu-id="5378f-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="5378f-136">Kliknij węzeł servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="5378f-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="5378f-137">Wzdłuż dolnej części okna wyświetlane są dwa widoki.</span><span class="sxs-lookup"><span data-stu-id="5378f-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="5378f-138">Wybierz **widoku funkcji** Jeśli nie została jeszcze wybrana.</span><span class="sxs-lookup"><span data-stu-id="5378f-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2.  <span data-ttu-id="5378f-139">Kliknij dwukrotnie pozycję **przeglądanie katalogów**.</span><span class="sxs-lookup"><span data-stu-id="5378f-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3.  <span data-ttu-id="5378f-140">W okienku Akcje, wybierz **włączyć** opcji.</span><span class="sxs-lookup"><span data-stu-id="5378f-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="5378f-141">Dzięki temu można uzyskać dostępu do katalogu katalogu przy użyciu programu Internet Explorer, która pomaga w przypadku debugowania usługi.</span><span class="sxs-lookup"><span data-stu-id="5378f-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="5378f-142">Ponadto należy ustawić właściwości zabezpieczeń folderu servicemodelsamples, aby zezwolić na dostęp do innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="5378f-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="5378f-143">Aby uzyskać więcej informacji, zobacz poniżej.</span><span class="sxs-lookup"><span data-stu-id="5378f-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="5378f-144">Aby ustawić właściwości dodatkowe katalogu wirtualnego w wersji 5.1 usług IIS lub 6.0</span><span class="sxs-lookup"><span data-stu-id="5378f-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="5378f-145">Kliknij prawym przyciskiem myszy węzeł servicemodelsamples, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5378f-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="5378f-146">Domyślnie wybrane są następujące pola wyboru:</span><span class="sxs-lookup"><span data-stu-id="5378f-146">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="5378f-147">**Odczyt**</span><span class="sxs-lookup"><span data-stu-id="5378f-147">**Read**</span></span>  
  
    -   <span data-ttu-id="5378f-148">**Odwiedza dziennika**</span><span class="sxs-lookup"><span data-stu-id="5378f-148">**Log visits**</span></span>  
  
    -   <span data-ttu-id="5378f-149">**Tego zasobu**</span><span class="sxs-lookup"><span data-stu-id="5378f-149">**Index this resource**</span></span>  
  
3.  <span data-ttu-id="5378f-150">Wybierz **przeglądanie katalogów** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="5378f-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="5378f-151">Dzięki temu można uzyskać dostępu do katalogu katalogu przy użyciu programu Internet Explorer, która pomaga w przypadku debugowania usługi.</span><span class="sxs-lookup"><span data-stu-id="5378f-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="5378f-152">Aby ustawić właściwości zabezpieczeń folderu w usługach IIS 7.0 lub 7.5</span><span class="sxs-lookup"><span data-stu-id="5378f-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="5378f-153">Przejdź do % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="5378f-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="5378f-154">Kliknij prawym przyciskiem myszy servicemodelsamples folder, a następnie kliknij przycisk **udziału** lub **udziału z**.</span><span class="sxs-lookup"><span data-stu-id="5378f-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3.  <span data-ttu-id="5378f-155">Kliknij strzałkę w dół do lewej strony **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5378f-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4.  <span data-ttu-id="5378f-156">Wybierz **znaleźć** wpisu.</span><span class="sxs-lookup"><span data-stu-id="5378f-156">Select the **Find** entry.</span></span> <span data-ttu-id="5378f-157">**Wybieranie użytkowników lub grup** zostanie otwarte okno.</span><span class="sxs-lookup"><span data-stu-id="5378f-157">The **Select Users or Groups** window opens.</span></span>  
  
5.  <span data-ttu-id="5378f-158">Kliknij przycisk **zaawansowane**.</span><span class="sxs-lookup"><span data-stu-id="5378f-158">Click **Advanced**.</span></span>  
  
6.  <span data-ttu-id="5378f-159">Kliknij przycisk **lokalizacje**.</span><span class="sxs-lookup"><span data-stu-id="5378f-159">Click **Locations**.</span></span> <span data-ttu-id="5378f-160">**Lokalizacje** okno jest już otwarty.</span><span class="sxs-lookup"><span data-stu-id="5378f-160">The **Locations** window is now open.</span></span>  
  
7.  <span data-ttu-id="5378f-161">Zaznacz wpis dla używanego komputera.</span><span class="sxs-lookup"><span data-stu-id="5378f-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="5378f-162">Należy wybrać komputer lokalny i nie wpis dla wszystkich domen lub sieci wyświetlanych na liście.</span><span class="sxs-lookup"><span data-stu-id="5378f-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="5378f-163">Po wybraniu komputera, kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="5378f-163">After you have selected the computer, click **OK**.</span></span>  
  
8.  <span data-ttu-id="5378f-164">Kliknij przycisk **Znajdź teraz**.</span><span class="sxs-lookup"><span data-stu-id="5378f-164">Click **Find Now**.</span></span> <span data-ttu-id="5378f-165">Spowoduje to wypełnienie wyniki wyszukiwania z obiektów skojarzonych z komputerem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="5378f-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="5378f-166">Znajdź **IIS_IUSRS** wpis w **Name (nazwa wyróżniająca względną)** kolumny.</span><span class="sxs-lookup"><span data-stu-id="5378f-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="5378f-167">Wybierz ten wpis i kliknij przycisk **OK** okno wyników aby zamknąć wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="5378f-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="5378f-168">Kliknij przycisk **OK** zamknąć **Wybieranie użytkowników lub grup** okna.</span><span class="sxs-lookup"><span data-stu-id="5378f-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="5378f-169">Kliknij przycisk **udziału** aby utrwalić zmiany.</span><span class="sxs-lookup"><span data-stu-id="5378f-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="5378f-170">Po zakończeniu wprowadzania zmian, aby włączyć udostępnianie, kliknij przycisk **gotowe** zamknąć **udostępniania plików** okna.</span><span class="sxs-lookup"><span data-stu-id="5378f-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="5378f-171">Aby ustawić właściwości zabezpieczeń folderu w wersji 5.1 usług IIS lub 6.0</span><span class="sxs-lookup"><span data-stu-id="5378f-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="5378f-172">Przejdź do % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="5378f-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="5378f-173">Kliknij prawym przyciskiem myszy **servicemodelsamples** folder, a następnie kliknij przycisk **udostępnianie i zabezpieczenia.**</span><span class="sxs-lookup"><span data-stu-id="5378f-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3.  <span data-ttu-id="5378f-174">Kliknij przycisk **zabezpieczeń** kartę.</span><span class="sxs-lookup"><span data-stu-id="5378f-174">Click the **Security** tab.</span></span>  
  
4.  <span data-ttu-id="5378f-175">Jeśli korzystasz z usług IIS 6.0, w **nazwy grup lub użytkowników** zaznacz pole wyboru czy **konta gościa Internet** ma na liście.</span><span class="sxs-lookup"><span data-stu-id="5378f-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="5378f-176">Jeśli nie ma na liście:</span><span class="sxs-lookup"><span data-stu-id="5378f-176">If it is not listed:</span></span>  
  
    1.  <span data-ttu-id="5378f-177">Kliknij przycisk **Start** , a następnie kliknij przycisk **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="5378f-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="5378f-178">Jeśli nie widzisz **kont użytkowników** ikony, kliknij przycisk **Przełącz do widoku kategorii**.</span><span class="sxs-lookup"><span data-stu-id="5378f-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3.  <span data-ttu-id="5378f-179">Kliknij przycisk **kont użytkowników** ikony.</span><span class="sxs-lookup"><span data-stu-id="5378f-179">Click the **User Accounts** icon.</span></span>  
  
    4.  <span data-ttu-id="5378f-180">W obszarze "lub wybierz ikonę Panelu sterowania," kliknij **kont użytkowników**.</span><span class="sxs-lookup"><span data-stu-id="5378f-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5.  <span data-ttu-id="5378f-181">W **kont użytkowników** okno dialogowe, kliknij przycisk **zaawansowane** kartę.</span><span class="sxs-lookup"><span data-stu-id="5378f-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6.  <span data-ttu-id="5378f-182">Kliknij przycisk **zaawansowane**.</span><span class="sxs-lookup"><span data-stu-id="5378f-182">Click **Advanced**.</span></span>  
  
    7.  <span data-ttu-id="5378f-183">W **lokalnych użytkowników i grup** okno dialogowe, kliknij, aby rozwinąć **użytkowników** folderu.</span><span class="sxs-lookup"><span data-stu-id="5378f-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8.  <span data-ttu-id="5378f-184">W prawym okienku kliknij dwukrotnie **konta gościa Internet**.</span><span class="sxs-lookup"><span data-stu-id="5378f-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="5378f-185">W **właściwości** okno dialogowe, kopiowania nazwę używane jako konto gościa Internet.</span><span class="sxs-lookup"><span data-stu-id="5378f-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="5378f-186">Domyślnie nazwa rozpoczyna się od "USR_", po której następuje nazwa komputera.</span><span class="sxs-lookup"><span data-stu-id="5378f-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="5378f-187">Zamknij okno dialogowe **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="5378f-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="5378f-188">Zamknij **lokalnych użytkowników i grup** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5378f-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="5378f-189">Zamknij **kont użytkowników** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5378f-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="5378f-190">Zamknij innych **kont użytkowników** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5378f-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="5378f-191">W **servicemodelsamples właściwości** na okna dialogowego **zabezpieczeń** , kliknij pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="5378f-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="5378f-192">Wpisz nazwę komputera, a następnie ukośnik odwrotny, a następnie wklej nazwę konta użytkownika, Internet, na przykład myMachineName\\InternetGuestAccountName %</span><span class="sxs-lookup"><span data-stu-id="5378f-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="5378f-193">Kliknij przycisk **Sprawdź nazwy** można zweryfikować operacji dodawania.</span><span class="sxs-lookup"><span data-stu-id="5378f-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="5378f-194">Jeśli jest on prawidłowy, nazwa jest wielkimi literami i podkreślony.</span><span class="sxs-lookup"><span data-stu-id="5378f-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5.  <span data-ttu-id="5378f-195">Dla usług IIS 6.0, również sprawdzić, czy Usługa sieciowa ma na liście **nazwy grup lub użytkowników** pole.</span><span class="sxs-lookup"><span data-stu-id="5378f-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="5378f-196">Jeśli usługa sieciowa nie ma na liście:</span><span class="sxs-lookup"><span data-stu-id="5378f-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1.  <span data-ttu-id="5378f-197">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="5378f-197">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="5378f-198">W **Wybieranie użytkowników lub grup** okno dialogowe, wpisz nazwę komputera, a następnie ukośnik odwrotny.</span><span class="sxs-lookup"><span data-stu-id="5378f-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3.  <span data-ttu-id="5378f-199">Typ **usługi** po ukośniku odwrotnym (bez spacji).</span><span class="sxs-lookup"><span data-stu-id="5378f-199">Type **service** after the backslash (no space).</span></span>  
  
    4.  <span data-ttu-id="5378f-200">Kliknij przycisk **Sprawdź nazwy**.</span><span class="sxs-lookup"><span data-stu-id="5378f-200">Click **Check names**.</span></span>  
  
    5.  <span data-ttu-id="5378f-201">W przypadku odnalezienia wielu nazw wybierz **usługi SIECIOWEJ** i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="5378f-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6.  <span data-ttu-id="5378f-202">Kliknij przycisk **OK** zamknąć **Wybieranie użytkowników lub grup** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5378f-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6.  <span data-ttu-id="5378f-203">Jeśli używasz systemu Windows XP z dodatkiem SP2 z wersji 5.1 usług IIS, sprawdź, czy zarówno konta gościa Internet i ASPNET są wymieniony w **nazwy grup lub użytkowników** pole.</span><span class="sxs-lookup"><span data-stu-id="5378f-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="5378f-204">Należy pamiętać, że użytkownik ASPNET może należeć do wbudowanych **użytkowników** grupy zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5378f-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="5378f-205">Jeśli tak, jeśli następnie **użytkowników** grupy znajduje się w oknie dialogowym, ale nie trzeba go dodać jako osobny element do listy dozwolonych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="5378f-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="5378f-206">Aby sprawdzić, czy ASPNET jest częścią **użytkowników** grupy zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="5378f-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1.  <span data-ttu-id="5378f-207">Na **Start** menu, kliknij przycisk **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="5378f-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="5378f-208">Kliknij przycisk **kont użytkowników** ikony.</span><span class="sxs-lookup"><span data-stu-id="5378f-208">Click the **User Accounts** icon.</span></span>  
  
    3.  <span data-ttu-id="5378f-209">W **grupy** kolumny, sprawdź, czy wartość **ASPNET** jest "Użytkownicy".</span><span class="sxs-lookup"><span data-stu-id="5378f-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5378f-210">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5378f-210">See Also</span></span>  
 [<span data-ttu-id="5378f-211">Informacje o usługi instrukcje dotyczące hostowania internetowej</span><span class="sxs-lookup"><span data-stu-id="5378f-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
