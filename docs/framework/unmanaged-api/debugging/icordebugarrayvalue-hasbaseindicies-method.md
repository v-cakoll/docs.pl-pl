---
title: ICorDebugArrayValue::HasBaseIndicies — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 574df434360dfab644a4c937dac46ebc3871a53a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="4d9fb-102">ICorDebugArrayValue::HasBaseIndicies — Metoda</span><span class="sxs-lookup"><span data-stu-id="4d9fb-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="4d9fb-103">Pobiera wartość wskazującą, czy żadnych wymiarów tej tablicy ma podstawowego indeksu z systemem innym niż zero.</span><span class="sxs-lookup"><span data-stu-id="4d9fb-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d9fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d9fb-104">Syntax</span></span>  
  
```  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d9fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d9fb-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="4d9fb-106">[out] Wskaźnik do wartość logiczna, która jest `true` Jeśli co najmniej jeden wymiar tego `ICorDebugArrayValue` obiekt posiada podstawowy indeks zera; w przeciwnym razie jest wartość logiczna `false`.</span><span class="sxs-lookup"><span data-stu-id="4d9fb-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d9fb-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d9fb-107">Requirements</span></span>  
 <span data-ttu-id="4d9fb-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d9fb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d9fb-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d9fb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d9fb-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d9fb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d9fb-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d9fb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
