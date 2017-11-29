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
ms.openlocfilehash: db5714c6669ac5fbdfd81656aa7659fdde05922a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Porady: wyświetlanie zawartości globalnej pamięci podręcznej zestawów
Użyj [narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) do wyświetlania zawartości pamięci podręcznej GAC.  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a>Aby wyświetlić listę zestawów w globalnej pamięci podręcznej zestawów  
  
1.  W [wiersz polecenia programu Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), wpisz następujące polecenie:  
  
     **Gacutil -l**   
     —lub—  
    **Gacutil /l**  
  
 We wcześniejszych wersjach programu .NET Framework [Shfusion.dll](http://msdn.microsoft.com/en-us/0d9464cf-ddba-4ca9-bbec-f678fb58f380) rozszerzenie powłoki Windows włączone, można wyświetlić w Eksploratorze plików pamięci podręcznej GAC. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll jest przestarzały.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z zestawami i Globalna pamięć podręczna zestawów](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Gacutil.exe (narzędzie Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
