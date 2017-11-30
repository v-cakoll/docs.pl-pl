---
title: "ICorDebugMDA::GetDescription — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA.GetDescription
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 18ffd8ab92829404b1eadae33f067a1ea8391396
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="1086f-102">ICorDebugMDA::GetDescription — Metoda</span><span class="sxs-lookup"><span data-stu-id="1086f-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="1086f-103">Pobiera ciąg zawierający opis zarządzany Asystent debugowania (MDA) reprezentowany przez [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="1086f-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1086f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1086f-104">Syntax</span></span>  
  
```  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1086f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1086f-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="1086f-106">[in] Rozmiar buforu ciągu, w którym będzie przechowywany opis.</span><span class="sxs-lookup"><span data-stu-id="1086f-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1086f-107">[out] Wskaźnik do liczba bajtów zwrócona w buforze ciągu.</span><span class="sxs-lookup"><span data-stu-id="1086f-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="1086f-108">[out] Bufor ciąg zawierający opis MDA.</span><span class="sxs-lookup"><span data-stu-id="1086f-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1086f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1086f-109">Remarks</span></span>  
 <span data-ttu-id="1086f-110">Ten ciąg może być zerowej długości.</span><span class="sxs-lookup"><span data-stu-id="1086f-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1086f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1086f-111">Requirements</span></span>  
 <span data-ttu-id="1086f-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1086f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1086f-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1086f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1086f-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1086f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1086f-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1086f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1086f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1086f-116">See Also</span></span>  
 [<span data-ttu-id="1086f-117">ICorDebugMDA — interfejs</span><span class="sxs-lookup"><span data-stu-id="1086f-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="1086f-118">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="1086f-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
