---
title: IMetaDataImport::GetRVA — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: a3a5cadc1b5a9df7967aae271ff10296843121dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436959"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="865ab-102">IMetaDataImport::GetRVA — Metoda</span><span class="sxs-lookup"><span data-stu-id="865ab-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="865ab-103">Pobiera względny adres wirtualny (RVA) oraz flagi implementacji metody lub pola reprezentowanego przez określony token.</span><span class="sxs-lookup"><span data-stu-id="865ab-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="865ab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="865ab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="865ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="865ab-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="865ab-106">podczas Token metadanych MethodDef lub FieldDef reprezentujący obiekt kodu do zwrócenia adresu RVA.</span><span class="sxs-lookup"><span data-stu-id="865ab-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="865ab-107">Jeśli token jest FieldDef, pole musi być zmienną globalną.</span><span class="sxs-lookup"><span data-stu-id="865ab-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="865ab-108">określoną Wskaźnik do względnego adresu wirtualnego obiektu kodu reprezentowanego przez token.</span><span class="sxs-lookup"><span data-stu-id="865ab-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="865ab-109">określoną Wskaźnik do flag implementacji dla metody.</span><span class="sxs-lookup"><span data-stu-id="865ab-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="865ab-110">Ta wartość jest maska bitowa z wyliczenia [CorMethodImpl —](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="865ab-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="865ab-111">Wartość `pdwImplFlags` jest prawidłowa tylko wtedy, gdy `tk` jest tokenem MethodDef.</span><span class="sxs-lookup"><span data-stu-id="865ab-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="865ab-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="865ab-112">Requirements</span></span>  
 <span data-ttu-id="865ab-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="865ab-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="865ab-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="865ab-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="865ab-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="865ab-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="865ab-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="865ab-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="865ab-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="865ab-117">See also</span></span>

- [<span data-ttu-id="865ab-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="865ab-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="865ab-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="865ab-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
