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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05d9eef36885aee05d88f7da994c8b168c3221b3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130536"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="48639-102">CorpubPublish — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="48639-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="48639-103">Udostępnia interfejsy do publikowania informacji o domenach aplikacji i procesów.</span><span class="sxs-lookup"><span data-stu-id="48639-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48639-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="48639-104">Syntax</span></span>  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="48639-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="48639-105">Interfaces</span></span>  
  
|<span data-ttu-id="48639-106">Interface</span><span class="sxs-lookup"><span data-stu-id="48639-106">Interface</span></span>|<span data-ttu-id="48639-107">Opis</span><span class="sxs-lookup"><span data-stu-id="48639-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="48639-108">ICorPublish, interfejs</span><span class="sxs-lookup"><span data-stu-id="48639-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="48639-109">Udostępnia metody do publikowania informacji o procesach i domen aplikacji w tych procesów.</span><span class="sxs-lookup"><span data-stu-id="48639-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="48639-110">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="48639-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="48639-111">Reprezentuje i zawiera informacje dotyczące domeny aplikacji w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="48639-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="48639-112">ICorPublishAppDomainEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="48639-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="48639-113">Udostępnia metody, które przemierzają kolekcję domen aplikacji, które obecnie istnieją w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="48639-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="48639-114">ICorPublishProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="48639-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="48639-115">Reprezentuje proces, który jest uruchomiony na komputerze.</span><span class="sxs-lookup"><span data-stu-id="48639-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="48639-116">ICorPublishProcessEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="48639-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="48639-117">Udostępnia metody, które przemierzają kolekcję procesów, które są uruchomione na komputerze.</span><span class="sxs-lookup"><span data-stu-id="48639-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48639-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="48639-118">Remarks</span></span>  
 <span data-ttu-id="48639-119">Typowy scenariusz publikowania obejmuje deweloperem i potrzebujesz do debugowania kodu zarządzanego, który jest uruchomiony na komputerze w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48639-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="48639-120">Środowisko hostingu może działać więcej niż jedną domenę aplikacji w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="48639-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="48639-121">Deweloper chce użyć graficznego interfejsu użytkownika lub inne metody, aby wyświetlić listę wszystkich procesów, które są uruchomione na komputerze, a następnie wybierz określony proces.</span><span class="sxs-lookup"><span data-stu-id="48639-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="48639-122">Listę powinien zawierać wszystkie domeny aplikacji wewnątrz procesów uruchomionych w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="48639-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="48639-123">Deweloper można zidentyfikować określonej domenie aplikacji i dołączyć debuger do tej domeny.</span><span class="sxs-lookup"><span data-stu-id="48639-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48639-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48639-124">Requirements</span></span>  
 <span data-ttu-id="48639-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48639-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48639-126">**Nagłówek:** CorPub.idl</span><span class="sxs-lookup"><span data-stu-id="48639-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="48639-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48639-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48639-128">**Wersje programu .NET framework:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48639-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48639-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48639-129">See also</span></span>

- [<span data-ttu-id="48639-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="48639-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
