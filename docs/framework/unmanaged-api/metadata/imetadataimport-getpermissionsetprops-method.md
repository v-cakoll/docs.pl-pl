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
ms.openlocfilehash: 5faf1a6ae89045b2ef17fab789ee6e5bf23eecf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175346"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="8fd78-102">IMetaDataImport::GetPermissionSetProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="8fd78-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="8fd78-103">Pobiera metadane skojarzone <xref:System.Security.PermissionSet?displayProperty=nameWithType> z reprezentowane przez token określony uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="8fd78-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fd78-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8fd78-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,
   [out] void const        **ppvPermission,
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fd78-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fd78-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="8fd78-106">[w] Token metadanych uprawnień, który reprezentuje zestaw uprawnień, aby uzyskać właściwości metadanych dla.</span><span class="sxs-lookup"><span data-stu-id="8fd78-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="8fd78-107">[na zewnątrz] Wskaźnik do zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="8fd78-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="8fd78-108">[na zewnątrz] Wskaźnik do binarnego podpisu metadanych zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="8fd78-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="8fd78-109">[na zewnątrz] Rozmiar w bajtach . `ppvPermission`</span><span class="sxs-lookup"><span data-stu-id="8fd78-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fd78-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8fd78-110">Requirements</span></span>  
 <span data-ttu-id="8fd78-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fd78-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fd78-112">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="8fd78-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8fd78-113">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8fd78-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8fd78-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fd78-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fd78-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8fd78-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="8fd78-116">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8fd78-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8fd78-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8fd78-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
