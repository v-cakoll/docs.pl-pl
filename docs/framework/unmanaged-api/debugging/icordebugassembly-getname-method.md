---
title: ICorDebugAssembly::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3077e0494816a083d97839d66d06b18130e5dac8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645581"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="1ac5f-102">ICorDebugAssembly::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="1ac5f-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="1ac5f-103">Pobiera nazwę zestawu, który to `ICorDebugAssembly` wystąpienie reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="1ac5f-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ac5f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ac5f-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ac5f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ac5f-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="1ac5f-106">[in] Rozmiar `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1ac5f-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1ac5f-107">[out] Wskaźnik na liczbę całkowitą określającą rzeczywista długość nazwy.</span><span class="sxs-lookup"><span data-stu-id="1ac5f-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="1ac5f-108">[out] Tablica, która przechowuje nazwę.</span><span class="sxs-lookup"><span data-stu-id="1ac5f-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ac5f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ac5f-109">Remarks</span></span>  
 <span data-ttu-id="1ac5f-110">`GetName` Metoda zwraca pełną ścieżkę i nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="1ac5f-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ac5f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ac5f-111">Requirements</span></span>  
 <span data-ttu-id="1ac5f-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ac5f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ac5f-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ac5f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ac5f-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ac5f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ac5f-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ac5f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
