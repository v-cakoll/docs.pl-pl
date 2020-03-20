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
ms.openlocfilehash: e766cec8fd84713e12c43cd1095650ed5b757bcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175476"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="f8d5e-102">IMetaDataImport::EnumMethodImpls — Metoda</span><span class="sxs-lookup"><span data-stu-id="f8d5e-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="f8d5e-103">Wylicza tokeny MethodBody i MethodDeclaration reprezentujące metody określonego typu.</span><span class="sxs-lookup"><span data-stu-id="f8d5e-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8d5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8d5e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f8d5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8d5e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f8d5e-106">[w, na zewnątrz] Wskaźnik do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="f8d5e-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="f8d5e-107">Musi to być null dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="f8d5e-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="f8d5e-108">[w] A TypeDef token dla typu, którego implementacje metody do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f8d5e-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="f8d5e-109">[na zewnątrz] Tablica do przechowywania tokenów MethodBody.</span><span class="sxs-lookup"><span data-stu-id="f8d5e-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="f8d5e-110">[na zewnątrz] Tablica do przechowywania tokenów MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="f8d5e-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f8d5e-111">[w] Maksymalny rozmiar `rMethodBody` tablic `rMethodDecl` i tablic.</span><span class="sxs-lookup"><span data-stu-id="f8d5e-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f8d5e-112">[w] Rzeczywista liczba metod `rMethodBody` zwróconych w i `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="f8d5e-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8d5e-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f8d5e-113">Return Value</span></span>  
  
|<span data-ttu-id="f8d5e-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f8d5e-114">HRESULT</span></span>|<span data-ttu-id="f8d5e-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f8d5e-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f8d5e-116">`EnumMethodImpls`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f8d5e-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f8d5e-117">Nie ma żadnych tokenów metody do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f8d5e-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="f8d5e-118">W takim `pcTokens` przypadku wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="f8d5e-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8d5e-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8d5e-119">Requirements</span></span>  
 <span data-ttu-id="f8d5e-120">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8d5e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8d5e-121">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="f8d5e-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f8d5e-122">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8d5e-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8d5e-123">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8d5e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d5e-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8d5e-124">See also</span></span>

- [<span data-ttu-id="f8d5e-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f8d5e-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f8d5e-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f8d5e-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
