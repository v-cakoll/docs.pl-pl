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
ms.openlocfilehash: 4708fa173725e4c91a13f5b92cdbb1fdf8a8a4d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432106"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="51989-102">IReferenceIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="51989-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="51989-103">Reprezentuje odwołanie do unikatowego podpisu obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="51989-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51989-104">Metody</span><span class="sxs-lookup"><span data-stu-id="51989-104">Methods</span></span>  
  
|<span data-ttu-id="51989-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="51989-105">Method</span></span>|<span data-ttu-id="51989-106">Opis</span><span class="sxs-lookup"><span data-stu-id="51989-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="51989-107">Pobiera wskaźnika interfejsu na nowy `IReferenceIdentity` wystąpienia, który jest taki sam jak to `IReferenceIdentity`, z wyjątkiem zmiany określonego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="51989-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="51989-108">Pobiera wskaźnika interfejsu do `IEnumIDENTITY_ATTRIBUTE` wystąpienia, które zawiera atrybuty skojarzone z tym `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="51989-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="51989-109">Pobiera wartość atrybutu w określonej przestrzeni nazw o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="51989-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="51989-110">Ustawia atrybut, który ma określonego obszaru nazw i nazwę określonego na określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="51989-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51989-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51989-111">Requirements</span></span>  
 <span data-ttu-id="51989-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51989-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51989-113">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="51989-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="51989-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51989-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51989-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51989-115">See Also</span></span>  
 [<span data-ttu-id="51989-116">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="51989-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="51989-117">IEnumIDENTITY_ATTRIBUTE, interfejs</span><span class="sxs-lookup"><span data-stu-id="51989-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
