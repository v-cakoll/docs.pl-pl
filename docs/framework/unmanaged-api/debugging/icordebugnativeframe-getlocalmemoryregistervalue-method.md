---
title: ICorDebugNativeFrame::GetLocalMemoryRegisterValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type:
- apiref
ms.openlocfilehash: 788ce2d47769caa72518e0357a0affdff5862699
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137282"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="8eb35-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="8eb35-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>
<span data-ttu-id="8eb35-103">Pobiera wartość argumentu lub zmiennej lokalnej, w której małe słowo i duże słowo są przechowywane odpowiednio w określonym rejestrze i lokalizacji pamięci dla tej ramki natywnej.</span><span class="sxs-lookup"><span data-stu-id="8eb35-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eb35-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8eb35-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eb35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8eb35-105">Parameters</span></span>  
 `highWordAddress`  
 <span data-ttu-id="8eb35-106">podczas Wartość `CORDB_ADDRESS`, która określa lokalizację pamięci zawierającej górne słowo wartości.</span><span class="sxs-lookup"><span data-stu-id="8eb35-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="8eb35-107">podczas Wartość wyliczenia "CorDebugRegister —", która określa rejestr zawierający dolny wyraz wartości.</span><span class="sxs-lookup"><span data-stu-id="8eb35-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8eb35-108">podczas Liczba całkowita określająca rozmiar podpisu metadanych binarnych, do którego odwołuje się parametr `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="8eb35-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8eb35-109">podczas Wartość `PCCOR_SIGNATURE`, która wskazuje na podpis metadanych binarnych typu wartości.</span><span class="sxs-lookup"><span data-stu-id="8eb35-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="8eb35-110">określoną Wskaźnik do adresu obiektu "ICorDebugValue" reprezentującego pobraną wartość, która jest przechowywana w określonym rejestrze i lokalizacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="8eb35-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eb35-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8eb35-111">Requirements</span></span>  
 <span data-ttu-id="8eb35-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eb35-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eb35-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8eb35-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8eb35-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8eb35-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8eb35-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eb35-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb35-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8eb35-116">See also</span></span>
