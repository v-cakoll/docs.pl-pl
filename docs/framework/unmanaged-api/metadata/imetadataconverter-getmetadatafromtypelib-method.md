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
ms.openlocfilehash: 6391e819d53c3ed8f0d596b15c4a2bb268f72fd5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436286"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="f93f2-102">IMetaDataConverter::GetMetaDataFromTypeLib — Metoda</span><span class="sxs-lookup"><span data-stu-id="f93f2-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="f93f2-103">Pobiera wskaźnik interfejsu do wystąpienia [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) , które reprezentuje sygnaturę metadanych biblioteki typów reprezentowanej przez określone wystąpienie `ITypeLib`.</span><span class="sxs-lookup"><span data-stu-id="f93f2-103">Gets an interface pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f93f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f93f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,   
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f93f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f93f2-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="f93f2-106">podczas Wskaźnik do obiektu `ITypeLib`, który reprezentuje bibliotekę typów.</span><span class="sxs-lookup"><span data-stu-id="f93f2-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="f93f2-107">określoną Wskaźnik do lokalizacji, która otrzymuje adres `IMetaDataImport` wystąpienia, które reprezentuje sygnaturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="f93f2-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f93f2-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f93f2-108">Requirements</span></span>  
 <span data-ttu-id="f93f2-109">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f93f2-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f93f2-110">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f93f2-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f93f2-111">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f93f2-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f93f2-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f93f2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f93f2-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f93f2-113">See also</span></span>

- [<span data-ttu-id="f93f2-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="f93f2-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f93f2-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="f93f2-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
