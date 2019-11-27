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
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="6fcd4-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="6fcd4-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="6fcd4-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="6fcd4-103">This method is not implemented.</span></span> <span data-ttu-id="6fcd4-104">Jeśli zostanie wywołana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="6fcd4-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fcd4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fcd4-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fcd4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fcd4-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="6fcd4-107">podczas Wskaźnik do interfejsu [Metoda ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) , który zawiera informacje o typie, na którym należy otworzyć zakres.</span><span class="sxs-lookup"><span data-stu-id="6fcd4-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="6fcd4-108">podczas Flagi trybu otwartego.</span><span class="sxs-lookup"><span data-stu-id="6fcd4-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="6fcd4-109">podczas Żądany interfejs.</span><span class="sxs-lookup"><span data-stu-id="6fcd4-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="6fcd4-110">określoną Wskaźnik na wskaźnik do zwracanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6fcd4-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fcd4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6fcd4-111">Requirements</span></span>  
 <span data-ttu-id="6fcd4-112">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fcd4-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fcd4-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6fcd4-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6fcd4-114">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6fcd4-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6fcd4-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fcd4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fcd4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fcd4-116">See also</span></span>

- [<span data-ttu-id="6fcd4-117">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="6fcd4-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="6fcd4-118">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="6fcd4-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
