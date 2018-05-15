---
title: Interfejs ICorDebugType2
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
ms.openlocfilehash: 038598e6fa8c0f7d47a161783d21f03b3c87af0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="eec16-102">Interfejs ICorDebugType2</span><span class="sxs-lookup"><span data-stu-id="eec16-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="eec16-103">Rozszerzenie interfejsu ICorDebugType można pobrać identyfikatora typu podstawowego typu lub typu złożonego (zdefiniowane przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="eec16-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eec16-104">Metody</span><span class="sxs-lookup"><span data-stu-id="eec16-104">Methods</span></span>  
  
|<span data-ttu-id="eec16-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="eec16-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="eec16-106">GetTypeID, metoda</span><span class="sxs-lookup"><span data-stu-id="eec16-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="eec16-107">Pobiera [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="eec16-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eec16-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eec16-108">Remarks</span></span>  
 <span data-ttu-id="eec16-109">Ten interfejs jest logiczną rozszerzenie interfejsu ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="eec16-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eec16-110">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="eec16-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eec16-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="eec16-111">Example</span></span>  
 <span data-ttu-id="eec16-112">Poniższy fragment kodu przedstawia użycie [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="eec16-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="eec16-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eec16-113">Requirements</span></span>  
 <span data-ttu-id="eec16-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eec16-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eec16-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eec16-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eec16-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eec16-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eec16-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eec16-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eec16-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eec16-118">See Also</span></span>  
 [<span data-ttu-id="eec16-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="eec16-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
