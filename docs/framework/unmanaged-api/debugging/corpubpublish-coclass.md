---
title: CorpubPublish — Klasa coclass
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
ms.openlocfilehash: 89af99fab1f1265701e0dbfe74a46000cb3bfaa6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132151"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="ba417-102">CorpubPublish — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="ba417-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="ba417-103">Udostępnia interfejsy umożliwiające publikowanie informacji o domenach i procesach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ba417-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba417-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba417-104">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="ba417-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ba417-105">Interfaces</span></span>  
  
|<span data-ttu-id="ba417-106">Interface</span><span class="sxs-lookup"><span data-stu-id="ba417-106">Interface</span></span>|<span data-ttu-id="ba417-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ba417-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="ba417-108">ICorPublish, interfejs</span><span class="sxs-lookup"><span data-stu-id="ba417-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="ba417-109">Zapewnia metody publikowania informacji o procesach i domenach aplikacji w tych procesach.</span><span class="sxs-lookup"><span data-stu-id="ba417-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="ba417-110">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="ba417-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="ba417-111">Reprezentuje i zawiera informacje dotyczące domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="ba417-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="ba417-112">ICorPublishAppDomainEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="ba417-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="ba417-113">Dostarcza metody, które przechodzą przez kolekcję domen aplikacji, które aktualnie istnieją w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="ba417-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="ba417-114">ICorPublishProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="ba417-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="ba417-115">Reprezentuje proces, który jest uruchomiony na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ba417-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="ba417-116">ICorPublishProcessEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="ba417-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="ba417-117">Dostarcza metody, które przechodzą przez kolekcję procesów uruchomionych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ba417-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba417-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba417-118">Remarks</span></span>  
 <span data-ttu-id="ba417-119">Typowy scenariusz publikowania obejmuje dewelopera, który chce debugować kod zarządzany uruchomiony na komputerze w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ba417-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="ba417-120">W środowisku hostingu może być uruchomiona więcej niż jedna domena aplikacji w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="ba417-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="ba417-121">Deweloper chce użyć graficznego interfejsu użytkownika lub innych metod, aby wyświetlić listę wszystkich procesów uruchomionych na komputerze i wybrać konkretny proces.</span><span class="sxs-lookup"><span data-stu-id="ba417-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="ba417-122">Lista powinna zawierać wszystkie domeny aplikacji w ramach procesów, które są uruchomione w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="ba417-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="ba417-123">Deweloper może następnie zidentyfikować konkretną domenę aplikacji i dołączyć debuger do tej domeny.</span><span class="sxs-lookup"><span data-stu-id="ba417-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba417-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ba417-124">Requirements</span></span>  
 <span data-ttu-id="ba417-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba417-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba417-126">**Nagłówek:** CorPub. idl</span><span class="sxs-lookup"><span data-stu-id="ba417-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="ba417-127">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ba417-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba417-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba417-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba417-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba417-129">See also</span></span>

- [<span data-ttu-id="ba417-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ba417-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
