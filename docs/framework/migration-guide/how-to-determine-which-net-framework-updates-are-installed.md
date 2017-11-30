---
title: "Porady: Określanie, które poprawki i aktualizacje zabezpieczeń .NET Framework są zainstalowane"
description: "Dowiedz się, jak ustalić, które poprawki i aktualizacje zabezpieczeń .NET Framework są zainstalowane na komputerze."
ms.date: 11/27/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ff10928b87834f9b8e74e269082919f49497023
ms.sourcegitcommit: 39b65a49271e082add68cb737b48fdbe09d24718
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2017
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="4d0f6-103">Porady: Określanie, które poprawki i aktualizacje zabezpieczeń .NET Framework są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="4d0f6-103">How to: Determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="4d0f6-104">W tym artykule przedstawiono sposób sprawdzić aktualizacje zabezpieczeń .NET Framework i poprawki są instalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="4d0f6-105">Wszystkie techniki, które są wyświetlane w tym artykule wymagają konta z uprawnieniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="to-find-installed-updates-using-the-registry"></a><span data-ttu-id="4d0f6-106">Aby znaleźć zainstalowane aktualizacje za pomocą rejestru</span><span class="sxs-lookup"><span data-stu-id="4d0f6-106">To find installed updates using the registry</span></span>

<span data-ttu-id="4d0f6-107">Zainstalowane aktualizacje i poprawki dla każdej wersji platformy .NET zainstalowany na komputerze są wyświetlane w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="4d0f6-108">Edytor rejestru (*regedit.exe*) program, aby wyświetlić te informacje.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="4d0f6-109">Otwórz program **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="4d0f6-110">W systemie Windows 8 i nowszych wersjach, kliknij prawym przyciskiem myszy **Start** ![logo systemu Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), a następnie wybierz pozycję **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-110">In Windows 8 and later versions, right-click **Start** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="4d0f6-111">W **Otwórz** wprowadź **regedit** i wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="4d0f6-112">W Edytorze rejestru otwórz następujący podklucz:</span><span class="sxs-lookup"><span data-stu-id="4d0f6-112">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     <span data-ttu-id="4d0f6-113">Zainstalowane aktualizacje są wyświetlane w obszarze podklucze identyfikowania wersji .NET Framework, które odnoszą się do.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-113">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="4d0f6-114">Każda aktualizacja jest identyfikowany przez numer bazy wiedzy Knowledge Base (KB).</span><span class="sxs-lookup"><span data-stu-id="4d0f6-114">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="4d0f6-115">W Edytorze rejestru wersje programu .NET Framework i zainstalowanych aktualizacji dla każdej wersji, są przechowywane w różnych podkluczy.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-115">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="4d0f6-116">Uzyskać informacji na temat wykrywania numery zainstalowanej wersji, zobacz [porady: Określanie, które wersje programu .NET Framework są zainstalowane](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="4d0f6-116">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a><span data-ttu-id="4d0f6-117">Aby znaleźć zainstalowane aktualizacje, badając rejestru w kodzie</span><span class="sxs-lookup"><span data-stu-id="4d0f6-117">To find installed updates by querying the registry in code</span></span>

<span data-ttu-id="4d0f6-118">Poniższy przykład określa programowo, aktualizacje zabezpieczeń .NET Framework i poprawki, które są zainstalowane na komputerze:</span><span class="sxs-lookup"><span data-stu-id="4d0f6-118">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="4d0f6-119">Przykład generuje dane wyjściowe podobne do następującego:</span><span class="sxs-lookup"><span data-stu-id="4d0f6-119">The example produces an output that's similar to the following one:</span></span>

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

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a><span data-ttu-id="4d0f6-120">Aby znaleźć zainstalowane aktualizacje, badając rejestru w programie PowerShell</span><span class="sxs-lookup"><span data-stu-id="4d0f6-120">To find installed updates by querying the registry in PowerShell</span></span>

<span data-ttu-id="4d0f6-121">Poniższy przykład przedstawia sposób określenia aktualizacje zabezpieczeń .NET Framework i poprawki, które są zainstalowane na komputerze przy użyciu programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="4d0f6-121">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

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

<span data-ttu-id="4d0f6-122">Przykład generuje dane wyjściowe podobne do następującego:</span><span class="sxs-lookup"><span data-stu-id="4d0f6-122">The example produces an output that's similar to the following one:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4d0f6-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d0f6-123">See also</span></span>

[<span data-ttu-id="4d0f6-124">Porady: Określanie, które wersje programu .NET Framework są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="4d0f6-124">How to: Determine which .NET Framework versions are installed</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
[<span data-ttu-id="4d0f6-125">Zainstaluj program .NET Framework dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="4d0f6-125">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
[<span data-ttu-id="4d0f6-126">Wersje i zależności</span><span class="sxs-lookup"><span data-stu-id="4d0f6-126">Versions and dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
