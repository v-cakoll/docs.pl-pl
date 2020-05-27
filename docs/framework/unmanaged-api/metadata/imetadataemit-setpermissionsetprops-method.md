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
ms.openlocfilehash: 1e6ee1f2f497ef30a5390e7afac55c54705248ed
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007809"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="2a068-102">IMetaDataEmit::SetPermissionSetProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="2a068-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="2a068-103">Ustawia lub aktualizuje funkcje sygnatury metadanych zestawu uprawnień zdefiniowanego przez poprzednie wywołanie do [IMetaDataEmit::D efinepermissionset](imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="2a068-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a068-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a068-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a068-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a068-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="2a068-106">podczas Token metadanych, który reprezentuje obiekt, który ma być dekoracyjny.</span><span class="sxs-lookup"><span data-stu-id="2a068-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="2a068-107">podczas Wartość [CorDeclSecurity —](cordeclsecurity-enumeration.md) , która określa typ zabezpieczenia deklaracyjnego do użycia.</span><span class="sxs-lookup"><span data-stu-id="2a068-107">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="2a068-108">podczas Obiekt BLOB uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2a068-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="2a068-109">podczas Rozmiar, w bajtach, z `pvPermission` .</span><span class="sxs-lookup"><span data-stu-id="2a068-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="2a068-110">określoną `mdPermission`Token metadanych, który reprezentuje zaktualizowane uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="2a068-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a068-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a068-111">Requirements</span></span>  
 <span data-ttu-id="2a068-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a068-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a068-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2a068-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2a068-114">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2a068-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a068-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a068-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a068-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a068-116">See also</span></span>

- [<span data-ttu-id="2a068-117">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2a068-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2a068-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2a068-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
