---
title: IEnumReferenceIdentity — Interfejs
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 766b17bae0c58d9872ff9c118f330ebc3220257e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123490"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="8517f-102">IEnumReferenceIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8517f-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="8517f-103">Służy jako moduł wyliczający dla kolekcji `IReferenceIdentity` obiektów.</span><span class="sxs-lookup"><span data-stu-id="8517f-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8517f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8517f-104">Methods</span></span>  
  
|<span data-ttu-id="8517f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8517f-105">Method</span></span>|<span data-ttu-id="8517f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8517f-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="8517f-107">Pobiera wskaźnik interfejsu do nowego `IEnumReferenceIdentity` zawiera te same elementy członkowskie, ponieważ `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="8517f-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="8517f-108">Pobiera określoną liczbę `IReferenceIdentity` obiektów, począwszy od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="8517f-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="8517f-109">Przesuwa wskaźnik instrukcji na początku `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="8517f-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="8517f-110">Przesuwa wskaźnik instrukcji do przodu o określoną liczbę elementów, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="8517f-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8517f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8517f-111">Requirements</span></span>  
 <span data-ttu-id="8517f-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8517f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8517f-113">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="8517f-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="8517f-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8517f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8517f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8517f-115">See also</span></span>

- [<span data-ttu-id="8517f-116">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="8517f-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="8517f-117">IReferenceIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="8517f-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
