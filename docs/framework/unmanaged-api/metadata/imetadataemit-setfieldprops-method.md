---
title: IMetaDataEmit::SetFieldProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: efc627619d9abf9cfa6010e1c0ca709989b9cad3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445460"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="bb418-102">IMetaDataEmit::SetFieldProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="bb418-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="bb418-103">Ustawia lub aktualizuje wartość domyślną dla pola, do którego odwołuje się określony token pola.</span><span class="sxs-lookup"><span data-stu-id="bb418-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb418-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb418-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb418-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb418-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="bb418-106">podczas Token dla pola docelowego.</span><span class="sxs-lookup"><span data-stu-id="bb418-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="bb418-107">podczas Atrybuty pola.</span><span class="sxs-lookup"><span data-stu-id="bb418-107">[in] Field attributes.</span></span> <span data-ttu-id="bb418-108">To jest maska bitów wartości `CorFieldAttr`.</span><span class="sxs-lookup"><span data-stu-id="bb418-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="bb418-109">podczas `ELEMENT_TYPE_` *\** wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="bb418-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="bb418-110">To jest wartość `CorElementType`.</span><span class="sxs-lookup"><span data-stu-id="bb418-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="bb418-111">Jeśli stała nie jest zdefiniowana, ustaw tę wartość na `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="bb418-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="bb418-112">podczas Stała wartość pola.</span><span class="sxs-lookup"><span data-stu-id="bb418-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="bb418-113">podczas Rozmiar w znakach Unicode `pValue`.</span><span class="sxs-lookup"><span data-stu-id="bb418-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb418-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb418-114">Requirements</span></span>  
 <span data-ttu-id="bb418-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb418-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb418-116">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bb418-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb418-117">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bb418-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb418-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb418-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb418-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb418-119">See also</span></span>

- [<span data-ttu-id="bb418-120">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb418-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bb418-121">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb418-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
