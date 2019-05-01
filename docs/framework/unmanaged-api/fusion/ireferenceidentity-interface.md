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
ms.openlocfilehash: dd46ea26532074c9ea42da4d07a38ed583aad076
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789685"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="27b22-102">IReferenceIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="27b22-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="27b22-103">Reprezentuje odwołanie do unikatowego podpisu obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="27b22-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27b22-104">Metody</span><span class="sxs-lookup"><span data-stu-id="27b22-104">Methods</span></span>  
  
|<span data-ttu-id="27b22-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="27b22-105">Method</span></span>|<span data-ttu-id="27b22-106">Opis</span><span class="sxs-lookup"><span data-stu-id="27b22-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="27b22-107">Pobiera wskaźnik interfejsu do nowego `IReferenceIdentity` wystąpienia, która jest taka sama jak ta `IReferenceIdentity`, z wyjątkiem zmiany określonego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="27b22-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="27b22-108">Pobiera wskaźnik interfejsu do `IEnumIDENTITY_ATTRIBUTE` wystąpienia, które zawiera atrybuty skojarzone z tym `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="27b22-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="27b22-109">Pobiera wartość atrybutu w określonej przestrzeni nazw o podanej nazwie.</span><span class="sxs-lookup"><span data-stu-id="27b22-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="27b22-110">Ustawia atrybut, który ma określonego obszaru nazw i nazwę określoną dla określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="27b22-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27b22-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27b22-111">Requirements</span></span>  
 <span data-ttu-id="27b22-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27b22-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27b22-113">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="27b22-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="27b22-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27b22-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27b22-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27b22-115">See also</span></span>

- [<span data-ttu-id="27b22-116">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="27b22-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="27b22-117">IEnumIDENTITY_ATTRIBUTE, interfejs</span><span class="sxs-lookup"><span data-stu-id="27b22-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
