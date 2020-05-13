---
title: ICorDebugLoadedModule::GetName — metoda
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 4a0c4e99f23dc949b0bbaa8bbda35cff1537cf3c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209867"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="a2b73-102">ICorDebugLoadedModule::GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="a2b73-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="a2b73-103">Pobiera nazwę załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="a2b73-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2b73-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2b73-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2b73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2b73-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="a2b73-106">podczas Liczba znaków w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="a2b73-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a2b73-107">określoną Wskaźnik do liczby znaków rzeczywiście zapisywana w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="a2b73-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="a2b73-108">określoną Tablica znaków, która zawiera nazwę załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="a2b73-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2b73-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2b73-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2b73-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a2b73-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2b73-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2b73-111">Requirements</span></span>  
 <span data-ttu-id="a2b73-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2b73-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2b73-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a2b73-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2b73-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a2b73-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2b73-115">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2b73-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2b73-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2b73-116">See also</span></span>

- [<span data-ttu-id="a2b73-117">ICorDebugLoadedModule — interfejs</span><span class="sxs-lookup"><span data-stu-id="a2b73-117">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="a2b73-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="a2b73-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
