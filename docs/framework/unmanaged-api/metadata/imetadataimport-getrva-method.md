---
title: IMetaDataImport::GetRVA — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1232e8c574f263f709a9b66c7b1b3d06cca5e4da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="38d0b-102">IMetaDataImport::GetRVA — Metoda</span><span class="sxs-lookup"><span data-stu-id="38d0b-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="38d0b-103">Pobiera adres względny wirtualnych (RVA) i flagi implementacji metody lub pola reprezentowany przez określony token.</span><span class="sxs-lookup"><span data-stu-id="38d0b-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38d0b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38d0b-104">Syntax</span></span>  
  
```  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38d0b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38d0b-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="38d0b-106">[in] MethodDef lub FieldDef metadanych token reprezentujący obiekt kod, aby zwrócić adres RVA dla.</span><span class="sxs-lookup"><span data-stu-id="38d0b-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="38d0b-107">Jeśli token jest FieldDef, to pole musi być zmienną globalną.</span><span class="sxs-lookup"><span data-stu-id="38d0b-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="38d0b-108">[out] Wskaźnik do wirtualnego adres względny kod obiektu reprezentowanego przez ten token.</span><span class="sxs-lookup"><span data-stu-id="38d0b-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="38d0b-109">[out] Wskaźnik do flagi implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="38d0b-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="38d0b-110">Ta wartość jest maską bitów z [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="38d0b-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="38d0b-111">Wartość `pdwImplFlags` jest prawidłowy tylko wtedy, gdy `tk` tokenu MethodDef.</span><span class="sxs-lookup"><span data-stu-id="38d0b-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38d0b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38d0b-112">Requirements</span></span>  
 <span data-ttu-id="38d0b-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38d0b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38d0b-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="38d0b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38d0b-115">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="38d0b-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38d0b-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38d0b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d0b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38d0b-117">See Also</span></span>  
 [<span data-ttu-id="38d0b-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="38d0b-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="38d0b-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="38d0b-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
