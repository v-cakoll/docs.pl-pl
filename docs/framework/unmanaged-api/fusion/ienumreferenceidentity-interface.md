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
ms.openlocfilehash: 4ebc9fe36955bac8b93ec95e9a55fc8ac1197d9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429124"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="20791-102">IEnumReferenceIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="20791-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="20791-103">Służy jako moduł wyliczający kolekcji `IReferenceIdentity` obiektów.</span><span class="sxs-lookup"><span data-stu-id="20791-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="20791-104">Metody</span><span class="sxs-lookup"><span data-stu-id="20791-104">Methods</span></span>  
  
|<span data-ttu-id="20791-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="20791-105">Method</span></span>|<span data-ttu-id="20791-106">Opis</span><span class="sxs-lookup"><span data-stu-id="20791-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="20791-107">Pobiera wskaźnika interfejsu na nowy `IEnumReferenceIdentity` zawierający członkowie to `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="20791-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="20791-108">Pobiera określoną liczbę `IReferenceIdentity` obiektów, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="20791-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="20791-109">Przesuwa wskaźnik instrukcji na początku `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="20791-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="20791-110">Przenosi do przodu wskaźnik instrukcji przez określoną liczbę elementów, licząc w bieżącym położeniu.</span><span class="sxs-lookup"><span data-stu-id="20791-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="20791-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20791-111">Requirements</span></span>  
 <span data-ttu-id="20791-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20791-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20791-113">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="20791-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="20791-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20791-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20791-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20791-115">See Also</span></span>  
 [<span data-ttu-id="20791-116">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="20791-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="20791-117">IReferenceIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="20791-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
