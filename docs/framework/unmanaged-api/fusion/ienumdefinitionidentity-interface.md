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
ms.openlocfilehash: 88c2513229b6a4183cadbdc78e505910e01e152c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796471"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="46c25-102">IEnumDefinitionIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="46c25-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="46c25-103">Służy jako moduł wyliczający dla kolekcji `IDefinitionIdentity` obiektów.</span><span class="sxs-lookup"><span data-stu-id="46c25-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46c25-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="46c25-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="methods"></a><span data-ttu-id="46c25-105">Metody</span><span class="sxs-lookup"><span data-stu-id="46c25-105">Methods</span></span>  
  
|<span data-ttu-id="46c25-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="46c25-106">Method</span></span>|<span data-ttu-id="46c25-107">Opis</span><span class="sxs-lookup"><span data-stu-id="46c25-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="46c25-108">Pobiera wskaźnik interfejsu do nowego `IEnumDefinitionIdentity` obiektu, który zawiera te same składowe. `IEnumDefinitionIdentity`</span><span class="sxs-lookup"><span data-stu-id="46c25-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="46c25-109">Pobiera określoną liczbę `IDefinitionIdentity` obiektów, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="46c25-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="46c25-110">Przenosi wskaźnik instrukcji na początek tego `IEnumDefinitionIdentity`elementu.</span><span class="sxs-lookup"><span data-stu-id="46c25-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="46c25-111">Przesuwa wskaźnik instrukcji do przodu o określoną liczbę elementów, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="46c25-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46c25-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46c25-112">Requirements</span></span>  
 <span data-ttu-id="46c25-113">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46c25-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46c25-114">**Nagłówki** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="46c25-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="46c25-115">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46c25-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c25-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46c25-116">See also</span></span>

- [<span data-ttu-id="46c25-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="46c25-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="46c25-118">IDefinitionIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="46c25-118">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
