---
title: "CorpubPublish — Klasa coclass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorpubPublish Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorpubPublish
helpviewer_keywords: CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3dec1175715bdbddc3c975924e91e238fa6d5f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="b6db8-102">CorpubPublish — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="b6db8-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="b6db8-103">Udostępnia interfejsy do publikowania informacji o domenach aplikacji i procesów.</span><span class="sxs-lookup"><span data-stu-id="b6db8-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6db8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6db8-104">Syntax</span></span>  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="b6db8-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b6db8-105">Interfaces</span></span>  
  
|<span data-ttu-id="b6db8-106">Interface</span><span class="sxs-lookup"><span data-stu-id="b6db8-106">Interface</span></span>|<span data-ttu-id="b6db8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b6db8-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="b6db8-108">ICorPublish, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6db8-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="b6db8-109">Udostępnia metody do publikowania informacji o procesach i domen aplikacji w tych procesów.</span><span class="sxs-lookup"><span data-stu-id="b6db8-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="b6db8-110">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6db8-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="b6db8-111">Reprezentuje i informacje dotyczące domeny aplikacji w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b6db8-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="b6db8-112">ICorPublishAppDomainEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6db8-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="b6db8-113">Udostępnia metody przechodzących przez kolekcję domen aplikacji, które obecnie istnieją w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b6db8-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="b6db8-114">ICorPublishProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6db8-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="b6db8-115">Reprezentuje proces, który jest uruchomiony na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b6db8-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="b6db8-116">ICorPublishProcessEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6db8-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="b6db8-117">Udostępnia metody przechodzących przez kolekcję procesów, które są uruchomione na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b6db8-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6db8-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6db8-118">Remarks</span></span>  
 <span data-ttu-id="b6db8-119">Typowy scenariusz publikowania obejmuje deweloperów, którzy chcą do debugowania kodu zarządzanego, który działa na komputerze w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6db8-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="b6db8-120">Środowisko macierzyste mogą działać więcej niż jednej domeny aplikacji w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b6db8-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="b6db8-121">Deweloper chce użyć graficznego interfejsu użytkownika lub inne środki, aby wyświetlić listę wszystkich procesów, które są uruchomione na komputerze i pobrania określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="b6db8-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="b6db8-122">Listę powinna zawierać wszystkie domeny aplikacji w ramach procesów uruchomionych kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="b6db8-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="b6db8-123">Deweloper można zidentyfikować domeny określonej aplikacji i dołączyć do tej domeny.</span><span class="sxs-lookup"><span data-stu-id="b6db8-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6db8-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6db8-124">Requirements</span></span>  
 <span data-ttu-id="b6db8-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6db8-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6db8-126">**Nagłówek:** CorPub.idl</span><span class="sxs-lookup"><span data-stu-id="b6db8-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="b6db8-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6db8-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6db8-128">**Wersje programu .NET framework:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6db8-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6db8-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6db8-129">See Also</span></span>  
 [<span data-ttu-id="b6db8-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b6db8-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
