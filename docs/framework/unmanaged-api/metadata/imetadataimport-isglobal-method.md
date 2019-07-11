---
title: IMetaDataImport::IsGlobal — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsGlobal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 13f8a50f3fcbe9d6e7602ca3bbeb36587ecff32c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778801"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="c7e7a-102">IMetaDataImport::IsGlobal — Metoda</span><span class="sxs-lookup"><span data-stu-id="c7e7a-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="c7e7a-103">Pobiera wartość wskazującą, czy pola, metody lub typu reprezentowanego przez token metadanych w określonym zakresie globalnym.</span><span class="sxs-lookup"><span data-stu-id="c7e7a-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7e7a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7e7a-104">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7e7a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7e7a-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="c7e7a-106">[in] Token metadanych, który reprezentuje typ, polem ani metodą.</span><span class="sxs-lookup"><span data-stu-id="c7e7a-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="c7e7a-107">[out] 1, jeśli obiekt ma zakres globalny; w przeciwnym razie 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="c7e7a-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7e7a-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7e7a-108">Requirements</span></span>  
 <span data-ttu-id="c7e7a-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7e7a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7e7a-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c7e7a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7e7a-111">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7e7a-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7e7a-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7e7a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7e7a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7e7a-113">See also</span></span>

- [<span data-ttu-id="c7e7a-114">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="c7e7a-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c7e7a-115">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c7e7a-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
