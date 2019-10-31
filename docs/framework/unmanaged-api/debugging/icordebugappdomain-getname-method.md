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
ms.openlocfilehash: 2c9aa6792885c685195049948a540453b1f5235e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110307"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="71307-102">ICorDebugAppDomain::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="71307-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="71307-103">Pobiera nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71307-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71307-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71307-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71307-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71307-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="71307-106">podczas Rozmiar tablicy `szName`.</span><span class="sxs-lookup"><span data-stu-id="71307-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="71307-107">Ustaw tę wartość na zero, aby ustawić tę metodę w trybie zapytania.</span><span class="sxs-lookup"><span data-stu-id="71307-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="71307-108">określoną Wskaźnik do rozmiaru nazwy lub liczby znaków faktycznie zwracanych w `szName`.</span><span class="sxs-lookup"><span data-stu-id="71307-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="71307-109">W trybie zapytania ta wartość umożliwia obiektowi wywołującemu określenie, jak duży bufor ma zostać przydzielony do nazwy.</span><span class="sxs-lookup"><span data-stu-id="71307-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="71307-110">określoną Tablica, w której jest przechowywana nazwa domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71307-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71307-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71307-111">Remarks</span></span>  
 <span data-ttu-id="71307-112">Debuger wywołuje metodę `GetName` raz, aby uzyskać rozmiar buforu wymaganego dla nazwy.</span><span class="sxs-lookup"><span data-stu-id="71307-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="71307-113">Debuger przydziela bufor, a następnie wywołuje metodę przy drugim czasie, aby wypełnić bufor.</span><span class="sxs-lookup"><span data-stu-id="71307-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="71307-114">Pierwsze wywołanie, aby uzyskać rozmiar nazwy, jest określany jako *tryb zapytania*.</span><span class="sxs-lookup"><span data-stu-id="71307-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71307-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71307-115">Requirements</span></span>  
 <span data-ttu-id="71307-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71307-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71307-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="71307-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71307-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="71307-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71307-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71307-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
