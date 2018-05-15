---
title: IMetaDataConverter::GetTypeLibFromMetaData — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9351738e979b49ec23b51a2fa554fc219e163541
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="b6d8b-102">IMetaDataConverter::GetTypeLibFromMetaData — Metoda</span><span class="sxs-lookup"><span data-stu-id="b6d8b-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="b6d8b-103">Pobiera wskaźnik do `ITypeLib` wystąpienia, który reprezentuje bibliotekę typu, która zawiera nazwy modułu i bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="b6d8b-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6d8b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6d8b-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6d8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6d8b-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="b6d8b-106">[in] Nazwa modułu biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="b6d8b-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="b6d8b-107">[in] Nazwa biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="b6d8b-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="b6d8b-108">[out] Wskaźnik do lokalizacji, która odbiera adres `ITypeLib` wystąpienia, który reprezentuje bibliotekę typów.</span><span class="sxs-lookup"><span data-stu-id="b6d8b-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6d8b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6d8b-109">Requirements</span></span>  
 <span data-ttu-id="b6d8b-110">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6d8b-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6d8b-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b6d8b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6d8b-112">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6d8b-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6d8b-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6d8b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6d8b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6d8b-114">See Also</span></span>  
 [<span data-ttu-id="b6d8b-115">IMetaDataConverter, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6d8b-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
