---
title: "IMetaDataImport::GetRVA — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6c055afaa129b52c67cd0463a5d44afec5cde103
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="8b136-102">IMetaDataImport::GetRVA — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b136-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="8b136-103">Pobiera adres względny wirtualnych (RVA) i flagi implementacji metody lub pola reprezentowany przez określony token.</span><span class="sxs-lookup"><span data-stu-id="8b136-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b136-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b136-104">Syntax</span></span>  
  
```  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b136-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b136-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="8b136-106">[in] MethodDef lub FieldDef metadanych token reprezentujący obiekt kod, aby zwrócić adres RVA dla.</span><span class="sxs-lookup"><span data-stu-id="8b136-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="8b136-107">Jeśli token jest FieldDef, to pole musi być zmienną globalną.</span><span class="sxs-lookup"><span data-stu-id="8b136-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="8b136-108">[out] Wskaźnik do wirtualnego adres względny kod obiektu reprezentowanego przez ten token.</span><span class="sxs-lookup"><span data-stu-id="8b136-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="8b136-109">[out] Wskaźnik do flagi implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="8b136-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="8b136-110">Ta wartość jest maską bitów z [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8b136-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="8b136-111">Wartość `pdwImplFlags` jest prawidłowy tylko wtedy, gdy `tk` tokenu MethodDef.</span><span class="sxs-lookup"><span data-stu-id="8b136-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b136-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b136-112">Requirements</span></span>  
 <span data-ttu-id="8b136-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b136-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b136-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8b136-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b136-115">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8b136-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b136-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b136-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b136-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b136-117">See Also</span></span>  
 [<span data-ttu-id="8b136-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b136-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="8b136-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b136-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
