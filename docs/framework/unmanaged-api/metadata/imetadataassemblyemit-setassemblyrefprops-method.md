---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: 6ad6bbb8a4c69f575bbeba3a297c46e049a97325
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176048"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="7427e-102">IMetaDataAssemblyEmit::SetAssemblyRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="7427e-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="7427e-103">Modyfikuje `AssemblyRef` strukturę określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="7427e-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7427e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7427e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,
    [in] const ASSEMBLYMETADATA     *pMetaData,
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7427e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7427e-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="7427e-106">[w] Token metadanych, który `AssemblyRef` określa strukturę metadanych, która ma zostać zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="7427e-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="7427e-107">[w] Klucz publiczny wydawcy zestawu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="7427e-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="7427e-108">[w] Rozmiar w bajtach . `pbPublicKeyOrToken`</span><span class="sxs-lookup"><span data-stu-id="7427e-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="7427e-109">[w] Nazwa tekstowa zestawu czytelna dla człowieka.</span><span class="sxs-lookup"><span data-stu-id="7427e-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="7427e-110">[w] Wskaźnik do assemblymetadata wystąpienie, który zawiera informacje o wersji, platformy i ustawień regionalnych dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="7427e-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="7427e-111">[w] Wskaźnik do danych mieszania skojarzonych z zestawem.</span><span class="sxs-lookup"><span data-stu-id="7427e-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="7427e-112">[w] Rozmiar w bajtach . `pbHashValue`</span><span class="sxs-lookup"><span data-stu-id="7427e-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="7427e-113">[w] Bitowa kombinacja [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) wartości, które określają atrybuty zestawu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="7427e-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7427e-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7427e-114">Remarks</span></span>  
 <span data-ttu-id="7427e-115">Aby utworzyć `AssemblyRef` strukturę metadanych, należy użyć [metody IMetaDataAssemblyEmit::DefineAssemblyRef.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)</span><span class="sxs-lookup"><span data-stu-id="7427e-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7427e-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7427e-116">Requirements</span></span>  
 <span data-ttu-id="7427e-117">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7427e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7427e-118">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="7427e-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7427e-119">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7427e-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7427e-120">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7427e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7427e-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7427e-121">See also</span></span>

- [<span data-ttu-id="7427e-122">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7427e-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
