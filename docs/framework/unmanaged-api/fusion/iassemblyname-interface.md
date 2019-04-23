---
title: IAssemblyName — Interfejs
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d8d59ef282818dd9852d0ff8d2ec2abd40986d0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097138"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="27a3b-102">IAssemblyName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="27a3b-102">IAssemblyName Interface</span></span>
<span data-ttu-id="27a3b-103">Udostępnia metody dla opisania i Praca z unikatową tożsamość zestawu.</span><span class="sxs-lookup"><span data-stu-id="27a3b-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27a3b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="27a3b-104">Methods</span></span>  
  
|<span data-ttu-id="27a3b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="27a3b-105">Method</span></span>|<span data-ttu-id="27a3b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="27a3b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27a3b-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="27a3b-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|<span data-ttu-id="27a3b-108">Tworzy kopię pobieżną to `IAssemblyName` obiektu.</span><span class="sxs-lookup"><span data-stu-id="27a3b-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="27a3b-109">Finalize, metoda</span><span class="sxs-lookup"><span data-stu-id="27a3b-109">Finalize Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|<span data-ttu-id="27a3b-110">Umożliwia to `IAssemblyName` obiekt, aby zwolnić zasoby i wykonywać inne operacje oczyszczania, przed jego destruktor jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="27a3b-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="27a3b-111">GetDisplayName, metoda</span><span class="sxs-lookup"><span data-stu-id="27a3b-111">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|<span data-ttu-id="27a3b-112">Pobiera nazwę zrozumiałą dla użytkownika, zestawu odwołuje się ten `IAssemblyName` obiektu.</span><span class="sxs-lookup"><span data-stu-id="27a3b-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="27a3b-113">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="27a3b-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|<span data-ttu-id="27a3b-114">Pobiera nazwę proste, niezaszyfrowane zestawu odwołuje się ten `IAssemblyName` obiektu.</span><span class="sxs-lookup"><span data-stu-id="27a3b-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="27a3b-115">GetProperty, metoda</span><span class="sxs-lookup"><span data-stu-id="27a3b-115">GetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|<span data-ttu-id="27a3b-116">Pobiera wskaźnik do właściwości odwołuje się określony `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="27a3b-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="27a3b-117">GetVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="27a3b-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|<span data-ttu-id="27a3b-118">Pobiera informacje o wersji dla zestawu odwołuje się ten `IAssemblyName` obiektu.</span><span class="sxs-lookup"><span data-stu-id="27a3b-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="27a3b-119">IsEqual, metoda</span><span class="sxs-lookup"><span data-stu-id="27a3b-119">IsEqual Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|<span data-ttu-id="27a3b-120">Określa, czy określony `IAssemblyName` obiekt jest taki sam tym `IAssemblyName`zgodnie z flagi porównania określony.</span><span class="sxs-lookup"><span data-stu-id="27a3b-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="27a3b-121">SetProperty, metoda</span><span class="sxs-lookup"><span data-stu-id="27a3b-121">SetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|<span data-ttu-id="27a3b-122">Ustawia wartość właściwości odwołuje się określony `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="27a3b-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27a3b-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27a3b-123">Requirements</span></span>  
 <span data-ttu-id="27a3b-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27a3b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27a3b-125">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="27a3b-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="27a3b-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27a3b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a3b-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27a3b-127">See also</span></span>

- [<span data-ttu-id="27a3b-128">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="27a3b-128">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="27a3b-129">IAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="27a3b-129">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
