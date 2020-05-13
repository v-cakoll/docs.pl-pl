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
ms.openlocfilehash: 55342c803756aa10c2e7c835d9e1d58b439bb36c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212545"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="f13a8-102">ICorDebugModule::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="f13a8-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="f13a8-103">Pobiera nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="f13a8-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f13a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f13a8-104">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f13a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f13a8-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="f13a8-106">podczas Rozmiar `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f13a8-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f13a8-107">podczas Wskaźnik do długości zwracanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="f13a8-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="f13a8-108">określoną Tablica przechowująca zwróconą nazwę.</span><span class="sxs-lookup"><span data-stu-id="f13a8-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f13a8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f13a8-109">Remarks</span></span>  
 <span data-ttu-id="f13a8-110">`GetName`Metoda zwraca S_OK HRESULT, jeśli nazwa pliku modułu jest zgodna z nazwą na dysku.</span><span class="sxs-lookup"><span data-stu-id="f13a8-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="f13a8-111">`GetName`Zwraca S_FALSE HRESULT, jeśli nazwa jest wypełniania, na przykład w module dynamicznym lub w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f13a8-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f13a8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f13a8-112">Requirements</span></span>  
 <span data-ttu-id="f13a8-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f13a8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f13a8-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f13a8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f13a8-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f13a8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f13a8-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f13a8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f13a8-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f13a8-117">See also</span></span>
