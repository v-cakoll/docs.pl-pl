---
title: ICorDebugNativeFrame::GetLocalRegisterValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type:
- apiref
ms.openlocfilehash: 132e0868426670ba61d8ee12ba7007be1a8a52de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139395"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="09365-102">ICorDebugNativeFrame::GetLocalRegisterValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="09365-102">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>
<span data-ttu-id="09365-103">Pobiera wartość argumentu lub zmiennej lokalnej przechowywanej w określonym rejestrze dla tej ramki natywnej.</span><span class="sxs-lookup"><span data-stu-id="09365-103">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09365-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09365-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09365-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09365-105">Parameters</span></span>  
 `reg`  
 <span data-ttu-id="09365-106">podczas Wartość wyliczenia "CorDebugRegister —", która określa rejestr zawierający wartość.</span><span class="sxs-lookup"><span data-stu-id="09365-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="09365-107">podczas Liczba całkowita określająca rozmiar podpisu metadanych binarnych, do którego odwołuje się parametr `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="09365-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="09365-108">podczas Wartość `PCCOR_SIGNATURE`, która wskazuje na podpis metadanych binarnych typu wartości.</span><span class="sxs-lookup"><span data-stu-id="09365-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="09365-109">określoną Wskaźnik do adresu obiektu "ICorDebugValue" reprezentującego pobraną wartość, która jest przechowywana w określonym rejestrze.</span><span class="sxs-lookup"><span data-stu-id="09365-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09365-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09365-110">Remarks</span></span>  
 <span data-ttu-id="09365-111">Metody `GetLocalRegisterValue` można użyć w ramce natywnej lub w ramce skompilowanej just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="09365-111">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09365-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09365-112">Requirements</span></span>  
 <span data-ttu-id="09365-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09365-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09365-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="09365-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09365-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="09365-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09365-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09365-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09365-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09365-117">See also</span></span>
