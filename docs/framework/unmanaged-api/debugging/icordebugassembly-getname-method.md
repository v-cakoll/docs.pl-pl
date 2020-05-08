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
ms.openlocfilehash: daf5319f5d57f44cb20ce9f28d3c7b84c7015ff6
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894917"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="e9daf-102">ICorDebugAssembly::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="e9daf-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="e9daf-103">Pobiera nazwę zestawu reprezentowanego przez to `ICorDebugAssembly` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="e9daf-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9daf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9daf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9daf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9daf-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e9daf-106">podczas Rozmiar `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="e9daf-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e9daf-107">określoną Wskaźnik do liczby całkowitej, która określa rzeczywistą długość nazwy.</span><span class="sxs-lookup"><span data-stu-id="e9daf-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="e9daf-108">określoną Tablica, która przechowuje nazwę.</span><span class="sxs-lookup"><span data-stu-id="e9daf-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9daf-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9daf-109">Remarks</span></span>  
 <span data-ttu-id="e9daf-110">`GetName` Metoda zwraca pełną ścieżkę i nazwę pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="e9daf-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9daf-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9daf-111">Requirements</span></span>  
 <span data-ttu-id="e9daf-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9daf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9daf-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e9daf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9daf-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e9daf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9daf-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9daf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
