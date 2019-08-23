---
title: ICorDebugLoadedModule::GetName — metoda
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63341bcd6079688ed1a8e18ec8c422bca1427c72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910082"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="38079-102">ICorDebugLoadedModule::GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="38079-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="38079-103">Pobiera nazwę załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="38079-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38079-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38079-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38079-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38079-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="38079-106">podczas Liczba znaków w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="38079-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="38079-107">określoną Wskaźnik do liczby znaków rzeczywiście zapisywana `szName` w buforze.</span><span class="sxs-lookup"><span data-stu-id="38079-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="38079-108">określoną Tablica znaków, która zawiera nazwę załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="38079-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38079-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38079-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38079-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="38079-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38079-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38079-111">Requirements</span></span>  
 <span data-ttu-id="38079-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38079-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38079-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38079-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38079-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38079-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38079-115">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38079-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38079-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38079-116">See also</span></span>

- [<span data-ttu-id="38079-117">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="38079-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="38079-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="38079-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
