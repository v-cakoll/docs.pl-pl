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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9794a44bfb0bd1b4739689359832ba8500c6e2ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539613"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="3d608-102">ICorDebugNativeFrame::GetLocalRegisterValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="3d608-102">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>
<span data-ttu-id="3d608-103">Pobiera wartość argumentu lub zmiennej lokalnej, która jest przechowywana w rejestrze określonej dla tej ramki natywne.</span><span class="sxs-lookup"><span data-stu-id="3d608-103">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d608-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d608-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d608-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d608-105">Parameters</span></span>  
 `reg`  
 <span data-ttu-id="3d608-106">[in] Wartość wyliczenia "cordebugregister —", który określa rejestru zawierającego wartość.</span><span class="sxs-lookup"><span data-stu-id="3d608-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3d608-107">[in] Liczba całkowita określająca rozmiar podpisu metadanych binarny, który odwołuje się do niej `pvSigBlob` parametru.</span><span class="sxs-lookup"><span data-stu-id="3d608-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3d608-108">[in] A `PCCOR_SIGNATURE` wartość, która wskazuje podpisu metadanych binarny o typie wartości.</span><span class="sxs-lookup"><span data-stu-id="3d608-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="3d608-109">[out] Wskaźnik na adres "ICorDebugValue" obiekt reprezentujący pobrana wartość, która jest przechowywana w określonej rejestru.</span><span class="sxs-lookup"><span data-stu-id="3d608-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d608-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d608-110">Remarks</span></span>  
 <span data-ttu-id="3d608-111">`GetLocalRegisterValue` Metoda może być używana w ramka natywna lub just-in-time (JIT)-skompilowany ramki.</span><span class="sxs-lookup"><span data-stu-id="3d608-111">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d608-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d608-112">Requirements</span></span>  
 <span data-ttu-id="3d608-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d608-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d608-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d608-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d608-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d608-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d608-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d608-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d608-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d608-117">See also</span></span>

