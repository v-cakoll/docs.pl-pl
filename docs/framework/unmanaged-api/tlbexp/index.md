---
title: Funkcje pomocy narzędziaTlbexp (Niezarządzany wykaz interfejsów API)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f41a233e9b5338bdb0a324ff9af267a97821d4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
