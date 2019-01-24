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
ms.openlocfilehash: 91cb42a5bf1115de82b5fe28693cb77b66915c9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600561"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="cc027-102">IMetaDataImport::GetInterfaceImplProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="cc027-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="cc027-103">Pobiera wskaźnik do tokenów metadanych dla <xref:System.Type> implementującej określonej metody, a dla interfejsu, który deklaruje tej metody.</span><span class="sxs-lookup"><span data-stu-id="cc027-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc027-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc027-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc027-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc027-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="cc027-106">[in] Token metadanych reprezentujący metodę do zwrócenia klas i interfejsu tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="cc027-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="cc027-107">[out] Klasa, która implementuje metody reprezentująca token metadanych.</span><span class="sxs-lookup"><span data-stu-id="cc027-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="cc027-108">[out] Interfejs, który definiuje zaimplementowano metody reprezentująca token metadanych.</span><span class="sxs-lookup"><span data-stu-id="cc027-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc027-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc027-109">Requirements</span></span>  
 <span data-ttu-id="cc027-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc027-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc027-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="cc027-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc027-112">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cc027-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cc027-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc027-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc027-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc027-114">See also</span></span>
- [<span data-ttu-id="cc027-115">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="cc027-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="cc027-116">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cc027-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
