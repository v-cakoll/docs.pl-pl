---
title: IMetaDataAssemblyEmit::SetAssemblyProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37d91ca7935e114504864683075f4809de7270fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599117"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="2e054-102">IMetaDataAssemblyEmit::SetAssemblyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="2e054-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="2e054-103">Modyfikuje określonego `Assembly` struktury metadanych.</span><span class="sxs-lookup"><span data-stu-id="2e054-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e054-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e054-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e054-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e054-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="2e054-106">[in] Token metadanych, który określa `Assembly` struktury metadanych do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="2e054-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="2e054-107">[in] Wskaźnik do klucza publicznego wydawcy zestawu.</span><span class="sxs-lookup"><span data-stu-id="2e054-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="2e054-108">[in] Rozmiar w bajtach `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="2e054-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="2e054-109">[in] Identyfikator algorytmu mieszania używany do tworzenia skrótu plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="2e054-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="2e054-110">[in] Nazwa tekstowych zrozumiałych zestawu.</span><span class="sxs-lookup"><span data-stu-id="2e054-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="2e054-111">[in] Wskaźnik do assemblymetadata —, który zawiera informacje o wersji, platformy i ustawienia regionalne dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="2e054-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="2e054-112">[in] Bitowa kombinacja [assemblyflags —](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) wartości, które określają różne atrybuty zestawu.</span><span class="sxs-lookup"><span data-stu-id="2e054-112">[in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e054-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e054-113">Remarks</span></span>  
 <span data-ttu-id="2e054-114">Aby utworzyć `Assembly` struktury metadanych, użyj [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2e054-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e054-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e054-115">Requirements</span></span>  
 <span data-ttu-id="2e054-116">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e054-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e054-117">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2e054-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2e054-118">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e054-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e054-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e054-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e054-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e054-120">See also</span></span>
- [<span data-ttu-id="2e054-121">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="2e054-121">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
