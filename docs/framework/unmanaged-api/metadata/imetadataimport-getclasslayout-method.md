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
ms.openlocfilehash: 36c0ffef2d984604be4ae19899e8f3f912cee123
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491475"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="b1832-102">IMetaDataImport::GetClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="b1832-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="b1832-103">Pobiera informacje o układzie dla klasy, do której odwołuje się określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="b1832-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1832-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1832-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b1832-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1832-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b1832-106">podczas Token TypeDef dla klasy z układem, który ma zostać zwrócony.</span><span class="sxs-lookup"><span data-stu-id="b1832-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="b1832-107">określoną Jedna z wartości 1, 2, 4, 8 lub 16 reprezentuje rozmiar pakietu klasy.</span><span class="sxs-lookup"><span data-stu-id="b1832-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="b1832-108">określoną Tablica wartości [COR_FIELD_OFFSET](cor-field-offset-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="b1832-108">[out] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b1832-109">podczas Maksymalny rozmiar `rFieldOffset` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b1832-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="b1832-110">określoną Liczba elementów zwróconych w `rFieldOffset` .</span><span class="sxs-lookup"><span data-stu-id="b1832-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="b1832-111">określoną Rozmiar w bajtach klasy reprezentowanej przez `td` .</span><span class="sxs-lookup"><span data-stu-id="b1832-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1832-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1832-112">Requirements</span></span>  
 <span data-ttu-id="b1832-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1832-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1832-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b1832-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1832-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b1832-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1832-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1832-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1832-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1832-117">See also</span></span>

- [<span data-ttu-id="b1832-118">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b1832-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b1832-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b1832-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
