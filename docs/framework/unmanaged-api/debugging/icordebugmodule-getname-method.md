---
title: ICorDebugModule::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
ms.openlocfilehash: b27e7a2cdcbfc3a88a734230118d99c2dd5c700e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129536"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="6a429-102">ICorDebugModule::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="6a429-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="6a429-103">Pobiera nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="6a429-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a429-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a429-104">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a429-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a429-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="6a429-106">podczas Rozmiar tablicy `szName`.</span><span class="sxs-lookup"><span data-stu-id="6a429-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6a429-107">podczas Wskaźnik do długości zwracanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="6a429-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="6a429-108">określoną Tablica przechowująca zwróconą nazwę.</span><span class="sxs-lookup"><span data-stu-id="6a429-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a429-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a429-109">Remarks</span></span>  
 <span data-ttu-id="6a429-110">Metoda `GetName` zwraca wartość HRESULT S_OK, jeśli nazwa pliku modułu jest zgodna z nazwą na dysku.</span><span class="sxs-lookup"><span data-stu-id="6a429-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="6a429-111">`GetName` zwraca S_FALSE HRESULT, jeśli nazwa jest wypełniania, na przykład w module dynamicznym lub w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6a429-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a429-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a429-112">Requirements</span></span>  
 <span data-ttu-id="6a429-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a429-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a429-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a429-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a429-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6a429-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a429-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a429-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a429-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a429-117">See also</span></span>
