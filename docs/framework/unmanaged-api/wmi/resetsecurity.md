---
title: ResetSecurity — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja ResetSecurity przypisuje token personifikacji do bieżącego wątku.
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
ms.openlocfilehash: 1636d7de8273389e785131dbc1145affd5d3b45f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798258"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="7dd09-103">ResetSecurity, funkcja</span><span class="sxs-lookup"><span data-stu-id="7dd09-103">ResetSecurity function</span></span>
<span data-ttu-id="7dd09-104">Przypisuje podany token personifikacji do bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="7dd09-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7dd09-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7dd09-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="7dd09-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7dd09-106">Parameters</span></span>

`token`  
<span data-ttu-id="7dd09-107">podczas Token personifikacji do skojarzenia z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="7dd09-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="7dd09-108">Jego wartością może być `null`.</span><span class="sxs-lookup"><span data-stu-id="7dd09-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="7dd09-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7dd09-109">Return value</span></span>

<span data-ttu-id="7dd09-110">Jeśli funkcja się powiedzie, zwracaną wartością jest `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="7dd09-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="7dd09-111">Jeśli funkcja się nie powiedzie, wartość zwracana jest kodem błędu o wartości innej niż zero.</span><span class="sxs-lookup"><span data-stu-id="7dd09-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="7dd09-112">Aby uzyskać rozszerzone informacje o błędzie, wywołaj funkcję [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="7dd09-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="7dd09-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7dd09-113">Requirements</span></span>  
 <span data-ttu-id="7dd09-114">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dd09-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dd09-115">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7dd09-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7dd09-116">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7dd09-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd09-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7dd09-117">See also</span></span>

- [<span data-ttu-id="7dd09-118">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="7dd09-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
