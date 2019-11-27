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
ms.openlocfilehash: 9d0f443b5b7d2d358534e888c3fc84ad3f554119
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450046"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="addf1-102">IMetaDataImport::EnumPermissionSets — Metoda</span><span class="sxs-lookup"><span data-stu-id="addf1-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="addf1-103">Wylicza uprawnienia dla obiektów w określonym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="addf1-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="addf1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="addf1-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="addf1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="addf1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="addf1-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="addf1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="addf1-107">Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="addf1-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="addf1-108">podczas Token metadanych, który ogranicza zakres wyszukiwania lub wartość NULL, aby przeszukać możliwie najszerszego zakresu.</span><span class="sxs-lookup"><span data-stu-id="addf1-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="addf1-109">podczas Flagi reprezentujące <xref:System.Security.Permissions.SecurityAction> wartości do uwzględnienia w `rPermission`, lub zero, aby zwrócić wszystkie akcje.</span><span class="sxs-lookup"><span data-stu-id="addf1-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="addf1-110">określoną Tablica służąca do przechowywania tokenów uprawnień.</span><span class="sxs-lookup"><span data-stu-id="addf1-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="addf1-111">podczas Maksymalny rozmiar tablicy `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="addf1-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="addf1-112">określoną Liczba tokenów uprawnień zwróconych w `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="addf1-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="addf1-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="addf1-113">Return Value</span></span>  
  
|<span data-ttu-id="addf1-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="addf1-114">HRESULT</span></span>|<span data-ttu-id="addf1-115">Opis</span><span class="sxs-lookup"><span data-stu-id="addf1-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="addf1-116">`EnumPermissionSets` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="addf1-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="addf1-117">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="addf1-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="addf1-118">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="addf1-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="addf1-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="addf1-119">Requirements</span></span>  
 <span data-ttu-id="addf1-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="addf1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="addf1-121">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="addf1-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="addf1-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="addf1-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="addf1-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="addf1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="addf1-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="addf1-124">See also</span></span>

- [<span data-ttu-id="addf1-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="addf1-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="addf1-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="addf1-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
