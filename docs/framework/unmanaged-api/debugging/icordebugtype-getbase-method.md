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
ms.openlocfilehash: cff527aa7cde6a13667d47d030a0ef7db96ad5ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122344"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="fd49e-102">ICorDebugType::GetBase — Metoda</span><span class="sxs-lookup"><span data-stu-id="fd49e-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="fd49e-103">Pobiera wskaźnik interfejsu do ICorDebugType, który reprezentuje typ podstawowy, jeśli taki istnieje, typu reprezentowanego przez ten `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="fd49e-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd49e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd49e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd49e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd49e-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="fd49e-106">określoną Wskaźnik do adresu obiektu `ICorDebugType`, który reprezentuje typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="fd49e-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd49e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd49e-107">Remarks</span></span>  
 <span data-ttu-id="fd49e-108">Wyszukiwanie typu podstawowego dla typu jest przydatne, aby zaimplementować typowe funkcje debugera, takie jak drukowanie wszystkich pól obiektu lub jego klas nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="fd49e-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd49e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd49e-109">Requirements</span></span>  
 <span data-ttu-id="fd49e-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd49e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd49e-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fd49e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd49e-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fd49e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd49e-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd49e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
