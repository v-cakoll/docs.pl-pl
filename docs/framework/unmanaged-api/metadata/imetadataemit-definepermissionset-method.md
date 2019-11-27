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
ms.openlocfilehash: 4e11a52c977de7796043868e80c147d8cfd1f506
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431575"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="4c109-102">IMetaDataEmit::DefinePermissionSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="4c109-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="4c109-103">Tworzy definicję zestawu uprawnień z określonym podpisem metadanych i pobiera token do tej definicji zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="4c109-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c109-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c109-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c109-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c109-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="4c109-106">podczas Obiekt, który ma być dekoracyjny.</span><span class="sxs-lookup"><span data-stu-id="4c109-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="4c109-107">podczas Wartość [CorDeclSecurity —](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) , która określa typ zabezpieczenia deklaracyjnego do użycia.</span><span class="sxs-lookup"><span data-stu-id="4c109-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="4c109-108">podczas Obiekt BLOB uprawnień.</span><span class="sxs-lookup"><span data-stu-id="4c109-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="4c109-109">podczas Rozmiar w bajtach `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="4c109-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="4c109-110">określoną Zwrócony token uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="4c109-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c109-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c109-111">Requirements</span></span>  
 <span data-ttu-id="4c109-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c109-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c109-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4c109-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c109-114">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4c109-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c109-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c109-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c109-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c109-116">See also</span></span>

- [<span data-ttu-id="4c109-117">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="4c109-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4c109-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4c109-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
