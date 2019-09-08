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
ms.openlocfilehash: a95ff535a4d0847fbd4b8af28f873b67a1829a4f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798823"
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
