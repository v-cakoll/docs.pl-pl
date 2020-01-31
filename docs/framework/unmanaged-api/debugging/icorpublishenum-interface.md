---
title: ICorPublishEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
ms.openlocfilehash: f54bb99df60d7b3fb7bb98de75fbae210597e45c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790626"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="56a9d-102">ICorPublishEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="56a9d-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="56a9d-103">Służy jako abstrakcyjny interfejs podstawowy dla modułów wyliczających, które są używane w publikowaniu informacji o procesach i domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="56a9d-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56a9d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="56a9d-104">Methods</span></span>  
  
|<span data-ttu-id="56a9d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="56a9d-105">Method</span></span>|<span data-ttu-id="56a9d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="56a9d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56a9d-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="56a9d-107">Clone Method</span></span>](icorpublishenum-clone-method.md)|<span data-ttu-id="56a9d-108">Tworzy kopię tego obiektu `ICorPublishEnum`.</span><span class="sxs-lookup"><span data-stu-id="56a9d-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="56a9d-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="56a9d-109">GetCount Method</span></span>](icorpublishenum-getcount-method.md)|<span data-ttu-id="56a9d-110">Pobiera liczbę elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="56a9d-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="56a9d-111">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="56a9d-111">Reset Method</span></span>](icorpublishenum-reset-method.md)|<span data-ttu-id="56a9d-112">Przenosi kursor do początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="56a9d-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="56a9d-113">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="56a9d-113">Skip Method</span></span>](icorpublishenum-skip-method.md)|<span data-ttu-id="56a9d-114">Przenosi kursor do przodu w wyliczeniu o określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="56a9d-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56a9d-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56a9d-115">Remarks</span></span>  
 <span data-ttu-id="56a9d-116">Następujące moduły wyliczające pochodzą z `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="56a9d-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="56a9d-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="56a9d-117">ICorPublishAppDomainEnum</span></span>](icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="56a9d-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="56a9d-118">ICorPublishProcessEnum</span></span>](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="56a9d-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56a9d-119">Requirements</span></span>  
 <span data-ttu-id="56a9d-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56a9d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56a9d-121">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="56a9d-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="56a9d-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="56a9d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56a9d-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56a9d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56a9d-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56a9d-124">See also</span></span>

- [<span data-ttu-id="56a9d-125">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="56a9d-125">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
- [<span data-ttu-id="56a9d-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="56a9d-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
