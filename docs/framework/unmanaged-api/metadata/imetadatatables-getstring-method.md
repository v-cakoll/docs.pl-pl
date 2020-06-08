---
title: IMetaDataTables::GetString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
ms.openlocfilehash: 41e7b8193ce3288d526db8d7d8c289b0a053ee4e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489759"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="b75ef-102">IMetaDataTables::GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="b75ef-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="b75ef-103">Pobiera ciąg o określonym indeksie z kolumny tabeli w bieżącym zakresie odwołania.</span><span class="sxs-lookup"><span data-stu-id="b75ef-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b75ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b75ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b75ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b75ef-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="b75ef-106">podczas Indeks, od którego należy zacząć wyszukiwanie następnej wartości.</span><span class="sxs-lookup"><span data-stu-id="b75ef-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="b75ef-107">określoną Wskaźnik do wskaźnika do zwracanej wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="b75ef-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b75ef-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b75ef-108">Requirements</span></span>  
 <span data-ttu-id="b75ef-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b75ef-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b75ef-110">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b75ef-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b75ef-111">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b75ef-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b75ef-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b75ef-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b75ef-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b75ef-113">See also</span></span>

- [<span data-ttu-id="b75ef-114">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="b75ef-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="b75ef-115">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b75ef-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
