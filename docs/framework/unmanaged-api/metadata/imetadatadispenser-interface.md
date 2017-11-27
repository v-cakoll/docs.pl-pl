---
title: "IMetaDataDispenser — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser
helpviewer_keywords: IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5a0464f2fb7b81d98fcbb4b04bc465cf57b1b0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="a7afc-102">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a7afc-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="a7afc-103">Udostępnia metody, aby utworzyć nowy zakres metadanych lub Otwórz istniejący.</span><span class="sxs-lookup"><span data-stu-id="a7afc-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7afc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a7afc-104">Methods</span></span>  
  
|<span data-ttu-id="a7afc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a7afc-105">Method</span></span>|<span data-ttu-id="a7afc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a7afc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7afc-107">DefineScope — metoda</span><span class="sxs-lookup"><span data-stu-id="a7afc-107">DefineScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|<span data-ttu-id="a7afc-108">Tworzy nowy obszar w pamięci, w którym można utworzyć nowe metadane.</span><span class="sxs-lookup"><span data-stu-id="a7afc-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="a7afc-109">OpenScope — metoda</span><span class="sxs-lookup"><span data-stu-id="a7afc-109">OpenScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|<span data-ttu-id="a7afc-110">Otwiera istniejący plik na dysku, a następnie mapuje metadanych do pamięci.</span><span class="sxs-lookup"><span data-stu-id="a7afc-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="a7afc-111">OpenScopeOnMemory — metoda</span><span class="sxs-lookup"><span data-stu-id="a7afc-111">OpenScopeOnMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="a7afc-112">Otwiera to obszar pamięci, która zawiera istniejące metadane.</span><span class="sxs-lookup"><span data-stu-id="a7afc-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="a7afc-113">Oznacza to ta metoda powoduje otwarcie określonego obszaru pamięci, w którym istniejących danych jest traktowany jak metadanych.</span><span class="sxs-lookup"><span data-stu-id="a7afc-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7afc-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7afc-114">Requirements</span></span>  
 <span data-ttu-id="a7afc-115">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7afc-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7afc-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a7afc-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7afc-117">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7afc-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7afc-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7afc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7afc-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7afc-119">See Also</span></span>  
 [<span data-ttu-id="a7afc-120">IMetaDataDispenserEx — interfejs</span><span class="sxs-lookup"><span data-stu-id="a7afc-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="a7afc-121">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="a7afc-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
