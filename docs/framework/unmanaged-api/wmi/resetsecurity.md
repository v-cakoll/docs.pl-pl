---
title: Funkcja ResetSecurity (niezarządzany wykaz interfejsów API)
description: Funkcja ResetSecurity przypisuje tokenu personifikacji w bieżącym wątku.
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3d87fa10dafba326147bcaa39836b631291ef1c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783124"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="5cf58-103">ResetSecurity — funkcja</span><span class="sxs-lookup"><span data-stu-id="5cf58-103">ResetSecurity function</span></span>
<span data-ttu-id="5cf58-104">Przypisuje token personifikacji dostarczony do bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="5cf58-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5cf58-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5cf58-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="5cf58-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5cf58-106">Parameters</span></span>

`token`  
<span data-ttu-id="5cf58-107">[in] Token personifikacji do skojarzenia z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="5cf58-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="5cf58-108">Wartość może być `null`.</span><span class="sxs-lookup"><span data-stu-id="5cf58-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="5cf58-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5cf58-109">Return value</span></span>

<span data-ttu-id="5cf58-110">Jeśli funkcja się powiedzie, wartość zwracana jest `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="5cf58-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="5cf58-111">Jeśli funkcja zawiedzie, wartość zwracana jest kod błędu różny od zera.</span><span class="sxs-lookup"><span data-stu-id="5cf58-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="5cf58-112">Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [geterrorinfo —](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="5cf58-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="5cf58-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5cf58-113">Requirements</span></span>  
 <span data-ttu-id="5cf58-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cf58-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cf58-115">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5cf58-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5cf58-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5cf58-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf58-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cf58-117">See also</span></span>

- [<span data-ttu-id="5cf58-118">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="5cf58-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
