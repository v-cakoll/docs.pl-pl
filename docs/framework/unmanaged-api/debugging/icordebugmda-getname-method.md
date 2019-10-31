---
title: ICorDebugMDA::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
ms.openlocfilehash: 1b19ce5e9f795fd9ff4dd15e10256a150063a314
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128042"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="b4281-102">ICorDebugMDA::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="b4281-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="b4281-103">Pobiera ciąg zawierający nazwę zarządzanego asystenta debugowania (MDA) reprezentowanego przez [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b4281-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4281-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4281-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4281-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4281-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b4281-106">podczas Rozmiar tablicy `szName`.</span><span class="sxs-lookup"><span data-stu-id="b4281-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b4281-107">określoną Wskaźnik do długości nazwy.</span><span class="sxs-lookup"><span data-stu-id="b4281-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="b4281-108">określoną Tablica, w której ma zostać przechowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="b4281-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4281-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4281-109">Remarks</span></span>  
 <span data-ttu-id="b4281-110">Nazwy MDA są unikatowymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="b4281-110">MDA names are unique values.</span></span> <span data-ttu-id="b4281-111">Metoda `GetName` jest wygodną alternatywą wydajności dla pobierania strumienia XML i wyodrębniania nazwy ze strumienia na podstawie schematu.</span><span class="sxs-lookup"><span data-stu-id="b4281-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4281-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4281-112">Requirements</span></span>  
 <span data-ttu-id="b4281-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4281-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4281-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b4281-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4281-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b4281-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4281-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4281-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4281-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4281-117">See also</span></span>

- [<span data-ttu-id="b4281-118">ICorDebugMDA, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4281-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="b4281-119">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="b4281-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
