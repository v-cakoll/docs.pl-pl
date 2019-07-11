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
ms.openlocfilehash: 8ac12d5b6bc2911e3bd879285a9a12f65c426f0d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745856"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="887dd-102">IMapToken::Map — Metoda</span><span class="sxs-lookup"><span data-stu-id="887dd-102">IMapToken::Map Method</span></span>
<span data-ttu-id="887dd-103">Mapuje relacji między zestawami, przy użyciu sygnatur metadanych.</span><span class="sxs-lookup"><span data-stu-id="887dd-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="887dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="887dd-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="887dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="887dd-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="887dd-106">[in] Token metadanych, który reprezentuje obiekt importowany kodu.</span><span class="sxs-lookup"><span data-stu-id="887dd-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="887dd-107">[in] Token metadanych, który reprezentuje obiekt emitowany kod.</span><span class="sxs-lookup"><span data-stu-id="887dd-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="887dd-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="887dd-108">Remarks</span></span>  
 <span data-ttu-id="887dd-109">Sytuacji tokenu mapowane ponownie podczas scalania, pierwotny token jest zakresem w zakresie metadanych importowanych (źródło) i obejmuje nowy token w zakresie metadanych emitowany (docelowy).</span><span class="sxs-lookup"><span data-stu-id="887dd-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="887dd-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="887dd-110">Requirements</span></span>  
 <span data-ttu-id="887dd-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="887dd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="887dd-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="887dd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="887dd-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="887dd-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="887dd-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="887dd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="887dd-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="887dd-115">See also</span></span>

- [<span data-ttu-id="887dd-116">IMapToken, interfejs</span><span class="sxs-lookup"><span data-stu-id="887dd-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
