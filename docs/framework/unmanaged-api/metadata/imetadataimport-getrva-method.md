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
ms.openlocfilehash: 96c013cd3e45e4ede0cbc9f42bf511a2eb3fc12d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223592"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="1149a-102">IMetaDataImport::GetRVA — Metoda</span><span class="sxs-lookup"><span data-stu-id="1149a-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="1149a-103">Pobiera względnych adresów wirtualnych (RVA) i flagi implementacji metody lub pola, reprezentowane przez określony token.</span><span class="sxs-lookup"><span data-stu-id="1149a-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1149a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1149a-104">Syntax</span></span>  
  
```  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1149a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1149a-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1149a-106">[in] MethodDef lub FieldDef metadanych token, który reprezentuje obiekt kodu, aby zwrócić adres RVA dla.</span><span class="sxs-lookup"><span data-stu-id="1149a-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="1149a-107">Jeśli token jest FieldDef, pole musi być zmienną globalną.</span><span class="sxs-lookup"><span data-stu-id="1149a-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="1149a-108">[out] Wskaźnik względne wirtualnym adresem kod obiektu reprezentowanego przez ten token.</span><span class="sxs-lookup"><span data-stu-id="1149a-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="1149a-109">[out] Wskaźnik flagi implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="1149a-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="1149a-110">Ta wartość jest z [cormethodimpl —](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1149a-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="1149a-111">Wartość `pdwImplFlags` jest prawidłowa tylko wtedy, gdy `tk` jest tokenem MethodDef.</span><span class="sxs-lookup"><span data-stu-id="1149a-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1149a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1149a-112">Requirements</span></span>  
 <span data-ttu-id="1149a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1149a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1149a-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1149a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1149a-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1149a-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="1149a-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1149a-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1149a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1149a-117">See also</span></span>

- [<span data-ttu-id="1149a-118">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1149a-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1149a-119">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1149a-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
