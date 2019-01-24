---
title: EnumCustomAttributes — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bba34b7f0956e602de690b8aa30d955acc526e8f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529492"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="996af-102">EnumCustomAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="996af-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="996af-103">Pobiera atrybuty niestandardowe na poziomie zestawu.</span><span class="sxs-lookup"><span data-stu-id="996af-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="996af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="996af-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="996af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="996af-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="996af-106">Uchwyt modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="996af-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="996af-107">Typ atrybutów, które mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="996af-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="996af-108">Użyj `mdTokenNill` dla wszystkich atrybutów.</span><span class="sxs-lookup"><span data-stu-id="996af-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="996af-109">Odbiera tokenów atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="996af-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="996af-110">Określa rozmiar `rCustomValues` tablicy.</span><span class="sxs-lookup"><span data-stu-id="996af-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="996af-111">Opcjonalnie odbiera token wartości.</span><span class="sxs-lookup"><span data-stu-id="996af-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="996af-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="996af-112">Return Value</span></span>  
 <span data-ttu-id="996af-113">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="996af-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="996af-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="996af-114">Requirements</span></span>  
 <span data-ttu-id="996af-115">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="996af-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="996af-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="996af-116">See also</span></span>
- [<span data-ttu-id="996af-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="996af-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="996af-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="996af-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="996af-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="996af-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
