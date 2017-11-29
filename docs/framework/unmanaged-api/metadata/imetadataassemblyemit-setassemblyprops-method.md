---
title: "IMetaDataAssemblyEmit::SetAssemblyProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetAssemblyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2c9336855d706a9861d4e832e5f0234cdf04db7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="ec61b-102">IMetaDataAssemblyEmit::SetAssemblyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="ec61b-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="ec61b-103">Modyfikuje określony `Assembly` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="ec61b-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec61b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec61b-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ec61b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec61b-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="ec61b-106">[in] Token metadanych, który określa `Assembly` struktura metadanych ma być zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="ec61b-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="ec61b-107">[in] Wskaźnik do klucza publicznego zestawu wydawcy.</span><span class="sxs-lookup"><span data-stu-id="ec61b-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="ec61b-108">[in] Wyrażony w bajtach rozmiar `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="ec61b-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="ec61b-109">[in] Identyfikator algorytmu wyznaczania wartości skrótu używany do tworzenia skrótu pliki zestawu.</span><span class="sxs-lookup"><span data-stu-id="ec61b-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="ec61b-110">[in] Tekst zrozumiałą nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="ec61b-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="ec61b-111">[in] Wskaźnik do assemblymetadata —, który zawiera informacje o wersji platformy i ustawień regionalnych dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="ec61b-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="ec61b-112">[in] Bitowe połączenie [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) wartości, które określają różne atrybuty zestawu.</span><span class="sxs-lookup"><span data-stu-id="ec61b-112">[in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec61b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec61b-113">Remarks</span></span>  
 <span data-ttu-id="ec61b-114">Aby utworzyć `Assembly` metadanych struktury, użyj [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ec61b-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec61b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec61b-115">Requirements</span></span>  
 <span data-ttu-id="ec61b-116">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec61b-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec61b-117">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ec61b-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec61b-118">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ec61b-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec61b-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec61b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec61b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec61b-120">See Also</span></span>  
 [<span data-ttu-id="ec61b-121">IMetaDataAssemblyEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="ec61b-121">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
