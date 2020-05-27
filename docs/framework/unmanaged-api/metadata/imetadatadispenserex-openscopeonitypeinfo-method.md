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
ms.openlocfilehash: 91ef9eaa855ed841bc75bfaeead462f045eb1d8b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007458"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="4f7dd-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="4f7dd-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="4f7dd-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="4f7dd-103">This method is not implemented.</span></span> <span data-ttu-id="4f7dd-104">Jeśli zostanie wywołana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="4f7dd-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f7dd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f7dd-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f7dd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f7dd-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="4f7dd-107">podczas Wskaźnik do interfejsu [Metoda ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) , który zawiera informacje o typie, na którym należy otworzyć zakres.</span><span class="sxs-lookup"><span data-stu-id="4f7dd-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="4f7dd-108">podczas Flagi trybu otwartego.</span><span class="sxs-lookup"><span data-stu-id="4f7dd-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="4f7dd-109">podczas Żądany interfejs.</span><span class="sxs-lookup"><span data-stu-id="4f7dd-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="4f7dd-110">określoną Wskaźnik na wskaźnik do zwracanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4f7dd-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f7dd-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f7dd-111">Requirements</span></span>  
 <span data-ttu-id="4f7dd-112">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f7dd-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f7dd-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4f7dd-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f7dd-114">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4f7dd-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f7dd-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f7dd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f7dd-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f7dd-116">See also</span></span>

- [<span data-ttu-id="4f7dd-117">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f7dd-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="4f7dd-118">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4f7dd-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
