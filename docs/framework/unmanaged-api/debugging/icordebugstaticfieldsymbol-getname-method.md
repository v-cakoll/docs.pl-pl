---
title: 'ICorDebugStaticFieldSymbol:: GetName — Metoda'
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: 75f5324296f9b42406157d06351f7e680a749444
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378750"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="f5f74-102">ICorDebugStaticFieldSymbol:: GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="f5f74-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="f5f74-103">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="f5f74-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5f74-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5f74-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5f74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5f74-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f5f74-106">podczas Liczba znaków w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="f5f74-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f5f74-107">określoną Wskaźnik do liczby znaków rzeczywiście zapisywana w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="f5f74-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="f5f74-108">określoną Tablica znaków przechowująca zwróconą nazwę.</span><span class="sxs-lookup"><span data-stu-id="f5f74-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5f74-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5f74-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5f74-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f5f74-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5f74-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5f74-111">Requirements</span></span>  
 <span data-ttu-id="f5f74-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5f74-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5f74-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5f74-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5f74-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f5f74-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5f74-115">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5f74-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5f74-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5f74-116">See also</span></span>

- [<span data-ttu-id="f5f74-117">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5f74-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="f5f74-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f5f74-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
