---
title: 'ICorDebugVariableSymbol:: SetValue — Metoda'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: fe6b63e4c0706dd69478753b3512f606e73bee7c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790857"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="c46f7-102">ICorDebugVariableSymbol:: SetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="c46f7-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="c46f7-103">Przypisuje wartość tablicy bajtów do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c46f7-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c46f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c46f7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c46f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c46f7-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="c46f7-106">podczas Przesunięcie początkowe w zmiennej, w której ma zostać ustawiona wartość.</span><span class="sxs-lookup"><span data-stu-id="c46f7-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="c46f7-107">Ten parametr jest używany podczas zapisywania do pól elementu członkowskiego w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="c46f7-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="c46f7-108">podczas Identyfikator wątku, którego kontekst musi zostać zaktualizowany w celu odzwierciedlenia nowej wartości.</span><span class="sxs-lookup"><span data-stu-id="c46f7-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="c46f7-109">podczas Rozmiar w bajtach kontekstu wątku.</span><span class="sxs-lookup"><span data-stu-id="c46f7-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="c46f7-110">podczas Kontekst wątku używany do zapisania wartości.</span><span class="sxs-lookup"><span data-stu-id="c46f7-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="c46f7-111">podczas Rozmiar w bajtach buforu `pValue`.</span><span class="sxs-lookup"><span data-stu-id="c46f7-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="c46f7-112">podczas Bufor, który zawiera wartość do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="c46f7-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c46f7-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c46f7-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c46f7-114">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c46f7-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c46f7-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c46f7-115">Requirements</span></span>  
 <span data-ttu-id="c46f7-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c46f7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c46f7-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c46f7-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c46f7-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c46f7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c46f7-119">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c46f7-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c46f7-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c46f7-120">See also</span></span>

- [<span data-ttu-id="c46f7-121">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="c46f7-121">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="c46f7-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c46f7-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
