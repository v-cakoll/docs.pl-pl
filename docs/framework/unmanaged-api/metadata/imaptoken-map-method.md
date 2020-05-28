---
title: IMapToken::Map — Metoda
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
ms.openlocfilehash: 027694cee1b3e4d990796ba31300918f6d859679
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008199"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="1c9a1-102">IMapToken::Map — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c9a1-102">IMapToken::Map Method</span></span>
<span data-ttu-id="1c9a1-103">Mapuje relacje między zestawami przy użyciu podpisów metadanych.</span><span class="sxs-lookup"><span data-stu-id="1c9a1-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c9a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c9a1-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c9a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c9a1-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="1c9a1-106">podczas Token metadanych reprezentujący zaimportowany obiekt kodu.</span><span class="sxs-lookup"><span data-stu-id="1c9a1-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="1c9a1-107">podczas Token metadanych reprezentujący emitowany obiekt kodu.</span><span class="sxs-lookup"><span data-stu-id="1c9a1-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c9a1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c9a1-108">Remarks</span></span>  
 <span data-ttu-id="1c9a1-109">Gdy ponowne mapowanie tokenu odbywa się podczas scalania, oryginalny token jest objęty zakresem zaimportowanego (źródłowego) zakresu metadanych, a nowy token jest objęty zakresem metadanych emitowanych (docelowych).</span><span class="sxs-lookup"><span data-stu-id="1c9a1-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c9a1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c9a1-110">Requirements</span></span>  
 <span data-ttu-id="1c9a1-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c9a1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c9a1-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1c9a1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1c9a1-113">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1c9a1-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1c9a1-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c9a1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c9a1-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c9a1-115">See also</span></span>

- [<span data-ttu-id="1c9a1-116">IMapToken, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c9a1-116">IMapToken Interface</span></span>](imaptoken-interface.md)
