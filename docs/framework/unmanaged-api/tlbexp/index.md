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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967703"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="91cf7-102">Funkcje pomocy narzędziaTlbexp (Niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="91cf7-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="91cf7-103">[Narzędzie Eksporter biblioteki typów](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe), ładuje bibliotekę dołączaną dynamicznie o nazwie TlbRef.dll.</span><span class="sxs-lookup"><span data-stu-id="91cf7-103">The [Type Library Exporter tool](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="91cf7-104">Ta biblioteka DLL zawiera dwóch funkcji pomocnika oraz interfejs, który korzysta z narzędzia eksportu w procesie konwersji zestawu do typu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="91cf7-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91cf7-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="91cf7-105">In This Section</span></span>  
 [<span data-ttu-id="91cf7-106">GetTypeLibInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="91cf7-106">GetTypeLibInfo Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 <span data-ttu-id="91cf7-107">Zawiera informacje o lokalizacji i systemu operacyjnego dla biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="91cf7-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="91cf7-108">LoadTypeLibWithResolver, funkcja</span><span class="sxs-lookup"><span data-stu-id="91cf7-108">LoadTypeLibWithResolver Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 <span data-ttu-id="91cf7-109">Ładuje bibliotekę typów, przy użyciu implementacji [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) do rozwiązania odwołanie do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="91cf7-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="91cf7-110">ITypeLibResolver, interfejs</span><span class="sxs-lookup"><span data-stu-id="91cf7-110">ITypeLibResolver Interface</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 <span data-ttu-id="91cf7-111">Udostępnia [resolvetypelib — metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), która zwraca w pełni kwalifikowaną ścieżkę biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="91cf7-111">Provides the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
