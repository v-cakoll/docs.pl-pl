---
title: IMetaDataImport::GetFieldProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 2bd05b49c3d51ac13865997910c99cc0cd5ca2d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491250"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="74c50-102">IMetaDataImport::GetFieldProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="74c50-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="74c50-103">Pobiera metadane skojarzone z polem, do którego odwołuje się określony token FieldDef.</span><span class="sxs-lookup"><span data-stu-id="74c50-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74c50-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="74c50-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74c50-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74c50-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="74c50-106">podczas Token FieldDef reprezentujący pole, dla którego mają zostać pobrane powiązane metadane.</span><span class="sxs-lookup"><span data-stu-id="74c50-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="74c50-107">określoną Wskaźnik do tokenu TypeDef, który reprezentuje typ klasy, do której należy pole.</span><span class="sxs-lookup"><span data-stu-id="74c50-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="74c50-108">określoną Nazwa pola.</span><span class="sxs-lookup"><span data-stu-id="74c50-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="74c50-109">podczas Rozmiar w postaci znaków dwubajtowych buforu dla *szField*.</span><span class="sxs-lookup"><span data-stu-id="74c50-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="74c50-110">określoną Rzeczywisty rozmiar zwróconego buforu.</span><span class="sxs-lookup"><span data-stu-id="74c50-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="74c50-111">określoną Flagi skojarzone z metadanymi pola.</span><span class="sxs-lookup"><span data-stu-id="74c50-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="74c50-112">podczas Wskaźnik do wartości metadanych Binary opisującej pole.</span><span class="sxs-lookup"><span data-stu-id="74c50-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="74c50-113">określoną Rozmiar w bajtach `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="74c50-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="74c50-114">określoną Flaga określająca typ wartości pola.</span><span class="sxs-lookup"><span data-stu-id="74c50-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="74c50-115">określoną Stała wartość pola.</span><span class="sxs-lookup"><span data-stu-id="74c50-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="74c50-116">określoną Rozmiar w znakach `ppValue` lub zero, jeśli nie istnieje ciąg.</span><span class="sxs-lookup"><span data-stu-id="74c50-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74c50-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74c50-117">Requirements</span></span>  
 <span data-ttu-id="74c50-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74c50-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74c50-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="74c50-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74c50-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="74c50-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="74c50-121">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74c50-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c50-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74c50-122">See also</span></span>

- [<span data-ttu-id="74c50-123">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="74c50-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="74c50-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="74c50-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
