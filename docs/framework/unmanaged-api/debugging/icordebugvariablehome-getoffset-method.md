---
title: "ICorDebugVariableHome::GetOffset — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetOffset
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ddedc83e4e51cf12a3f8a0504d90bda7f944a6d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="d9948-102">ICorDebugVariableHome::GetOffset — metoda</span><span class="sxs-lookup"><span data-stu-id="d9948-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="d9948-103">Pobiera przesunięcie z podstawowej rejestru dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d9948-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9948-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9948-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9948-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9948-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="d9948-106">[out] Przesunięcie z podstawowej rejestru.</span><span class="sxs-lookup"><span data-stu-id="d9948-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9948-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d9948-107">Return Value</span></span>  
 <span data-ttu-id="d9948-108">Metoda zwraca następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="d9948-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="d9948-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="d9948-109">Value</span></span>|<span data-ttu-id="d9948-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d9948-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="d9948-111">Zmienna znajduje się w lokalizacji pamięci względem rejestru.</span><span class="sxs-lookup"><span data-stu-id="d9948-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="d9948-112">Zmienna nie jest w lokalizacji pamięci względem rejestru.</span><span class="sxs-lookup"><span data-stu-id="d9948-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9948-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9948-113">Requirements</span></span>  
 <span data-ttu-id="d9948-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9948-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9948-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9948-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9948-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9948-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9948-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9948-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9948-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9948-118">See Also</span></span>  
 [<span data-ttu-id="d9948-119">Interfejs ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="d9948-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
