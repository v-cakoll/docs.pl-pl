---
title: 'Porady: wyświetlanie zawartości globalnej pamięci podręcznej zestawów'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4142c3f12cc5a0e2277cc8dba28a281d5cf0ba55
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112247"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="a1a9e-102">Porady: wyświetlanie zawartości globalnej pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="a1a9e-102">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="a1a9e-103">Użyj [narzędzie global assembly cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) do wyświetlania zawartości globalnej pamięci podręcznej zestawów (GAC).</span><span class="sxs-lookup"><span data-stu-id="a1a9e-103">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="a1a9e-104">Wyświetlanie zestawów w globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="a1a9e-104">View the assemblies in the GAC</span></span>

<span data-ttu-id="a1a9e-105">Aby wyświetlić listę zestawów w globalnej pamięci podręcznej, należy otworzyć [wiersz polecenia programisty dla programu Visual Studio](../tools/developer-command-prompt-for-vs.md), a następnie wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="a1a9e-105">To view a list of the assemblies in the global assembly cache, open [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="a1a9e-106">—lub—</span><span class="sxs-lookup"><span data-stu-id="a1a9e-106">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="a1a9e-107">We wcześniejszych wersjach programu .NET Framework [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) rozszerzenie powłoki Windows umożliwia wyświetlanie globalnej pamięci podręcznej w Eksploratorze plików.</span><span class="sxs-lookup"><span data-stu-id="a1a9e-107">In earlier versions of the .NET Framework, the [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="a1a9e-108">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], biblioteka Shfusion.dll jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a1a9e-108">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1a9e-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1a9e-109">See also</span></span>

- [<span data-ttu-id="a1a9e-110">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="a1a9e-110">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="a1a9e-111">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="a1a9e-111">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)