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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ae9bc5925634f8bba71731a0c51eb19cf9eec04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663956"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="c7196-102">ICorDebugModule::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="c7196-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="c7196-103">Pobiera nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="c7196-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7196-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7196-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7196-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7196-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="c7196-106">[in] Rozmiar `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c7196-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c7196-107">[in] Wskaźnik do długości nazwy zwrócone.</span><span class="sxs-lookup"><span data-stu-id="c7196-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="c7196-108">[out] Tablica, która przechowuje nazwę zwracanego.</span><span class="sxs-lookup"><span data-stu-id="c7196-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7196-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7196-109">Remarks</span></span>  
 <span data-ttu-id="c7196-110">`GetName` Metoda zwraca wartość HRESULT S_OK, jeśli nazwa pliku modułu jest zgodna z nazwą, na dysku.</span><span class="sxs-lookup"><span data-stu-id="c7196-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="c7196-111">`GetName` Zwraca wartość HRESULT S_FALSE, jeśli nazwa jest metalowych, tak samo jak w przypadku modułu dynamicznego lub w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c7196-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7196-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7196-112">Requirements</span></span>  
 <span data-ttu-id="c7196-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7196-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7196-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7196-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7196-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7196-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7196-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7196-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7196-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7196-117">See also</span></span>


