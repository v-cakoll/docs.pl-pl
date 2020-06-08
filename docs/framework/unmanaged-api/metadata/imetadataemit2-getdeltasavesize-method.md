---
title: IMetaDataEmit2::GetDeltaSaveSize — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
ms.openlocfilehash: 24fe8fd65b36e133b767cd07c8602aa1ea7b9dfc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493113"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="f0bf5-102">IMetaDataEmit2::GetDeltaSaveSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0bf5-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="f0bf5-103">Pobiera wartość wskazującą wszelkie zmiany rozmiaru metadanych, które wynikają z bieżącej sesji Edit-and-Continue.</span><span class="sxs-lookup"><span data-stu-id="f0bf5-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0bf5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0bf5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0bf5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0bf5-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="f0bf5-106">podczas Jeden z wartości [CorSaveSize —](corsavesize-enumeration.md) , wskazujący żądany poziom precyzji.</span><span class="sxs-lookup"><span data-stu-id="f0bf5-106">[in] One of the [CorSaveSize](corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="f0bf5-107">W przypadku .NET Framework w wersji 2,0 ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="f0bf5-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="f0bf5-108">określoną Zmiana rozmiaru metadanych.</span><span class="sxs-lookup"><span data-stu-id="f0bf5-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0bf5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0bf5-109">Requirements</span></span>  
 <span data-ttu-id="f0bf5-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0bf5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0bf5-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f0bf5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f0bf5-112">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f0bf5-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f0bf5-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0bf5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0bf5-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0bf5-114">See also</span></span>

- [<span data-ttu-id="f0bf5-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0bf5-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="f0bf5-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f0bf5-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
