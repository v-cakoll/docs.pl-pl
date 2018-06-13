---
title: IMetaDataEmit::DefinePermissionSet — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05339787b112ad029cb9870e8c6ffca37e55e631
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445192"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="b5299-102">IMetaDataEmit::DefinePermissionSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="b5299-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="b5299-103">Tworzy definicji zestawu uprawnień o podpisu określonych metadanych, a następnie pobiera token do tej definicji zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="b5299-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5299-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5299-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5299-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5299-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b5299-106">[in] Obiekt do korzystać.</span><span class="sxs-lookup"><span data-stu-id="b5299-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="b5299-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) wartość, która określa typ Zabezpieczenia deklaracyjne mają być używane.</span><span class="sxs-lookup"><span data-stu-id="b5299-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="b5299-108">[in] Obiektu BLOB uprawnień.</span><span class="sxs-lookup"><span data-stu-id="b5299-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="b5299-109">[in] Rozmiar w bajtach z `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="b5299-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="b5299-110">[out] Token zwrócony uprawnień.</span><span class="sxs-lookup"><span data-stu-id="b5299-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5299-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b5299-111">Requirements</span></span>  
 <span data-ttu-id="b5299-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5299-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5299-113">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b5299-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b5299-114">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5299-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5299-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5299-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5299-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5299-116">See Also</span></span>  
 [<span data-ttu-id="b5299-117">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="b5299-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="b5299-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b5299-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
