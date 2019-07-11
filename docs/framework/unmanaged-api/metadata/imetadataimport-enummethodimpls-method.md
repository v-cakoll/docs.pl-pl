---
title: IMetaDataImport::EnumMethodImpls — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8be30e8c3b6bc7c03ede5f897f176e04153003b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781963"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="4d0d0-102">IMetaDataImport::EnumMethodImpls — Metoda</span><span class="sxs-lookup"><span data-stu-id="4d0d0-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="4d0d0-103">Wylicza MethodBody i MethodDeclaration tokenów reprezentujący metody określonego typu.</span><span class="sxs-lookup"><span data-stu-id="4d0d0-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d0d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d0d0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d0d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d0d0-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4d0d0-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="4d0d0-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4d0d0-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="4d0d0-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="4d0d0-108">[in] Element TypeDef dla typu tokenu implementacje metod, których można wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="4d0d0-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="4d0d0-109">[out] Tablica do przechowywania tokenów MethodBody.</span><span class="sxs-lookup"><span data-stu-id="4d0d0-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="4d0d0-110">[out] Tablica do przechowywania tokenów MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="4d0d0-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4d0d0-111">[in] Maksymalny rozmiar `rMethodBody` i `rMethodDecl` tablic.</span><span class="sxs-lookup"><span data-stu-id="4d0d0-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4d0d0-112">[in] Rzeczywista liczba zwracanych w metodach `rMethodBody` i `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="4d0d0-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d0d0-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4d0d0-113">Return Value</span></span>  
  
|<span data-ttu-id="4d0d0-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4d0d0-114">HRESULT</span></span>|<span data-ttu-id="4d0d0-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4d0d0-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4d0d0-116">`EnumMethodImpls` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="4d0d0-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4d0d0-117">Nie ma żadnych tokeny metoda wyliczania.</span><span class="sxs-lookup"><span data-stu-id="4d0d0-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="4d0d0-118">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="4d0d0-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d0d0-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d0d0-119">Requirements</span></span>  
 <span data-ttu-id="4d0d0-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d0d0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d0d0-121">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4d0d0-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d0d0-122">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4d0d0-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d0d0-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d0d0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d0d0-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d0d0-124">See also</span></span>

- [<span data-ttu-id="4d0d0-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d0d0-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4d0d0-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d0d0-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
