---
title: ResetSecurity, funkcja (odwołanie do niezarządzanego interfejsu API)
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
ms.openlocfilehash: ce74494455c6cc7fe382a4ea4ef2ff0c4e98c61b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174865"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="37404-103">ResetSecurity, funkcja</span><span class="sxs-lookup"><span data-stu-id="37404-103">ResetSecurity function</span></span>
<span data-ttu-id="37404-104">Przypisuje dostarczony token personifikacji do bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="37404-104">Assigns the supplied impersonation token to the current thread.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="37404-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="37404-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
);
```  

## <a name="parameters"></a><span data-ttu-id="37404-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="37404-106">Parameters</span></span>

`token`  
<span data-ttu-id="37404-107">[w] Token personifikacji do skojarzenia z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="37404-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="37404-108">Jego wartość `null`może być .</span><span class="sxs-lookup"><span data-stu-id="37404-108">Its value can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="37404-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="37404-109">Return value</span></span>

<span data-ttu-id="37404-110">Jeśli funkcja powiedzie się, `S_OK` zwracana wartość wynosi (0).</span><span class="sxs-lookup"><span data-stu-id="37404-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="37404-111">Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego.</span><span class="sxs-lookup"><span data-stu-id="37404-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="37404-112">Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję [GetErrorInfo.](geterrorinfo.md)</span><span class="sxs-lookup"><span data-stu-id="37404-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="37404-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37404-113">Requirements</span></span>  
 <span data-ttu-id="37404-114">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37404-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37404-115">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="37404-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="37404-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="37404-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37404-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37404-117">See also</span></span>

- [<span data-ttu-id="37404-118">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="37404-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
