---
title: ICorDebugAppDomain, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
ms.openlocfilehash: da7c0fb472df89d94fa702a13eff968a4c7e68e3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785043"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="fded8-102">ICorDebugAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="fded8-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="fded8-103">Dostarcza metody do debugowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fded8-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="fded8-104">Ten interfejs jest podklasą elementu ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="fded8-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fded8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fded8-105">Methods</span></span>  
  
|<span data-ttu-id="fded8-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fded8-106">Method</span></span>|<span data-ttu-id="fded8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fded8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fded8-108">Attach, metoda</span><span class="sxs-lookup"><span data-stu-id="fded8-108">Attach Method</span></span>](icordebugappdomain-attach-method.md)|<span data-ttu-id="fded8-109">Dołącza debuger do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fded8-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="fded8-110">EnumerateAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="fded8-110">EnumerateAssemblies Method</span></span>](icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="fded8-111">Pobiera moduł wyliczający dla zestawów w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fded8-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="fded8-112">EnumerateBreakpoints, metoda</span><span class="sxs-lookup"><span data-stu-id="fded8-112">EnumerateBreakpoints Method</span></span>](icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="fded8-113">Pobiera moduł wyliczający dla wszystkich aktywnych punktów przerwania w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fded8-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="fded8-114">EnumerateSteppers, metoda</span><span class="sxs-lookup"><span data-stu-id="fded8-114">EnumerateSteppers Method</span></span>](icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="fded8-115">Pobiera moduł wyliczający dla wszystkich aktywnych współdziałań w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fded8-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="fded8-116">GetID, metoda</span><span class="sxs-lookup"><span data-stu-id="fded8-116">GetId Method</span></span>](icordebugappdomain-getid-method.md)|<span data-ttu-id="fded8-117">Pobiera unikatowy identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fded8-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="fded8-118">GetModuleFromMetaDataInterface, metoda</span><span class="sxs-lookup"><span data-stu-id="fded8-118">GetModuleFromMetaDataInterface Method</span></span>](icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="fded8-119">Pobiera obiekt ICorDebugModule z danym interfejsem metadanych.</span><span class="sxs-lookup"><span data-stu-id="fded8-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="fded8-120">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="fded8-120">GetName Method</span></span>](icordebugappdomain-getname-method.md)|<span data-ttu-id="fded8-121">Pobiera nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fded8-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="fded8-122">GetObject, metoda</span><span class="sxs-lookup"><span data-stu-id="fded8-122">GetObject Method</span></span>](icordebugappdomain-getobject-method.md)|<span data-ttu-id="fded8-123">Pobiera wskaźnik interfejsu do domeny aplikacji środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="fded8-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="fded8-124">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="fded8-124">GetProcess Method</span></span>](icordebugappdomain-getprocess-method.md)|<span data-ttu-id="fded8-125">Pobiera proces zawierający domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fded8-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="fded8-126">IsAttached, metoda</span><span class="sxs-lookup"><span data-stu-id="fded8-126">IsAttached Method</span></span>](icordebugappdomain-isattached-method.md)|<span data-ttu-id="fded8-127">Określa, czy debuger jest dołączony do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fded8-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fded8-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fded8-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fded8-129">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="fded8-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fded8-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fded8-130">Requirements</span></span>  
 <span data-ttu-id="fded8-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fded8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fded8-132">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fded8-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fded8-133">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fded8-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fded8-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fded8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fded8-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fded8-135">See also</span></span>

- [<span data-ttu-id="fded8-136">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fded8-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
