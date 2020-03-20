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
ms.openlocfilehash: 8c3f98a124dbbcae3b0500932a2357ed1757951f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177247"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="bca77-102">IMetaDataImport::GetFieldProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="bca77-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="bca77-103">Pobiera metadane skojarzone z polem, do którego odwołuje się określony token FieldDef.</span><span class="sxs-lookup"><span data-stu-id="bca77-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca77-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bca77-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="bca77-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bca77-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="bca77-106">[w] A FieldDef token, który reprezentuje pole, aby uzyskać skojarzone metadane dla.</span><span class="sxs-lookup"><span data-stu-id="bca77-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="bca77-107">[na zewnątrz] Wskaźnik do Tokenu TypeDef, który reprezentuje typ klasy, do której należy pole.</span><span class="sxs-lookup"><span data-stu-id="bca77-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="bca77-108">[na zewnątrz] Nazwa pola.</span><span class="sxs-lookup"><span data-stu-id="bca77-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="bca77-109">[w] Rozmiar w szerokich znaków buforu dla *szField*.</span><span class="sxs-lookup"><span data-stu-id="bca77-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="bca77-110">[na zewnątrz] Rzeczywisty rozmiar zwróconego buforu.</span><span class="sxs-lookup"><span data-stu-id="bca77-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="bca77-111">[na zewnątrz] Flagi skojarzone z metadanymi pola.</span><span class="sxs-lookup"><span data-stu-id="bca77-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="bca77-112">[w] Wskaźnik do wartości metadanych binarnych, który opisuje pole.</span><span class="sxs-lookup"><span data-stu-id="bca77-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="bca77-113">[na zewnątrz] Rozmiar w bajtach . `ppvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="bca77-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="bca77-114">[na zewnątrz] Flaga określająca typ wartości pola.</span><span class="sxs-lookup"><span data-stu-id="bca77-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="bca77-115">[na zewnątrz] Stała wartość pola.</span><span class="sxs-lookup"><span data-stu-id="bca77-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="bca77-116">[na zewnątrz] Rozmiar w znakach `ppValue`, lub zero, jeśli nie istnieje ciąg.</span><span class="sxs-lookup"><span data-stu-id="bca77-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bca77-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bca77-117">Requirements</span></span>  
 <span data-ttu-id="bca77-118">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bca77-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bca77-119">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="bca77-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bca77-120">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bca77-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bca77-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bca77-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca77-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bca77-122">See also</span></span>

- [<span data-ttu-id="bca77-123">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bca77-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bca77-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bca77-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
