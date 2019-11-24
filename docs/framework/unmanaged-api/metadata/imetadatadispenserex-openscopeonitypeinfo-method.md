---
title: IMetaDataDispenserEx::OpenScopeOnITypeInfo — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type:
- apiref
ms.openlocfilehash: 8deefe026e32a56d853e173e6a8fa3be942ccd9c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431130"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="b71b5-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="b71b5-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="b71b5-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="b71b5-103">This method is not implemented.</span></span> <span data-ttu-id="b71b5-104">If called, it returns E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="b71b5-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b71b5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b71b5-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b71b5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b71b5-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="b71b5-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span><span class="sxs-lookup"><span data-stu-id="b71b5-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="b71b5-108">[in] The open mode flags.</span><span class="sxs-lookup"><span data-stu-id="b71b5-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="b71b5-109">[in] The desired interface.</span><span class="sxs-lookup"><span data-stu-id="b71b5-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="b71b5-110">[out] Pointer to a pointer to the returned interface.</span><span class="sxs-lookup"><span data-stu-id="b71b5-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b71b5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b71b5-111">Requirements</span></span>  
 <span data-ttu-id="b71b5-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b71b5-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b71b5-113">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b71b5-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b71b5-114">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b71b5-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b71b5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b71b5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b71b5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b71b5-116">See also</span></span>

- [<span data-ttu-id="b71b5-117">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="b71b5-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="b71b5-118">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="b71b5-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
