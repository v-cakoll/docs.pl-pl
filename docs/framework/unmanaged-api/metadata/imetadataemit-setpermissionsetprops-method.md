---
title: IMetaDataEmit::SetPermissionSetProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
ms.openlocfilehash: de4cfdf2a9353eebdebaf4df9e481d06d776ff04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177488"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="83876-102">IMetaDataEmit::SetPermissionSetProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="83876-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="83876-103">Ustawia lub aktualizuje funkcje podpisu metadanych zestawu uprawnień zdefiniowanego przez wcześniejsze wywołanie [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="83876-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83876-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83876-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83876-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83876-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="83876-106">[w] Token metadanych, który reprezentuje obiekt, który ma zostać ozdobiony.</span><span class="sxs-lookup"><span data-stu-id="83876-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="83876-107">[w] Wartość [CorDeclSecurity,](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) która określa typ zabezpieczeń deklaratywnych, które mają być używane.</span><span class="sxs-lookup"><span data-stu-id="83876-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="83876-108">[w] Obiekt BLOB uprawnień.</span><span class="sxs-lookup"><span data-stu-id="83876-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="83876-109">[w] Rozmiar w bajtach `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="83876-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="83876-110">[na zewnątrz] Token `mdPermission` metadanych reprezentujący zaktualizowane uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="83876-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83876-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83876-111">Requirements</span></span>  
 <span data-ttu-id="83876-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83876-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83876-113">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="83876-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83876-114">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83876-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83876-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83876-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83876-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83876-116">See also</span></span>

- [<span data-ttu-id="83876-117">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="83876-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="83876-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="83876-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
