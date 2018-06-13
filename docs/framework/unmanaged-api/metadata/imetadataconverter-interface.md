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
ms.openlocfilehash: 29709a4297d53cc5e40daf732ac89751ead95152
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449044"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="97cc8-102">IMetaDataConverter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="97cc8-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="97cc8-103">Udostępnia metody do mapowania biblioteki typów na ich podpisów metadanych i przekonwertować z jednego do drugiego.</span><span class="sxs-lookup"><span data-stu-id="97cc8-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97cc8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="97cc8-104">Methods</span></span>  
  
|<span data-ttu-id="97cc8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="97cc8-105">Method</span></span>|<span data-ttu-id="97cc8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="97cc8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97cc8-107">GetMetaDataFromTypeInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="97cc8-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="97cc8-108">Pobiera wskaźnik do [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) wystąpienie, które reprezentuje podpis metadanych dla biblioteki typów odwołuje się określony `ITypeInfo` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="97cc8-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="97cc8-109">GetMetaDataFromTypeLib, metoda</span><span class="sxs-lookup"><span data-stu-id="97cc8-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="97cc8-110">Pobiera wskaźnik do `IMetaDataImport` wystąpienie, które reprezentuje podpis metadanych dla biblioteki typów reprezentowany przez określony `ITypeLib` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="97cc8-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="97cc8-111">GetTypeLibFromMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="97cc8-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="97cc8-112">Pobiera wskaźnik do `ITypeLib` wystąpienia, który reprezentuje bibliotekę typu, która zawiera nazwy modułu i bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="97cc8-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97cc8-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97cc8-113">Requirements</span></span>  
 <span data-ttu-id="97cc8-114">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97cc8-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97cc8-115">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="97cc8-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="97cc8-116">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="97cc8-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="97cc8-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97cc8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97cc8-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97cc8-118">See Also</span></span>  
 [<span data-ttu-id="97cc8-119">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="97cc8-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="97cc8-120">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="97cc8-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
