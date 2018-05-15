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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2633bfadaabf208a2b86fda83375c3a136b93b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="339b1-102">IMapToken::Map — Metoda</span><span class="sxs-lookup"><span data-stu-id="339b1-102">IMapToken::Map Method</span></span>
<span data-ttu-id="339b1-103">Mapuje relacji między zestawami przy użyciu podpisów metadanych.</span><span class="sxs-lookup"><span data-stu-id="339b1-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="339b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="339b1-104">Syntax</span></span>  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="339b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="339b1-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="339b1-106">[in] Token metadanych, który reprezentuje obiekt importowany kodu.</span><span class="sxs-lookup"><span data-stu-id="339b1-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="339b1-107">[in] Token metadanych, który reprezentuje obiekt emitowany kodu.</span><span class="sxs-lookup"><span data-stu-id="339b1-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="339b1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="339b1-108">Remarks</span></span>  
 <span data-ttu-id="339b1-109">Token mapowane ponownie wystąpi podczas scalania, oryginalny token ma zakres w zakresie metadanych importowanych (źródło), a nowy token, ma zakres w zakresie metadanych emitowany (docelowy).</span><span class="sxs-lookup"><span data-stu-id="339b1-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="339b1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="339b1-110">Requirements</span></span>  
 <span data-ttu-id="339b1-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="339b1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="339b1-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="339b1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="339b1-113">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="339b1-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="339b1-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="339b1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="339b1-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="339b1-115">See Also</span></span>  
 [<span data-ttu-id="339b1-116">IMapToken, interfejs</span><span class="sxs-lookup"><span data-stu-id="339b1-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
