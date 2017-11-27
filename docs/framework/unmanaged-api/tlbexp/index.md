---
title: "Funkcje pomocy narzędziaTlbexp (Niezarządzany wykaz interfejsów API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d5d0a0b08be725a50442a3db9f9942bceea7cf8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="ed59a-102">Funkcje pomocy narzędziaTlbexp (Niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="ed59a-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="ed59a-103">[Narzędzie Eksporter biblioteki typów](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) biblioteki dołączanej dynamicznie o nazwie TlbRef.dll ładuje (Tlbexp.exe).</span><span class="sxs-lookup"><span data-stu-id="ed59a-103">The [Type Library Exporter tool](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="ed59a-104">Ta biblioteka DLL zawiera dwie funkcje pomocnicze i interfejs, który używa narzędzie eksportu w procesie konwersji zestawu do typu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ed59a-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ed59a-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ed59a-105">In This Section</span></span>  
 [<span data-ttu-id="ed59a-106">Gettypelibinfo — funkcja</span><span class="sxs-lookup"><span data-stu-id="ed59a-106">GetTypeLibInfo Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 <span data-ttu-id="ed59a-107">Zawiera informacje o lokalizacji i systemu operacyjnego dla biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="ed59a-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="ed59a-108">Loadtypelibwithresolver — funkcja</span><span class="sxs-lookup"><span data-stu-id="ed59a-108">LoadTypeLibWithResolver Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 <span data-ttu-id="ed59a-109">Ładuje bibliotekę typów przy użyciu implementacja [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) rozwiązywać wszelkie odwołania do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="ed59a-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="ed59a-110">Itypelibresolver — interfejs</span><span class="sxs-lookup"><span data-stu-id="ed59a-110">ITypeLibResolver Interface</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 <span data-ttu-id="ed59a-111">Udostępnia [ResolveTypeLib — metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), która zwraca pełną ścieżkę biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="ed59a-111">Provides the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
