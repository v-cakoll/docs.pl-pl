---
title: "Initialize — funkcja (niezarządzany wykaz interfejsów API)"
description: "Funkcję inicjowania wykonuje inicjowania usługi WMI."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Initialize
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Initialize
helpviewer_keywords: Initialize function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ed0e0127608f9f80a2661067dd9a6025fd579a7
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="initialize-function"></a><span data-ttu-id="18ab4-103">Initialize — funkcja</span><span class="sxs-lookup"><span data-stu-id="18ab4-103">Initialize function</span></span>
<span data-ttu-id="18ab4-104">Wykonuje inicjowania usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="18ab4-104">Performs WMI initialization.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="18ab4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="18ab4-105">Syntax</span></span> 
```  
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
); 
```  
## <a name="parameters"></a><span data-ttu-id="18ab4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="18ab4-106">Parameters</span></span>

`bAllowIManagementObjectQI`   
<span data-ttu-id="18ab4-107">[in] `true` wskazująca, czy są dozwolone wywołania metody QueryInterface w obiektach WMI; `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="18ab4-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="18ab4-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="18ab4-108">Return value</span></span>

<span data-ttu-id="18ab4-109">Funkcja zawsze zwraca wartość `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="18ab4-109">The function always returns `S_OK` (0).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="18ab4-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="18ab4-110">Requirements</span></span>  
 <span data-ttu-id="18ab4-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18ab4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18ab4-112">**Nagłówek:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="18ab4-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="18ab4-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="18ab4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18ab4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18ab4-114">See also</span></span>  
[<span data-ttu-id="18ab4-115">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="18ab4-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
