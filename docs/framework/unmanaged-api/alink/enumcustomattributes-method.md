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
ms.openlocfilehash: 6a5b3f1e9bf1444feb73949ef7133fbd9ae35134
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446473"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="506f7-102">EnumCustomAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="506f7-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="506f7-103">Pobiera niestandardowe atrybuty na poziomie zestawu.</span><span class="sxs-lookup"><span data-stu-id="506f7-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="506f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="506f7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="506f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="506f7-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="506f7-106">Uchwyt modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="506f7-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="506f7-107">Typ atrybutów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="506f7-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="506f7-108">Użyj `mdTokenNill` dla wszystkich atrybutów.</span><span class="sxs-lookup"><span data-stu-id="506f7-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="506f7-109">Odbiera tokeny atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="506f7-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="506f7-110">Określa rozmiar tablicy `rCustomValues`.</span><span class="sxs-lookup"><span data-stu-id="506f7-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="506f7-111">Opcjonalnie otrzymuje liczbę wartości tokenu.</span><span class="sxs-lookup"><span data-stu-id="506f7-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="506f7-112">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="506f7-112">Return Value</span></span>  
 <span data-ttu-id="506f7-113">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="506f7-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="506f7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="506f7-114">Requirements</span></span>  
 <span data-ttu-id="506f7-115">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="506f7-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="506f7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="506f7-116">See also</span></span>

- [<span data-ttu-id="506f7-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="506f7-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="506f7-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="506f7-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="506f7-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="506f7-119">ALink API</span></span>](index.md)
