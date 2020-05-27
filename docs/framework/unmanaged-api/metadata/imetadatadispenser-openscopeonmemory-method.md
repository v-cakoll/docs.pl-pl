---
title: IMetaDataDispenser::OpenScopeOnMemory — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
ms.openlocfilehash: 69e5e05012d2b44a76a986591ec990f66bf8ae20
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007328"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="64211-102">IMetaDataDispenser::OpenScopeOnMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="64211-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="64211-103">Otwiera obszar pamięci, który zawiera istniejące metadane.</span><span class="sxs-lookup"><span data-stu-id="64211-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="64211-104">Oznacza to, że ta metoda otwiera określony obszar pamięci, w której istniejące dane są traktowane jako metadane.</span><span class="sxs-lookup"><span data-stu-id="64211-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64211-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="64211-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64211-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="64211-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="64211-107">podczas Wskaźnik określający adres początkowy obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="64211-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="64211-108">podczas Rozmiar obszaru pamięci (w bajtach).</span><span class="sxs-lookup"><span data-stu-id="64211-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="64211-109">podczas Wartość wyliczenia [CorOpenFlags —](coropenflags-enumeration.md) w celu określenia trybu (odczyt, zapis itd.) do otwarcia.</span><span class="sxs-lookup"><span data-stu-id="64211-109">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="64211-110">podczas Identyfikator IID żądanego interfejsu metadanych do zwrócenia; Obiekt wywołujący będzie używać interfejsu do importowania metadanych (odczytu) lub emisji (zapisu).</span><span class="sxs-lookup"><span data-stu-id="64211-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="64211-111">Wartość `riid` musi określać jeden z interfejsów "Import" lub "Emituj".</span><span class="sxs-lookup"><span data-stu-id="64211-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="64211-112">Prawidłowe wartości to IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 lub IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="64211-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="64211-113">określoną Wskaźnik do zwracanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="64211-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64211-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="64211-114">Remarks</span></span>  
 <span data-ttu-id="64211-115">Kopię metadanych w pamięci można zbadać przy użyciu metod z jednego z interfejsów "Import" lub dodać do metod przy użyciu metody z jednego z interfejsów "Emituj".</span><span class="sxs-lookup"><span data-stu-id="64211-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="64211-116">`OpenScopeOnMemory`Metoda jest podobna do metody [IMetaDataDispenser:: OpenScope —](imetadatadispenser-openscope-method.md) , z tą różnicą, że metadane zainteresowania już istnieją w pamięci, a nie w pliku na dysku.</span><span class="sxs-lookup"><span data-stu-id="64211-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="64211-117">Jeśli obszar docelowy pamięci nie zawiera metadanych środowiska uruchomieniowego języka wspólnego (CLR), `OpenScopeOnMemory` Metoda zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="64211-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64211-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="64211-118">Requirements</span></span>  
 <span data-ttu-id="64211-119">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64211-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64211-120">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="64211-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64211-121">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="64211-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64211-122">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64211-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64211-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64211-123">See also</span></span>

- [<span data-ttu-id="64211-124">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="64211-124">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="64211-125">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="64211-125">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="64211-126">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="64211-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="64211-127">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="64211-127">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="64211-128">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="64211-128">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="64211-129">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="64211-129">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="64211-130">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="64211-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="64211-131">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="64211-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
