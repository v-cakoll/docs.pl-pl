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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c24d6e9c42a091eafbe6d4bdee2bb4e055fd8852
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772034"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="ecad2-102">ICorDebugType::GetBase — Metoda</span><span class="sxs-lookup"><span data-stu-id="ecad2-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="ecad2-103">Pobiera wskaźnik interfejsu do ICorDebugType, który reprezentuje typ podstawowy, jeśli taki istnieje, typu reprezentowanego przez ten `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="ecad2-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecad2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecad2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecad2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecad2-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="ecad2-106">[out] Wskaźnik na adres `ICorDebugType` obiekt, który reprezentuje typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="ecad2-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecad2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecad2-107">Remarks</span></span>  
 <span data-ttu-id="ecad2-108">Wyszukiwanie z typem podstawowym typem jest przydatne do zaimplementowania typowych funkcji debugowania, takich jak drukowanie wszystkich pól obiektu lub jej klas nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="ecad2-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecad2-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ecad2-109">Requirements</span></span>  
 <span data-ttu-id="ecad2-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecad2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecad2-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ecad2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ecad2-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ecad2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecad2-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecad2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
