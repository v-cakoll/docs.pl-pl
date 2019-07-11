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
ms.openlocfilehash: d305aa59c1b9e9e1225b30f12e36fc689d584db1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778885"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="b6877-102">IMetaDataImport::GetRVA — Metoda</span><span class="sxs-lookup"><span data-stu-id="b6877-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="b6877-103">Pobiera względnych adresów wirtualnych (RVA) i flagi implementacji metody lub pola, reprezentowane przez określony token.</span><span class="sxs-lookup"><span data-stu-id="b6877-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6877-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6877-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6877-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6877-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b6877-106">[in] MethodDef lub FieldDef metadanych token, który reprezentuje obiekt kodu, aby zwrócić adres RVA dla.</span><span class="sxs-lookup"><span data-stu-id="b6877-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="b6877-107">Jeśli token jest FieldDef, pole musi być zmienną globalną.</span><span class="sxs-lookup"><span data-stu-id="b6877-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="b6877-108">[out] Wskaźnik względne wirtualnym adresem kod obiektu reprezentowanego przez ten token.</span><span class="sxs-lookup"><span data-stu-id="b6877-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="b6877-109">[out] Wskaźnik flagi implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="b6877-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="b6877-110">Ta wartość jest z [cormethodimpl —](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b6877-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="b6877-111">Wartość `pdwImplFlags` jest prawidłowa tylko wtedy, gdy `tk` jest tokenem MethodDef.</span><span class="sxs-lookup"><span data-stu-id="b6877-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6877-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6877-112">Requirements</span></span>  
 <span data-ttu-id="b6877-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6877-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6877-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b6877-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6877-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6877-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6877-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6877-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6877-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6877-117">See also</span></span>

- [<span data-ttu-id="b6877-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6877-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b6877-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6877-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
