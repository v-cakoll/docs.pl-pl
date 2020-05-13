---
title: ICorDebugType::GetBase — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
ms.openlocfilehash: fc406f6e87e5b2be48c6fe7d5fc988774ac5cd11
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379989"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="12504-102">ICorDebugType::GetBase — Metoda</span><span class="sxs-lookup"><span data-stu-id="12504-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="12504-103">Pobiera wskaźnik interfejsu do ICorDebugType, który reprezentuje typ podstawowy, jeśli taki istnieje, typu reprezentowanego przez ten element `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="12504-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12504-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="12504-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12504-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12504-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="12504-106">określoną Wskaźnik do adresu `ICorDebugType` obiektu, który reprezentuje typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="12504-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12504-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="12504-107">Remarks</span></span>  
 <span data-ttu-id="12504-108">Wyszukiwanie typu podstawowego dla typu jest przydatne, aby zaimplementować typowe funkcje debugera, takie jak drukowanie wszystkich pól obiektu lub jego klas nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="12504-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12504-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12504-109">Requirements</span></span>  
 <span data-ttu-id="12504-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12504-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12504-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="12504-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12504-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="12504-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12504-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12504-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
