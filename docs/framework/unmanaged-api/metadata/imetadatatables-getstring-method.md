---
title: "IMetaDataTables::GetString — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 687380d3a09a80db216aafbf1ee84c76e31bbf36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="ba708-102">IMetaDataTables::GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="ba708-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="ba708-103">Pobiera ciąg pod określonym indeksem z kolumną tabeli w bieżącym zakresie odwołania.</span><span class="sxs-lookup"><span data-stu-id="ba708-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba708-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba708-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba708-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba708-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="ba708-106">[in] Indeks, w którym należy uruchomić wyszukać następnej wartości.</span><span class="sxs-lookup"><span data-stu-id="ba708-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="ba708-107">[out] Wskaźnik na wskaźnik do wartości zwracany ciąg.</span><span class="sxs-lookup"><span data-stu-id="ba708-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba708-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ba708-108">Requirements</span></span>  
 <span data-ttu-id="ba708-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba708-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba708-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ba708-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ba708-111">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ba708-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ba708-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba708-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba708-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba708-113">See Also</span></span>  
 [<span data-ttu-id="ba708-114">IMetaDataTables — interfejs</span><span class="sxs-lookup"><span data-stu-id="ba708-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="ba708-115">IMetaDataTables2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="ba708-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
