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
ms.openlocfilehash: aee9b986c1e26c1b2e34dac7151a00172451bbad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796555"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="b9500-102">IAssemblyName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b9500-102">IAssemblyName Interface</span></span>
<span data-ttu-id="b9500-103">Zapewnia metody opisujące unikatową tożsamość zestawu i pracę z nim.</span><span class="sxs-lookup"><span data-stu-id="b9500-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9500-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b9500-104">Methods</span></span>  
  
|<span data-ttu-id="b9500-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b9500-105">Method</span></span>|<span data-ttu-id="b9500-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b9500-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9500-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="b9500-107">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="b9500-108">Tworzy skróconą kopię tego `IAssemblyName` obiektu.</span><span class="sxs-lookup"><span data-stu-id="b9500-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="b9500-109">Finalize, metoda</span><span class="sxs-lookup"><span data-stu-id="b9500-109">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="b9500-110">Zezwala temu `IAssemblyName` obiektowi na zwalnianie zasobów i wykonywanie innych operacji czyszczenia przed wywołaniem destruktora.</span><span class="sxs-lookup"><span data-stu-id="b9500-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="b9500-111">GetDisplayName, metoda</span><span class="sxs-lookup"><span data-stu-id="b9500-111">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="b9500-112">Pobiera nazwę zestawu, do którego odwołuje się ten `IAssemblyName` obiekt.</span><span class="sxs-lookup"><span data-stu-id="b9500-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="b9500-113">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="b9500-113">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="b9500-114">Pobiera prostą, niezaszyfrowaną nazwę zestawu, do którego odwołuje `IAssemblyName` się ten obiekt.</span><span class="sxs-lookup"><span data-stu-id="b9500-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="b9500-115">GetProperty, metoda</span><span class="sxs-lookup"><span data-stu-id="b9500-115">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="b9500-116">Pobiera wskaźnik do właściwości, do której odwołuje się `PropertyId`określony.</span><span class="sxs-lookup"><span data-stu-id="b9500-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="b9500-117">GetVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="b9500-117">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="b9500-118">Pobiera informacje o wersji zestawu, do którego odwołuje `IAssemblyName` się ten obiekt.</span><span class="sxs-lookup"><span data-stu-id="b9500-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="b9500-119">IsEqual, metoda</span><span class="sxs-lookup"><span data-stu-id="b9500-119">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="b9500-120">Określa, czy określony `IAssemblyName` obiekt jest równy temu `IAssemblyName`, na podstawie określonych flag porównania.</span><span class="sxs-lookup"><span data-stu-id="b9500-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="b9500-121">SetProperty, metoda</span><span class="sxs-lookup"><span data-stu-id="b9500-121">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="b9500-122">Ustawia wartość właściwości, do której odwołuje się określony `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="b9500-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b9500-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b9500-123">Requirements</span></span>  
 <span data-ttu-id="b9500-124">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9500-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9500-125">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b9500-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b9500-126">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9500-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9500-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9500-127">See also</span></span>

- [<span data-ttu-id="b9500-128">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="b9500-128">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="b9500-129">IAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b9500-129">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
