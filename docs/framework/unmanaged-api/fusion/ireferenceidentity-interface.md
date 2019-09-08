---
title: IReferenceIdentity — Interfejs
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bb151d7c77104d8e24acefaac2e1f109b67f168
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796360"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="b6312-102">IReferenceIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b6312-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="b6312-103">Reprezentuje odwołanie do unikatowego podpisu obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="b6312-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6312-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b6312-104">Methods</span></span>  
  
|<span data-ttu-id="b6312-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b6312-105">Method</span></span>|<span data-ttu-id="b6312-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b6312-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="b6312-107">Pobiera wskaźnik interfejsu do nowego `IReferenceIdentity` wystąpienia, które jest identyczne z tą `IReferenceIdentity`różnicą, z wyjątkiem określonych zmian atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b6312-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="b6312-108">Pobiera wskaźnik interfejsu do `IEnumIDENTITY_ATTRIBUTE` wystąpienia, które zawiera atrybuty skojarzone z tym `IReferenceIdentity`elementem.</span><span class="sxs-lookup"><span data-stu-id="b6312-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="b6312-109">Pobiera wartość atrybutu w określonym obszarze nazw z określoną nazwą.</span><span class="sxs-lookup"><span data-stu-id="b6312-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="b6312-110">Ustawia atrybut, który ma określoną przestrzeń nazw i określoną nazwę określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="b6312-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6312-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6312-111">Requirements</span></span>  
 <span data-ttu-id="b6312-112">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6312-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6312-113">**Nagłówki** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="b6312-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b6312-114">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6312-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6312-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6312-115">See also</span></span>

- [<span data-ttu-id="b6312-116">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="b6312-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="b6312-117">IEnumIDENTITY_ATTRIBUTE, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6312-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
