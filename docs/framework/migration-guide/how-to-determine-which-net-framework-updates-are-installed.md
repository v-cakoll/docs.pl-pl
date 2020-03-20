---
title: Zobacz zainstalowane aktualizacje zabezpieczeń i poprawki programu .NET Framework
description: Dowiedz się, jak ustalić, które aktualizacje zabezpieczeń i poprawki programu .NET Framework są zainstalowane na komputerze.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
ms.openlocfilehash: 5c7bf48d5786530a9bcb69fb7cf605ac2c80a4eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181268"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="deccd-103">Jak określić, które aktualizacje zabezpieczeń i poprawki programu .NET Framework są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="deccd-103">How to determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="deccd-104">W tym artykule pokazano, jak sprawdzić, które aktualizacje zabezpieczeń i poprawki programu .NET Framework są zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="deccd-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="deccd-105">Wszystkie techniki pokazane w tym artykule wymagają konta z uprawnieniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="deccd-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="use-registry-editor"></a><span data-ttu-id="deccd-106">Korzystanie z Edytora rejestru</span><span class="sxs-lookup"><span data-stu-id="deccd-106">Use Registry Editor</span></span>

<span data-ttu-id="deccd-107">Zainstalowane aktualizacje zabezpieczeń i poprawki dla każdej wersji programu .NET Framework zainstalowanej na komputerze są wymienione w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="deccd-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="deccd-108">Do wyświetlenia tych informacji można użyć programu Registry Editor (*regedit.exe).*</span><span class="sxs-lookup"><span data-stu-id="deccd-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="deccd-109">Otwórz program **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="deccd-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="deccd-110">W systemie Windows 8 i nowszych wersjach kliknij prawym **Run**przyciskiem myszy pozycję ![Rozpocznij zrzut ekranu z logo klucza systemu Windows.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo (dziennik klawiatury systemu Windows)") **Start**</span><span class="sxs-lookup"><span data-stu-id="deccd-110">In Windows 8 and later versions, right-click **Start** ![Screenshot of the Windows key logo.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="deccd-111">W polu **Otwórz** wprowadź **regedit** i wybierz **PRZYCISK OK**.</span><span class="sxs-lookup"><span data-stu-id="deccd-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="deccd-112">W Edytorze rejestru otwórz następujący podklucz:</span><span class="sxs-lookup"><span data-stu-id="deccd-112">In the Registry Editor, open the following subkey:</span></span>

     <span data-ttu-id="deccd-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span><span class="sxs-lookup"><span data-stu-id="deccd-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span></span>

     <span data-ttu-id="deccd-114">Zainstalowane aktualizacje są wyświetlane w podkluczach, które identyfikują wersję programu .NET Framework, do których się odnoszą.</span><span class="sxs-lookup"><span data-stu-id="deccd-114">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="deccd-115">Każda aktualizacja jest identyfikowana za pomocą numeru bazy wiedzy (KB).</span><span class="sxs-lookup"><span data-stu-id="deccd-115">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="deccd-116">W Edytorze rejestru wersje programu .NET Framework i zainstalowane aktualizacje dla każdej wersji są przechowywane w różnych podkluczach.</span><span class="sxs-lookup"><span data-stu-id="deccd-116">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="deccd-117">Aby uzyskać informacje dotyczące wykrywania zainstalowanych numerów wersji, zobacz [Jak: Określanie zainstalowanych wersji programu .NET Framework](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="deccd-117">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="query-the-registry-using-code"></a><span data-ttu-id="deccd-118">Kwerenda rejestru przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="deccd-118">Query the registry using code</span></span>

<span data-ttu-id="deccd-119">Poniższy przykład programowo określa aktualizacje zabezpieczeń programu .NET Framework i poprawki zainstalowane na komputerze:</span><span class="sxs-lookup"><span data-stu-id="deccd-119">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="deccd-120">W przykładzie daje dane wyjściowe, które są podobne do następującego:</span><span class="sxs-lookup"><span data-stu-id="deccd-120">The example produces an output that's similar to the following one:</span></span>

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

## <a name="use-powershell-to-query-the-registry"></a><span data-ttu-id="deccd-121">Używanie programu PowerShell do wykonywania zapytań do rejestru</span><span class="sxs-lookup"><span data-stu-id="deccd-121">Use PowerShell to query the registry</span></span>

<span data-ttu-id="deccd-122">W poniższym przykładzie pokazano, jak określić aktualizacje zabezpieczeń programu .NET Framework i poprawki zainstalowane na komputerze przy użyciu programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="deccd-122">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

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

<span data-ttu-id="deccd-123">W przykładzie daje dane wyjściowe, które są podobne do następującego:</span><span class="sxs-lookup"><span data-stu-id="deccd-123">The example produces an output that's similar to the following one:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="deccd-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="deccd-124">See also</span></span>

- [<span data-ttu-id="deccd-125">Jak: Określ, które wersje programu .NET Framework są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="deccd-125">How to: Determine which .NET Framework versions are installed</span></span>](how-to-determine-which-versions-are-installed.md)
- [<span data-ttu-id="deccd-126">Instalowanie programu .NET Framework dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="deccd-126">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="deccd-127">Wersje i zależności</span><span class="sxs-lookup"><span data-stu-id="deccd-127">Versions and dependencies</span></span>](versions-and-dependencies.md)
