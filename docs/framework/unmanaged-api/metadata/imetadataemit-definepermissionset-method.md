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
ms.openlocfilehash: a0fd3fdb6dde9fd6b88ea6c64ed907c8a3e9e46d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175801"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="194a8-102">IMetaDataEmit::DefinePermissionSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="194a8-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="194a8-103">Tworzy definicję zestawu uprawnień z określonym podpisem metadanych i pobiera token do tej definicji zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="194a8-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="194a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="194a8-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="194a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="194a8-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="194a8-106">[w] Obiekt, który ma być ozdobiony.</span><span class="sxs-lookup"><span data-stu-id="194a8-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="194a8-107">[w] Wartość [CorDeclSecurity,](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) która określa typ zabezpieczeń deklaratywnych, które mają być używane.</span><span class="sxs-lookup"><span data-stu-id="194a8-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="194a8-108">[w] Obiekt BLOB uprawnień.</span><span class="sxs-lookup"><span data-stu-id="194a8-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="194a8-109">[w] Rozmiar w bajtach `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="194a8-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="194a8-110">[na zewnątrz] Token zwróconego uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="194a8-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="194a8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="194a8-111">Requirements</span></span>  
 <span data-ttu-id="194a8-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="194a8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="194a8-113">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="194a8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="194a8-114">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="194a8-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="194a8-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="194a8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="194a8-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="194a8-116">See also</span></span>

- [<span data-ttu-id="194a8-117">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="194a8-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="194a8-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="194a8-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
