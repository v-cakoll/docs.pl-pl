---
title: Funkcje pomocy narzędziaTlbexp (Niezarządzany wykaz interfejsów API)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8a9d483e101fdb94a43055b6081fcc31a458a1ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Funkcje pomocy narzędziaTlbexp (Niezarządzany wykaz interfejsów API)
[Narzędzie Eksporter biblioteki typów](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) biblioteki dołączanej dynamicznie o nazwie TlbRef.dll ładuje (Tlbexp.exe). Ta biblioteka DLL zawiera dwie funkcje pomocnicze i interfejs, który używa narzędzie eksportu w procesie konwersji zestawu do typu biblioteki.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [GetTypeLibInfo, funkcja](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 Zawiera informacje o lokalizacji i systemu operacyjnego dla biblioteki typów.  
  
 [LoadTypeLibWithResolver, funkcja](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 Ładuje bibliotekę typów przy użyciu implementacja [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) rozwiązywać wszelkie odwołania do biblioteki typów.  
  
 [ITypeLibResolver, interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 Udostępnia [ResolveTypeLib — metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), która zwraca pełną ścieżkę biblioteki typów.
