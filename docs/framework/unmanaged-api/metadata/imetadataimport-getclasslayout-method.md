---
title: IMetaDataImport::GetClassLayout — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
ms.openlocfilehash: 8360a74e9e18e5b68ecc9edd7be2e3a711cb61c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437780"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="d1fc8-102">IMetaDataImport::GetClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1fc8-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="d1fc8-103">Pobiera informacje o układzie dla klasy, do której odwołuje się określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="d1fc8-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1fc8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1fc8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout  (   
   [in]  mdTypeDef          td,   
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1fc8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1fc8-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d1fc8-106">podczas Token TypeDef dla klasy z układem, który ma zostać zwrócony.</span><span class="sxs-lookup"><span data-stu-id="d1fc8-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="d1fc8-107">określoną Jedna z wartości 1, 2, 4, 8 lub 16 reprezentuje rozmiar pakietu klasy.</span><span class="sxs-lookup"><span data-stu-id="d1fc8-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="d1fc8-108">określoną Tablica wartości [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="d1fc8-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d1fc8-109">podczas Maksymalny rozmiar tablicy `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="d1fc8-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="d1fc8-110">określoną Liczba elementów zwróconych w `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="d1fc8-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="d1fc8-111">określoną Rozmiar w bajtach klasy reprezentowanej przez `td`.</span><span class="sxs-lookup"><span data-stu-id="d1fc8-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1fc8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1fc8-112">Requirements</span></span>  
 <span data-ttu-id="d1fc8-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1fc8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1fc8-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d1fc8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1fc8-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d1fc8-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1fc8-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1fc8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1fc8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1fc8-117">See also</span></span>

- [<span data-ttu-id="d1fc8-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1fc8-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d1fc8-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1fc8-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
