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
ms.openlocfilehash: 34186ee8825c0981ec095cf855c76ff5f800907d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432357"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="9e040-102">IEnumDefinitionIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9e040-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="9e040-103">Pełni rolę modułu wyliczającego dla kolekcji `IDefinitionIdentity` obiektów.</span><span class="sxs-lookup"><span data-stu-id="9e040-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e040-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e040-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="9e040-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9e040-105">Methods</span></span>  
  
|<span data-ttu-id="9e040-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9e040-106">Method</span></span>|<span data-ttu-id="9e040-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9e040-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="9e040-108">Pobiera wskaźnika interfejsu na nowy `IEnumDefinitionIdentity` obiekt, który zawiera tych samych elementów członkowskich jako to `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="9e040-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="9e040-109">Pobiera określoną liczbę `IDefinitionIdentity` obiektów, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="9e040-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="9e040-110">Przesuwa wskaźnik instrukcji na początku `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="9e040-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="9e040-111">Przenosi do przodu wskaźnik instrukcji przez określoną liczbę elementów, licząc w bieżącym położeniu.</span><span class="sxs-lookup"><span data-stu-id="9e040-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e040-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e040-112">Requirements</span></span>  
 <span data-ttu-id="9e040-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e040-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e040-114">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="9e040-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="9e040-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e040-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e040-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e040-116">See Also</span></span>  
 [<span data-ttu-id="9e040-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="9e040-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="9e040-118">IDefinitionIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e040-118">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
