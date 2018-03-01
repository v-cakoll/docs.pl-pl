---
title: "ICorDebugArrayValue::GetElement — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9aba987aa6f806bfe1608e081aac4cb501cd23fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="3840b-102">ICorDebugArrayValue::GetElement — Metoda</span><span class="sxs-lookup"><span data-stu-id="3840b-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="3840b-103">Pobiera wartość elementu podanej tablicy.</span><span class="sxs-lookup"><span data-stu-id="3840b-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3840b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3840b-104">Syntax</span></span>  
  
```  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3840b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3840b-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="3840b-106">[in] Liczba wymiarów tego `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3840b-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="3840b-107">Ta wartość jest również rozmiar `indices` tablicy, ponieważ jego rozmiar jest równa liczbie wymiarów `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3840b-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="3840b-108">[in] Tablica wartości indeksów, z których każdy określa pozycja w wymiarze z `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3840b-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="3840b-109">Ta wartość nie może być pusta.</span><span class="sxs-lookup"><span data-stu-id="3840b-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="3840b-110">[out] Wskaźnik do adres obiektu ICorDebugValue reprezentujący wartość określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="3840b-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3840b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3840b-111">Requirements</span></span>  
 <span data-ttu-id="3840b-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3840b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3840b-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3840b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3840b-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3840b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3840b-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3840b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
