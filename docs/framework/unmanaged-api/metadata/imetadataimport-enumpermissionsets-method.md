---
title: IMetaDataImport::EnumPermissionSets — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 990910b8b30e9794550d71cf9eaf8cd53639f696
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492247"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="58493-102">IMetaDataImport::EnumPermissionSets — Metoda</span><span class="sxs-lookup"><span data-stu-id="58493-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="58493-103">Wylicza uprawnienia dla obiektów w zakresie określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="58493-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58493-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58493-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="58493-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="58493-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="58493-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="58493-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="58493-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="58493-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="58493-108">[in] Token metadanych, który ogranicza zakres wyszukiwania lub wartość NULL, wyszukiwanie najszerszego zakresu możliwe.</span><span class="sxs-lookup"><span data-stu-id="58493-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="58493-109">[in] Flagi reprezentujący <xref:System.Security.Permissions.SecurityAction> wartości, które mają zostać objęte `rPermission`, lub wartość zero, aby zwrócić wszystkie akcje.</span><span class="sxs-lookup"><span data-stu-id="58493-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="58493-110">[out] Tablica do przechowywania tokenów uprawnień.</span><span class="sxs-lookup"><span data-stu-id="58493-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="58493-111">[in] Maksymalny rozmiar `rPermission` tablicy.</span><span class="sxs-lookup"><span data-stu-id="58493-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="58493-112">[out] Liczba tokenów uprawnienie zwracane w `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="58493-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58493-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="58493-113">Return Value</span></span>  
  
|<span data-ttu-id="58493-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="58493-114">HRESULT</span></span>|<span data-ttu-id="58493-115">Opis</span><span class="sxs-lookup"><span data-stu-id="58493-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="58493-116">`EnumPermissionSets` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="58493-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="58493-117">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="58493-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="58493-118">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="58493-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="58493-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="58493-119">Requirements</span></span>  
 <span data-ttu-id="58493-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58493-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58493-121">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="58493-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="58493-122">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="58493-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="58493-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58493-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58493-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58493-124">See also</span></span>
- [<span data-ttu-id="58493-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="58493-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="58493-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="58493-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
