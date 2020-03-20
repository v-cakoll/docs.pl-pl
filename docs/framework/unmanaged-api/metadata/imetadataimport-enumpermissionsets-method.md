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
ms.openlocfilehash: e628cf5dab8006b0df0ab6c60dc995cd0c6bb29d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175450"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="b0cd2-102">IMetaDataImport::EnumPermissionSets — Metoda</span><span class="sxs-lookup"><span data-stu-id="b0cd2-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="b0cd2-103">Wylicza uprawnienia dla obiektów w określonym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="b0cd2-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0cd2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0cd2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,
   [in]      mdToken       tk,
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0cd2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0cd2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b0cd2-106">[w, na zewnątrz] Wskaźnik do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="b0cd2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b0cd2-107">Musi to być null dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="b0cd2-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="b0cd2-108">[w] Token metadanych, który ogranicza zakres wyszukiwania lub NULL do wyszukiwania w najszerszym możliwym zakresie.</span><span class="sxs-lookup"><span data-stu-id="b0cd2-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="b0cd2-109">[w] Flagi reprezentujące <xref:System.Security.Permissions.SecurityAction> wartości, `rPermission`które mają być uwzględnione w , lub zero, aby zwrócić wszystkie akcje.</span><span class="sxs-lookup"><span data-stu-id="b0cd2-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="b0cd2-110">[na zewnątrz] Tablica używana do przechowywania tokenów uprawnień.</span><span class="sxs-lookup"><span data-stu-id="b0cd2-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b0cd2-111">[w] Maksymalny rozmiar `rPermission` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b0cd2-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b0cd2-112">[na zewnątrz] Liczba tokenów uprawnień `rPermission`zwróconych w pliku .</span><span class="sxs-lookup"><span data-stu-id="b0cd2-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0cd2-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b0cd2-113">Return Value</span></span>  
  
|<span data-ttu-id="b0cd2-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b0cd2-114">HRESULT</span></span>|<span data-ttu-id="b0cd2-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b0cd2-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b0cd2-116">`EnumPermissionSets`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b0cd2-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b0cd2-117">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b0cd2-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="b0cd2-118">W takim `pcTokens` przypadku wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="b0cd2-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0cd2-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0cd2-119">Requirements</span></span>  
 <span data-ttu-id="b0cd2-120">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0cd2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0cd2-121">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="b0cd2-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b0cd2-122">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0cd2-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b0cd2-123">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0cd2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0cd2-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0cd2-124">See also</span></span>

- [<span data-ttu-id="b0cd2-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b0cd2-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b0cd2-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0cd2-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
