---
title: "IMetaDataImport::EnumInterfaceImpls — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumInterfaceImpls
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1d9f2883c32daafd8938bd1c80c035a3527cc6a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="98484-102">IMetaDataImport::EnumInterfaceImpls — Metoda</span><span class="sxs-lookup"><span data-stu-id="98484-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="98484-103">Wylicza tokeny MethodDef reprezentujący implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="98484-103">Enumerates MethodDef tokens representing interface implementations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98484-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="98484-104">Syntax</span></span>  
  
```  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98484-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98484-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="98484-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="98484-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="98484-107">[in] Token TypeDef tokeny MethodDef, którego reprezentujący implementacji interfejsu są mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="98484-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="98484-108">[out] Tablica używany do przechowywania tokenów MethodDef.</span><span class="sxs-lookup"><span data-stu-id="98484-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="98484-109">[in] Maksymalny rozmiar `rImpls` tablicy.</span><span class="sxs-lookup"><span data-stu-id="98484-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="98484-110">[out] Rzeczywista liczba tokenów zwracanych w `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="98484-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98484-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="98484-111">Return Value</span></span>  
  
|<span data-ttu-id="98484-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98484-112">HRESULT</span></span>|<span data-ttu-id="98484-113">Opis</span><span class="sxs-lookup"><span data-stu-id="98484-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="98484-114">`EnumInterfaceImpls`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="98484-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="98484-115">Nie ma żadnych tokenów MethodDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="98484-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="98484-116">W takim przypadku `pcImpls` jest ustawiony na zero.</span><span class="sxs-lookup"><span data-stu-id="98484-116">In that case, `pcImpls` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98484-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="98484-117">Requirements</span></span>  
 <span data-ttu-id="98484-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98484-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98484-119">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="98484-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98484-120">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="98484-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="98484-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98484-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98484-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98484-122">See Also</span></span>  
 [<span data-ttu-id="98484-123">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="98484-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="98484-124">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="98484-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
