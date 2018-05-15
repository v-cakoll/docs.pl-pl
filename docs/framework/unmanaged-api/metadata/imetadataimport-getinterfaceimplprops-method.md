---
title: IMetaDataImport::GetInterfaceImplProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9fca044b5dce260a1eed55b01531e7ae21a16ebd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="57dde-102">IMetaDataImport::GetInterfaceImplProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="57dde-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="57dde-103">Pobiera wskaźnik do tokenów metadanych dla <xref:System.Type> implementującej określonej metody i dla interfejsu, który deklaruje tej metody.</span><span class="sxs-lookup"><span data-stu-id="57dde-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57dde-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="57dde-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57dde-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57dde-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="57dde-106">[in] Token metadanych reprezentujący metodę, aby zwrócić klas i interfejsu tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="57dde-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="57dde-107">[out] Token metadanych reprezentujący klasę, która implementuje metody.</span><span class="sxs-lookup"><span data-stu-id="57dde-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="57dde-108">[out] Token metadanych reprezentujący interfejs, który definiuje metody implementowane.</span><span class="sxs-lookup"><span data-stu-id="57dde-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57dde-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57dde-109">Requirements</span></span>  
 <span data-ttu-id="57dde-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57dde-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57dde-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="57dde-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57dde-112">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57dde-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57dde-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57dde-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57dde-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57dde-114">See Also</span></span>  
 [<span data-ttu-id="57dde-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="57dde-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="57dde-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="57dde-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
