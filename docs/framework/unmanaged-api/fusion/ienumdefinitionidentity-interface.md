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
ms.openlocfilehash: 09c6431ec885c8b797dc9bb5f5c3ffe21890ccc7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107941"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="5cd2c-102">IEnumDefinitionIdentity — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5cd2c-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="5cd2c-103">Służy jako moduł wyliczający dla kolekcji obiektów `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="5cd2c-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cd2c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5cd2c-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="5cd2c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5cd2c-105">Methods</span></span>  
  
|<span data-ttu-id="5cd2c-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5cd2c-106">Method</span></span>|<span data-ttu-id="5cd2c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5cd2c-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="5cd2c-108">Pobiera wskaźnik interfejsu do nowego obiektu `IEnumDefinitionIdentity`, który zawiera te same elementy członkowskie co ten `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="5cd2c-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="5cd2c-109">Pobiera określoną liczbę `IDefinitionIdentity` obiektów, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="5cd2c-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="5cd2c-110">Przenosi wskaźnik instrukcji na początek tego `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="5cd2c-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="5cd2c-111">Przesuwa wskaźnik instrukcji do przodu o określoną liczbę elementów, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="5cd2c-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5cd2c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5cd2c-112">Requirements</span></span>  
 <span data-ttu-id="5cd2c-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cd2c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cd2c-114">**Nagłówek:** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="5cd2c-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="5cd2c-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cd2c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cd2c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cd2c-116">See also</span></span>

- [<span data-ttu-id="5cd2c-117">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="5cd2c-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="5cd2c-118">IDefinitionIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="5cd2c-118">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
