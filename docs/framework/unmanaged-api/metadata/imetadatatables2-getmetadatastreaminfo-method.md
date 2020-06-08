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
ms.openlocfilehash: 7d39d089c348b7320651ed21ea14ba07d7877fd4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501098"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="f77dc-102">IMetaDataTables2::GetMetaDataStreamInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="f77dc-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="f77dc-103">Pobiera nazwę, rozmiar i zawartość strumienia metadanych o określonym indeksie.</span><span class="sxs-lookup"><span data-stu-id="f77dc-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f77dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f77dc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f77dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f77dc-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="f77dc-106">podczas Indeks żądanego strumienia metadanych.</span><span class="sxs-lookup"><span data-stu-id="f77dc-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="f77dc-107">określoną Wskaźnik do nazwy strumienia.</span><span class="sxs-lookup"><span data-stu-id="f77dc-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="f77dc-108">określoną Wskaźnik do strumienia metadanych.</span><span class="sxs-lookup"><span data-stu-id="f77dc-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="f77dc-109">określoną Rozmiar, w bajtach, z `ppv` .</span><span class="sxs-lookup"><span data-stu-id="f77dc-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f77dc-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f77dc-110">Requirements</span></span>  
 <span data-ttu-id="f77dc-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f77dc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f77dc-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f77dc-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f77dc-113">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f77dc-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f77dc-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f77dc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f77dc-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f77dc-115">See also</span></span>

- [<span data-ttu-id="f77dc-116">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f77dc-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="f77dc-117">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="f77dc-117">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
