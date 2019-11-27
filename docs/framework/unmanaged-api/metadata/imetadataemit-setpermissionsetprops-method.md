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
ms.openlocfilehash: 53a75b8e7edd15cd233577e0a3714fb5d981495f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432325"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="bde8b-102">IMetaDataEmit::SetPermissionSetProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="bde8b-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="bde8b-103">Ustawia lub aktualizuje funkcje sygnatury metadanych zestawu uprawnień zdefiniowanego przez poprzednie wywołanie do [IMetaDataEmit::D efinepermissionset](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="bde8b-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bde8b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bde8b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bde8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bde8b-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="bde8b-106">podczas Token metadanych, który reprezentuje obiekt, który ma być dekoracyjny.</span><span class="sxs-lookup"><span data-stu-id="bde8b-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="bde8b-107">podczas Wartość [CorDeclSecurity —](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) , która określa typ zabezpieczenia deklaracyjnego do użycia.</span><span class="sxs-lookup"><span data-stu-id="bde8b-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="bde8b-108">podczas Obiekt BLOB uprawnień.</span><span class="sxs-lookup"><span data-stu-id="bde8b-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="bde8b-109">podczas Rozmiar w bajtach `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="bde8b-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="bde8b-110">określoną `mdPermission` token metadanych, który reprezentuje zaktualizowane uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="bde8b-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bde8b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bde8b-111">Requirements</span></span>  
 <span data-ttu-id="bde8b-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bde8b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bde8b-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bde8b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bde8b-114">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bde8b-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bde8b-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bde8b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bde8b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bde8b-116">See also</span></span>

- [<span data-ttu-id="bde8b-117">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="bde8b-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bde8b-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bde8b-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
