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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119369"
---
# <a name="init-method"></a><span data-ttu-id="45aaa-102">Init — Metoda</span><span class="sxs-lookup"><span data-stu-id="45aaa-102">Init Method</span></span>
<span data-ttu-id="45aaa-103">Przygotowuje obiektów Implementowanie [ialink — interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) do użycia.</span><span class="sxs-lookup"><span data-stu-id="45aaa-103">Prepares objects implementing the [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45aaa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="45aaa-104">Syntax</span></span>  
  
```  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="45aaa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45aaa-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="45aaa-106">[Imetadatadispenserex — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) wskaźnik do rozdzielacz metadanych.</span><span class="sxs-lookup"><span data-stu-id="45aaa-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="45aaa-107">[Imetadataerror — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) wskaźnik do opcjonalne błąd obsługi interfejsu.</span><span class="sxs-lookup"><span data-stu-id="45aaa-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45aaa-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="45aaa-108">Return Value</span></span>  
 <span data-ttu-id="45aaa-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="45aaa-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45aaa-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45aaa-110">Requirements</span></span>  
 <span data-ttu-id="45aaa-111">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="45aaa-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45aaa-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45aaa-112">See also</span></span>

- [<span data-ttu-id="45aaa-113">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="45aaa-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="45aaa-114">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="45aaa-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="45aaa-115">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="45aaa-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
