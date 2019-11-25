---
title: Identyfikatory GUID znanych folderów dla niestandardowych miejsc okna dialogowego plików
ms.date: 03/30/2017
helpviewer_keywords:
- Known Folder GUIDs [Windows Forms], Custom Places
- Custom Places [Windows Forms], Known Folder GUIDs
- Windows Vista Known Folder GUIDs [Windows Forms], Custom Places
ms.assetid: d8d8b544-8b4d-4da5-ba3a-b05e93244778
ms.openlocfilehash: 0ae9c406e91bc947ec73bb2393bb05962ca41177
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974353"
---
# <a name="known-folder-guids-for-file-dialog-custom-places"></a><span data-ttu-id="8be5b-102">Identyfikatory GUID znanych folderów dla niestandardowych miejsc okna dialogowego plików</span><span class="sxs-lookup"><span data-stu-id="8be5b-102">Known Folder GUIDs for File Dialog Custom Places</span></span>
<span data-ttu-id="8be5b-103">Aby określić folder, który jest znany w systemie Windows Vista podczas dodawania folderów do kolekcji <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>, należy użyć <xref:System.Guid>.</span><span class="sxs-lookup"><span data-stu-id="8be5b-103">You use a <xref:System.Guid> to specify a Windows Vista Known Folder when you add folders to a <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span> <span data-ttu-id="8be5b-104">W przypadku znanych identyfikatorów GUID folderów nie jest rozróżniana wielkość liter i są one zdefiniowane w pliku KnownFolders. h w Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="8be5b-104">Known Folder GUIDs are not case sensitive and are defined in the KnownFolders.h file in the Windows SDK.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8be5b-105">W niektórych przypadkach znany folder dodany do <xref:System.Windows.Forms.FileDialogCustomPlacesCollection> nie będzie wyświetlany w obszarze **Ulubione linki** .</span><span class="sxs-lookup"><span data-stu-id="8be5b-105">In some cases, a Known Folder added to the <xref:System.Windows.Forms.FileDialogCustomPlacesCollection> will not be shown in the **Favorite Links** area.</span></span> <span data-ttu-id="8be5b-106">Na przykład jeśli określony znany folder nie istnieje na komputerze, na którym jest uruchomiona aplikacja, znany folder nie jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="8be5b-106">For example, if the specified Known Folder is not present on the computer that is running the application, the Known Folder is not shown.</span></span>  
  
