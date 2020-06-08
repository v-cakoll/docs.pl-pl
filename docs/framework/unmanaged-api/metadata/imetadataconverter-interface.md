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
ms.openlocfilehash: 7a2a5080872f49a84e36c53ac337d91738c15e45
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501342"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="73a05-102">IMetaDataConverter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="73a05-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="73a05-103">Zapewnia metody mapowania bibliotek typów na ich sygnatury metadanych oraz do konwersji między nimi.</span><span class="sxs-lookup"><span data-stu-id="73a05-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73a05-104">Metody</span><span class="sxs-lookup"><span data-stu-id="73a05-104">Methods</span></span>  
  
|<span data-ttu-id="73a05-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="73a05-105">Method</span></span>|<span data-ttu-id="73a05-106">Opis</span><span class="sxs-lookup"><span data-stu-id="73a05-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73a05-107">GetMetaDataFromTypeInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="73a05-107">GetMetaDataFromTypeInfo Method</span></span>](imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="73a05-108">Pobiera wskaźnik do wystąpienia [IMetaDataImport](imetadataimport-interface.md) , które reprezentuje sygnaturę metadanych dla biblioteki typów, do której odwołuje się określone `ITypeInfo` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="73a05-108">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="73a05-109">GetMetaDataFromTypeLib — Metoda</span><span class="sxs-lookup"><span data-stu-id="73a05-109">GetMetaDataFromTypeLib Method</span></span>](imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="73a05-110">Pobiera wskaźnik do `IMetaDataImport` wystąpienia, które reprezentuje sygnaturę metadanych dla biblioteki typów reprezentowanej przez określone `ITypeLib` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="73a05-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="73a05-111">GetTypeLibFromMetaData — Metoda</span><span class="sxs-lookup"><span data-stu-id="73a05-111">GetTypeLibFromMetaData Method</span></span>](imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="73a05-112">Pobiera wskaźnik do `ITypeLib` wystąpienia, które reprezentuje bibliotekę typów, która ma określone nazwy modułów i bibliotek.</span><span class="sxs-lookup"><span data-stu-id="73a05-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73a05-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73a05-113">Requirements</span></span>  
 <span data-ttu-id="73a05-114">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73a05-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73a05-115">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="73a05-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73a05-116">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="73a05-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73a05-117">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73a05-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a05-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73a05-118">See also</span></span>

- [<span data-ttu-id="73a05-119">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="73a05-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="73a05-120">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="73a05-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
