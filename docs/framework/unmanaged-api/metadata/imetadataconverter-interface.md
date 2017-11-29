---
title: "IMetaDataConverter — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataConverter
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataConverter
helpviewer_keywords: IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f551a774a860f595cc90a7cca9eee2c726ef50ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="eb2f9-102">IMetaDataConverter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="eb2f9-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="eb2f9-103">Udostępnia metody do mapowania biblioteki typów na ich podpisów metadanych i przekonwertować z jednego do drugiego.</span><span class="sxs-lookup"><span data-stu-id="eb2f9-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb2f9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="eb2f9-104">Methods</span></span>  
  
|<span data-ttu-id="eb2f9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="eb2f9-105">Method</span></span>|<span data-ttu-id="eb2f9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="eb2f9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb2f9-107">GetMetaDataFromTypeInfo — metoda</span><span class="sxs-lookup"><span data-stu-id="eb2f9-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="eb2f9-108">Pobiera wskaźnik do [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) wystąpienie, które reprezentuje podpis metadanych dla biblioteki typów odwołuje się określony `ITypeInfo` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="eb2f9-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="eb2f9-109">GetMetaDataFromTypeLib — metoda</span><span class="sxs-lookup"><span data-stu-id="eb2f9-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="eb2f9-110">Pobiera wskaźnik do `IMetaDataImport` wystąpienie, które reprezentuje podpis metadanych dla biblioteki typów reprezentowany przez określony `ITypeLib` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="eb2f9-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="eb2f9-111">GetTypeLibFromMetaData — metoda</span><span class="sxs-lookup"><span data-stu-id="eb2f9-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="eb2f9-112">Pobiera wskaźnik do `ITypeLib` wystąpienia, który reprezentuje bibliotekę typu, która zawiera nazwy modułu i bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="eb2f9-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eb2f9-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb2f9-113">Requirements</span></span>  
 <span data-ttu-id="eb2f9-114">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb2f9-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb2f9-115">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eb2f9-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eb2f9-116">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eb2f9-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eb2f9-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb2f9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2f9-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb2f9-118">See Also</span></span>  
 [<span data-ttu-id="eb2f9-119">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="eb2f9-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="eb2f9-120">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="eb2f9-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
