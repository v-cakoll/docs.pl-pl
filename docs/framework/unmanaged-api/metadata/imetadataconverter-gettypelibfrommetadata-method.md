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
ms.openlocfilehash: 9da4e34fa948db2fc73cbde813bac9b3430605ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436251"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="6552f-102">IMetaDataConverter::GetTypeLibFromMetaData — Metoda</span><span class="sxs-lookup"><span data-stu-id="6552f-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="6552f-103">Pobiera wskaźnik do wystąpienia `ITypeLib`, które reprezentuje bibliotekę typów, która ma określoną nazwę biblioteki i modułu.</span><span class="sxs-lookup"><span data-stu-id="6552f-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6552f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6552f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6552f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6552f-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="6552f-106">podczas Nazwa modułu biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="6552f-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="6552f-107">podczas Nazwa biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="6552f-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="6552f-108">określoną Wskaźnik do lokalizacji, która otrzymuje adres `ITypeLib` wystąpienia, które reprezentuje bibliotekę typów.</span><span class="sxs-lookup"><span data-stu-id="6552f-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6552f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6552f-109">Requirements</span></span>  
 <span data-ttu-id="6552f-110">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6552f-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6552f-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6552f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6552f-112">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6552f-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6552f-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6552f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6552f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6552f-114">See also</span></span>

- [<span data-ttu-id="6552f-115">IMetaDataConverter, interfejs</span><span class="sxs-lookup"><span data-stu-id="6552f-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
