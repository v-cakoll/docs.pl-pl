---
title: IEnumDefinitionIdentity — Interfejs
ms.date: 03/30/2017
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d19ca92db6f57a004dca54f6e22db10603c9498a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214848"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="ed910-102">IEnumDefinitionIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ed910-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="ed910-103">Służy jako modułu wyliczającego dla kolekcji `IDefinitionIdentity` obiektów.</span><span class="sxs-lookup"><span data-stu-id="ed910-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed910-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed910-104">Syntax</span></span>  
  
```  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ed910-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ed910-105">Methods</span></span>  
  
|<span data-ttu-id="ed910-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="ed910-106">Method</span></span>|<span data-ttu-id="ed910-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ed910-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="ed910-108">Pobiera wskaźnik interfejsu do nowego `IEnumDefinitionIdentity` obiekt, który zawiera te same elementy członkowskie, ponieważ `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="ed910-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="ed910-109">Pobiera określoną liczbę `IDefinitionIdentity` obiektów, począwszy od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="ed910-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="ed910-110">Przesuwa wskaźnik instrukcji na początku `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="ed910-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="ed910-111">Przesuwa wskaźnik instrukcji do przodu o określoną liczbę elementów, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="ed910-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed910-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed910-112">Requirements</span></span>  
 <span data-ttu-id="ed910-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed910-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed910-114">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="ed910-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="ed910-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed910-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed910-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed910-116">See also</span></span>

- [<span data-ttu-id="ed910-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="ed910-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="ed910-118">IDefinitionIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed910-118">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
