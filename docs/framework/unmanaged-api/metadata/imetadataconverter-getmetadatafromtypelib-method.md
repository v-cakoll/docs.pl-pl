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
ms.openlocfilehash: 8f8c0c2cb8dea8ad2b9c0040654122ef5942aca0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008394"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="cca23-102">IMetaDataConverter::GetMetaDataFromTypeLib — Metoda</span><span class="sxs-lookup"><span data-stu-id="cca23-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>
<span data-ttu-id="cca23-103">Pobiera wskaźnik interfejsu do wystąpienia [IMetaDataImport](imetadataimport-interface.md) , które reprezentuje sygnaturę metadanych biblioteki typów reprezentowanej przez określone `ITypeLib` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="cca23-103">Gets an interface pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cca23-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cca23-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cca23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cca23-105">Parameters</span></span>  
 `pITL`  
 <span data-ttu-id="cca23-106">podczas Wskaźnik do `ITypeLib` obiektu, który reprezentuje bibliotekę typów.</span><span class="sxs-lookup"><span data-stu-id="cca23-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="cca23-107">określoną Wskaźnik do lokalizacji, która otrzymuje adres `IMetaDataImport` wystąpienia, które reprezentuje sygnaturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="cca23-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cca23-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cca23-108">Requirements</span></span>  
 <span data-ttu-id="cca23-109">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cca23-109">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cca23-110">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cca23-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cca23-111">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cca23-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cca23-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cca23-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cca23-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cca23-113">See also</span></span>

- [<span data-ttu-id="cca23-114">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cca23-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="cca23-115">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cca23-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
