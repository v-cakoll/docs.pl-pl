---
title: ICorDebugStringValue::GetString — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bf62d8855b3f9de5629b9cfc6e0bcd0878a0d17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987366"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="44b93-102">ICorDebugStringValue::GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="44b93-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="44b93-103">Pobiera ciąg odwołuje się ten icordebugstringvalue —.</span><span class="sxs-lookup"><span data-stu-id="44b93-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44b93-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="44b93-104">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]   
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44b93-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44b93-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="44b93-106">[in] Rozmiar `szString` tablicy.</span><span class="sxs-lookup"><span data-stu-id="44b93-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="44b93-107">[out] Wskaźnik do liczby znaków zwracane w `szString` tablicy.</span><span class="sxs-lookup"><span data-stu-id="44b93-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="44b93-108">[out] Tablica, która przechowuje pobraną ciągu.</span><span class="sxs-lookup"><span data-stu-id="44b93-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44b93-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44b93-109">Requirements</span></span>  
 <span data-ttu-id="44b93-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44b93-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44b93-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44b93-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44b93-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44b93-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44b93-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44b93-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
