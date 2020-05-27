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
ms.openlocfilehash: 7c6adcbcfe64f63048078b4ccba6727a58531033
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008108"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="471d2-102">IMetaDataAssemblyEmit::SetAssemblyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="471d2-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="471d2-103">Modyfikuje określoną `Assembly` strukturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="471d2-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="471d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="471d2-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="471d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="471d2-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="471d2-106">podczas Token metadanych określający `Assembly` strukturę metadanych, która ma zostać zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="471d2-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="471d2-107">podczas Wskaźnik do klucza publicznego wydawcy zestawu.</span><span class="sxs-lookup"><span data-stu-id="471d2-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="471d2-108">podczas Rozmiar w bajtach `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="471d2-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="471d2-109">podczas Identyfikator algorytmu wyznaczania wartości skrótu używany do mieszania plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="471d2-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="471d2-110">podczas Nazwa tekstu do odczytania przez człowieka.</span><span class="sxs-lookup"><span data-stu-id="471d2-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="471d2-111">podczas Wskaźnik do ASSEMBLYMETADATA, który zawiera wersję, platformę i informacje o ustawieniach regionalnych dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="471d2-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="471d2-112">podczas Bitowa kombinacja wartości [AssemblyFlags —](assemblyflags-enumeration.md) , które określają różne atrybuty zestawu.</span><span class="sxs-lookup"><span data-stu-id="471d2-112">[in] A bitwise combination of [AssemblyFlags](assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="471d2-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="471d2-113">Remarks</span></span>  
 <span data-ttu-id="471d2-114">Aby utworzyć `Assembly` strukturę metadanych, użyj metody [IMetaDataAssemblyEmit::D efineassembly](imetadataassemblyemit-defineassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="471d2-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="471d2-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="471d2-115">Requirements</span></span>  
 <span data-ttu-id="471d2-116">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="471d2-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="471d2-117">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="471d2-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="471d2-118">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="471d2-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="471d2-119">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="471d2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="471d2-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="471d2-120">See also</span></span>

- [<span data-ttu-id="471d2-121">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="471d2-121">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
