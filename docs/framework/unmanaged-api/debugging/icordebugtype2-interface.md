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
ms.openlocfilehash: 878941f7af71fa5e3de8e38c4a68a66cb964983d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223163"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="aae8e-102">ICorDebugType2, interfejs</span><span class="sxs-lookup"><span data-stu-id="aae8e-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="aae8e-103">Rozszerza interfejs ICorDebugType, aby pobrać identyfikator typu Typ podstawowy lub złożony (typ zdefiniowany przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="aae8e-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aae8e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="aae8e-104">Methods</span></span>  
  
|<span data-ttu-id="aae8e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="aae8e-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="aae8e-106">GetTypeID, metoda</span><span class="sxs-lookup"><span data-stu-id="aae8e-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="aae8e-107">Pobiera [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="aae8e-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aae8e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aae8e-108">Remarks</span></span>  
 <span data-ttu-id="aae8e-109">Ten interfejs jest logicznym rozszerzeniem icordebugtype — interfejs.</span><span class="sxs-lookup"><span data-stu-id="aae8e-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aae8e-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="aae8e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aae8e-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="aae8e-111">Example</span></span>  
 <span data-ttu-id="aae8e-112">Poniższy fragment kodu ilustruje użycie [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="aae8e-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="aae8e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aae8e-113">Requirements</span></span>  
 <span data-ttu-id="aae8e-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aae8e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aae8e-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aae8e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aae8e-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aae8e-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="aae8e-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="aae8e-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aae8e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aae8e-118">See also</span></span>

- [<span data-ttu-id="aae8e-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="aae8e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
