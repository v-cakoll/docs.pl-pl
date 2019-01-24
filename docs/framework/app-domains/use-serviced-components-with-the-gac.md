---
title: Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60d42fa296585d26186a2e75a49c5b3cf761e846
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583249"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Używanie obsługiwanych składników z globalną pamięcią podręczną zestawów
Obsługiwane składniki (kodu zarządzanego modelu COM +) należy umieszczać w globalnej pamięci podręcznej zestawów. W niektórych scenariuszach środowisko uruchomieniowe języka wspólnego i usług COM + mogą obsługiwać obsługiwanych składników, które nie znajdują się w globalnej pamięci podręcznej zestawów; w innych sytuacjach nie jest to możliwe. Następujące scenariusze przedstawiają to:  
  
-   Dla obsługiwanych składników w aplikacji serwera COM + zestaw zawierający składniki musi być w globalnej pamięci podręcznej zestawów, ponieważ Dllhost.exe nie działa w tym samym katalogu, która zawiera obsługiwanych składników.  
  
-   Dla obsługiwanych składników w aplikacji modelu COM + biblioteki środowiska uruchomieniowego i usług COM +, można rozwiązać odwołania do zestawu zawierającego składniki, wyszukując w bieżącym katalogu. W tym przypadku zestaw nie ma znajdować się w globalnej pamięci podręcznej.  
  
-   Dla obsługiwanych składników w aplikacji ASP.NET ta sytuacja jest różne. Jeśli umieścić zestaw zawierający obsługiwanych składników w katalogu bin aplikacji i użyć rejestracji na żądanie, zestaw będą kopiowane w tle w pamięci podręcznej pobierania ponieważ ASP.NET wykorzystuje możliwości w tle środowiska uruchomieniowego.  
  
## <a name="see-also"></a>Zobacz także
- [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (narzędzie Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
