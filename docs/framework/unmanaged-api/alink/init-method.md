---
title: Init — Metoda
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf96770dd58c9b84596c082a615f626ec723cc6c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787246"
---
# <a name="init-method"></a><span data-ttu-id="8e977-102">Init — Metoda</span><span class="sxs-lookup"><span data-stu-id="8e977-102">Init Method</span></span>
<span data-ttu-id="8e977-103">Przygotowuje obiekty implementujące [interfejs IALink —](ialink-interface.md) do użytku.</span><span class="sxs-lookup"><span data-stu-id="8e977-103">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e977-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e977-104">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e977-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e977-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="8e977-106">Wskaźnik [interfejsu IMetaDataDispenserEx](../metadata/imetadatadispenserex-interface.md) do rozdzielacza metadanych.</span><span class="sxs-lookup"><span data-stu-id="8e977-106">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="8e977-107">Wskaźnik [interfejsu IMetaDataError](../metadata/imetadataerror-interface.md) do opcjonalnego interfejsu obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="8e977-107">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e977-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8e977-108">Return Value</span></span>  
 <span data-ttu-id="8e977-109">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8e977-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e977-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e977-110">Requirements</span></span>  
 <span data-ttu-id="8e977-111">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="8e977-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e977-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e977-112">See also</span></span>

- [<span data-ttu-id="8e977-113">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e977-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8e977-114">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8e977-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8e977-115">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="8e977-115">ALink API</span></span>](index.md)
