---
title: IMetaDataImport::GetPermissionSetProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48cd62f89f1112a1007a5661dc55fe2977dace2b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778918"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="938ca-102">IMetaDataImport::GetPermissionSetProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="938ca-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="938ca-103">Pobiera metadane skojarzone z <xref:System.Security.PermissionSet?displayProperty=nameWithType> reprezentowany przez określony token uprawnień.</span><span class="sxs-lookup"><span data-stu-id="938ca-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="938ca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="938ca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="938ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="938ca-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="938ca-106">[in] Token metadanych uprawnienie reprezentuje zestaw uprawnień, aby pobrać właściwości metadanych.</span><span class="sxs-lookup"><span data-stu-id="938ca-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="938ca-107">[out] Wskaźnik do zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="938ca-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="938ca-108">[out] Wskaźnik do podpisu binarne metadanych zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="938ca-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="938ca-109">[out] Rozmiar w bajtach `ppvPermission`.</span><span class="sxs-lookup"><span data-stu-id="938ca-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="938ca-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="938ca-110">Requirements</span></span>  
 <span data-ttu-id="938ca-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="938ca-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="938ca-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="938ca-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="938ca-113">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="938ca-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="938ca-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="938ca-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938ca-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="938ca-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="938ca-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="938ca-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="938ca-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="938ca-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
