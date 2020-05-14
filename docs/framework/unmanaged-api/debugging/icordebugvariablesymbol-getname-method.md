---
title: 'ICorDebugVariableSymbol:: GetName — Metoda'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: ea414a39e140c74df736764dbbb1bb3934bda78f
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397127"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="9e09d-102">ICorDebugVariableSymbol:: GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="9e09d-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="9e09d-103">Pobiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9e09d-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e09d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e09d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e09d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e09d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="9e09d-106">podczas Liczba znaków w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="9e09d-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9e09d-107">określoną Wskaźnik do liczby znaków rzeczywiście zapisywana w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="9e09d-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="9e09d-108">Wskaźnik do tablicy znaków, która zawiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9e09d-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e09d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e09d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e09d-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9e09d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e09d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e09d-111">Requirements</span></span>  
 <span data-ttu-id="9e09d-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e09d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e09d-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9e09d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e09d-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9e09d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e09d-115">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e09d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e09d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e09d-116">See also</span></span>

- [<span data-ttu-id="9e09d-117">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e09d-117">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="9e09d-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="9e09d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
