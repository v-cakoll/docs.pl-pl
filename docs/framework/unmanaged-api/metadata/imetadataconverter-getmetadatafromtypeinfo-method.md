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
ms.openlocfilehash: a4bbe3bf259c6d06964f105113ecb30da4e7d8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="e5d1f-102">IMetaDataConverter::GetMetaDataFromTypeInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5d1f-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="e5d1f-103">Pobiera wskaźnik do [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) wystąpienie, które reprezentuje podpis metadanych biblioteki typów odwołuje się określony `ITypeInfo` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e5d1f-103">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5d1f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5d1f-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5d1f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5d1f-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="e5d1f-106">[in] Wskaźnik do `ITypeInfo` obiekt, który odwołuje się do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="e5d1f-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="e5d1f-107">[out] Wskaźnik do lokalizacji, która odbiera adres `IMetaDataImport` wystąpienie, które reprezentuje podpis metadanych.</span><span class="sxs-lookup"><span data-stu-id="e5d1f-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5d1f-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5d1f-108">Requirements</span></span>  
 <span data-ttu-id="e5d1f-109">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5d1f-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5d1f-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e5d1f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5d1f-111">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5d1f-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5d1f-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5d1f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5d1f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5d1f-113">See Also</span></span>  
 [<span data-ttu-id="e5d1f-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5d1f-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="e5d1f-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5d1f-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
