---
title: Geterrorinfo — funkcja (niezarządzany wykaz interfejsów API)
description: Funkcja geterrorinfo — pobiera informacje o błędzie z poprzedniego wywołania funkcji.
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
ms.openlocfilehash: 5f25777402fa31e72cbbf36f58a6c4cc65542979
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44352417"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="2081b-103">Geterrorinfo — funkcja</span><span class="sxs-lookup"><span data-stu-id="2081b-103">GetErrorInfo function</span></span>
<span data-ttu-id="2081b-104">Pobiera informacje o błędzie z poprzedniego wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="2081b-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2081b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2081b-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="2081b-106">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2081b-106">Return value</span></span>

<span data-ttu-id="2081b-107">Wskaźnik do [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) obiektu, jeśli wywołanie funkcji zakończy się pomyślnie, lub `null` Jeśli zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="2081b-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="2081b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2081b-108">Remarks</span></span>

<span data-ttu-id="2081b-109">Ta funkcja zawija wywołanie do [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) metody.</span><span class="sxs-lookup"><span data-stu-id="2081b-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2081b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2081b-110">Requirements</span></span>  
 <span data-ttu-id="2081b-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2081b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2081b-112">**Nagłówek:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="2081b-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="2081b-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2081b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2081b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2081b-114">See also</span></span>  
[<span data-ttu-id="2081b-115">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="2081b-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
