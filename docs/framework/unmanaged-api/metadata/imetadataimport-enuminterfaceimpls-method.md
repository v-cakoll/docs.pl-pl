---
title: IMetaDataImport::EnumInterfaceImpls — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c94960478e6b2eb4e7b8f1e9592b0831af3ec686
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603771"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="6b34d-102">IMetaDataImport::EnumInterfaceImpls — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b34d-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="6b34d-103">Wylicza tokenów MethodDef reprezentujący implementacje interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6b34d-103">Enumerates MethodDef tokens representing interface implementations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b34d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b34d-104">Syntax</span></span>  
  
```  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b34d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b34d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6b34d-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="6b34d-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="6b34d-107">[in] Token TypeDef, w których tokeny MethodDef reprezentujący implementacje interfejsu są do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="6b34d-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="6b34d-108">[out] Tablica do przechowywania tokenów MethodDef.</span><span class="sxs-lookup"><span data-stu-id="6b34d-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6b34d-109">[in] Maksymalny rozmiar `rImpls` tablicy.</span><span class="sxs-lookup"><span data-stu-id="6b34d-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="6b34d-110">[out] Rzeczywista liczba zwracane w tokenach `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="6b34d-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b34d-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6b34d-111">Return Value</span></span>  
  
|<span data-ttu-id="6b34d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b34d-112">HRESULT</span></span>|<span data-ttu-id="6b34d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6b34d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6b34d-114">`EnumInterfaceImpls` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="6b34d-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6b34d-115">Nie ma żadnych tokeny MethodDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="6b34d-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="6b34d-116">W takim przypadku `pcImpls` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="6b34d-116">In that case, `pcImpls` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b34d-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b34d-117">Requirements</span></span>  
 <span data-ttu-id="6b34d-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b34d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b34d-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6b34d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b34d-120">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6b34d-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b34d-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b34d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b34d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b34d-122">See also</span></span>
- [<span data-ttu-id="6b34d-123">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b34d-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6b34d-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b34d-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
