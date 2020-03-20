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
ms.openlocfilehash: 45d27fca888bdabedf197525c63dbd03af7ba1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179088"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="beb88-102">ICorDebugAppDomain::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="beb88-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="beb88-103">Pobiera nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="beb88-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beb88-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="beb88-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="beb88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="beb88-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="beb88-106">[w] Rozmiar tablicy. `szName`</span><span class="sxs-lookup"><span data-stu-id="beb88-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="beb88-107">Ustaw tę wartość na zero, aby umieścić tę metodę w trybie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="beb88-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="beb88-108">[na zewnątrz] Wskaźnik do rozmiaru nazwy lub liczby znaków faktycznie `szName`zwróconych w .</span><span class="sxs-lookup"><span data-stu-id="beb88-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="beb88-109">W trybie kwerendy ta wartość pozwala wywołującemu wiedzieć, jak duży bufor do przydzielenia dla nazwy.</span><span class="sxs-lookup"><span data-stu-id="beb88-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="beb88-110">[na zewnątrz] Tablica, która przechowuje nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="beb88-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="beb88-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="beb88-111">Remarks</span></span>  
 <span data-ttu-id="beb88-112">Debuger wywołuje `GetName` metodę raz, aby uzyskać rozmiar buforu wymaganego dla nazwy.</span><span class="sxs-lookup"><span data-stu-id="beb88-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="beb88-113">Debuger przydziela bufor, a następnie wywołuje metodę po raz drugi, aby wypełnić bufor.</span><span class="sxs-lookup"><span data-stu-id="beb88-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="beb88-114">Pierwsze wywołanie, aby uzyskać rozmiar nazwy, jest określany jako *tryb kwerendy*.</span><span class="sxs-lookup"><span data-stu-id="beb88-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beb88-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="beb88-115">Requirements</span></span>  
 <span data-ttu-id="beb88-116">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="beb88-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beb88-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="beb88-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="beb88-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="beb88-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="beb88-119">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beb88-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
