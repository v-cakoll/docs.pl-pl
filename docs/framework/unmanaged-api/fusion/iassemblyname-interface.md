---
title: "IAssemblyName — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName
helpviewer_keywords: IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 902ad9f67d06306e79666f0e10d85bdb9c65c377
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="f87c1-102">IAssemblyName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f87c1-102">IAssemblyName Interface</span></span>
<span data-ttu-id="f87c1-103">Udostępnia metody opisujące i pracy z unikatowych tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="f87c1-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f87c1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f87c1-104">Methods</span></span>  
  
|<span data-ttu-id="f87c1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f87c1-105">Method</span></span>|<span data-ttu-id="f87c1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f87c1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f87c1-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="f87c1-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|<span data-ttu-id="f87c1-108">Tworzy kopię pobieżną to `IAssemblyName` obiektu.</span><span class="sxs-lookup"><span data-stu-id="f87c1-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="f87c1-109">Finalize, metoda</span><span class="sxs-lookup"><span data-stu-id="f87c1-109">Finalize Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|<span data-ttu-id="f87c1-110">Umożliwia to `IAssemblyName` obiekt, aby zwolnić zasoby i wykonywać inne zadania oczyszczania, przed jego destruktor jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="f87c1-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="f87c1-111">GetDisplayName, metoda</span><span class="sxs-lookup"><span data-stu-id="f87c1-111">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|<span data-ttu-id="f87c1-112">Pobiera nazwę zrozumiałą zestawu odwołuje się ten `IAssemblyName` obiektu.</span><span class="sxs-lookup"><span data-stu-id="f87c1-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="f87c1-113">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="f87c1-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|<span data-ttu-id="f87c1-114">Pobiera nazwę proste, niezaszyfrowanym zestawu odwołuje się ten `IAssemblyName` obiektu.</span><span class="sxs-lookup"><span data-stu-id="f87c1-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="f87c1-115">GetProperty, metoda</span><span class="sxs-lookup"><span data-stu-id="f87c1-115">GetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|<span data-ttu-id="f87c1-116">Pobiera wskaźnik odwołuje się określony we właściwości `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="f87c1-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="f87c1-117">GetVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="f87c1-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|<span data-ttu-id="f87c1-118">Pobiera informacje o wersji dla zestawu odwołuje się ten `IAssemblyName` obiektu.</span><span class="sxs-lookup"><span data-stu-id="f87c1-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="f87c1-119">IsEqual, metoda</span><span class="sxs-lookup"><span data-stu-id="f87c1-119">IsEqual Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|<span data-ttu-id="f87c1-120">Określa, czy określonej `IAssemblyName` obiekt jest taki sam `IAssemblyName`zgodnie flagi porównania określony.</span><span class="sxs-lookup"><span data-stu-id="f87c1-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="f87c1-121">SetProperty, metoda</span><span class="sxs-lookup"><span data-stu-id="f87c1-121">SetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|<span data-ttu-id="f87c1-122">Ustawia wartości właściwości odwołuje się określony `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="f87c1-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f87c1-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f87c1-123">Requirements</span></span>  
 <span data-ttu-id="f87c1-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f87c1-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f87c1-125">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f87c1-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f87c1-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f87c1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f87c1-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f87c1-127">See Also</span></span>  
 [<span data-ttu-id="f87c1-128">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="f87c1-128">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="f87c1-129">IAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="f87c1-129">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
