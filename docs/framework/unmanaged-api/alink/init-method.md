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
ms.openlocfilehash: 60602462376543fe934bb3c58bc4988fa8ab34bf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119369"
---
# <a name="init-method"></a><span data-ttu-id="1afb9-102">Init — Metoda</span><span class="sxs-lookup"><span data-stu-id="1afb9-102">Init Method</span></span>
<span data-ttu-id="1afb9-103">Przygotowuje obiektów Implementowanie [ialink — interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) do użycia.</span><span class="sxs-lookup"><span data-stu-id="1afb9-103">Prepares objects implementing the [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1afb9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1afb9-104">Syntax</span></span>  
  
```  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1afb9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1afb9-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="1afb9-106">[Imetadatadispenserex — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) wskaźnik do rozdzielacz metadanych.</span><span class="sxs-lookup"><span data-stu-id="1afb9-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="1afb9-107">[Imetadataerror — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) wskaźnik do opcjonalne błąd obsługi interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1afb9-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1afb9-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1afb9-108">Return Value</span></span>  
 <span data-ttu-id="1afb9-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="1afb9-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1afb9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1afb9-110">Requirements</span></span>  
 <span data-ttu-id="1afb9-111">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="1afb9-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1afb9-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1afb9-112">See also</span></span>

- [<span data-ttu-id="1afb9-113">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1afb9-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="1afb9-114">IALink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1afb9-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="1afb9-115">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="1afb9-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
