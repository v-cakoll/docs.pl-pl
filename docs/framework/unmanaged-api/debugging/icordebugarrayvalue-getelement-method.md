---
title: ICorDebugArrayValue::GetElement — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 356f7ec9c50ce511883cbf0f5fbcb729493c92af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737572"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="ab3b8-102">ICorDebugArrayValue::GetElement — Metoda</span><span class="sxs-lookup"><span data-stu-id="ab3b8-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="ab3b8-103">Pobiera wartość elementu danej tablicy.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab3b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab3b8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab3b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab3b8-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="ab3b8-106">[in] Liczba wymiarów to `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="ab3b8-107">Ta wartość jest również rozmiar `indices` tablicy, ponieważ jego rozmiar jest równa liczbie wymiarów `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="ab3b8-108">[in] Tablica wartości indeksu, z których każdy określa położenie w obrębie wymiaru `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="ab3b8-109">Ta wartość nie może być zerowy.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ab3b8-110">[out] Wskaźnik do adresu obiektu ICorDebugValue, która reprezentuje wartość określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab3b8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab3b8-111">Requirements</span></span>  
 <span data-ttu-id="ab3b8-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab3b8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab3b8-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab3b8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab3b8-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab3b8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab3b8-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab3b8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
