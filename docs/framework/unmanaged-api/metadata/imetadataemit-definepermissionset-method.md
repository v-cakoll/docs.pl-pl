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
ms.openlocfilehash: 33eadccf691b14289a46ff460f3cef8ae636b129
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043982"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="abc2f-102">IMetaDataEmit::DefinePermissionSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="abc2f-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="abc2f-103">Tworzy definicję zestawu uprawnień o podpisu określonych metadanych, a następnie pobiera token do tej definicji zestaw uprawnień.</span><span class="sxs-lookup"><span data-stu-id="abc2f-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abc2f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="abc2f-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abc2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abc2f-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="abc2f-106">[in] Obiekt do posiadać.</span><span class="sxs-lookup"><span data-stu-id="abc2f-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="abc2f-107">[in] A [cordeclsecurity —](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) wartość, która określa typ zabezpieczenia deklaratywne ma być używany.</span><span class="sxs-lookup"><span data-stu-id="abc2f-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="abc2f-108">[in] Uprawnienie obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="abc2f-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="abc2f-109">[in] Rozmiar w bajtach z `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="abc2f-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="abc2f-110">[out] Token zwracany uprawnień.</span><span class="sxs-lookup"><span data-stu-id="abc2f-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abc2f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abc2f-111">Requirements</span></span>  
 <span data-ttu-id="abc2f-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abc2f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abc2f-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="abc2f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="abc2f-114">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="abc2f-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abc2f-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abc2f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc2f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abc2f-116">See also</span></span>

- [<span data-ttu-id="abc2f-117">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="abc2f-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="abc2f-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="abc2f-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
