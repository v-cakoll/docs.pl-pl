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
ms.openlocfilehash: b9ffd9ab9ddb95945744ecf210d0ae1d9d9812ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779815"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="2156c-102">IMetaDataTables::GetNumTables — Metoda</span><span class="sxs-lookup"><span data-stu-id="2156c-102">IMetaDataTables::GetNumTables Method</span></span>
<span data-ttu-id="2156c-103">Pobiera liczbę tabel w zakresie bieżącego `IMetaDataTables` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2156c-103">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2156c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2156c-104">Syntax</span></span>  
  
```  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2156c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2156c-105">Parameters</span></span>  
 `pcTables`  
 <span data-ttu-id="2156c-106">[out] Wskaźnik do liczby tabel w bieżącym zakresie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2156c-106">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2156c-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2156c-107">Requirements</span></span>  
 <span data-ttu-id="2156c-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2156c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2156c-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2156c-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2156c-110">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2156c-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2156c-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2156c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2156c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2156c-112">See also</span></span>

- [<span data-ttu-id="2156c-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="2156c-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="2156c-114">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2156c-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
