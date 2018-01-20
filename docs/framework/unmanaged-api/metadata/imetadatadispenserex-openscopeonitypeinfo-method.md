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
ms.openlocfilehash: 45c65d0194ed44122a87dcd000359187fc020d0e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="d0708-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="d0708-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="d0708-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="d0708-103">This method is not implemented.</span></span> <span data-ttu-id="d0708-104">Wywołuje się, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="d0708-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0708-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0708-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0708-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0708-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="d0708-107">[in] Wskaźnik do [ITypeInfo](http://msdn.microsoft.com/library/f3356463-3373-4279-bae1-953378aa2680) interfejs, który zawiera informacje o typie, na którym ma zostać otwarty zakresu.</span><span class="sxs-lookup"><span data-stu-id="d0708-107">[in] Pointer to an [ITypeInfo](http://msdn.microsoft.com/library/f3356463-3373-4279-bae1-953378aa2680) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="d0708-108">[in] Flagi trybu otwartego.</span><span class="sxs-lookup"><span data-stu-id="d0708-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="d0708-109">[in] Żądany interfejs.</span><span class="sxs-lookup"><span data-stu-id="d0708-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="d0708-110">[out] Wskaźnik na wskaźnik do interfejsu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="d0708-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0708-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0708-111">Requirements</span></span>  
 <span data-ttu-id="d0708-112">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0708-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0708-113">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d0708-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d0708-114">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0708-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d0708-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0708-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0708-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0708-116">See Also</span></span>  
 [<span data-ttu-id="d0708-117">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="d0708-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="d0708-118">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="d0708-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
