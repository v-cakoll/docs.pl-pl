---
title: IMetaDataTables2::GetMetaDataStreamInfo — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0301506d591a3738ea403393236c2574d48a7cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593969"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="410d5-102">IMetaDataTables2::GetMetaDataStreamInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="410d5-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="410d5-103">Pobiera nazwę, rozmiar i zawartość strumienia metadanych pod określonym indeksem.</span><span class="sxs-lookup"><span data-stu-id="410d5-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="410d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="410d5-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="410d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="410d5-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="410d5-106">[in] Indeks strumienia metadanych żądanej.</span><span class="sxs-lookup"><span data-stu-id="410d5-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="410d5-107">[out] Wskaźnik na nazwę strumienia.</span><span class="sxs-lookup"><span data-stu-id="410d5-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="410d5-108">[out] Wskaźnik do strumienia metadanych.</span><span class="sxs-lookup"><span data-stu-id="410d5-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="410d5-109">[out] Rozmiar w bajtach z `ppv`.</span><span class="sxs-lookup"><span data-stu-id="410d5-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="410d5-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="410d5-110">Requirements</span></span>  
 <span data-ttu-id="410d5-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="410d5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="410d5-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="410d5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="410d5-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="410d5-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="410d5-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="410d5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="410d5-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="410d5-115">See also</span></span>
- [<span data-ttu-id="410d5-116">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="410d5-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="410d5-117">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="410d5-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
