---
title: "IMetaDataTables::GetUserString — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetUserString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3d7ffc2c7334a6b5873581bf9f079b2b7c8053e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="abdd2-102">IMetaDataTables::GetUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="abdd2-102">IMetaDataTables::GetUserString Method</span></span>
<span data-ttu-id="abdd2-103">Pobiera ciąg ustalony pod określonym indeksem w kolumnie ciągu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="abdd2-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abdd2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="abdd2-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
    [in]  ULONG       ixUserString,  
    [out] ULONG       *pcbData,  
    [out] const void  **ppData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abdd2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abdd2-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="abdd2-106">[in] Wartość indeksu, z którego będzie można pobrać ciągu ustalony.</span><span class="sxs-lookup"><span data-stu-id="abdd2-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="abdd2-107">[out] P; skaźnika rozmiar `ppData`.</span><span class="sxs-lookup"><span data-stu-id="abdd2-107">[out] A p;ointer to the size of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="abdd2-108">[out] Wskaźnik na wskaźnik do zwracany ciąg.</span><span class="sxs-lookup"><span data-stu-id="abdd2-108">[out] A pointer to a pointer to the returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abdd2-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abdd2-109">Requirements</span></span>  
 <span data-ttu-id="abdd2-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abdd2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abdd2-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="abdd2-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="abdd2-112">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="abdd2-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="abdd2-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abdd2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abdd2-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abdd2-114">See Also</span></span>  
 [<span data-ttu-id="abdd2-115">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="abdd2-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="abdd2-116">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="abdd2-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
