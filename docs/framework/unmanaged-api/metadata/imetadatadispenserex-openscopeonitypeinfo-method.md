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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ba8cb8cdf89fc07238a9d5f788c76b0cb7f7153
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681342"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="dbdce-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="dbdce-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="dbdce-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="dbdce-103">This method is not implemented.</span></span> <span data-ttu-id="dbdce-104">Jeżeli jest wywoływana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="dbdce-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbdce-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dbdce-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbdce-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbdce-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="dbdce-107">[in] Wskaźnik do [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interfejs, który zawiera informacje o typie, na którym ma zostać otwarty zakresu.</span><span class="sxs-lookup"><span data-stu-id="dbdce-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="dbdce-108">[in] Otwórz tryb flagi.</span><span class="sxs-lookup"><span data-stu-id="dbdce-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="dbdce-109">[in] Żądanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dbdce-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="dbdce-110">[out] Wskaźnik do wskaźnika do interfejsu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="dbdce-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbdce-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dbdce-111">Requirements</span></span>  
 <span data-ttu-id="dbdce-112">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbdce-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbdce-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="dbdce-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dbdce-114">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbdce-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dbdce-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbdce-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbdce-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dbdce-116">See also</span></span>
- [<span data-ttu-id="dbdce-117">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="dbdce-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="dbdce-118">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="dbdce-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
