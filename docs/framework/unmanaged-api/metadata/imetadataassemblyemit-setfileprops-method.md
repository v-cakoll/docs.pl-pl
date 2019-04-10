---
title: IMetaDataAssemblyEmit::SetFileProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd0c2da234fa89bbf92c2117d6428d64502da0c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208179"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="22954-102">IMetaDataAssemblyEmit::SetFileProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="22954-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="22954-103">Modyfikuje określonego `File` struktury metadanych.</span><span class="sxs-lookup"><span data-stu-id="22954-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22954-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22954-104">Syntax</span></span>  
  
```  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22954-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22954-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="22954-106">[in] Token metadanych, który określa `File` struktury metadanych do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="22954-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="22954-107">[in] Wskaźnik do danych wyznaczania wartości skrótu, skojarzone z plikiem.</span><span class="sxs-lookup"><span data-stu-id="22954-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="22954-108">[in] Rozmiar w bajtach `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="22954-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="22954-109">[in] Bitowa kombinacja [corfileflags —](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) wartości, które określają różne atrybuty pliku.</span><span class="sxs-lookup"><span data-stu-id="22954-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22954-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22954-110">Remarks</span></span>  
 <span data-ttu-id="22954-111">Aby utworzyć `File` struktury metadanych, użyj [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="22954-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22954-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22954-112">Requirements</span></span>  
 <span data-ttu-id="22954-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22954-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22954-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="22954-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22954-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22954-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="22954-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="22954-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="22954-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22954-117">See also</span></span>

- [<span data-ttu-id="22954-118">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="22954-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
