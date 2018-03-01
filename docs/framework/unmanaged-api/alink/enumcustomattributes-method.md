---
title: "EnumCustomAttributes — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d616babb47ac0282ef56d119ab448a94fd24c7c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="c996e-102">EnumCustomAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="c996e-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="c996e-103">Pobiera atrybuty niestandardowe na poziomie zestawu.</span><span class="sxs-lookup"><span data-stu-id="c996e-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c996e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c996e-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c996e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c996e-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="c996e-106">Dojście do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="c996e-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="c996e-107">Typ atrybutów, które mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="c996e-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="c996e-108">Użyj `mdTokenNill` dla wszystkich atrybutów.</span><span class="sxs-lookup"><span data-stu-id="c996e-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="c996e-109">Odbiera tokeny atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="c996e-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c996e-110">Określa rozmiar `rCustomValues` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c996e-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="c996e-111">Opcjonalnie odbiera token wartości.</span><span class="sxs-lookup"><span data-stu-id="c996e-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c996e-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c996e-112">Return Value</span></span>  
 <span data-ttu-id="c996e-113">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c996e-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c996e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c996e-114">Requirements</span></span>  
 <span data-ttu-id="c996e-115">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="c996e-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c996e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c996e-116">See Also</span></span>  
 [<span data-ttu-id="c996e-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="c996e-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c996e-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c996e-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c996e-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="c996e-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
