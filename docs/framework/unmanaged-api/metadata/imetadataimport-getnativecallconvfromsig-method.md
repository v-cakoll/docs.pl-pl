---
title: IMetaDataImport::GetNativeCallConvFromSig — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNativeCallConvFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1002aa9e01fedaacf80622952bbba82caa7081c1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498017"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="78100-102">IMetaDataImport::GetNativeCallConvFromSig — Metoda</span><span class="sxs-lookup"><span data-stu-id="78100-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="78100-103">Pobiera natywnych konwencja wywołania dla metody, która jest reprezentowana przez wskaźnik określonej sygnaturze.</span><span class="sxs-lookup"><span data-stu-id="78100-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78100-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78100-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78100-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78100-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="78100-106">[in] Wskaźnik do metody do zwrócenia konwencja wywołania dla podpisu metadanych.</span><span class="sxs-lookup"><span data-stu-id="78100-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="78100-107">[in] Rozmiar w bajtach `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="78100-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="78100-108">[out] Wskaźnik do natywną Konwencję wywoływania.</span><span class="sxs-lookup"><span data-stu-id="78100-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78100-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78100-109">Requirements</span></span>  
 <span data-ttu-id="78100-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78100-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78100-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="78100-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78100-112">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78100-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78100-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78100-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78100-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78100-114">See also</span></span>
- <xref:System.Runtime.InteropServices.CallingConvention>
- [<span data-ttu-id="78100-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="78100-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="78100-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="78100-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
