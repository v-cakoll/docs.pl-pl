---
title: Lokalizacja zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91fc7cf6ea66952fa5770ce73ecb1a8c129a9a2d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="assembly-location"></a>Lokalizacja zestawu
Lokalizacji zestawu Określa, czy można zlokalizować gdy odwołuje się do środowisko uruchomieniowe języka wspólnego i można również określić, czy zestaw może być współużytkowana z innych zestawów. Można wdrożyć zestawu w następujących lokalizacjach:  
  
-   Katalog aplikacji lub jego podkatalogach.  
  
     Jest to lokalizacja najczęściej używane do wdrażania zestawu. Podkatalogi katalogu głównego aplikacji może być oparta na języka i kultury. Jeśli zestaw informacji w atrybucie kultury, musi być w podkatalogu w katalogu aplikacji o nazwie tej kultury.  
  
-   Globalna pamięć podręczna zestawów.  
  
     To jest kod komputera pamięci podręcznej, zainstalowanym wszędzie tam, gdzie jest zainstalowane środowisko uruchomieniowe języka wspólnego. W większości przypadków Jeśli zamierzasz dzielenie się zestawem z wielu aplikacji, należy wdrożyć ją w pamięci podręcznej GAC.  
  
-   Na serwerze HTTP.  
  
     Zestaw wdrożonych na serwerze HTTP musi mieć silnej nazwy; wskaż zestawu w sekcji codebase pliku konfiguracji aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)  
 [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
