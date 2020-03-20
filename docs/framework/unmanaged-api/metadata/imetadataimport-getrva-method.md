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
ms.openlocfilehash: 190bcacc84646cfd9294cf2b6b53b0474f38758f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177219"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="97fd2-102">IMetaDataImport::GetRVA — Metoda</span><span class="sxs-lookup"><span data-stu-id="97fd2-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="97fd2-103">Pobiera względny adres wirtualny (RVA) i flagi implementacji metody lub pola reprezentowane przez określony token.</span><span class="sxs-lookup"><span data-stu-id="97fd2-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97fd2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97fd2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97fd2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97fd2-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="97fd2-106">[w] A MethodDef lub FieldDef token metadanych, który reprezentuje obiekt kodu do zwrócenia RVY dla.</span><span class="sxs-lookup"><span data-stu-id="97fd2-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="97fd2-107">Jeśli token jest FieldDef, pole musi być zmienną globalną.</span><span class="sxs-lookup"><span data-stu-id="97fd2-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="97fd2-108">[na zewnątrz] Wskaźnik do względnego adresu wirtualnego obiektu kodu reprezentowanego przez token.</span><span class="sxs-lookup"><span data-stu-id="97fd2-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="97fd2-109">[na zewnątrz] Wskaźnik do flagi implementacji dla metody.</span><span class="sxs-lookup"><span data-stu-id="97fd2-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="97fd2-110">Ta wartość jest maską bitową z wyliczenia [CorMethodImpl.](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="97fd2-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="97fd2-111">Wartość jest `pdwImplFlags` prawidłowa `tk` tylko wtedy, gdy jest tokenem MethodDef.</span><span class="sxs-lookup"><span data-stu-id="97fd2-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97fd2-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97fd2-112">Requirements</span></span>  
 <span data-ttu-id="97fd2-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97fd2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97fd2-114">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="97fd2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="97fd2-115">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="97fd2-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="97fd2-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97fd2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97fd2-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97fd2-117">See also</span></span>

- [<span data-ttu-id="97fd2-118">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="97fd2-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="97fd2-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="97fd2-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
