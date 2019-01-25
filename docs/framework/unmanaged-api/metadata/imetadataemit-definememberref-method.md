---
title: IMetaDataEmit::DefineMemberRef — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 578f79136f6ccc8a6b7eac644b2a5084d30d2ba0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722832"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="de334-102">IMetaDataEmit::DefineMemberRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="de334-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="de334-103">Określa odwołanie do elementu członkowskiego modułu poza bieżącym zakresem, a następnie pobiera token do tej definicji odwołania.</span><span class="sxs-lookup"><span data-stu-id="de334-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de334-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de334-104">Syntax</span></span>  
  
```  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de334-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de334-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="de334-106">[in] Tokenu dla docelowego elementu członkowskiego klasy lub interfejsu, jeśli element nie jest globalne; Jeśli element jest globalnym, `mdModuleRef` tokenu dla tego innego pliku.</span><span class="sxs-lookup"><span data-stu-id="de334-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="de334-107">[in] Nazwa elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="de334-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="de334-108">[in] Podpis elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="de334-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="de334-109">[in] Liczba bajtów w `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="de334-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="de334-110">[out] `mdMemberRef` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="de334-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de334-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de334-111">Requirements</span></span>  
 <span data-ttu-id="de334-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de334-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de334-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="de334-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de334-114">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="de334-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de334-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de334-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de334-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de334-116">See also</span></span>
- [<span data-ttu-id="de334-117">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="de334-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="de334-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="de334-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
