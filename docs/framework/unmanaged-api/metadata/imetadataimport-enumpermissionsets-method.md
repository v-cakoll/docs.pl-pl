---
title: "IMetaDataImport::EnumPermissionSets — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumPermissionSets
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f31d35f21a16983b6ab9c23f1f65c3916b5138d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="e4ef5-102">IMetaDataImport::EnumPermissionSets — Metoda</span><span class="sxs-lookup"><span data-stu-id="e4ef5-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="e4ef5-103">Wylicza uprawnienia dla obiektów w zakresie określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="e4ef5-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ef5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4ef5-104">Syntax</span></span>  
  
```  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,   
   [in]      mdToken       tk,   
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4ef5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4ef5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e4ef5-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="e4ef5-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e4ef5-107">Musi to być wartość NULL dla pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="e4ef5-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="e4ef5-108">[in] Token metadanych, który ogranicza zakres wyszukiwania lub wartość NULL, najszerszych możliwych zakres wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="e4ef5-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="e4ef5-109">[in] Flagi reprezentujący <xref:System.Security.Permissions.SecurityAction> wartości do uwzględnienia w `rPermission`, lub zero, aby zwrócić wszystkie akcje.</span><span class="sxs-lookup"><span data-stu-id="e4ef5-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="e4ef5-110">[out] Tablica używany do przechowywania tokenów uprawnień.</span><span class="sxs-lookup"><span data-stu-id="e4ef5-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e4ef5-111">[in] Maksymalny rozmiar `rPermission` tablicy.</span><span class="sxs-lookup"><span data-stu-id="e4ef5-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e4ef5-112">[out] Liczba tokenów uprawnienia zwracane w `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="e4ef5-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4ef5-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e4ef5-113">Return Value</span></span>  
  
|<span data-ttu-id="e4ef5-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4ef5-114">HRESULT</span></span>|<span data-ttu-id="e4ef5-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e4ef5-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e4ef5-116">`EnumPermissionSets`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e4ef5-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e4ef5-117">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e4ef5-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="e4ef5-118">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="e4ef5-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4ef5-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4ef5-119">Requirements</span></span>  
 <span data-ttu-id="e4ef5-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4ef5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4ef5-121">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e4ef5-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e4ef5-122">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4ef5-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e4ef5-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4ef5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ef5-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4ef5-124">See Also</span></span>  
 [<span data-ttu-id="e4ef5-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4ef5-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="e4ef5-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4ef5-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
