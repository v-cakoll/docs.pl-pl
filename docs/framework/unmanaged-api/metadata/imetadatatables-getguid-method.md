---
title: IMetaDataTables::GetGuid — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f589225dde1ba2aabc4ca32542339a771c3287d4
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43859520"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="95634-102">IMetaDataTables::GetGuid — Metoda</span><span class="sxs-lookup"><span data-stu-id="95634-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="95634-103">Pobiera identyfikator GUID z wiersz pod określonym indeksem.</span><span class="sxs-lookup"><span data-stu-id="95634-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95634-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="95634-104">Syntax</span></span>  
  
```  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95634-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95634-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="95634-106">[in] Indeks wiersza, z którego można pobrać identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="95634-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="95634-107">[out] Wskaźnik do wskaźnika, zgodnie z identyfikatorem GUID.</span><span class="sxs-lookup"><span data-stu-id="95634-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95634-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95634-108">Remarks</span></span>  
 <span data-ttu-id="95634-109">Firma Microsoft nie zaleca się użycie tej metody, ponieważ zwraca spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="95634-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="95634-110">Informacje w tabeli z identyfikatorem GUID zobacz dokumentację Common Language Infrastructure (CLI), szczególnie "partycja II: metadane definicji i semantyka".</span><span class="sxs-lookup"><span data-stu-id="95634-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="95634-111">Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) w witrynie Ecma International w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="95634-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95634-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95634-112">Requirements</span></span>  
 <span data-ttu-id="95634-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95634-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95634-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="95634-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95634-115">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95634-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95634-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95634-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95634-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95634-117">See Also</span></span>  
 [<span data-ttu-id="95634-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="95634-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="95634-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="95634-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
