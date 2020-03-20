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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73104126"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Funkcje pomocy narzędziaTlbexp (Niezarządzany wykaz interfejsów API)
[Narzędzie Eksporter biblioteki typów](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) ładuje bibliotekę łączy dynamicznych o nazwie TlbRef.dll. Ta biblioteka DLL zawiera dwie funkcje pomocnicze i interfejs używany przez narzędzie eksportera podczas procesu konwersji biblioteki typu zestawu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [GetTypeLibInfo, funkcja](gettypelibinfo-function.md)  
 Zawiera informacje o lokalizacji i systemie operacyjnym dla biblioteki typów.  
  
 [LoadTypeLibWithResolver — Funkcja](loadtypelibwithresolver-function.md)  
 Ładuje bibliotekę typów przy użyciu implementacji [interfejsu ITypeLibResolver,](itypelibresolver-interface.md) aby rozwiązać wszelkie biblioteki typów, do których istnieje odwołanie.  
  
 [ITypeLibResolver — Interfejs](itypelibresolver-interface.md)  
 Zawiera [ResolveTypeLib metoda](resolvetypelib-method.md), która zwraca w pełni kwalifikowaną ścieżkę biblioteki typów.
