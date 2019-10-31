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
ms.openlocfilehash: bfe77982b88b2fc96dc2846b9db04df28bfc0c38
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131452"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="0c609-102">ICorDebugMDA::GetDescription — Metoda</span><span class="sxs-lookup"><span data-stu-id="0c609-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="0c609-103">Pobiera ciąg zawierający opis zarządzanego asystenta debugowania (MDA) reprezentowanego przez [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0c609-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c609-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c609-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c609-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c609-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="0c609-106">podczas Rozmiar buforu ciągu, który będzie przechowywać opis.</span><span class="sxs-lookup"><span data-stu-id="0c609-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0c609-107">określoną Wskaźnik do liczby bajtów zwróconych w buforze ciągów.</span><span class="sxs-lookup"><span data-stu-id="0c609-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="0c609-108">określoną Bufor ciągu zawierający opis MDA.</span><span class="sxs-lookup"><span data-stu-id="0c609-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c609-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c609-109">Remarks</span></span>  
 <span data-ttu-id="0c609-110">Ciąg może mieć długość zero.</span><span class="sxs-lookup"><span data-stu-id="0c609-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c609-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c609-111">Requirements</span></span>  
 <span data-ttu-id="0c609-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c609-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c609-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0c609-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c609-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0c609-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c609-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c609-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c609-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c609-116">See also</span></span>

- [<span data-ttu-id="0c609-117">ICorDebugMDA, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c609-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="0c609-118">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="0c609-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
