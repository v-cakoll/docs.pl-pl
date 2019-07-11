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
ms.openlocfilehash: 208dd5ff2ba9eb450cac5a9807f0cd09852d5cf3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777821"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="16c20-102">IMetaDataConverter::GetTypeLibFromMetaData — Metoda</span><span class="sxs-lookup"><span data-stu-id="16c20-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="16c20-103">Pobiera wskaźnik do `ITypeLib` wystąpienia, która reprezentuje biblioteki typów, która ma określonej nazwy biblioteki i moduł.</span><span class="sxs-lookup"><span data-stu-id="16c20-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16c20-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16c20-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16c20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16c20-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="16c20-106">[in] Nazwa modułu biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="16c20-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="16c20-107">[in] Nazwa biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="16c20-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="16c20-108">[out] Wskaźnik do lokalizacji, która otrzymuje adres `ITypeLib` wystąpienia, która reprezentuje biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="16c20-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16c20-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16c20-109">Requirements</span></span>  
 <span data-ttu-id="16c20-110">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16c20-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16c20-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="16c20-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16c20-112">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16c20-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16c20-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16c20-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c20-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16c20-114">See also</span></span>

- [<span data-ttu-id="16c20-115">IMetaDataConverter, interfejs</span><span class="sxs-lookup"><span data-stu-id="16c20-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
