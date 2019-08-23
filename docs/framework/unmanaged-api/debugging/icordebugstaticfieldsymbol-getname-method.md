---
title: 'ICorDebugStaticFieldSymbol:: GetName — Metoda'
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2187a205b41388d191ad4f06db6d6caa86971e13
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913415"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="bbd9c-102">ICorDebugStaticFieldSymbol:: GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="bbd9c-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="bbd9c-103">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="bbd9c-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbd9c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbd9c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbd9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bbd9c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="bbd9c-106">podczas Liczba znaków w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="bbd9c-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="bbd9c-107">określoną Wskaźnik do liczby znaków rzeczywiście zapisywana `szName` w buforze.</span><span class="sxs-lookup"><span data-stu-id="bbd9c-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="bbd9c-108">określoną Tablica znaków przechowująca zwróconą nazwę.</span><span class="sxs-lookup"><span data-stu-id="bbd9c-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbd9c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bbd9c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bbd9c-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bbd9c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbd9c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bbd9c-111">Requirements</span></span>  
 <span data-ttu-id="bbd9c-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbd9c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbd9c-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbd9c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbd9c-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbd9c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbd9c-115">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbd9c-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd9c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bbd9c-116">See also</span></span>

- [<span data-ttu-id="bbd9c-117">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="bbd9c-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="bbd9c-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bbd9c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
