---
title: IMetaDataConverter — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d3377617ddd6b82ad88d22f6ffda04b1d6ae837
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904751"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="a2792-102">IMetaDataConverter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a2792-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="a2792-103">Udostępnia metody, aby zamapować bibliotek typów na ich podpisy metadanych i konwersji z jednego do drugiego.</span><span class="sxs-lookup"><span data-stu-id="a2792-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a2792-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a2792-104">Methods</span></span>  
  
|<span data-ttu-id="a2792-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a2792-105">Method</span></span>|<span data-ttu-id="a2792-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a2792-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a2792-107">GetMetaDataFromTypeInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="a2792-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="a2792-108">Pobiera wskaźnik do [imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) wystąpienia, która reprezentuje podpis metadanych dla biblioteki typów, odwołuje się określony `ITypeInfo` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a2792-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="a2792-109">GetMetaDataFromTypeLib, metoda</span><span class="sxs-lookup"><span data-stu-id="a2792-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="a2792-110">Pobiera wskaźnik do `IMetaDataImport` wystąpienia, która reprezentuje podpis metadanych dla biblioteki typów, reprezentowane przez określony `ITypeLib` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a2792-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="a2792-111">GetTypeLibFromMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="a2792-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="a2792-112">Pobiera wskaźnik do `ITypeLib` wystąpienia, która reprezentuje biblioteki typów, który ma określonej nazwy modułów i Biblioteka.</span><span class="sxs-lookup"><span data-stu-id="a2792-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a2792-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2792-113">Requirements</span></span>  
 <span data-ttu-id="a2792-114">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2792-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2792-115">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a2792-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2792-116">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a2792-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a2792-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2792-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2792-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2792-118">See also</span></span>

- [<span data-ttu-id="a2792-119">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="a2792-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="a2792-120">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2792-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
