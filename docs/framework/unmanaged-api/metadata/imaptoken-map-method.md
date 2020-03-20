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
ms.openlocfilehash: 428b022ed560648f59798154d5987d382938c280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176074"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="ae939-102">IMapToken::Map — Metoda</span><span class="sxs-lookup"><span data-stu-id="ae939-102">IMapToken::Map Method</span></span>
<span data-ttu-id="ae939-103">Mapuje relację między zestawami przy użyciu podpisów metadanych.</span><span class="sxs-lookup"><span data-stu-id="ae939-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae939-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae939-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae939-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae939-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="ae939-106">[w] Token metadanych reprezentujący importowany obiekt kodu.</span><span class="sxs-lookup"><span data-stu-id="ae939-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="ae939-107">[w] Token metadanych, który reprezentuje obiekt emitowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="ae939-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae939-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae939-108">Remarks</span></span>  
 <span data-ttu-id="ae939-109">Gdy ponowna mapa tokenu występuje podczas scalania, oryginalny token jest objęty zakresem w zakresie metadanych importowanych (źródłowych), a nowy token jest objęty zakresem w zakresie metadanych emitowanych (docelowych).</span><span class="sxs-lookup"><span data-stu-id="ae939-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae939-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae939-110">Requirements</span></span>  
 <span data-ttu-id="ae939-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae939-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae939-112">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="ae939-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae939-113">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ae939-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ae939-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae939-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae939-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae939-115">See also</span></span>

- [<span data-ttu-id="ae939-116">IMapToken, interfejs</span><span class="sxs-lookup"><span data-stu-id="ae939-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
