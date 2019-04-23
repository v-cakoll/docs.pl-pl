---
title: ICorDebugMDA::GetDescription — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 998d4baf03123f1ffc174b2a7aeed0ff4a25b001
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133492"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="ebd33-102">ICorDebugMDA::GetDescription — Metoda</span><span class="sxs-lookup"><span data-stu-id="ebd33-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="ebd33-103">Pobiera ciąg zawierający opis zarządzanego Asystenta debugowania (MDA), reprezentowana przez [icordebugmda —](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ebd33-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebd33-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebd33-104">Syntax</span></span>  
  
```  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebd33-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebd33-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ebd33-106">[in] Rozmiar buforu ciągu, w którym będą przechowywane opis.</span><span class="sxs-lookup"><span data-stu-id="ebd33-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ebd33-107">[out] Wskaźnik do liczby bajtów zwróconych w buforu ciągu.</span><span class="sxs-lookup"><span data-stu-id="ebd33-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ebd33-108">[out] Bufor ciągu zawierający opis MDA.</span><span class="sxs-lookup"><span data-stu-id="ebd33-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebd33-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ebd33-109">Remarks</span></span>  
 <span data-ttu-id="ebd33-110">Ciąg może być zerowej długości.</span><span class="sxs-lookup"><span data-stu-id="ebd33-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebd33-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ebd33-111">Requirements</span></span>  
 <span data-ttu-id="ebd33-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebd33-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebd33-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebd33-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebd33-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebd33-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebd33-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebd33-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebd33-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebd33-116">See also</span></span>

- [<span data-ttu-id="ebd33-117">ICorDebugMDA, interfejs</span><span class="sxs-lookup"><span data-stu-id="ebd33-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="ebd33-118">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="ebd33-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
