---
title: "ICorDebugModule::GetName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b10e0eed3c2df8781aa7085cc43157894cc6e2c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="aa61e-102">ICorDebugModule::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa61e-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="aa61e-103">Pobiera nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="aa61e-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa61e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa61e-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa61e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa61e-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="aa61e-106">[in] Rozmiar `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="aa61e-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="aa61e-107">[in] Wskaźnik do długość nazwy zwracane.</span><span class="sxs-lookup"><span data-stu-id="aa61e-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="aa61e-108">[out] Tablica, która przechowuje nazwę zwrócony.</span><span class="sxs-lookup"><span data-stu-id="aa61e-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa61e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aa61e-109">Remarks</span></span>  
 <span data-ttu-id="aa61e-110">`GetName` Metoda zwraca wartość S_OK HRESULT, jeśli nazwa pliku modułu jest zgodna z nazwą na dysku.</span><span class="sxs-lookup"><span data-stu-id="aa61e-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="aa61e-111">`GetName`Zwraca S_FALSE HRESULT, jeśli nazwa metalowych, takich jak moduł dynamicznej lub w pamięci.</span><span class="sxs-lookup"><span data-stu-id="aa61e-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa61e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa61e-112">Requirements</span></span>  
 <span data-ttu-id="aa61e-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa61e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa61e-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa61e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa61e-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa61e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa61e-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa61e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa61e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa61e-117">See Also</span></span>  
    
 
