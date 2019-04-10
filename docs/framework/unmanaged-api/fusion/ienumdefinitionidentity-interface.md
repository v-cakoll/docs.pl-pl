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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214848"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="00fba-102">IEnumDefinitionIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="00fba-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="00fba-103">Służy jako modułu wyliczającego dla kolekcji `IDefinitionIdentity` obiektów.</span><span class="sxs-lookup"><span data-stu-id="00fba-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00fba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00fba-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="00fba-105">Metody</span><span class="sxs-lookup"><span data-stu-id="00fba-105">Methods</span></span>  
  
|<span data-ttu-id="00fba-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="00fba-106">Method</span></span>|<span data-ttu-id="00fba-107">Opis</span><span class="sxs-lookup"><span data-stu-id="00fba-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="00fba-108">Pobiera wskaźnik interfejsu do nowego `IEnumDefinitionIdentity` obiekt, który zawiera te same elementy członkowskie, ponieważ `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="00fba-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="00fba-109">Pobiera określoną liczbę `IDefinitionIdentity` obiektów, począwszy od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="00fba-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="00fba-110">Przesuwa wskaźnik instrukcji na początku `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="00fba-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="00fba-111">Przesuwa wskaźnik instrukcji do przodu o określoną liczbę elementów, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="00fba-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00fba-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00fba-112">Requirements</span></span>  
 <span data-ttu-id="00fba-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00fba-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00fba-114">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="00fba-114">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="00fba-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="00fba-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="00fba-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00fba-116">See also</span></span>

- [<span data-ttu-id="00fba-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="00fba-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="00fba-118">IDefinitionIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="00fba-118">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
