---
title: ICorDebugMDA::GetXML — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e78b8a2069671d0fe790956ca914225325a78bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228825"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="9a317-102">ICorDebugMDA::GetXML — Metoda</span><span class="sxs-lookup"><span data-stu-id="9a317-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="9a317-103">Pobiera pełną strumień XML skojarzony z zarządzanego Asystenta debugowania (MDA), reprezentowana przez [icordebugmda —](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="9a317-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a317-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a317-104">Syntax</span></span>  
  
```  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a317-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a317-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="9a317-106">[in] Rozmiar `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="9a317-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9a317-107">[out] Wskaźnik do długość strumienia XML.</span><span class="sxs-lookup"><span data-stu-id="9a317-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="9a317-108">[out] Tablica do przechowywania strumień XML.</span><span class="sxs-lookup"><span data-stu-id="9a317-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="9a317-109">Tablica może być pusta.</span><span class="sxs-lookup"><span data-stu-id="9a317-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a317-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a317-110">Remarks</span></span>  
 <span data-ttu-id="9a317-111">`GetXML` Metoda może wpłynąć na wydajność, w zależności od rozmiaru skojarzonego strumienia XML.</span><span class="sxs-lookup"><span data-stu-id="9a317-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a317-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a317-112">Requirements</span></span>  
 <span data-ttu-id="9a317-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a317-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a317-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a317-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a317-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a317-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9a317-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9a317-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9a317-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a317-117">See also</span></span>

- [<span data-ttu-id="9a317-118">ICorDebugMDA — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9a317-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="9a317-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="9a317-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
