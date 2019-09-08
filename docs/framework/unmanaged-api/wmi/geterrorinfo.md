---
title: GetErrorInfo — funkcja (niezarządzana dokumentacja interfejsu API)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab801ec7899403f568d953535fcd430a862a2fd8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798580"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="4daf1-103">GetErrorInfo — funkcja</span><span class="sxs-lookup"><span data-stu-id="4daf1-103">GetErrorInfo function</span></span>
<span data-ttu-id="4daf1-104">Pobiera informacje o błędzie z poprzedniego wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="4daf1-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="4daf1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4daf1-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="4daf1-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4daf1-106">Return value</span></span>

<span data-ttu-id="4daf1-107">Wskaźnik do obiektu [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) , jeśli wywołanie funkcji zakończy się pomyślnie lub `null` nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="4daf1-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="4daf1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4daf1-108">Remarks</span></span>

<span data-ttu-id="4daf1-109">Ta funkcja otacza wywołanie metody [IComThreadingInfo:: GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .</span><span class="sxs-lookup"><span data-stu-id="4daf1-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4daf1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4daf1-110">Requirements</span></span>  
 <span data-ttu-id="4daf1-111">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4daf1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4daf1-112">**Nagłówki** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="4daf1-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="4daf1-113">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4daf1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4daf1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4daf1-114">See also</span></span>

- [<span data-ttu-id="4daf1-115">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="4daf1-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
