---
title: "Porady: wyświetlanie zawartości globalnej pamięci podręcznej zestawów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b4cc4b1a3e68d6d39e13a56b2a519d15b72bd3a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="9cdd0-102">Porady: wyświetlanie zawartości globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="9cdd0-102">How to: View the Contents of the Global Assembly Cache</span></span>
<span data-ttu-id="9cdd0-103">Użyj [narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) do wyświetlania zawartości pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="9cdd0-103">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="9cdd0-104">Aby wyświetlić listę zestawów w globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="9cdd0-104">To view a list of the assemblies in the global assembly cache</span></span>  
  
1.  <span data-ttu-id="9cdd0-105">W [wiersz polecenia programu Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="9cdd0-105">At the [Visual Studio command prompt](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="9cdd0-106">**Gacutil -l** </span><span class="sxs-lookup"><span data-stu-id="9cdd0-106">**gacutil -l** </span></span>  
     <span data-ttu-id="9cdd0-107">—lub—</span><span class="sxs-lookup"><span data-stu-id="9cdd0-107">-or-</span></span>  
    <span data-ttu-id="9cdd0-108">**Gacutil /l**</span><span class="sxs-lookup"><span data-stu-id="9cdd0-108">**gacutil /l**</span></span>  
  
 <span data-ttu-id="9cdd0-109">We wcześniejszych wersjach programu .NET Framework [Shfusion.dll](http://msdn.microsoft.com/en-us/0d9464cf-ddba-4ca9-bbec-f678fb58f380) rozszerzenie powłoki Windows włączone, można wyświetlić w Eksploratorze plików pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="9cdd0-109">In earlier versions of the .NET Framework, the [Shfusion.dll](http://msdn.microsoft.com/en-us/0d9464cf-ddba-4ca9-bbec-f678fb58f380) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="9cdd0-110">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="9cdd0-110">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cdd0-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cdd0-111">See Also</span></span>  
 [<span data-ttu-id="9cdd0-112">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="9cdd0-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="9cdd0-113">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="9cdd0-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
