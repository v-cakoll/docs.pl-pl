---
title: IMetaDataEmit::DefineUserString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f24dd3864be1bda454ac5e863f3fa2caf736bda9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050119"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="f6fb4-102">IMetaDataEmit::DefineUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="f6fb4-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="f6fb4-103">Pobiera metadane token dla określonego ciągu literału.</span><span class="sxs-lookup"><span data-stu-id="f6fb4-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6fb4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6fb4-104">Syntax</span></span>  
  
```  
HRESULT DefineUserString (   
    [in]  LPCWSTR     szString,   
    [in]  ULONG       cchString,   
    [out] mdString    *pstk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6fb4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6fb4-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="f6fb4-106">[in] Ciąg użytkowników do przechowywania.</span><span class="sxs-lookup"><span data-stu-id="f6fb4-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="f6fb4-107">[in] Liczba znaków dwubajtowych w `szString`.</span><span class="sxs-lookup"><span data-stu-id="f6fb4-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="f6fb4-108">[out] Token ciągu przypisany.</span><span class="sxs-lookup"><span data-stu-id="f6fb4-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6fb4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6fb4-109">Requirements</span></span>  
 <span data-ttu-id="f6fb4-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6fb4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6fb4-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f6fb4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6fb4-112">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6fb4-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6fb4-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6fb4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6fb4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6fb4-114">See also</span></span>

- [<span data-ttu-id="f6fb4-115">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="f6fb4-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f6fb4-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f6fb4-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
