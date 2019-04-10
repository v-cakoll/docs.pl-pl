---
title: IMetaDataDispenser — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dda284fc86f0a82472c59d6bab08fd4a87364723
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225979"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="98ab2-102">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="98ab2-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="98ab2-103">Dostarcza metody do tworzenia nowego zakresu metadanych lub Otwórz istniejący.</span><span class="sxs-lookup"><span data-stu-id="98ab2-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98ab2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="98ab2-104">Methods</span></span>  
  
|<span data-ttu-id="98ab2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="98ab2-105">Method</span></span>|<span data-ttu-id="98ab2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="98ab2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98ab2-107">DefineScope, metoda</span><span class="sxs-lookup"><span data-stu-id="98ab2-107">DefineScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|<span data-ttu-id="98ab2-108">Tworzy nowy obszar w pamięci, w którym można tworzyć nowe metadane.</span><span class="sxs-lookup"><span data-stu-id="98ab2-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="98ab2-109">OpenScope, metoda</span><span class="sxs-lookup"><span data-stu-id="98ab2-109">OpenScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|<span data-ttu-id="98ab2-110">Otwiera istniejący plik na dysku i mapuje jego metadane do pamięci.</span><span class="sxs-lookup"><span data-stu-id="98ab2-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="98ab2-111">OpenScopeOnMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="98ab2-111">OpenScopeOnMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="98ab2-112">Zostanie otwarty obszar pamięci, który zawiera istniejące metadane.</span><span class="sxs-lookup"><span data-stu-id="98ab2-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="98ab2-113">Oznacza to ta metoda powoduje otwarcie określonego obszaru pamięci, w którym istniejących danych jest traktowana jako metadanych.</span><span class="sxs-lookup"><span data-stu-id="98ab2-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98ab2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="98ab2-114">Requirements</span></span>  
 <span data-ttu-id="98ab2-115">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98ab2-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98ab2-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="98ab2-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98ab2-117">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="98ab2-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="98ab2-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="98ab2-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="98ab2-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98ab2-119">See also</span></span>

- [<span data-ttu-id="98ab2-120">IMetaDataDispenserEx — Interfejs</span><span class="sxs-lookup"><span data-stu-id="98ab2-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="98ab2-121">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="98ab2-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
