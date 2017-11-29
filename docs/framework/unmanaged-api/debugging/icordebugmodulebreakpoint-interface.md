---
title: ICorDebugModuleBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModuleBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModuleBreakpoint
helpviewer_keywords: ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e3937c6c0baef4cc927b5c5d789826c70beebf2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulebreakpoint-interface1"></a><span data-ttu-id="4e483-102">ICorDebugModuleBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="4e483-102">ICorDebugModuleBreakpoint Interface1</span></span>
<span data-ttu-id="4e483-103">Zapewnia dostęp do określonych modułów.</span><span class="sxs-lookup"><span data-stu-id="4e483-103">Provides access to specific modules.</span></span> <span data-ttu-id="4e483-104">Ten interfejs jest podklasą klasy interfejsu ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="4e483-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e483-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4e483-105">Methods</span></span>  
  
|<span data-ttu-id="4e483-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="4e483-106">Method</span></span>|<span data-ttu-id="4e483-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4e483-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e483-108">GetModule — metoda</span><span class="sxs-lookup"><span data-stu-id="4e483-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="4e483-109">Pobiera wskaźnika interfejsu do ICorDebugModule, który odwołuje się do modułu, w których ustawiony jest ten punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="4e483-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e483-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e483-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e483-111">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="4e483-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e483-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4e483-112">Requirements</span></span>  
 <span data-ttu-id="4e483-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e483-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e483-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e483-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e483-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e483-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e483-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e483-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e483-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e483-117">See Also</span></span>  
 [<span data-ttu-id="4e483-118">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="4e483-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
