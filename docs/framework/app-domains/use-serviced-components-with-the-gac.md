---
title: "Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów"
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
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb9bd85797dd129f6f34992c58c9772668ce2cb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów
Obsługiwane składniki (zarządzany kod modelu COM +) należy umieścić w globalnej pamięci podręcznej zestawów. W niektórych scenariuszach środowisko uruchomieniowe języka wspólnego i usług COM + mogą obsługiwać obsługiwanych składników, które nie znajdują się w globalnej pamięci podręcznej zestawów; w innych sytuacjach nie jest to możliwe. Poniższe scenariusze ilustrują to:  
  
-   Dla obsługiwanych składników w aplikacji COM + serwera zestaw zawierający składniki musi być w globalnej pamięci podręcznej zestawów, ponieważ Dllhost.exe nie działa w tym samym katalogu co, która zawiera serwisowanych składników.  
  
-   Dla obsługiwanych składników w aplikacji COM + biblioteki środowiska uruchomieniowego i usług COM + mogą rozpoznać odwołania do zestawu zawierającego składników przez wyszukiwanie w bieżącym katalogu. W takim przypadku zestaw nie ma w globalnej pamięci podręcznej zestawów.  
  
-   Obsługiwane składniki w aplikacji ASP.NET sytuacji różni się. Umieść zestaw zawierający obsługiwanych składników w katalogu bin baza aplikacji, użyj rejestracji na żądanie zestawu będzie można skopiować cienia w pamięci podręcznej pobierania, ponieważ ASP.NET wykorzystuje funkcje tle środowiska uruchomieniowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Gacutil.exe (narzędzie Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
