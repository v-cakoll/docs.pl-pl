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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7f8cccf8d583645982eb37f6afcb553914679ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075678"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="a9452-102">IMetaDataImport::GetFieldProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="a9452-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="a9452-103">Pobiera metadane skojarzone z polem odwołuje się określona FieldDef token.</span><span class="sxs-lookup"><span data-stu-id="a9452-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9452-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9452-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="a9452-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9452-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="a9452-106">[in] Token FieldDef, który reprezentuje pole, które można pobrać skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="a9452-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="a9452-107">[out] Wskaźnik do TypeDef token, który reprezentuje typ klasy, które pole należy do.</span><span class="sxs-lookup"><span data-stu-id="a9452-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="a9452-108">[out] Nazwa pola.</span><span class="sxs-lookup"><span data-stu-id="a9452-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="a9452-109">[in] Rozmiar w znaki dwubajtowe buforu dla *szField*.</span><span class="sxs-lookup"><span data-stu-id="a9452-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="a9452-110">[out] Rzeczywisty rozmiar buforu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="a9452-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="a9452-111">[out] Flagi skojarzone ze pola metadanych.</span><span class="sxs-lookup"><span data-stu-id="a9452-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="a9452-112">[in] Wskaźnik do wartości binarne metadanych, opisujący pola.</span><span class="sxs-lookup"><span data-stu-id="a9452-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="a9452-113">[out] Rozmiar w bajtach `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="a9452-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="a9452-114">[out] Flaga, która określa typ wartości pola.</span><span class="sxs-lookup"><span data-stu-id="a9452-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a9452-115">[out] Stała wartość dla pola.</span><span class="sxs-lookup"><span data-stu-id="a9452-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="a9452-116">[out] Rozmiar w znaki z `ppValue`, lub zero, jeśli ciąg nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="a9452-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9452-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9452-117">Requirements</span></span>  
 <span data-ttu-id="a9452-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9452-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9452-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a9452-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9452-120">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9452-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9452-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9452-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9452-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9452-122">See also</span></span>

- [<span data-ttu-id="a9452-123">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9452-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a9452-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9452-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
