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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130536"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="8955c-102">CorpubPublish — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="8955c-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="8955c-103">Udostępnia interfejsy do publikowania informacji o domenach aplikacji i procesów.</span><span class="sxs-lookup"><span data-stu-id="8955c-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8955c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8955c-104">Syntax</span></span>  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="8955c-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="8955c-105">Interfaces</span></span>  
  
|<span data-ttu-id="8955c-106">Interface</span><span class="sxs-lookup"><span data-stu-id="8955c-106">Interface</span></span>|<span data-ttu-id="8955c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8955c-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="8955c-108">ICorPublish — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8955c-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="8955c-109">Udostępnia metody do publikowania informacji o procesach i domen aplikacji w tych procesów.</span><span class="sxs-lookup"><span data-stu-id="8955c-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="8955c-110">ICorPublishAppDomain — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8955c-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="8955c-111">Reprezentuje i zawiera informacje dotyczące domeny aplikacji w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8955c-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="8955c-112">ICorPublishAppDomainEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8955c-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="8955c-113">Udostępnia metody, które przemierzają kolekcję domen aplikacji, które obecnie istnieją w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8955c-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="8955c-114">ICorPublishProcess — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8955c-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="8955c-115">Reprezentuje proces, który jest uruchomiony na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8955c-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="8955c-116">ICorPublishProcessEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8955c-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="8955c-117">Udostępnia metody, które przemierzają kolekcję procesów, które są uruchomione na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8955c-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8955c-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8955c-118">Remarks</span></span>  
 <span data-ttu-id="8955c-119">Typowy scenariusz publikowania obejmuje deweloperem i potrzebujesz do debugowania kodu zarządzanego, który jest uruchomiony na komputerze w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8955c-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="8955c-120">Środowisko hostingu może działać więcej niż jedną domenę aplikacji w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8955c-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="8955c-121">Deweloper chce użyć graficznego interfejsu użytkownika lub inne metody, aby wyświetlić listę wszystkich procesów, które są uruchomione na komputerze, a następnie wybierz określony proces.</span><span class="sxs-lookup"><span data-stu-id="8955c-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="8955c-122">Listę powinien zawierać wszystkie domeny aplikacji wewnątrz procesów uruchomionych w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="8955c-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="8955c-123">Deweloper można zidentyfikować określonej domenie aplikacji i dołączyć debuger do tej domeny.</span><span class="sxs-lookup"><span data-stu-id="8955c-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8955c-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8955c-124">Requirements</span></span>  
 <span data-ttu-id="8955c-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8955c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8955c-126">**Nagłówek:** CorPub.idl</span><span class="sxs-lookup"><span data-stu-id="8955c-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="8955c-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8955c-127">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8955c-128">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8955c-128">.NET Framework Versions:</span></span>**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8955c-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8955c-129">See also</span></span>

- [<span data-ttu-id="8955c-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8955c-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
