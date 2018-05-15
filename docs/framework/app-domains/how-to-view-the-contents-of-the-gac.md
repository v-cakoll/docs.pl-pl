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
ms.openlocfilehash: d6e582f86eac03a51437b965f87f1bc7f29294eb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="1c8ed-102">Porady: wyświetlanie zawartości globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="1c8ed-102">How to: View the Contents of the Global Assembly Cache</span></span>
<span data-ttu-id="1c8ed-103">Użyj [narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) do wyświetlania zawartości pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="1c8ed-103">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="1c8ed-104">Aby wyświetlić listę zestawów w globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="1c8ed-104">To view a list of the assemblies in the global assembly cache</span></span>  
  
1.  <span data-ttu-id="1c8ed-105">W [wiersz polecenia programu Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="1c8ed-105">At the [Visual Studio command prompt](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="1c8ed-106">**Gacutil -l** </span><span class="sxs-lookup"><span data-stu-id="1c8ed-106">**gacutil -l** </span></span>  
     <span data-ttu-id="1c8ed-107">—lub—</span><span class="sxs-lookup"><span data-stu-id="1c8ed-107">-or-</span></span>  
    <span data-ttu-id="1c8ed-108">**Gacutil /l**</span><span class="sxs-lookup"><span data-stu-id="1c8ed-108">**gacutil /l**</span></span>  
  
 <span data-ttu-id="1c8ed-109">We wcześniejszych wersjach programu .NET Framework [Shfusion.dll](http://msdn.microsoft.com/library/0d9464cf-ddba-4ca9-bbec-f678fb58f380) rozszerzenie powłoki Windows włączone, można wyświetlić w Eksploratorze plików pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="1c8ed-109">In earlier versions of the .NET Framework, the [Shfusion.dll](http://msdn.microsoft.com/library/0d9464cf-ddba-4ca9-bbec-f678fb58f380) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="1c8ed-110">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="1c8ed-110">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c8ed-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c8ed-111">See Also</span></span>  
 [<span data-ttu-id="1c8ed-112">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="1c8ed-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="1c8ed-113">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="1c8ed-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
