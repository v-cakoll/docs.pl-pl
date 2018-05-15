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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d80e3206f74c3c50c8436563b0e39d1229a963b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="98145-102">IMetaDataEmit::SetPermissionSetProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="98145-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="98145-103">Ustawia lub aktualizuje funkcje podpisu metadanych zestawu uprawnień wynika z wcześniejszym wywołaniu [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="98145-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98145-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="98145-104">Syntax</span></span>  
  
```  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98145-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98145-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="98145-106">[in] Token metadanych, który reprezentuje obiekt umożliwiający korzystać.</span><span class="sxs-lookup"><span data-stu-id="98145-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="98145-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) wartość, która określa typ Zabezpieczenia deklaracyjne mają być używane.</span><span class="sxs-lookup"><span data-stu-id="98145-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="98145-108">[in] Obiektu BLOB uprawnień.</span><span class="sxs-lookup"><span data-stu-id="98145-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="98145-109">[in] Rozmiar w bajtach z `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="98145-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="98145-110">[out] `mdPermission` Token metadanych, który reprezentuje zaktualizowano uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="98145-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98145-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="98145-111">Requirements</span></span>  
 <span data-ttu-id="98145-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98145-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98145-113">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="98145-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98145-114">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="98145-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98145-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98145-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98145-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98145-116">See Also</span></span>  
 [<span data-ttu-id="98145-117">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="98145-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="98145-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="98145-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