## <a name="list-of-guids"></a><span data-ttu-id="8be5b-107">Lista identyfikatorów GUID</span><span class="sxs-lookup"><span data-stu-id="8be5b-107">List of GUIDs</span></span>  
 <span data-ttu-id="8be5b-108">Poniższa tabela zawiera listę znanych folderów systemu Windows Vista i skojarzonych z nimi <xref:System.Guid>.</span><span class="sxs-lookup"><span data-stu-id="8be5b-108">The following table lists Windows Vista Known Folders and their associated <xref:System.Guid>.</span></span>  
  
 <span data-ttu-id="8be5b-109">AddNewPrograms</span><span class="sxs-lookup"><span data-stu-id="8be5b-109">AddNewPrograms</span></span>  
 <span data-ttu-id="8be5b-110">DE61D971-5EBC-4F02-A3A9-6C82895E5C04</span><span class="sxs-lookup"><span data-stu-id="8be5b-110">DE61D971-5EBC-4F02-A3A9-6C82895E5C04</span></span>  
  
 <span data-ttu-id="8be5b-111">AdminTools</span><span class="sxs-lookup"><span data-stu-id="8be5b-111">AdminTools</span></span>  
 <span data-ttu-id="8be5b-112">724EF170-A42D-4FEF-9F26-B60E846FBA4F</span><span class="sxs-lookup"><span data-stu-id="8be5b-112">724EF170-A42D-4FEF-9F26-B60E846FBA4F</span></span>  
  
 <span data-ttu-id="8be5b-113">AppDataLow</span><span class="sxs-lookup"><span data-stu-id="8be5b-113">AppDataLow</span></span>  
 <span data-ttu-id="8be5b-114">A520A1A4-1780-4FF6-BD18-167343C5AF16</span><span class="sxs-lookup"><span data-stu-id="8be5b-114">A520A1A4-1780-4FF6-BD18-167343C5AF16</span></span>  
  
 <span data-ttu-id="8be5b-115">AppUpdates</span><span class="sxs-lookup"><span data-stu-id="8be5b-115">AppUpdates</span></span>  
 <span data-ttu-id="8be5b-116">A305CE99-F527-492B-8B1A-7E76FA98D6E4</span><span class="sxs-lookup"><span data-stu-id="8be5b-116">A305CE99-F527-492B-8B1A-7E76FA98D6E4</span></span>  
  
 <span data-ttu-id="8be5b-117">CDBurning</span><span class="sxs-lookup"><span data-stu-id="8be5b-117">CDBurning</span></span>  
 <span data-ttu-id="8be5b-118">9E52AB10-F80D-49DF-ACB8-4330F5687855</span><span class="sxs-lookup"><span data-stu-id="8be5b-118">9E52AB10-F80D-49DF-ACB8-4330F5687855</span></span>  
  
 <span data-ttu-id="8be5b-119">ChangeRemovePrograms</span><span class="sxs-lookup"><span data-stu-id="8be5b-119">ChangeRemovePrograms</span></span>  
 <span data-ttu-id="8be5b-120">DF7266AC-9274-4867-8D55-3BD661DE872D</span><span class="sxs-lookup"><span data-stu-id="8be5b-120">DF7266AC-9274-4867-8D55-3BD661DE872D</span></span>  
  
 <span data-ttu-id="8be5b-121">CommonAdminTools</span><span class="sxs-lookup"><span data-stu-id="8be5b-121">CommonAdminTools</span></span>  
 <span data-ttu-id="8be5b-122">D0384E7D-BAC3-4797-8F14-CBA229B392B5</span><span class="sxs-lookup"><span data-stu-id="8be5b-122">D0384E7D-BAC3-4797-8F14-CBA229B392B5</span></span>  
  
 <span data-ttu-id="8be5b-123">CommonOEMLinks</span><span class="sxs-lookup"><span data-stu-id="8be5b-123">CommonOEMLinks</span></span>  
 <span data-ttu-id="8be5b-124">C1BAE2D0-10DF-4334-BEDD-7AA20B227A9D</span><span class="sxs-lookup"><span data-stu-id="8be5b-124">C1BAE2D0-10DF-4334-BEDD-7AA20B227A9D</span></span>  
  
 <span data-ttu-id="8be5b-125">CommonPrograms</span><span class="sxs-lookup"><span data-stu-id="8be5b-125">CommonPrograms</span></span>  
 <span data-ttu-id="8be5b-126">0139D44E-6AFE-49F2-8690-3DAFCAE6FFB8</span><span class="sxs-lookup"><span data-stu-id="8be5b-126">0139D44E-6AFE-49F2-8690-3DAFCAE6FFB8</span></span>  
  
 <span data-ttu-id="8be5b-127">CommonStartMenu</span><span class="sxs-lookup"><span data-stu-id="8be5b-127">CommonStartMenu</span></span>  
 <span data-ttu-id="8be5b-128">A4115719-D62E-491D-AA7C-E74B8BE3B067</span><span class="sxs-lookup"><span data-stu-id="8be5b-128">A4115719-D62E-491D-AA7C-E74B8BE3B067</span></span>  
  
 <span data-ttu-id="8be5b-129">CommonStartup</span><span class="sxs-lookup"><span data-stu-id="8be5b-129">CommonStartup</span></span>  
 <span data-ttu-id="8be5b-130">82A5EA35-D9CD-47C5-9629-E15D2F714E6E</span><span class="sxs-lookup"><span data-stu-id="8be5b-130">82A5EA35-D9CD-47C5-9629-E15D2F714E6E</span></span>  
  
 <span data-ttu-id="8be5b-131">CommonTemplates</span><span class="sxs-lookup"><span data-stu-id="8be5b-131">CommonTemplates</span></span>  
 <span data-ttu-id="8be5b-132">B94237E7-57AC-4347-9151-B08C6C32D1F7</span><span class="sxs-lookup"><span data-stu-id="8be5b-132">B94237E7-57AC-4347-9151-B08C6C32D1F7</span></span>  
  
 <span data-ttu-id="8be5b-133">Komputerem</span><span class="sxs-lookup"><span data-stu-id="8be5b-133">Computer</span></span>  
 <span data-ttu-id="8be5b-134">0AC0837C-BBF8-452A-850D-79D08E667CA7</span><span class="sxs-lookup"><span data-stu-id="8be5b-134">0AC0837C-BBF8-452A-850D-79D08E667CA7</span></span>  
  
 <span data-ttu-id="8be5b-135">kolizj</span><span class="sxs-lookup"><span data-stu-id="8be5b-135">Conflict</span></span>  
 <span data-ttu-id="8be5b-136">4BFEFB45-347D-4006-A5BE-AC0CB0567192</span><span class="sxs-lookup"><span data-stu-id="8be5b-136">4BFEFB45-347D-4006-A5BE-AC0CB0567192</span></span>  
  
 <span data-ttu-id="8be5b-137">Połączenia</span><span class="sxs-lookup"><span data-stu-id="8be5b-137">Connections</span></span>  
 <span data-ttu-id="8be5b-138">6F0CD92B-2E97-45D1-88FF-B0D186B8DEDD</span><span class="sxs-lookup"><span data-stu-id="8be5b-138">6F0CD92B-2E97-45D1-88FF-B0D186B8DEDD</span></span>  
  
 <span data-ttu-id="8be5b-139">Kontakty</span><span class="sxs-lookup"><span data-stu-id="8be5b-139">Contacts</span></span>  
 <span data-ttu-id="8be5b-140">56784854-C6CB-462B-8169-88E350ACB882</span><span class="sxs-lookup"><span data-stu-id="8be5b-140">56784854-C6CB-462B-8169-88E350ACB882</span></span>  
  
 <span data-ttu-id="8be5b-141">ControlPanel</span><span class="sxs-lookup"><span data-stu-id="8be5b-141">ControlPanel</span></span>  
 <span data-ttu-id="8be5b-142">82A74AEB-AEB4-465C-A014-D097EE346D63</span><span class="sxs-lookup"><span data-stu-id="8be5b-142">82A74AEB-AEB4-465C-A014-D097EE346D63</span></span>  
  
 <span data-ttu-id="8be5b-143">Cookie</span><span class="sxs-lookup"><span data-stu-id="8be5b-143">Cookies</span></span>  
 <span data-ttu-id="8be5b-144">2B0F765D-C0E9-4171-908E-08A611B84FF6</span><span class="sxs-lookup"><span data-stu-id="8be5b-144">2B0F765D-C0E9-4171-908E-08A611B84FF6</span></span>  
  
 <span data-ttu-id="8be5b-145">Aplikacje klasyczne</span><span class="sxs-lookup"><span data-stu-id="8be5b-145">Desktop</span></span>  
 <span data-ttu-id="8be5b-146">B4BFCC3A-DB2C-424C-B029-7FE99A87C641</span><span class="sxs-lookup"><span data-stu-id="8be5b-146">B4BFCC3A-DB2C-424C-B029-7FE99A87C641</span></span>  
  
 <span data-ttu-id="8be5b-147">Dokumenty</span><span class="sxs-lookup"><span data-stu-id="8be5b-147">Documents</span></span>  
 <span data-ttu-id="8be5b-148">FDD39AD0-238F-46AF-ADB4-6C85480369C7</span><span class="sxs-lookup"><span data-stu-id="8be5b-148">FDD39AD0-238F-46AF-ADB4-6C85480369C7</span></span>  
  
 <span data-ttu-id="8be5b-149">Pliki do pobrania</span><span class="sxs-lookup"><span data-stu-id="8be5b-149">Downloads</span></span>  
 <span data-ttu-id="8be5b-150">374DE290-123F-4565-9164-39C4925E467B</span><span class="sxs-lookup"><span data-stu-id="8be5b-150">374DE290-123F-4565-9164-39C4925E467B</span></span>  
  
 <span data-ttu-id="8be5b-151">Ulubiony</span><span class="sxs-lookup"><span data-stu-id="8be5b-151">Favorites</span></span>  
 <span data-ttu-id="8be5b-152">1777F761-68AD-4D8A-87BD-30B759FA33DD</span><span class="sxs-lookup"><span data-stu-id="8be5b-152">1777F761-68AD-4D8A-87BD-30B759FA33DD</span></span>  
  
 <span data-ttu-id="8be5b-153">Czcionki</span><span class="sxs-lookup"><span data-stu-id="8be5b-153">Fonts</span></span>  
 <span data-ttu-id="8be5b-154">FD228CB7-AE11-4AE3-864C-16F3910AB8FE</span><span class="sxs-lookup"><span data-stu-id="8be5b-154">FD228CB7-AE11-4AE3-864C-16F3910AB8FE</span></span>  
  
 <span data-ttu-id="8be5b-155">Zainstalowane</span><span class="sxs-lookup"><span data-stu-id="8be5b-155">Games</span></span>  
 <span data-ttu-id="8be5b-156">CAC52C1A-B53D-4EDC-92D7-6B2E8AC19434</span><span class="sxs-lookup"><span data-stu-id="8be5b-156">CAC52C1A-B53D-4EDC-92D7-6B2E8AC19434</span></span>  
  
 <span data-ttu-id="8be5b-157">GameTasks</span><span class="sxs-lookup"><span data-stu-id="8be5b-157">GameTasks</span></span>  
 <span data-ttu-id="8be5b-158">054FAE61-4DD8-4787-80B6-090220C4B700</span><span class="sxs-lookup"><span data-stu-id="8be5b-158">054FAE61-4DD8-4787-80B6-090220C4B700</span></span>  
  
 <span data-ttu-id="8be5b-159">Historia</span><span class="sxs-lookup"><span data-stu-id="8be5b-159">History</span></span>  
 <span data-ttu-id="8be5b-160">D9DC8A3B-B784-432E-A781-5A1130A75963</span><span class="sxs-lookup"><span data-stu-id="8be5b-160">D9DC8A3B-B784-432E-A781-5A1130A75963</span></span>  
  
 <span data-ttu-id="8be5b-161">Internet</span><span class="sxs-lookup"><span data-stu-id="8be5b-161">Internet</span></span>  
 <span data-ttu-id="8be5b-162">4D9F7874-4E0C-4904-967B-40B0D20C3E4B</span><span class="sxs-lookup"><span data-stu-id="8be5b-162">4D9F7874-4E0C-4904-967B-40B0D20C3E4B</span></span>  
  
 <span data-ttu-id="8be5b-163">InternetCache</span><span class="sxs-lookup"><span data-stu-id="8be5b-163">InternetCache</span></span>  
 <span data-ttu-id="8be5b-164">352481E8-33BE-4251-BA85-6007CAEDCF9D</span><span class="sxs-lookup"><span data-stu-id="8be5b-164">352481E8-33BE-4251-BA85-6007CAEDCF9D</span></span>  
  
 <span data-ttu-id="8be5b-165">Łącza</span><span class="sxs-lookup"><span data-stu-id="8be5b-165">Links</span></span>  
 <span data-ttu-id="8be5b-166">BFB9D5E0-C6A9-404C-B2B2-AE6DB6AF4968</span><span class="sxs-lookup"><span data-stu-id="8be5b-166">BFB9D5E0-C6A9-404C-B2B2-AE6DB6AF4968</span></span>  
  
 <span data-ttu-id="8be5b-167">LocalAppData</span><span class="sxs-lookup"><span data-stu-id="8be5b-167">LocalAppData</span></span>  
 <span data-ttu-id="8be5b-168">F1B32785-6FBA-4FCF-9D55-7B8E7F157091</span><span class="sxs-lookup"><span data-stu-id="8be5b-168">F1B32785-6FBA-4FCF-9D55-7B8E7F157091</span></span>  
  
 <span data-ttu-id="8be5b-169">LocalizedResourcesDir</span><span class="sxs-lookup"><span data-stu-id="8be5b-169">LocalizedResourcesDir</span></span>  
 <span data-ttu-id="8be5b-170">2A00375E-224C-49DE-B8D1-440DF7EF3DDC</span><span class="sxs-lookup"><span data-stu-id="8be5b-170">2A00375E-224C-49DE-B8D1-440DF7EF3DDC</span></span>  
  
 <span data-ttu-id="8be5b-171">Muzyk</span><span class="sxs-lookup"><span data-stu-id="8be5b-171">Music</span></span>  
 <span data-ttu-id="8be5b-172">4BD8D571-6D19-48D3-BE97-422220080E43</span><span class="sxs-lookup"><span data-stu-id="8be5b-172">4BD8D571-6D19-48D3-BE97-422220080E43</span></span>  
  
 <span data-ttu-id="8be5b-173">Okap</span><span class="sxs-lookup"><span data-stu-id="8be5b-173">NetHood</span></span>  
 <span data-ttu-id="8be5b-174">C5ABBF53-E17F-4121-8900-86626FC2C973</span><span class="sxs-lookup"><span data-stu-id="8be5b-174">C5ABBF53-E17F-4121-8900-86626FC2C973</span></span>  
  
 <span data-ttu-id="8be5b-175">Sieć</span><span class="sxs-lookup"><span data-stu-id="8be5b-175">Network</span></span>  
 <span data-ttu-id="8be5b-176">D20BEEC4-5CA8-4905-AE3B-BF251EA09B53</span><span class="sxs-lookup"><span data-stu-id="8be5b-176">D20BEEC4-5CA8-4905-AE3B-BF251EA09B53</span></span>  
  
 <span data-ttu-id="8be5b-177">OriginalImages</span><span class="sxs-lookup"><span data-stu-id="8be5b-177">OriginalImages</span></span>  
 <span data-ttu-id="8be5b-178">2C36C0AA-5812-4B87-BFD0-4CD0DFB19B39</span><span class="sxs-lookup"><span data-stu-id="8be5b-178">2C36C0AA-5812-4B87-BFD0-4CD0DFB19B39</span></span>  
  
 <span data-ttu-id="8be5b-179">Albumy</span><span class="sxs-lookup"><span data-stu-id="8be5b-179">PhotoAlbums</span></span>  
 <span data-ttu-id="8be5b-180">69D2CF90-FC33-4FB7-9A0C-EBB0F0FCB43C</span><span class="sxs-lookup"><span data-stu-id="8be5b-180">69D2CF90-FC33-4FB7-9A0C-EBB0F0FCB43C</span></span>  
  
 <span data-ttu-id="8be5b-181">Obrazki</span><span class="sxs-lookup"><span data-stu-id="8be5b-181">Pictures</span></span>  
 <span data-ttu-id="8be5b-182">33E28130-4E1E-4676-835A-98395C3BC3BB</span><span class="sxs-lookup"><span data-stu-id="8be5b-182">33E28130-4E1E-4676-835A-98395C3BC3BB</span></span>  
  
 <span data-ttu-id="8be5b-183">Wybrane</span><span class="sxs-lookup"><span data-stu-id="8be5b-183">Playlists</span></span>  
 <span data-ttu-id="8be5b-184">DE92C1C7-837F-4F69-A3BB-86E631204A23</span><span class="sxs-lookup"><span data-stu-id="8be5b-184">DE92C1C7-837F-4F69-A3BB-86E631204A23</span></span>  
  
 <span data-ttu-id="8be5b-185">Drukarz</span><span class="sxs-lookup"><span data-stu-id="8be5b-185">Printers</span></span>  
 <span data-ttu-id="8be5b-186">76FC4E2D-D6AD-4519-A663-37BD56068185</span><span class="sxs-lookup"><span data-stu-id="8be5b-186">76FC4E2D-D6AD-4519-A663-37BD56068185</span></span>  
  
 <span data-ttu-id="8be5b-187">PrintHood</span><span class="sxs-lookup"><span data-stu-id="8be5b-187">PrintHood</span></span>  
 <span data-ttu-id="8be5b-188">9274BD8D-CFD1-41C3-B35E-B13F55A758F4</span><span class="sxs-lookup"><span data-stu-id="8be5b-188">9274BD8D-CFD1-41C3-B35E-B13F55A758F4</span></span>  
  
 <span data-ttu-id="8be5b-189">profilu</span><span class="sxs-lookup"><span data-stu-id="8be5b-189">Profile</span></span>  
 <span data-ttu-id="8be5b-190">5E6C858F-0E22-4760-9AFE-EA3317B67173</span><span class="sxs-lookup"><span data-stu-id="8be5b-190">5E6C858F-0E22-4760-9AFE-EA3317B67173</span></span>  
  
 <span data-ttu-id="8be5b-191">ProgramData</span><span class="sxs-lookup"><span data-stu-id="8be5b-191">ProgramData</span></span>  
 <span data-ttu-id="8be5b-192">62AB5D82-FDC1-4DC3-A9DD-070D1D495D97</span><span class="sxs-lookup"><span data-stu-id="8be5b-192">62AB5D82-FDC1-4DC3-A9DD-070D1D495D97</span></span>  
  
 <span data-ttu-id="8be5b-193">ProgramFiles</span><span class="sxs-lookup"><span data-stu-id="8be5b-193">ProgramFiles</span></span>  
 <span data-ttu-id="8be5b-194">905E63B6-C1BF-494E-B29C-65B732D3D21A</span><span class="sxs-lookup"><span data-stu-id="8be5b-194">905E63B6-C1BF-494E-B29C-65B732D3D21A</span></span>  
  
 <span data-ttu-id="8be5b-195">ProgramFilesCommon</span><span class="sxs-lookup"><span data-stu-id="8be5b-195">ProgramFilesCommon</span></span>  
 <span data-ttu-id="8be5b-196">F7F1ED05-9F6D-47A2-AAAE-29D317C6F066</span><span class="sxs-lookup"><span data-stu-id="8be5b-196">F7F1ED05-9F6D-47A2-AAAE-29D317C6F066</span></span>  
  
 <span data-ttu-id="8be5b-197">ProgramFilesCommonX64</span><span class="sxs-lookup"><span data-stu-id="8be5b-197">ProgramFilesCommonX64</span></span>  
 <span data-ttu-id="8be5b-198">6365D5A7-0F0D-45E5-87F6-0DA56B6A4F7D</span><span class="sxs-lookup"><span data-stu-id="8be5b-198">6365D5A7-0F0D-45E5-87F6-0DA56B6A4F7D</span></span>  
  
 <span data-ttu-id="8be5b-199">ProgramFilesCommonX86</span><span class="sxs-lookup"><span data-stu-id="8be5b-199">ProgramFilesCommonX86</span></span>  
 <span data-ttu-id="8be5b-200">DE974D24-D9C6-4D3E-BF91-F4455120B917</span><span class="sxs-lookup"><span data-stu-id="8be5b-200">DE974D24-D9C6-4D3E-BF91-F4455120B917</span></span>  
  
 <span data-ttu-id="8be5b-201">ProgramFilesX64</span><span class="sxs-lookup"><span data-stu-id="8be5b-201">ProgramFilesX64</span></span>  
 <span data-ttu-id="8be5b-202">6D809377-6AF0-444B-8957-A3773F02200E</span><span class="sxs-lookup"><span data-stu-id="8be5b-202">6D809377-6AF0-444B-8957-A3773F02200E</span></span>  
  
 <span data-ttu-id="8be5b-203">ProgramFilesX86</span><span class="sxs-lookup"><span data-stu-id="8be5b-203">ProgramFilesX86</span></span>  
 <span data-ttu-id="8be5b-204">7C5A40EF-A0FB-4BFC-874A-C0F2E0B9FA8E</span><span class="sxs-lookup"><span data-stu-id="8be5b-204">7C5A40EF-A0FB-4BFC-874A-C0F2E0B9FA8E</span></span>  
  
 <span data-ttu-id="8be5b-205">Programy</span><span class="sxs-lookup"><span data-stu-id="8be5b-205">Programs</span></span>  
 <span data-ttu-id="8be5b-206">A77F5D77-2E2B-44C3-A6A2-ABA601054A51</span><span class="sxs-lookup"><span data-stu-id="8be5b-206">A77F5D77-2E2B-44C3-A6A2-ABA601054A51</span></span>  
  
 <span data-ttu-id="8be5b-207">Public</span><span class="sxs-lookup"><span data-stu-id="8be5b-207">Public</span></span>  
 <span data-ttu-id="8be5b-208">DFDF76A2-C82A-4D63-906A-5644AC457385</span><span class="sxs-lookup"><span data-stu-id="8be5b-208">DFDF76A2-C82A-4D63-906A-5644AC457385</span></span>  
  
 <span data-ttu-id="8be5b-209">PublicDesktop</span><span class="sxs-lookup"><span data-stu-id="8be5b-209">PublicDesktop</span></span>  
 <span data-ttu-id="8be5b-210">C4AA340D-F20F-4863-AFEF-F87EF2E6BA25</span><span class="sxs-lookup"><span data-stu-id="8be5b-210">C4AA340D-F20F-4863-AFEF-F87EF2E6BA25</span></span>  
  
 <span data-ttu-id="8be5b-211">PublicDocuments</span><span class="sxs-lookup"><span data-stu-id="8be5b-211">PublicDocuments</span></span>  
 <span data-ttu-id="8be5b-212">ED4824AF-DCE4-45A8-81E2-FC7965083634</span><span class="sxs-lookup"><span data-stu-id="8be5b-212">ED4824AF-DCE4-45A8-81E2-FC7965083634</span></span>  
  
 <span data-ttu-id="8be5b-213">PublicDownloads</span><span class="sxs-lookup"><span data-stu-id="8be5b-213">PublicDownloads</span></span>  
 <span data-ttu-id="8be5b-214">3D644C9B-1FB8-4F30-9B45-F670235F79C0</span><span class="sxs-lookup"><span data-stu-id="8be5b-214">3D644C9B-1FB8-4F30-9B45-F670235F79C0</span></span>  
  
 <span data-ttu-id="8be5b-215">PublicGameTasks</span><span class="sxs-lookup"><span data-stu-id="8be5b-215">PublicGameTasks</span></span>  
 <span data-ttu-id="8be5b-216">DEBF2536-E1A8-4C59-B6A2-414586476AEA</span><span class="sxs-lookup"><span data-stu-id="8be5b-216">DEBF2536-E1A8-4C59-B6A2-414586476AEA</span></span>  
  
 <span data-ttu-id="8be5b-217">PublicMusic</span><span class="sxs-lookup"><span data-stu-id="8be5b-217">PublicMusic</span></span>  
 <span data-ttu-id="8be5b-218">3214FAB5-9757-4298-BB61-92A9DEAA44FF</span><span class="sxs-lookup"><span data-stu-id="8be5b-218">3214FAB5-9757-4298-BB61-92A9DEAA44FF</span></span>  
  
 <span data-ttu-id="8be5b-219">PublicPictures</span><span class="sxs-lookup"><span data-stu-id="8be5b-219">PublicPictures</span></span>  
 <span data-ttu-id="8be5b-220">B6EBFB86-6907-413C-9AF7-4FC2ABF07CC5</span><span class="sxs-lookup"><span data-stu-id="8be5b-220">B6EBFB86-6907-413C-9AF7-4FC2ABF07CC5</span></span>  
  
 <span data-ttu-id="8be5b-221">PublicVideos</span><span class="sxs-lookup"><span data-stu-id="8be5b-221">PublicVideos</span></span>  
 <span data-ttu-id="8be5b-222">2400183A-6185-49FB-A2D8-4A392A602BA3</span><span class="sxs-lookup"><span data-stu-id="8be5b-222">2400183A-6185-49FB-A2D8-4A392A602BA3</span></span>  
  
 <span data-ttu-id="8be5b-223">Szybkiego uruchamiania</span><span class="sxs-lookup"><span data-stu-id="8be5b-223">QuickLaunch</span></span>  
 <span data-ttu-id="8be5b-224">52A4F021-7B75-48A9-9F6B-4B87A210BC8F</span><span class="sxs-lookup"><span data-stu-id="8be5b-224">52A4F021-7B75-48A9-9F6B-4B87A210BC8F</span></span>  
  
 <span data-ttu-id="8be5b-225">Ostatnie</span><span class="sxs-lookup"><span data-stu-id="8be5b-225">Recent</span></span>  
 <span data-ttu-id="8be5b-226">AE50C081-EBD2-438A-8655-8A092E34987A</span><span class="sxs-lookup"><span data-stu-id="8be5b-226">AE50C081-EBD2-438A-8655-8A092E34987A</span></span>  
  
 <span data-ttu-id="8be5b-227">RecordedTV</span><span class="sxs-lookup"><span data-stu-id="8be5b-227">RecordedTV</span></span>  
 <span data-ttu-id="8be5b-228">BD85E001-112E-431E-983B-7B15AC09FFF1</span><span class="sxs-lookup"><span data-stu-id="8be5b-228">BD85E001-112E-431E-983B-7B15AC09FFF1</span></span>  
  
 <span data-ttu-id="8be5b-229">RecycleBin</span><span class="sxs-lookup"><span data-stu-id="8be5b-229">RecycleBin</span></span>  
 <span data-ttu-id="8be5b-230">B7534046-3ECB-4C18-BE4E-64CD4CB7D6AC</span><span class="sxs-lookup"><span data-stu-id="8be5b-230">B7534046-3ECB-4C18-BE4E-64CD4CB7D6AC</span></span>  
  
 <span data-ttu-id="8be5b-231">ResourceDir</span><span class="sxs-lookup"><span data-stu-id="8be5b-231">ResourceDir</span></span>  
 <span data-ttu-id="8be5b-232">8AD10C31-2ADB-4296-A8F7-E4701232C972</span><span class="sxs-lookup"><span data-stu-id="8be5b-232">8AD10C31-2ADB-4296-A8F7-E4701232C972</span></span>  
  
 <span data-ttu-id="8be5b-233">RoamingAppData</span><span class="sxs-lookup"><span data-stu-id="8be5b-233">RoamingAppData</span></span>  
 <span data-ttu-id="8be5b-234">3EB685DB-65F9-4CF6-A03A-E3EF65729F3D</span><span class="sxs-lookup"><span data-stu-id="8be5b-234">3EB685DB-65F9-4CF6-A03A-E3EF65729F3D</span></span>  
  
 <span data-ttu-id="8be5b-235">SampleMusic</span><span class="sxs-lookup"><span data-stu-id="8be5b-235">SampleMusic</span></span>  
 <span data-ttu-id="8be5b-236">B250C668-F57D-4EE1-A63C-290EE7D1AA1F</span><span class="sxs-lookup"><span data-stu-id="8be5b-236">B250C668-F57D-4EE1-A63C-290EE7D1AA1F</span></span>  
  
 <span data-ttu-id="8be5b-237">SamplePictures</span><span class="sxs-lookup"><span data-stu-id="8be5b-237">SamplePictures</span></span>  
 <span data-ttu-id="8be5b-238">C4900540-2379-4C75-844B-64E6FAF8716B</span><span class="sxs-lookup"><span data-stu-id="8be5b-238">C4900540-2379-4C75-844B-64E6FAF8716B</span></span>  
  
 <span data-ttu-id="8be5b-239">SamplePlaylists</span><span class="sxs-lookup"><span data-stu-id="8be5b-239">SamplePlaylists</span></span>  
 <span data-ttu-id="8be5b-240">15CA69B3-30EE-49C1-ACE1-6B5EC372AFB5</span><span class="sxs-lookup"><span data-stu-id="8be5b-240">15CA69B3-30EE-49C1-ACE1-6B5EC372AFB5</span></span>  
  
 <span data-ttu-id="8be5b-241">SampleVideos</span><span class="sxs-lookup"><span data-stu-id="8be5b-241">SampleVideos</span></span>  
 <span data-ttu-id="8be5b-242">859EAD94-2E85-48AD-A71A-0969CB56A6CD</span><span class="sxs-lookup"><span data-stu-id="8be5b-242">859EAD94-2E85-48AD-A71A-0969CB56A6CD</span></span>  
  
 <span data-ttu-id="8be5b-243">SavedGames</span><span class="sxs-lookup"><span data-stu-id="8be5b-243">SavedGames</span></span>  
 <span data-ttu-id="8be5b-244">4C5C32FF-BB9D-43B0-B5B4-2D72E54EAAA4</span><span class="sxs-lookup"><span data-stu-id="8be5b-244">4C5C32FF-BB9D-43B0-B5B4-2D72E54EAAA4</span></span>  
  
 <span data-ttu-id="8be5b-245">savedSearches</span><span class="sxs-lookup"><span data-stu-id="8be5b-245">SavedSearches</span></span>  
 <span data-ttu-id="8be5b-246">7D1D3A04-DEBB-4115-95CF-2F29DA2920DA</span><span class="sxs-lookup"><span data-stu-id="8be5b-246">7D1D3A04-DEBB-4115-95CF-2F29DA2920DA</span></span>  
  
 <span data-ttu-id="8be5b-247">SEARCH_CSC</span><span class="sxs-lookup"><span data-stu-id="8be5b-247">SEARCH_CSC</span></span>  
 <span data-ttu-id="8be5b-248">EE32E446-31CA-4ABA-814F-A5EBD2FD6D5E</span><span class="sxs-lookup"><span data-stu-id="8be5b-248">EE32E446-31CA-4ABA-814F-A5EBD2FD6D5E</span></span>  
  
 <span data-ttu-id="8be5b-249">SEARCH_MAPI</span><span class="sxs-lookup"><span data-stu-id="8be5b-249">SEARCH_MAPI</span></span>  
 <span data-ttu-id="8be5b-250">98EC0E18-2098-4D44-8644-66979315A281</span><span class="sxs-lookup"><span data-stu-id="8be5b-250">98EC0E18-2098-4D44-8644-66979315A281</span></span>  
  
 <span data-ttu-id="8be5b-251">SearchHome</span><span class="sxs-lookup"><span data-stu-id="8be5b-251">SearchHome</span></span>  
 <span data-ttu-id="8be5b-252">190337D1-B8CA-4121-A639-6D472D16972A</span><span class="sxs-lookup"><span data-stu-id="8be5b-252">190337D1-B8CA-4121-A639-6D472D16972A</span></span>  
  
 <span data-ttu-id="8be5b-253">SendTo</span><span class="sxs-lookup"><span data-stu-id="8be5b-253">SendTo</span></span>  
 <span data-ttu-id="8be5b-254">8983036C-27C0-404B-8F08-102D10DCFD74</span><span class="sxs-lookup"><span data-stu-id="8be5b-254">8983036C-27C0-404B-8F08-102D10DCFD74</span></span>  
  
 <span data-ttu-id="8be5b-255">SidebarDefaultParts</span><span class="sxs-lookup"><span data-stu-id="8be5b-255">SidebarDefaultParts</span></span>  
 <span data-ttu-id="8be5b-256">7B396E54-9EC5-4300-BE0A-2482EBAE1A26</span><span class="sxs-lookup"><span data-stu-id="8be5b-256">7B396E54-9EC5-4300-BE0A-2482EBAE1A26</span></span>  
  
 <span data-ttu-id="8be5b-257">SidebarParts</span><span class="sxs-lookup"><span data-stu-id="8be5b-257">SidebarParts</span></span>  
 <span data-ttu-id="8be5b-258">A75D362E-50FC-4FB7-AC2C-A8BEAA314493</span><span class="sxs-lookup"><span data-stu-id="8be5b-258">A75D362E-50FC-4FB7-AC2C-A8BEAA314493</span></span>  
  
 <span data-ttu-id="8be5b-259">StartMenu</span><span class="sxs-lookup"><span data-stu-id="8be5b-259">StartMenu</span></span>  
 <span data-ttu-id="8be5b-260">625B53C3-AB48-4EC1-BA1F-A1EF4146FC19</span><span class="sxs-lookup"><span data-stu-id="8be5b-260">625B53C3-AB48-4EC1-BA1F-A1EF4146FC19</span></span>  
  
 <span data-ttu-id="8be5b-261">Folderze</span><span class="sxs-lookup"><span data-stu-id="8be5b-261">Startup</span></span>  
 <span data-ttu-id="8be5b-262">B97D20BB-F46A-4C97-BA10-5E3608430854</span><span class="sxs-lookup"><span data-stu-id="8be5b-262">B97D20BB-F46A-4C97-BA10-5E3608430854</span></span>  
  
 <span data-ttu-id="8be5b-263">Syncmanager</span><span class="sxs-lookup"><span data-stu-id="8be5b-263">SyncManager</span></span>  
 <span data-ttu-id="8be5b-264">43668BF8-C14E-49B2-97C9-747784D784B7</span><span class="sxs-lookup"><span data-stu-id="8be5b-264">43668BF8-C14E-49B2-97C9-747784D784B7</span></span>  
  
 <span data-ttu-id="8be5b-265">SyncResults</span><span class="sxs-lookup"><span data-stu-id="8be5b-265">SyncResults</span></span>  
 <span data-ttu-id="8be5b-266">289A9A43-BE44-4057-A41B-587A76D7E7F9</span><span class="sxs-lookup"><span data-stu-id="8be5b-266">289A9A43-BE44-4057-A41B-587A76D7E7F9</span></span>  
  
 <span data-ttu-id="8be5b-267">SyncSetup</span><span class="sxs-lookup"><span data-stu-id="8be5b-267">SyncSetup</span></span>  
 <span data-ttu-id="8be5b-268">0F214138-B1D3-4A90-BBA9-27CBC0C5389A</span><span class="sxs-lookup"><span data-stu-id="8be5b-268">0F214138-B1D3-4A90-BBA9-27CBC0C5389A</span></span>  
  
 <span data-ttu-id="8be5b-269">System</span><span class="sxs-lookup"><span data-stu-id="8be5b-269">System</span></span>  
 <span data-ttu-id="8be5b-270">1AC14E77-02E7-4E5D-B744-2EB1AE5198B7</span><span class="sxs-lookup"><span data-stu-id="8be5b-270">1AC14E77-02E7-4E5D-B744-2EB1AE5198B7</span></span>  
  
 <span data-ttu-id="8be5b-271">SystemX86</span><span class="sxs-lookup"><span data-stu-id="8be5b-271">SystemX86</span></span>  
 <span data-ttu-id="8be5b-272">D65231B0-B2F1-4857-A4CE-A8E7C6EA7D27</span><span class="sxs-lookup"><span data-stu-id="8be5b-272">D65231B0-B2F1-4857-A4CE-A8E7C6EA7D27</span></span>  
  
 <span data-ttu-id="8be5b-273">Szablony</span><span class="sxs-lookup"><span data-stu-id="8be5b-273">Templates</span></span>  
 <span data-ttu-id="8be5b-274">A63293E8-664E-48DB-A079-DF759E0509F7</span><span class="sxs-lookup"><span data-stu-id="8be5b-274">A63293E8-664E-48DB-A079-DF759E0509F7</span></span>  
  
 <span data-ttu-id="8be5b-275">TreeProperties</span><span class="sxs-lookup"><span data-stu-id="8be5b-275">TreeProperties</span></span>  
 <span data-ttu-id="8be5b-276">5B3749AD-B49F-49C1-83EB-15370FBD4882</span><span class="sxs-lookup"><span data-stu-id="8be5b-276">5B3749AD-B49F-49C1-83EB-15370FBD4882</span></span>  
  
 <span data-ttu-id="8be5b-277">UserProfiles</span><span class="sxs-lookup"><span data-stu-id="8be5b-277">UserProfiles</span></span>  
 <span data-ttu-id="8be5b-278">0762D272-C50A-4BB0-A382-697DCD729B80</span><span class="sxs-lookup"><span data-stu-id="8be5b-278">0762D272-C50A-4BB0-A382-697DCD729B80</span></span>  
  
 <span data-ttu-id="8be5b-279">UsersFiles</span><span class="sxs-lookup"><span data-stu-id="8be5b-279">UsersFiles</span></span>  
 <span data-ttu-id="8be5b-280">F3CE0F7C-4901-4ACC-8648-D5D44B04EF8F</span><span class="sxs-lookup"><span data-stu-id="8be5b-280">F3CE0F7C-4901-4ACC-8648-D5D44B04EF8F</span></span>  
  
 <span data-ttu-id="8be5b-281">Wideo</span><span class="sxs-lookup"><span data-stu-id="8be5b-281">Videos</span></span>  
 <span data-ttu-id="8be5b-282">18989B1D-99B5-455B-841C-AB7C74E4DDFC</span><span class="sxs-lookup"><span data-stu-id="8be5b-282">18989B1D-99B5-455B-841C-AB7C74E4DDFC</span></span>  
  
 <span data-ttu-id="8be5b-283">Windows</span><span class="sxs-lookup"><span data-stu-id="8be5b-283">Windows</span></span>  
 <span data-ttu-id="8be5b-284">F38BF404-1D43-42F2-9305-67DE0B28FC23</span><span class="sxs-lookup"><span data-stu-id="8be5b-284">F38BF404-1D43-42F2-9305-67DE0B28FC23</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8be5b-285">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8be5b-285">See also</span></span>

- <xref:System.Windows.Forms.FileDialogCustomPlace>
- [<span data-ttu-id="8be5b-286">Instrukcje: dodawanie niestandardowego miejsca do okna dialogowego obsługi plików</span><span class="sxs-lookup"><span data-stu-id="8be5b-286">How To: Add a Custom Place to a File Dialog Box</span></span>](how-to-add-a-custom-place-to-a-file-dialog-box.md)
