---
title: Initialize — funkcja (niezarządzany wykaz interfejsów API)
description: Funkcję inicjowania wykonuje inicjowania usługi WMI.
ms.date: 11/06/2017
api_name:
- Initialize
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Initialize
helpviewer_keywords:
- Initialize function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca8e87157a7adf45f35608aeba1067f2d66c8972
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081609"
---
# <a name="initialize-function"></a><span data-ttu-id="27d3d-103">Initialize — funkcja</span><span class="sxs-lookup"><span data-stu-id="27d3d-103">Initialize function</span></span>
<span data-ttu-id="27d3d-104">Wykonuje inicjowania usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="27d3d-104">Performs WMI initialization.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="27d3d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="27d3d-105">Syntax</span></span> 
```  
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
); 
```  
## <a name="parameters"></a><span data-ttu-id="27d3d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="27d3d-106">Parameters</span></span>

`bAllowIManagementObjectQI`   
<span data-ttu-id="27d3d-107">[in] `true` do wskazania, że wywołania QueryInterface obiektów WMI są dozwolone `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="27d3d-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="27d3d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="27d3d-108">Return value</span></span>

<span data-ttu-id="27d3d-109">Funkcja zawsze zwraca `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="27d3d-109">The function always returns `S_OK` (0).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="27d3d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27d3d-110">Requirements</span></span>  
 <span data-ttu-id="27d3d-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27d3d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27d3d-112">**Nagłówek:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="27d3d-112">**Header:** WMINet_Utils.def</span></span>  
  
 **<span data-ttu-id="27d3d-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="27d3d-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="27d3d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27d3d-114">See also</span></span>

- [<span data-ttu-id="27d3d-115">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="27d3d-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
