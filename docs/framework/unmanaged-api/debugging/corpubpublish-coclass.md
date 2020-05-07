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
ms.openlocfilehash: e33029e8244fdfa180a79aa4a5b05b07f594d928
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860912"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="703f6-102">CorpubPublish — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="703f6-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="703f6-103">Udostępnia interfejsy umożliwiające publikowanie informacji o domenach i procesach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="703f6-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="703f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="703f6-104">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="703f6-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="703f6-105">Interfaces</span></span>  
  
|<span data-ttu-id="703f6-106">Interface</span><span class="sxs-lookup"><span data-stu-id="703f6-106">Interface</span></span>|<span data-ttu-id="703f6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="703f6-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="703f6-108">ICorPublish — Interfejs</span><span class="sxs-lookup"><span data-stu-id="703f6-108">ICorPublish Interface</span></span>](icorpublish-interface.md)|<span data-ttu-id="703f6-109">Zapewnia metody publikowania informacji o procesach i domenach aplikacji w tych procesach.</span><span class="sxs-lookup"><span data-stu-id="703f6-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="703f6-110">ICorPublishAppDomain — Interfejs</span><span class="sxs-lookup"><span data-stu-id="703f6-110">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)|<span data-ttu-id="703f6-111">Reprezentuje i zawiera informacje dotyczące domeny aplikacji w procesie.</span><span class="sxs-lookup"><span data-stu-id="703f6-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="703f6-112">ICorPublishAppDomainEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="703f6-112">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)|<span data-ttu-id="703f6-113">Dostarcza metody, które przechodzą przez kolekcję domen aplikacji, które aktualnie istnieją w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="703f6-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="703f6-114">ICorPublishProcess — Interfejs</span><span class="sxs-lookup"><span data-stu-id="703f6-114">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)|<span data-ttu-id="703f6-115">Reprezentuje proces, który jest uruchomiony na komputerze.</span><span class="sxs-lookup"><span data-stu-id="703f6-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="703f6-116">ICorPublishProcessEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="703f6-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)|<span data-ttu-id="703f6-117">Dostarcza metody, które przechodzą przez kolekcję procesów uruchomionych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="703f6-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="703f6-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="703f6-118">Remarks</span></span>  
 <span data-ttu-id="703f6-119">Typowy scenariusz publikowania obejmuje dewelopera, który chce debugować kod zarządzany uruchomiony na komputerze w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="703f6-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="703f6-120">W środowisku hostingu może być uruchomiona więcej niż jedna domena aplikacji w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="703f6-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="703f6-121">Deweloper chce użyć graficznego interfejsu użytkownika lub innych metod, aby wyświetlić listę wszystkich procesów uruchomionych na komputerze i wybrać konkretny proces.</span><span class="sxs-lookup"><span data-stu-id="703f6-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="703f6-122">Lista powinna zawierać wszystkie domeny aplikacji w ramach procesów, które są uruchomione w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="703f6-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="703f6-123">Deweloper może następnie zidentyfikować konkretną domenę aplikacji i dołączyć debuger do tej domeny.</span><span class="sxs-lookup"><span data-stu-id="703f6-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="703f6-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="703f6-124">Requirements</span></span>  
 <span data-ttu-id="703f6-125">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="703f6-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="703f6-126">**Nagłówek:** CorPub. idl</span><span class="sxs-lookup"><span data-stu-id="703f6-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="703f6-127">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="703f6-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="703f6-128">**.NET Framework wersje:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="703f6-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="703f6-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="703f6-129">See also</span></span>

- [<span data-ttu-id="703f6-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="703f6-130">Debugging</span></span>](index.md)
