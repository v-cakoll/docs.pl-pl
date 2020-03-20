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
ms.openlocfilehash: 25baa6ffda3d50915cc7898275d6a557c1b3e947
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176035"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="78d0f-102">IMetaDataAssemblyEmit::SetFileProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="78d0f-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="78d0f-103">Modyfikuje `File` strukturę określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="78d0f-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78d0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78d0f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78d0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78d0f-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="78d0f-106">[w] Token metadanych, który `File` określa strukturę metadanych, która ma zostać zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="78d0f-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="78d0f-107">[w] Wskaźnik do danych skrótu skojarzonych z plikiem.</span><span class="sxs-lookup"><span data-stu-id="78d0f-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="78d0f-108">[w] Rozmiar w bajtach . `pbHashValue`</span><span class="sxs-lookup"><span data-stu-id="78d0f-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="78d0f-109">[w] Bitowe połączenie wartości [CorFileFlags,](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) które określają różne atrybuty pliku.</span><span class="sxs-lookup"><span data-stu-id="78d0f-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78d0f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78d0f-110">Remarks</span></span>  
 <span data-ttu-id="78d0f-111">Aby utworzyć `File` strukturę metadanych, należy użyć [metody IMetaDataAssemblyEmit::DefineFile.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)</span><span class="sxs-lookup"><span data-stu-id="78d0f-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78d0f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78d0f-112">Requirements</span></span>  
 <span data-ttu-id="78d0f-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78d0f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78d0f-114">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="78d0f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78d0f-115">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78d0f-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78d0f-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78d0f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78d0f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78d0f-117">See also</span></span>

- [<span data-ttu-id="78d0f-118">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="78d0f-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
