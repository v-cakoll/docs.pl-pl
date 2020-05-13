---
title: ICorDebugNativeFrame::GetLocalDoubleRegisterValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
ms.openlocfilehash: 21c4d00e4156b9db27ae4188aace19764a2be53e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213078"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="9d933-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d933-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>
<span data-ttu-id="9d933-103">Pobiera wartość argumentu lub zmiennej lokalnej przechowywanej w dwóch określonych rejestrach dla tej ramki natywnej.</span><span class="sxs-lookup"><span data-stu-id="9d933-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d933-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d933-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d933-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d933-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="9d933-106">podczas Wartość wyliczenia "CorDebugRegister —", która określa rejestr zawierający wysokie słowo wartości.</span><span class="sxs-lookup"><span data-stu-id="9d933-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="9d933-107">podczas Wartość `CorDebugRegister` wyliczenia, która określa rejestr zawierający dolny wyraz wartości.</span><span class="sxs-lookup"><span data-stu-id="9d933-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="9d933-108">podczas Liczba całkowita określająca rozmiar podpisu metadanych binarnych, do którego odwołuje się `pvSigBlob` parametr.</span><span class="sxs-lookup"><span data-stu-id="9d933-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="9d933-109">podczas Wartość wskazująca `PCCOR_SIGNATURE` na podpis metadanych binarnych typu wartości.</span><span class="sxs-lookup"><span data-stu-id="9d933-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9d933-110">określoną Wskaźnik do adresu obiektu "ICorDebugValue" reprezentującego pobraną wartość, która jest przechowywana w określonych rejestrach.</span><span class="sxs-lookup"><span data-stu-id="9d933-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d933-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d933-111">Remarks</span></span>  
 <span data-ttu-id="9d933-112">`GetLocalDoubleRegisterValue`Metoda może być używana w ramce natywnej lub w postaci wbudowanej w tryb just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="9d933-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d933-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d933-113">Requirements</span></span>  
 <span data-ttu-id="9d933-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d933-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d933-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9d933-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d933-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9d933-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d933-117">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d933-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d933-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d933-118">See also</span></span>
