---
title: "Funkcja VerifyClientKey (niezarządzany wykaz interfejsów API)"
description: "Funkcja VerifyClientKey gwarantuje, że klucz klienta ma poprawne zabezpieczeń."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: VerifyClientKey
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: VerifyClientKey
helpviewer_keywords: VerifyClientKey function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ada878ff8bc430ab2a2d48cac13a81b1f64d39f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="ee13e-103">Funkcja VerifyClientKey</span><span class="sxs-lookup"><span data-stu-id="ee13e-103">VerifyClientKey function</span></span>
<span data-ttu-id="ee13e-104">Zapewnia, że klucz klienta ma poprawnych zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ee13e-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ee13e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee13e-105">Syntax</span></span>  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="ee13e-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ee13e-106">Return value</span></span>

<span data-ttu-id="ee13e-107">Jeśli funkcja zakończy się powodzeniem, jest zwracana wartość `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="ee13e-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="ee13e-108">Jeśli funkcja nie powiedzie się, wartość zwracana jest kodu zera błąd zdefiniowany w *pliku WinError.h*.</span><span class="sxs-lookup"><span data-stu-id="ee13e-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee13e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee13e-109">Requirements</span></span>  
 <span data-ttu-id="ee13e-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee13e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee13e-111">**Nagłówek:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="ee13e-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="ee13e-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ee13e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee13e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee13e-113">See also</span></span>  
[<span data-ttu-id="ee13e-114">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="ee13e-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
