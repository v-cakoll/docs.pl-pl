---
title: IMetaDataImport::GetTypeDefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
ms.openlocfilehash: 6346b1e34e508e5c173bfd0119ac7451d7eef40e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490799"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="0b25c-102">IMetaDataImport::GetTypeDefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b25c-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="0b25c-103">Zwraca informacje o metadanych <xref:System.Type> reprezentowane przez określony token typedef.</span><span class="sxs-lookup"><span data-stu-id="0b25c-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b25c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b25c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b25c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b25c-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="0b25c-106">podczas Token TypeDef, który reprezentuje typ do zwrócenia metadanych.</span><span class="sxs-lookup"><span data-stu-id="0b25c-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="0b25c-107">określoną Bufor zawierający nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="0b25c-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="0b25c-108">podczas Rozmiar w postaci znaków dwubajtowych `szTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="0b25c-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="0b25c-109">określoną Liczba znaków dwubajtowych zwracana w `szTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="0b25c-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="0b25c-110">określoną Wskaźnik do każdej flagi modyfikującej definicję typu.</span><span class="sxs-lookup"><span data-stu-id="0b25c-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="0b25c-111">Ta wartość jest maska bitowa z wyliczenia [CorTypeAttr —](cortypeattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="0b25c-111">This value is a bitmask from the [CorTypeAttr](cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="0b25c-112">określoną Token metadanych TypeDef lub TypeRef reprezentujący typ podstawowy żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="0b25c-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b25c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b25c-113">Requirements</span></span>  
 <span data-ttu-id="0b25c-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b25c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b25c-115">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0b25c-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b25c-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0b25c-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b25c-117">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b25c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b25c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b25c-118">See also</span></span>

- [<span data-ttu-id="0b25c-119">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0b25c-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="0b25c-120">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0b25c-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
