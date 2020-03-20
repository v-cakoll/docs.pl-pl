---
title: Funkcja GetErrorInfo (niezarządzane odwołanie do interfejsu API)
description: Funkcja GetErrorInfo pobiera informacje o błędzie z poprzedniego wywołania funkcji.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 802ee66a5be213ac7a599b193ec6de589773ea17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176815"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="d984d-103">GetErrorInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="d984d-103">GetErrorInfo function</span></span>
<span data-ttu-id="d984d-104">Pobiera informacje o błędzie z poprzedniego wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="d984d-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d984d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d984d-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a><span data-ttu-id="d984d-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d984d-106">Return value</span></span>

<span data-ttu-id="d984d-107">Wskaźnik do obiektu [IErrorInfo,](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) jeśli wywołanie `null` funkcji powiedzie się lub jeśli zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d984d-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="d984d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d984d-108">Remarks</span></span>

<span data-ttu-id="d984d-109">Ta funkcja zawija wywołanie metody [IComThreadingInfo::GetErrorInfo.](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)</span><span class="sxs-lookup"><span data-stu-id="d984d-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d984d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d984d-110">Requirements</span></span>  
 <span data-ttu-id="d984d-111">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d984d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d984d-112">**Nagłówek:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="d984d-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="d984d-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d984d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d984d-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d984d-114">See also</span></span>

- [<span data-ttu-id="d984d-115">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="d984d-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
