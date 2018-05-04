---
title: Zestawy i wykonywanie równoczesne
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 605cb6dfd3232d90d6c278f9563ac8d9f101b053
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="assemblies-and-side-by-side-execution"></a>Zestawy i wykonywanie równoczesne
Wykonanie Side-by-side jest możliwość przechowywania i wykonywanie wielu wersji aplikacji lub składnika na tym samym komputerze. Oznacza to, że może mieć wiele wersji środowiska uruchomieniowego i wiele wersji aplikacji i składników, których używana jest wersja środowiska uruchomieniowego, na tym samym komputerze, w tym samym czasie. Wykonanie Side-by-side zapewnia większą kontrolę nad jakich wersji składnika aplikacji wiąże i większą kontrolę nad którą wersję środowiska uruchomieniowego aplikacji używane.  
  
 Obsługa magazynu side-by-side i wykonywania różnych wersji tego samego zestawu jest integralną częścią silne nazwy i jest wbudowana w infrastrukturze środowiska uruchomieniowego. Ponieważ numer wersji zestawu o silnej nazwie jest częścią jego tożsamość, środowisko uruchomieniowe można przechowywać wiele wersji tego samego zestawu w pamięci podręcznej GAC i ładowanie tych zestawów w czasie wykonywania.  
  
 Mimo że środowisko uruchomieniowe umożliwia tworzenie aplikacji side-by-side, wykonanie side-by-side nie jest automatyczna. Aby uzyskać więcej informacji na temat tworzenia aplikacji dla wykonywania side-by-side, zobacz [wytyczne dotyczące tworzenia składników do wykonania Side-by-Side](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
