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
ms.openlocfilehash: f9f3e3f196f74a7dea3c722925f1d03968688882
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009005"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="447c8-102">IMetaDataConverter::GetMetaDataFromTypeInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="447c8-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="447c8-103">Pobiera wskaźnik do wystąpienia [IMetaDataImport](imetadataimport-interface.md) , które reprezentuje sygnaturę metadanych biblioteki typów, do której odwołuje się określone `ITypeInfo` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="447c8-103">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="447c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="447c8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="447c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="447c8-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="447c8-106">podczas Wskaźnik do `ITypeInfo` obiektu, który odwołuje się do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="447c8-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="447c8-107">określoną Wskaźnik do lokalizacji, która otrzymuje adres `IMetaDataImport` wystąpienia, które reprezentuje sygnaturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="447c8-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="447c8-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="447c8-108">Requirements</span></span>  
 <span data-ttu-id="447c8-109">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="447c8-109">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="447c8-110">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="447c8-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="447c8-111">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="447c8-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="447c8-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="447c8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="447c8-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="447c8-113">See also</span></span>

- [<span data-ttu-id="447c8-114">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="447c8-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="447c8-115">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="447c8-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
