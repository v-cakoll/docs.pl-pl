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
ms.openlocfilehash: 09ccf731f0494b6eda49f6a15d04970a723c473b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742055"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="99512-102">EnumCustomAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="99512-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="99512-103">Pobiera atrybuty niestandardowe na poziomie zestawu.</span><span class="sxs-lookup"><span data-stu-id="99512-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99512-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99512-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="99512-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99512-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="99512-106">Uchwyt modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="99512-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="99512-107">Typ atrybutów, które mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="99512-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="99512-108">Użyj `mdTokenNill` dla wszystkich atrybutów.</span><span class="sxs-lookup"><span data-stu-id="99512-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="99512-109">Odbiera tokenów atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="99512-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="99512-110">Określa rozmiar `rCustomValues` tablicy.</span><span class="sxs-lookup"><span data-stu-id="99512-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="99512-111">Opcjonalnie odbiera token wartości.</span><span class="sxs-lookup"><span data-stu-id="99512-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99512-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="99512-112">Return Value</span></span>  
 <span data-ttu-id="99512-113">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="99512-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99512-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99512-114">Requirements</span></span>  
 <span data-ttu-id="99512-115">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="99512-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99512-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99512-116">See also</span></span>

- [<span data-ttu-id="99512-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="99512-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="99512-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="99512-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="99512-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="99512-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
