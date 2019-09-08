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
ms.openlocfilehash: 5d8827f46a12bd090fa27e71072d833607d34677
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777352"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="c2626-102">EnumCustomAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2626-102">EnumCustomAttributes Method</span></span>
<span data-ttu-id="c2626-103">Pobiera niestandardowe atrybuty na poziomie zestawu.</span><span class="sxs-lookup"><span data-stu-id="c2626-103">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2626-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2626-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2626-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2626-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="c2626-106">Uchwyt modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="c2626-106">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="c2626-107">Typ atrybutów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c2626-107">Type of attributes to be enumerated.</span></span> <span data-ttu-id="c2626-108">Używać `mdTokenNill` dla wszystkich atrybutów.</span><span class="sxs-lookup"><span data-stu-id="c2626-108">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="c2626-109">Odbiera tokeny atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="c2626-109">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c2626-110">Określa rozmiar `rCustomValues` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c2626-110">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="c2626-111">Opcjonalnie otrzymuje liczbę wartości tokenu.</span><span class="sxs-lookup"><span data-stu-id="c2626-111">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2626-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c2626-112">Return Value</span></span>  
 <span data-ttu-id="c2626-113">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c2626-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2626-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2626-114">Requirements</span></span>  
 <span data-ttu-id="c2626-115">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="c2626-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2626-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2626-116">See also</span></span>

- [<span data-ttu-id="c2626-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="c2626-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c2626-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c2626-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c2626-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="c2626-119">ALink API</span></span>](index.md)
