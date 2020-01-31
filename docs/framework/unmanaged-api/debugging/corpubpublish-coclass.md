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
ms.openlocfilehash: 24d245bbb0f9ac86e321491e0af3b66b1e011baa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789216"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="8e103-102">CorpubPublish — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="8e103-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="8e103-103">Udostępnia interfejsy umożliwiające publikowanie informacji o domenach i procesach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8e103-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e103-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e103-104">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="8e103-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="8e103-105">Interfaces</span></span>  
  
|<span data-ttu-id="8e103-106">Interfejs</span><span class="sxs-lookup"><span data-stu-id="8e103-106">Interface</span></span>|<span data-ttu-id="8e103-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8e103-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="8e103-108">ICorPublish, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e103-108">ICorPublish Interface</span></span>](icorpublish-interface.md)|<span data-ttu-id="8e103-109">Zapewnia metody publikowania informacji o procesach i domenach aplikacji w tych procesach.</span><span class="sxs-lookup"><span data-stu-id="8e103-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="8e103-110">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e103-110">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)|<span data-ttu-id="8e103-111">Reprezentuje i zawiera informacje dotyczące domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="8e103-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="8e103-112">ICorPublishAppDomainEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e103-112">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)|<span data-ttu-id="8e103-113">Dostarcza metody, które przechodzą przez kolekcję domen aplikacji, które aktualnie istnieją w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8e103-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="8e103-114">ICorPublishProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e103-114">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)|<span data-ttu-id="8e103-115">Reprezentuje proces, który jest uruchomiony na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8e103-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="8e103-116">ICorPublishProcessEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e103-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)|<span data-ttu-id="8e103-117">Dostarcza metody, które przechodzą przez kolekcję procesów uruchomionych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8e103-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e103-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e103-118">Remarks</span></span>  
 <span data-ttu-id="8e103-119">Typowy scenariusz publikowania obejmuje dewelopera, który chce debugować kod zarządzany uruchomiony na komputerze w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8e103-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="8e103-120">W środowisku hostingu może być uruchomiona więcej niż jedna domena aplikacji w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8e103-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="8e103-121">Deweloper chce użyć graficznego interfejsu użytkownika lub innych metod, aby wyświetlić listę wszystkich procesów uruchomionych na komputerze i wybrać konkretny proces.</span><span class="sxs-lookup"><span data-stu-id="8e103-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="8e103-122">Lista powinna zawierać wszystkie domeny aplikacji w ramach procesów, które są uruchomione w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="8e103-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="8e103-123">Deweloper może następnie zidentyfikować konkretną domenę aplikacji i dołączyć debuger do tej domeny.</span><span class="sxs-lookup"><span data-stu-id="8e103-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e103-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e103-124">Requirements</span></span>  
 <span data-ttu-id="8e103-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e103-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e103-126">**Nagłówek:** CorPub. idl</span><span class="sxs-lookup"><span data-stu-id="8e103-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="8e103-127">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8e103-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e103-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e103-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e103-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e103-129">See also</span></span>

- [<span data-ttu-id="8e103-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8e103-130">Debugging</span></span>](index.md)
