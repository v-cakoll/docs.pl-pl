---
title: IMetaDataTables::GetUserString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52f3f382e022600e946a4c8f531f4eea5f3d8a34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693746"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="eb6eb-102">IMetaDataTables::GetUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="eb6eb-102">IMetaDataTables::GetUserString Method</span></span>
<span data-ttu-id="eb6eb-103">Pobiera ciąg ustaloną dla podanego indeksu w kolumnie ciągu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb6eb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb6eb-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
    [in]  ULONG       ixUserString,  
    [out] ULONG       *pcbData,  
    [out] const void  **ppData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb6eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb6eb-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="eb6eb-106">[in] Wartość indeksu, z którego będą pobierane ciągu ustalonych.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="eb6eb-107">[out] P; skaźnika rozmiar `ppData`.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-107">[out] A p;ointer to the size of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="eb6eb-108">[out] Wskaźnik do wskaźnika do zwracanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-108">[out] A pointer to a pointer to the returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb6eb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb6eb-109">Requirements</span></span>  
 <span data-ttu-id="eb6eb-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb6eb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb6eb-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="eb6eb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eb6eb-112">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eb6eb-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eb6eb-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb6eb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb6eb-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb6eb-114">See also</span></span>
- [<span data-ttu-id="eb6eb-115">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb6eb-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="eb6eb-116">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb6eb-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
