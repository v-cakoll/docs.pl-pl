---
title: "IMetaDataImport::GetInterfaceImplProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetInterfaceImplProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: afc73536f332bd24fadee33d6321a106ccd175f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="fb76d-102">IMetaDataImport::GetInterfaceImplProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="fb76d-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="fb76d-103">Pobiera wskaźnik do tokenów metadanych dla <xref:System.Type> implementującej określonej metody i dla interfejsu, który deklaruje tej metody.</span><span class="sxs-lookup"><span data-stu-id="fb76d-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb76d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb76d-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb76d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb76d-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="fb76d-106">[in] Token metadanych reprezentujący metodę, aby zwrócić klas i interfejsu tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="fb76d-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="fb76d-107">[out] Token metadanych reprezentujący klasę, która implementuje metody.</span><span class="sxs-lookup"><span data-stu-id="fb76d-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="fb76d-108">[out] Token metadanych reprezentujący interfejs, który definiuje metody implementowane.</span><span class="sxs-lookup"><span data-stu-id="fb76d-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb76d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb76d-109">Requirements</span></span>  
 <span data-ttu-id="fb76d-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb76d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb76d-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fb76d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb76d-112">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fb76d-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fb76d-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb76d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb76d-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb76d-114">See Also</span></span>  
 [<span data-ttu-id="fb76d-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb76d-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="fb76d-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb76d-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
