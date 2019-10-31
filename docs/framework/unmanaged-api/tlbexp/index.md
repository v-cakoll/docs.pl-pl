---
title: Funkcje pomocy narzędziaTlbexp (Niezarządzany wykaz interfejsów API)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: cbde2af9c8a03e6c41f571120027030713f1b8d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104126"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Funkcje pomocy narzędziaTlbexp (Niezarządzany wykaz interfejsów API)
[Narzędzie eksportu biblioteki typów](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp. exe) ładuje bibliotekę dołączaną dynamicznie o nazwie TlbRef. dll. Ta biblioteka DLL zawiera dwie funkcje pomocnika i interfejs, którego używa narzędzie eksportu w procesie konwersji zestawu na typ biblioteki.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [GetTypeLibInfo, funkcja](gettypelibinfo-function.md)  
 Zapewnia lokalizację i informacje o systemie operacyjnym dla biblioteki typów.  
  
 [LoadTypeLibWithResolver, funkcja](loadtypelibwithresolver-function.md)  
 Ładuje bibliotekę typów przy użyciu implementacji [interfejsu ITypeLibResolver](itypelibresolver-interface.md) , aby rozwiązać wszelkie odwołania do bibliotek typów.  
  
 [ITypeLibResolver, interfejs](itypelibresolver-interface.md)  
 Udostępnia [metodę ResolveTypeLib —](resolvetypelib-method.md), która zwraca w pełni kwalifikowaną ścieżkę do biblioteki typów.
