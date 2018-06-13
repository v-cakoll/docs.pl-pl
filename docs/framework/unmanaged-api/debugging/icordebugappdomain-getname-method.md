---
title: ICorDebugAppDomain::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84f895e749fc8f2520dbce3caf9e6c11fda78a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405772"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="0b277-102">ICorDebugAppDomain::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b277-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="0b277-103">Pobiera nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0b277-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b277-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b277-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b277-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b277-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="0b277-106">[in] Rozmiar `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="0b277-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="0b277-107">Ta wartość zero, aby umieścić tę metodę w trybie zapytania.</span><span class="sxs-lookup"><span data-stu-id="0b277-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0b277-108">[out] Wskaźnik do rozmiaru nazwę lub liczbę znaków, które faktycznie zwracane w `szName`.</span><span class="sxs-lookup"><span data-stu-id="0b277-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="0b277-109">W trybie zapytania, ta wartość umożliwia wywołującego wiedzieć, jak duży buforu do przydzielenia dla nazwy.</span><span class="sxs-lookup"><span data-stu-id="0b277-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="0b277-110">[out] Tablica, która przechowuje nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0b277-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b277-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b277-111">Remarks</span></span>  
 <span data-ttu-id="0b277-112">Wywołuje debugera `GetName` metodę raz, aby pobrać rozmiaru buforu potrzebne dla nazwy.</span><span class="sxs-lookup"><span data-stu-id="0b277-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="0b277-113">Debuger przydziela buforu, a następnie wywołuje metodę po raz drugi do wypełnienia buforu.</span><span class="sxs-lookup"><span data-stu-id="0b277-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="0b277-114">Pierwsze wywołanie, aby uzyskać nazwę, rozmiar jest określany jako *tryb zapytania*.</span><span class="sxs-lookup"><span data-stu-id="0b277-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b277-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b277-115">Requirements</span></span>  
 <span data-ttu-id="0b277-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b277-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b277-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b277-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b277-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b277-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b277-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b277-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
