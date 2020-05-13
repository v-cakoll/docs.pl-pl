---
title: ICorDebugNativeFrame::GetLocalMemoryValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type:
- apiref
ms.openlocfilehash: 4c4bfe6a797fc1476ff53a8f2db4f80debc41f6b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212441"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="5e903-102">ICorDebugNativeFrame::GetLocalMemoryValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e903-102">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>
<span data-ttu-id="5e903-103">Pobiera wartość argumentu lub zmiennej lokalnej przechowywanej w określonej lokalizacji pamięci dla tej ramki natywnej.</span><span class="sxs-lookup"><span data-stu-id="5e903-103">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e903-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e903-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e903-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e903-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="5e903-106">podczas Wartość określająca `CORDB_ADDRESS` lokalizację pamięci zawierającą wartość.</span><span class="sxs-lookup"><span data-stu-id="5e903-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="5e903-107">podczas Liczba całkowita określająca rozmiar podpisu metadanych binarnych, do którego odwołuje się `pvSigBlob` parametr.</span><span class="sxs-lookup"><span data-stu-id="5e903-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="5e903-108">podczas Wartość wskazująca `PCCOR_SIGNATURE` na podpis metadanych binarnych typu wartości.</span><span class="sxs-lookup"><span data-stu-id="5e903-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5e903-109">określoną Wskaźnik do adresu obiektu "ICorDebugValue" reprezentującego pobraną wartość przechowywaną w określonej lokalizacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="5e903-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e903-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e903-110">Requirements</span></span>  
 <span data-ttu-id="5e903-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e903-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e903-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5e903-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e903-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5e903-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e903-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e903-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e903-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e903-115">See also</span></span>
