---
title: IMetaDataError::OnError — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataError.OnError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 011183d2f60e4abb967e5381d30a4c28e619e34c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479782"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="f90ed-102">IMetaDataError::OnError — Metoda</span><span class="sxs-lookup"><span data-stu-id="f90ed-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="f90ed-103">Zapewnia powiadomienie błędów występujących podczas scalania metadanych.</span><span class="sxs-lookup"><span data-stu-id="f90ed-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f90ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f90ed-104">Syntax</span></span>  
  
```  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f90ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f90ed-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="f90ed-106">[in] Wartość błędu HRESULT zwracane do wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="f90ed-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="f90ed-107">[in] Token metadanych obiektu kod, który został scalane, gdy wystąpił błąd.</span><span class="sxs-lookup"><span data-stu-id="f90ed-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f90ed-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f90ed-108">Requirements</span></span>  
 <span data-ttu-id="f90ed-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f90ed-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f90ed-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f90ed-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f90ed-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f90ed-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f90ed-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f90ed-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f90ed-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f90ed-113">See also</span></span>
- [<span data-ttu-id="f90ed-114">IMetaDataError, interfejs</span><span class="sxs-lookup"><span data-stu-id="f90ed-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
