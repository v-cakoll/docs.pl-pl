---
title: IMetaDataEmit2::GetDeltaSaveSize — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad6e565db634477e4f0382afdec12361ce7111a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446512"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="1a3dc-102">IMetaDataEmit2::GetDeltaSaveSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="1a3dc-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="1a3dc-103">Pobiera wartość wskazującą, wszelkie zmiany rozmiaru metadanych, będącą wynikiem bieżącej sesji edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="1a3dc-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a3dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a3dc-104">Syntax</span></span>  
  
```  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1a3dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a3dc-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="1a3dc-106">[in] Jeden z [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) wartości i wskazujący poziom dokładności potrzebne.</span><span class="sxs-lookup"><span data-stu-id="1a3dc-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="1a3dc-107">Ten parametr jest ignorowany dla programu .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="1a3dc-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="1a3dc-108">[out] Zmiana rozmiaru metadanych.</span><span class="sxs-lookup"><span data-stu-id="1a3dc-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a3dc-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a3dc-109">Requirements</span></span>  
 <span data-ttu-id="1a3dc-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a3dc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a3dc-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1a3dc-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a3dc-112">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1a3dc-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a3dc-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a3dc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a3dc-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a3dc-114">See Also</span></span>  
 [<span data-ttu-id="1a3dc-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1a3dc-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="1a3dc-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="1a3dc-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
