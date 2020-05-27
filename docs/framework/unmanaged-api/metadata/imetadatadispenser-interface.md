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
ms.openlocfilehash: 2bdfe65dbf923ec61d91a259b5257d892fef53da
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007341"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="ae1a9-102">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ae1a9-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="ae1a9-103">Zawiera metody tworzenia nowego zakresu metadanych lub otwierania istniejącego.</span><span class="sxs-lookup"><span data-stu-id="ae1a9-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae1a9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ae1a9-104">Methods</span></span>  
  
|<span data-ttu-id="ae1a9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ae1a9-105">Method</span></span>|<span data-ttu-id="ae1a9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ae1a9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae1a9-107">DefineScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="ae1a9-107">DefineScope Method</span></span>](imetadatadispenser-definescope-method.md)|<span data-ttu-id="ae1a9-108">Tworzy nowy obszar w pamięci, w którym można tworzyć nowe metadane.</span><span class="sxs-lookup"><span data-stu-id="ae1a9-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="ae1a9-109">OpenScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="ae1a9-109">OpenScope Method</span></span>](imetadatadispenser-openscope-method.md)|<span data-ttu-id="ae1a9-110">Otwiera istniejący plik na dysku i mapuje jego metadane do pamięci.</span><span class="sxs-lookup"><span data-stu-id="ae1a9-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="ae1a9-111">OpenScopeOnMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="ae1a9-111">OpenScopeOnMemory Method</span></span>](imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="ae1a9-112">Otwiera obszar pamięci, który zawiera istniejące metadane.</span><span class="sxs-lookup"><span data-stu-id="ae1a9-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="ae1a9-113">Oznacza to, że ta metoda otwiera określony obszar pamięci, w której istniejące dane są traktowane jako metadane.</span><span class="sxs-lookup"><span data-stu-id="ae1a9-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae1a9-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae1a9-114">Requirements</span></span>  
 <span data-ttu-id="ae1a9-115">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae1a9-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae1a9-116">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ae1a9-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae1a9-117">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ae1a9-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ae1a9-118">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae1a9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae1a9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae1a9-119">See also</span></span>

- [<span data-ttu-id="ae1a9-120">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="ae1a9-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="ae1a9-121">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="ae1a9-121">Metadata Interfaces</span></span>](metadata-interfaces.md)
