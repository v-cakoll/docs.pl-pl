---
title: IMetaDataConverter::GetMetaDataFromTypeLib — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeLib
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type:
- apiref
ms.openlocfilehash: 09a1605deda5b51be604c3b8f0c69fa5adcf9dc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175957"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="196c8-102">IMetaDataConverter::GetMetaDataFromTypeLib — Metoda</span><span class="sxs-lookup"><span data-stu-id="196c8-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="196c8-103">Pobiera wskaźnik interfejsu do wystąpienia [IMetaDataImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) który reprezentuje podpis metadanych `ITypeLib` biblioteki typów reprezentowanych przez określone wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="196c8-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="196c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="196c8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="196c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="196c8-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="196c8-106">[w] Wskaźnik do `ITypeLib` obiektu reprezentującego bibliotekę typów.</span><span class="sxs-lookup"><span data-stu-id="196c8-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="196c8-107">[na zewnątrz] Wskaźnik do lokalizacji, która odbiera `IMetaDataImport` adres wystąpienia, który reprezentuje podpis metadanych.</span><span class="sxs-lookup"><span data-stu-id="196c8-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="196c8-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="196c8-108">Requirements</span></span>  
 <span data-ttu-id="196c8-109">**Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="196c8-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="196c8-110">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="196c8-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="196c8-111">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="196c8-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="196c8-112">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="196c8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="196c8-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="196c8-113">See also</span></span>

- [<span data-ttu-id="196c8-114">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="196c8-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="196c8-115">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="196c8-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
