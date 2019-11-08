---
title: Które .NET Framework aktualizacje zabezpieczeń i poprawki
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
ms.openlocfilehash: aad202e7c9df01c2893e74a39744f2c32783f1f0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735201"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="9c831-103">Jak określić, które .NET Framework aktualizacje zabezpieczeń i poprawki</span><span class="sxs-lookup"><span data-stu-id="9c831-103">How to determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="9c831-104">W tym artykule opisano, jak dowiedzieć się, które .NET Framework aktualizacje zabezpieczeń i poprawki są zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="9c831-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="9c831-105">Wszystkie techniki przedstawione w tym artykule wymagają konta z uprawnieniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="9c831-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="use-registry-editor"></a><span data-ttu-id="9c831-106">Korzystanie z edytora rejestru</span><span class="sxs-lookup"><span data-stu-id="9c831-106">Use Registry Editor</span></span>

<span data-ttu-id="9c831-107">Zainstalowane aktualizacje zabezpieczeń i poprawki dla każdej wersji .NET Framework zainstalowanej na komputerze są wymienione w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9c831-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="9c831-108">Aby wyświetlić te informacje, można użyć programu edytora rejestru (*regedit. exe*).</span><span class="sxs-lookup"><span data-stu-id="9c831-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="9c831-109">Otwórz program **regedit. exe**.</span><span class="sxs-lookup"><span data-stu-id="9c831-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="9c831-110">W systemie Windows 8 i nowszych wersjach kliknij prawym przyciskiem myszy **Start** ![zrzut ekranu logo klucza systemu Windows.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo")następnie wybierz polecenie **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="9c831-110">In Windows 8 and later versions, right-click **Start** ![Screenshot of the Windows key logo.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="9c831-111">W polu **Otwórz** wprowadź ciąg **regedit** , a następnie wybierz **przycisk OK**.</span><span class="sxs-lookup"><span data-stu-id="9c831-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="9c831-112">W Edytorze rejestru otwórz następujący podklucz:</span><span class="sxs-lookup"><span data-stu-id="9c831-112">In the Registry Editor, open the following subkey:</span></span>

     <span data-ttu-id="9c831-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span><span class="sxs-lookup"><span data-stu-id="9c831-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span></span>

     <span data-ttu-id="9c831-114">Zainstalowane aktualizacje są wymienione w obszarze podkluczy, które identyfikują .NET Framework wersji, do których mają zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="9c831-114">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="9c831-115">Każda aktualizacja jest identyfikowana przez numer bazy wiedzy (KB).</span><span class="sxs-lookup"><span data-stu-id="9c831-115">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="9c831-116">W Edytorze rejestru wersje .NET Framework i zainstalowane aktualizacje dla każdej wersji są przechowywane w różnych podkluczach.</span><span class="sxs-lookup"><span data-stu-id="9c831-116">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="9c831-117">Informacje o wykrywaniu zainstalowanych numerów wersji znajdują się w temacie [How to: Określanie, które wersje .NET Framework są zainstalowane](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="9c831-117">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="query-the-registry-using-code"></a><span data-ttu-id="9c831-118">Tworzenie zapytań dotyczących rejestru przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="9c831-118">Query the registry using code</span></span>

<span data-ttu-id="9c831-119">Poniższy przykład programowo określa .NET Framework aktualizacje zabezpieczeń i poprawki, które są zainstalowane na komputerze:</span><span class="sxs-lookup"><span data-stu-id="9c831-119">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="9c831-120">Przykład generuje dane wyjściowe podobne do następującego:</span><span class="sxs-lookup"><span data-stu-id="9c831-120">The example produces an output that's similar to the following one:</span></span>

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

## <a name="use-powershell-to-query-the-registry"></a><span data-ttu-id="9c831-121">Używanie programu PowerShell do wysyłania zapytań do rejestru</span><span class="sxs-lookup"><span data-stu-id="9c831-121">Use PowerShell to query the registry</span></span>

<span data-ttu-id="9c831-122">Poniższy przykład pokazuje, jak określić .NET Framework aktualizacje zabezpieczeń i poprawki, które są zainstalowane na komputerze przy użyciu programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9c831-122">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

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

<span data-ttu-id="9c831-123">Przykład generuje dane wyjściowe podobne do następującego:</span><span class="sxs-lookup"><span data-stu-id="9c831-123">The example produces an output that's similar to the following one:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9c831-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c831-124">See also</span></span>

- [<span data-ttu-id="9c831-125">Instrukcje: Określanie, które wersje .NET Framework są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="9c831-125">How to: Determine which .NET Framework versions are installed</span></span>](how-to-determine-which-versions-are-installed.md)
- [<span data-ttu-id="9c831-126">Zainstaluj .NET Framework dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="9c831-126">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="9c831-127">Wersje i zależności</span><span class="sxs-lookup"><span data-stu-id="9c831-127">Versions and dependencies</span></span>](versions-and-dependencies.md)
