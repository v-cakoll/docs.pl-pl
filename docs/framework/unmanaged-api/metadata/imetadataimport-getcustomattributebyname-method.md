---
title: IMetaDataImport::GetCustomAttributeByName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61029074347d554faaefe790c1e408e860e34690
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183030"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="6e8e0-102">IMetaDataImport::GetCustomAttributeByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="6e8e0-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="6e8e0-103">Pobiera atrybut niestandardowy, biorąc pod uwagę jej nazwę i właściciela.</span><span class="sxs-lookup"><span data-stu-id="6e8e0-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e8e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e8e0-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e8e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e8e0-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="6e8e0-106">[in] Token metadanych reprezentujący obiekt, który jest właścicielem atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="6e8e0-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="6e8e0-107">[in] Nazwa atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="6e8e0-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="6e8e0-108">[out] Wskaźnik do tablicy danych, która jest wartością atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="6e8e0-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="6e8e0-109">[out] Rozmiar w bajtach dane zwrócone w \*`ppData`.</span><span class="sxs-lookup"><span data-stu-id="6e8e0-109">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e8e0-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e8e0-110">Remarks</span></span>  
 <span data-ttu-id="6e8e0-111">Jest legalne, aby zdefiniować wiele atrybutów niestandardowych dla tego samego właściciela; nawet mają taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="6e8e0-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="6e8e0-112">Jednak `GetCustomAttributeByName` zwraca tylko jedno wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="6e8e0-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="6e8e0-113">(`GetCustomAttributeByName` zwraca pierwsze wystąpienie, które napotka.) Aby znaleźć wszystkie wystąpienia elementu atrybutów niestandardowych, należy wywołać [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6e8e0-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e8e0-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6e8e0-114">Requirements</span></span>  
 <span data-ttu-id="6e8e0-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e8e0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e8e0-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6e8e0-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e8e0-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e8e0-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6e8e0-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e8e0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e8e0-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e8e0-119">See also</span></span>

- [<span data-ttu-id="6e8e0-120">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="6e8e0-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6e8e0-121">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6e8e0-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
