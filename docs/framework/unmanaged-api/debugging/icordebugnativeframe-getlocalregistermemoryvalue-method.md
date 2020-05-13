---
title: ICorDebugNativeFrame::GetLocalRegisterMemoryValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type:
- apiref
ms.openlocfilehash: f16150ad7d9ecec4b4aceee5c9266e9a7859f1cb
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213299"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="d3abb-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3abb-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="d3abb-103">Pobiera wartość argumentu lub zmiennej lokalnej, w której dolny wyraz i duże słowo są przechowywane w lokalizacji pamięci i określone zarejestrowane odpowiednio dla tej ramki natywnej.</span><span class="sxs-lookup"><span data-stu-id="d3abb-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3abb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3abb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3abb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3abb-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="d3abb-106">podczas Wartość wyliczenia "CorDebugRegister —", która określa rejestr zawierający wysokie słowo wartości.</span><span class="sxs-lookup"><span data-stu-id="d3abb-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="d3abb-107">podczas Wartość określająca `CORDB_ADDRESS` lokalizację pamięci zawierającą dolne słowo wartości.</span><span class="sxs-lookup"><span data-stu-id="d3abb-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d3abb-108">podczas Liczba całkowita określająca rozmiar podpisu metadanych binarnych, do którego odwołuje się `pvSigBlob` parametr.</span><span class="sxs-lookup"><span data-stu-id="d3abb-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d3abb-109">podczas Wartość wskazująca `PCCOR_SIGNATURE` na podpis metadanych binarnych typu wartości.</span><span class="sxs-lookup"><span data-stu-id="d3abb-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d3abb-110">określoną Wskaźnik do adresu obiektu "ICorDebugValue" reprezentującego pobraną wartość, która jest przechowywana w określonym rejestrze i lokalizacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="d3abb-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3abb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3abb-111">Requirements</span></span>  
 <span data-ttu-id="d3abb-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3abb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3abb-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d3abb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3abb-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d3abb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3abb-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3abb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3abb-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3abb-116">See also</span></span>
