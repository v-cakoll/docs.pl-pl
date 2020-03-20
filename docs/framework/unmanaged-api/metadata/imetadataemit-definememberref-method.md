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
ms.openlocfilehash: e371330336002c673f2c54d882e70dbed41b743c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175840"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="16697-102">IMetaDataEmit::DefineMemberRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="16697-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="16697-103">Definiuje odwołanie do elementu członkowskiego modułu poza bieżącym zakresem i pobiera token do tej definicji odwołania.</span><span class="sxs-lookup"><span data-stu-id="16697-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16697-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16697-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (
    [in]  mdToken           tkImport,
    [in]  LPCWSTR           szName,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMemberRef       *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16697-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16697-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="16697-106">[w] Token dla klasy lub interfejsu docelowego elementu członkowskiego, jeśli element członkowski nie jest globalny; jeśli element członkowski `mdModuleRef` jest globalny, token dla tego innego pliku.</span><span class="sxs-lookup"><span data-stu-id="16697-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="16697-107">[w] Nazwa elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="16697-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="16697-108">[w] Podpis elementu członkowskiego docelowego.</span><span class="sxs-lookup"><span data-stu-id="16697-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="16697-109">[w] Liczba bajtów `pvSigBlob`w pliku .</span><span class="sxs-lookup"><span data-stu-id="16697-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="16697-110">[na zewnątrz] Token `mdMemberRef` przypisany.</span><span class="sxs-lookup"><span data-stu-id="16697-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16697-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16697-111">Requirements</span></span>  
 <span data-ttu-id="16697-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16697-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16697-113">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="16697-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16697-114">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16697-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16697-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16697-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16697-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16697-116">See also</span></span>

- [<span data-ttu-id="16697-117">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="16697-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="16697-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="16697-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
