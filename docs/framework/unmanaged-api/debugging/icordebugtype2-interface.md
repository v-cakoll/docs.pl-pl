---
title: ICorDebugType2, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e953fa129308527f63df8dd8c5061252f8be57b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772444"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="a9c53-102">ICorDebugType2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9c53-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="a9c53-103">Rozszerza interfejs ICorDebugType, aby pobrać identyfikator typu Typ podstawowy lub złożony (typ zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="a9c53-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a9c53-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a9c53-104">Methods</span></span>  
  
|<span data-ttu-id="a9c53-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a9c53-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="a9c53-106">GetTypeID, metoda</span><span class="sxs-lookup"><span data-stu-id="a9c53-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="a9c53-107">Pobiera [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="a9c53-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9c53-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9c53-108">Remarks</span></span>  
 <span data-ttu-id="a9c53-109">Ten interfejs jest logicznym rozszerzeniem icordebugtype — interfejs.</span><span class="sxs-lookup"><span data-stu-id="a9c53-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9c53-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="a9c53-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9c53-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9c53-111">Example</span></span>  
 <span data-ttu-id="a9c53-112">Poniższy fragment kodu ilustruje użycie [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a9c53-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="a9c53-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9c53-113">Requirements</span></span>  
 <span data-ttu-id="a9c53-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9c53-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9c53-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9c53-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9c53-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9c53-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9c53-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9c53-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c53-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9c53-118">See also</span></span>

- [<span data-ttu-id="a9c53-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a9c53-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
