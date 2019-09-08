---
title: 'Instrukcje: Określanie, które .NET Framework aktualizacje zabezpieczeń i poprawki są zainstalowane'
description: Dowiedz się, jak określić, które .NET Framework aktualizacje zabezpieczeń i poprawki są zainstalowane na komputerze.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4c505c679c46494f7dc2534c2bbe9f50243a7dd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790067"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="42dd7-103">Instrukcje: Określanie, które .NET Framework aktualizacje zabezpieczeń i poprawki są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="42dd7-103">How to: Determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="42dd7-104">W tym artykule opisano, jak dowiedzieć się, które .NET Framework aktualizacje zabezpieczeń i poprawki są zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="42dd7-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="42dd7-105">Wszystkie techniki przedstawione w tym artykule wymagają konta z uprawnieniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="42dd7-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="to-find-installed-updates-using-the-registry"></a><span data-ttu-id="42dd7-106">Aby znaleźć zainstalowane aktualizacje przy użyciu rejestru</span><span class="sxs-lookup"><span data-stu-id="42dd7-106">To find installed updates using the registry</span></span>

<span data-ttu-id="42dd7-107">Zainstalowane aktualizacje zabezpieczeń i poprawki dla każdej wersji .NET Framework zainstalowanej na komputerze są wymienione w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="42dd7-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="42dd7-108">Aby wyświetlić te informacje, można użyć programu edytora rejestru (*regedit. exe*).</span><span class="sxs-lookup"><span data-stu-id="42dd7-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="42dd7-109">Otwórz program **regedit. exe**.</span><span class="sxs-lookup"><span data-stu-id="42dd7-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="42dd7-110">W systemie Windows 8 i nowszych wersjach kliknij prawym przyciskiem myszy pozycję **Uruchom** ![logo systemu Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), a następnie wybierz polecenie **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="42dd7-110">In Windows 8 and later versions, right-click **Start** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="42dd7-111">W polu **Otwórz** wprowadź ciąg **regedit** , a następnie wybierz **przycisk OK**.</span><span class="sxs-lookup"><span data-stu-id="42dd7-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="42dd7-112">W Edytorze rejestru otwórz następujący podklucz:</span><span class="sxs-lookup"><span data-stu-id="42dd7-112">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     <span data-ttu-id="42dd7-113">Zainstalowane aktualizacje są wymienione w obszarze podkluczy, które identyfikują .NET Framework wersji, do których mają zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="42dd7-113">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="42dd7-114">Każda aktualizacja jest identyfikowana przez numer bazy wiedzy (KB).</span><span class="sxs-lookup"><span data-stu-id="42dd7-114">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="42dd7-115">W Edytorze rejestru wersje .NET Framework i zainstalowane aktualizacje dla każdej wersji są przechowywane w różnych podkluczach.</span><span class="sxs-lookup"><span data-stu-id="42dd7-115">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="42dd7-116">Informacje o wykrywaniu zainstalowanych numerów wersji znajdują się [w temacie How to: Ustal, które wersje .NET Framework są](how-to-determine-which-versions-are-installed.md)zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="42dd7-116">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a><span data-ttu-id="42dd7-117">Aby znaleźć zainstalowane aktualizacje, badając rejestr w kodzie</span><span class="sxs-lookup"><span data-stu-id="42dd7-117">To find installed updates by querying the registry in code</span></span>

<span data-ttu-id="42dd7-118">Poniższy przykład programowo określa .NET Framework aktualizacje zabezpieczeń i poprawki, które są zainstalowane na komputerze:</span><span class="sxs-lookup"><span data-stu-id="42dd7-118">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="42dd7-119">Przykład generuje dane wyjściowe podobne do następującego:</span><span class="sxs-lookup"><span data-stu-id="42dd7-119">The example produces an output that's similar to the following one:</span></span>

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a><span data-ttu-id="42dd7-120">Aby znaleźć zainstalowane aktualizacje, badając rejestr w programie PowerShell</span><span class="sxs-lookup"><span data-stu-id="42dd7-120">To find installed updates by querying the registry in PowerShell</span></span>

<span data-ttu-id="42dd7-121">Poniższy przykład pokazuje, jak określić .NET Framework aktualizacje zabezpieczeń i poprawki, które są zainstalowane na komputerze przy użyciu programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="42dd7-121">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

```powershell
$DotNetVersions = Get-ChildItem HKLM:\SOFTWARE\WOW6432Node\Microsoft\Updates | Where-Object {$_.name -like
 "*.NET Framework*"}

ForEach($Version in $DotNetVersions){
    
   $Updates = Get-ChildItem $Version.PSPath
    $Version.PSChildName
    ForEach ($Update in $Updates){
       $Update.PSChildName
       }
}
```

<span data-ttu-id="42dd7-122">Przykład generuje dane wyjściowe podobne do następującego:</span><span class="sxs-lookup"><span data-stu-id="42dd7-122">The example produces an output that's similar to the following one:</span></span>

```console
Microsoft .NET Framework 4 Client Profile
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
Microsoft .NET Framework 4 Extended
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
```

## <a name="see-also"></a><span data-ttu-id="42dd7-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42dd7-123">See also</span></span>

- [<span data-ttu-id="42dd7-124">Instrukcje: Ustal, które wersje .NET Framework są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="42dd7-124">How to: Determine which .NET Framework versions are installed</span></span>](how-to-determine-which-versions-are-installed.md)
- [<span data-ttu-id="42dd7-125">Zainstaluj .NET Framework dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="42dd7-125">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="42dd7-126">Wersje i zależności</span><span class="sxs-lookup"><span data-stu-id="42dd7-126">Versions and dependencies</span></span>](versions-and-dependencies.md)
