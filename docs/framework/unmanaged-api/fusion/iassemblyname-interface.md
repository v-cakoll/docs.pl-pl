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
ms.openlocfilehash: de49d66667033dfc6918b139f90cd5523661597f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134315"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="a8843-102">IAssemblyName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a8843-102">IAssemblyName Interface</span></span>
<span data-ttu-id="a8843-103">Zapewnia metody opisujące unikatową tożsamość zestawu i pracę z nim.</span><span class="sxs-lookup"><span data-stu-id="a8843-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8843-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a8843-104">Methods</span></span>  
  
|<span data-ttu-id="a8843-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a8843-105">Method</span></span>|<span data-ttu-id="a8843-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a8843-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8843-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="a8843-107">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="a8843-108">Tworzy skróconą kopię tego obiektu `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="a8843-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="a8843-109">Finalize, metoda</span><span class="sxs-lookup"><span data-stu-id="a8843-109">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="a8843-110">Umożliwia temu obiektowi `IAssemblyName` zwalnianie zasobów i wykonywanie innych operacji czyszczenia przed wywołaniem destruktora.</span><span class="sxs-lookup"><span data-stu-id="a8843-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="a8843-111">GetDisplayName, metoda</span><span class="sxs-lookup"><span data-stu-id="a8843-111">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="a8843-112">Pobiera nazwę zestawu, do którego odwołuje się ten obiekt `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="a8843-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="a8843-113">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="a8843-113">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="a8843-114">Pobiera prostą, niezaszyfrowaną nazwę zestawu, do którego odwołuje się ten obiekt `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="a8843-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="a8843-115">GetProperty, metoda</span><span class="sxs-lookup"><span data-stu-id="a8843-115">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="a8843-116">Pobiera wskaźnik do właściwości, do której odwołuje się określony `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="a8843-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="a8843-117">GetVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="a8843-117">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="a8843-118">Pobiera informacje o wersji zestawu, do którego odwołuje się ten obiekt `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="a8843-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="a8843-119">IsEqual, metoda</span><span class="sxs-lookup"><span data-stu-id="a8843-119">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="a8843-120">Określa, czy określony obiekt `IAssemblyName` jest równy temu `IAssemblyName`, na podstawie określonych flag porównania.</span><span class="sxs-lookup"><span data-stu-id="a8843-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="a8843-121">SetProperty, metoda</span><span class="sxs-lookup"><span data-stu-id="a8843-121">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="a8843-122">Ustawia wartość właściwości, do której odwołuje się określony `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="a8843-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a8843-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a8843-123">Requirements</span></span>  
 <span data-ttu-id="a8843-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8843-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8843-125">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a8843-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a8843-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8843-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8843-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8843-127">See also</span></span>

- [<span data-ttu-id="a8843-128">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="a8843-128">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="a8843-129">IAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="a8843-129">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
