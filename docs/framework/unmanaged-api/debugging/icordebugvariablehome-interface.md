---
title: ICorDebugVariableHome, interfejs
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 339a0f502b7e47f7bee82a0da92185481d909e64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202914"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="62b2a-102">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="62b2a-102">ICorDebugVariableHome Interface</span></span>
<span data-ttu-id="62b2a-103">Reprezentuje zmiennej lokalnej lub argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="62b2a-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="62b2a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="62b2a-104">Methods</span></span>  
  
|<span data-ttu-id="62b2a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="62b2a-105">Method</span></span>|<span data-ttu-id="62b2a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="62b2a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="62b2a-107">GetArgumentIndex, metoda</span><span class="sxs-lookup"><span data-stu-id="62b2a-107">GetArgumentIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="62b2a-108">Pobiera indeks argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="62b2a-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="62b2a-109">GetCode, metoda</span><span class="sxs-lookup"><span data-stu-id="62b2a-109">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|<span data-ttu-id="62b2a-110">Pobiera wystąpienie "ICorDebugCode", który zawiera ten `ICorDebugVariableHome` obiektu.</span><span class="sxs-lookup"><span data-stu-id="62b2a-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="62b2a-111">GetLiveRange, metoda</span><span class="sxs-lookup"><span data-stu-id="62b2a-111">GetLiveRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="62b2a-112">Pobiera natywne zakresu, w którym ta zmienna jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="62b2a-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="62b2a-113">GetLocationType, metoda</span><span class="sxs-lookup"><span data-stu-id="62b2a-113">GetLocationType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="62b2a-114">Pobiera typ zmiennej natywnych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="62b2a-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="62b2a-115">GetOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="62b2a-115">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="62b2a-116">Pobiera przesunięcie z podstawowej rejestru dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="62b2a-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="62b2a-117">GetRegister, metoda</span><span class="sxs-lookup"><span data-stu-id="62b2a-117">GetRegister Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|<span data-ttu-id="62b2a-118">Pobiera rejestr, który zawiera zmienną typu lokalizacji `VLT_REGISTER`oraz podstawowego rejestru dla zmiennej o typie lokalizacji `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="62b2a-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="62b2a-119">GetSlotIndex, metoda</span><span class="sxs-lookup"><span data-stu-id="62b2a-119">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="62b2a-120">Pobiera zarządzane miejsce indeks zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="62b2a-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="62b2a-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="62b2a-121">Example</span></span>  
 <span data-ttu-id="62b2a-122">Poniższy fragment kodu używa [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) obiektu o nazwie `pCode4`.</span><span class="sxs-lookup"><span data-stu-id="62b2a-122">The following code fragment uses the [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="62b2a-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62b2a-123">Requirements</span></span>  
 <span data-ttu-id="62b2a-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62b2a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62b2a-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62b2a-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62b2a-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62b2a-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="62b2a-127">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="62b2a-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="62b2a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62b2a-128">See also</span></span>

- [<span data-ttu-id="62b2a-129">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="62b2a-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="62b2a-130">ICorDebugVariableHomeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="62b2a-130">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
