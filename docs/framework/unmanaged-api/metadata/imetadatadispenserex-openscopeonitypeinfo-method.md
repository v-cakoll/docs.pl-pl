---
title: "IMetaDataDispenserEx::OpenScopeOnITypeInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e13211a43c42d66fccd88473c8f881b9edd071d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="7c56f-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c56f-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="7c56f-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="7c56f-103">This method is not implemented.</span></span> <span data-ttu-id="7c56f-104">Wywołuje się, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="7c56f-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c56f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c56f-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c56f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c56f-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="7c56f-107">[in] Wskaźnik do [ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680) interfejs, który zawiera informacje o typie, na którym ma zostać otwarty zakresu.</span><span class="sxs-lookup"><span data-stu-id="7c56f-107">[in] Pointer to an [ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="7c56f-108">[in] Flagi trybu otwartego.</span><span class="sxs-lookup"><span data-stu-id="7c56f-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="7c56f-109">[in] Żądany interfejs.</span><span class="sxs-lookup"><span data-stu-id="7c56f-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="7c56f-110">[out] Wskaźnik na wskaźnik do interfejsu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="7c56f-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c56f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c56f-111">Requirements</span></span>  
 <span data-ttu-id="7c56f-112">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c56f-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c56f-113">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7c56f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c56f-114">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c56f-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7c56f-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c56f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c56f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c56f-116">See Also</span></span>  
 [<span data-ttu-id="7c56f-117">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c56f-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="7c56f-118">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c56f-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
