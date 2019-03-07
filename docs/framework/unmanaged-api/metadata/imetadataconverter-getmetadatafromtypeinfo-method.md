---
title: IMetaDataConverter::GetMetaDataFromTypeInfo — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeInfo
helpviewer_keywords:
- GetMetaDataFromTypeInfo method [.NET Framework metadata]
- IMetaDataConverter::GetMetaDataFromTypeInfo method [.NET Framework metadata]
ms.assetid: d44484bb-23a3-49c3-9e46-69d0d9ab4f0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8619bf0e62752513b1ae03fa01d22be40f65e58e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468861"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="7ee54-102">IMetaDataConverter::GetMetaDataFromTypeInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="7ee54-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="7ee54-103">Pobiera wskaźnik do [imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) wystąpienia, która reprezentuje podpis metadanych biblioteki typów, które odwołuje się określony `ITypeInfo` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7ee54-103">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ee54-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ee54-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ee54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ee54-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="7ee54-106">[in] Wskaźnik do `ITypeInfo` obiekt, który odwołuje się do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="7ee54-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="7ee54-107">[out] Wskaźnik do lokalizacji, która otrzymuje adres `IMetaDataImport` wystąpienia, która reprezentuje podpis metadanych.</span><span class="sxs-lookup"><span data-stu-id="7ee54-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ee54-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ee54-108">Requirements</span></span>  
 <span data-ttu-id="7ee54-109">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ee54-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ee54-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7ee54-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7ee54-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ee54-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ee54-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ee54-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee54-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ee54-113">See also</span></span>
- [<span data-ttu-id="7ee54-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ee54-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7ee54-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ee54-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
