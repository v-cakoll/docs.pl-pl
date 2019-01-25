---
title: IMetaDataTables::GetNumTables — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNumTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNumTables
helpviewer_keywords:
- GetNumTables method [.NET Framework metadata]
- IMetaDataTables::GetNumTables method [.NET Framework metadata]
ms.assetid: 8196f2a3-bbf2-45d3-a6cd-74502c356644
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2dc7d8c339e5f77bad44960092198035e13735b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621295"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="daad3-102">IMetaDataTables::GetNumTables — Metoda</span><span class="sxs-lookup"><span data-stu-id="daad3-102">IMetaDataTables::GetNumTables Method</span></span>
<span data-ttu-id="daad3-103">Pobiera liczbę tabel w zakresie bieżącego `IMetaDataTables` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="daad3-103">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daad3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="daad3-104">Syntax</span></span>  
  
```  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="daad3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="daad3-105">Parameters</span></span>  
 `pcTables`  
 <span data-ttu-id="daad3-106">[out] Wskaźnik do liczby tabel w bieżącym zakresie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="daad3-106">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daad3-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="daad3-107">Requirements</span></span>  
 <span data-ttu-id="daad3-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daad3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daad3-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="daad3-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="daad3-110">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="daad3-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="daad3-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daad3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daad3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="daad3-112">See also</span></span>
- [<span data-ttu-id="daad3-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="daad3-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="daad3-114">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="daad3-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
