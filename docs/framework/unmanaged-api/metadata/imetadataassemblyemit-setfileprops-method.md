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
ms.openlocfilehash: 9990daea1b097532de53684921d3f10c520a3b1a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008069"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="3be0c-102">IMetaDataAssemblyEmit::SetFileProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="3be0c-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="3be0c-103">Modyfikuje określoną `File` strukturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="3be0c-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3be0c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3be0c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3be0c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3be0c-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="3be0c-106">podczas Token metadanych określający `File` strukturę metadanych, która ma zostać zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="3be0c-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="3be0c-107">podczas Wskaźnik do danych skrótu skojarzonych z plikiem.</span><span class="sxs-lookup"><span data-stu-id="3be0c-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="3be0c-108">podczas Rozmiar w bajtach `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="3be0c-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="3be0c-109">podczas Bitowa kombinacja wartości [CorFileFlags —](corfileflags-enumeration.md) , które określają różne atrybuty pliku.</span><span class="sxs-lookup"><span data-stu-id="3be0c-109">[in] A bitwise combination of [CorFileFlags](corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3be0c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3be0c-110">Remarks</span></span>  
 <span data-ttu-id="3be0c-111">Aby utworzyć `File` strukturę metadanych, użyj metody [IMetaDataAssemblyEmit::D efinefile](imetadataassemblyemit-definefile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3be0c-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3be0c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3be0c-112">Requirements</span></span>  
 <span data-ttu-id="3be0c-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3be0c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3be0c-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3be0c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3be0c-115">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3be0c-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3be0c-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3be0c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be0c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3be0c-117">See also</span></span>

- [<span data-ttu-id="3be0c-118">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3be0c-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
