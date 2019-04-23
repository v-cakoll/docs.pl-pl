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
ms.openlocfilehash: 510c33b8e0e26bead00dcb85a6ceba102a5f267d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163777"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="5f578-102">IMetaDataEmit::SetPermissionSetProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="5f578-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="5f578-103">Ustawia lub aktualizuje funkcji podpisu metadanych zestawu uprawnień, zdefiniowane przez wcześniejsze wywołanie [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="5f578-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f578-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f578-104">Syntax</span></span>  
  
```  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f578-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f578-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="5f578-106">[in] Token metadanych, który reprezentuje obiekt umożliwiający posiadać.</span><span class="sxs-lookup"><span data-stu-id="5f578-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="5f578-107">[in] A [cordeclsecurity —](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) wartość, która określa typ zabezpieczenia deklaratywne ma być używany.</span><span class="sxs-lookup"><span data-stu-id="5f578-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="5f578-108">[in] Uprawnienie obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="5f578-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="5f578-109">[in] Rozmiar w bajtach z `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="5f578-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="5f578-110">[out] `mdPermission` Token metadanych, który reprezentuje zaktualizowanymi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="5f578-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f578-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f578-111">Requirements</span></span>  
 <span data-ttu-id="5f578-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f578-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f578-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5f578-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5f578-114">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5f578-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f578-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f578-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f578-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f578-116">See also</span></span>

- [<span data-ttu-id="5f578-117">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f578-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5f578-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f578-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
