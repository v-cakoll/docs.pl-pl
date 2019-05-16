---
title: IMetaDataTables::GetUserString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4eaf426bc9c933de1d4b774928f2b0a54dfb472
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636961"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="6dae9-102">IMetaDataTables::GetUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="6dae9-102">IMetaDataTables::GetUserString Method</span></span>

<span data-ttu-id="6dae9-103">Pobiera ciąg ustaloną dla podanego indeksu w kolumnie ciągu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="6dae9-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="6dae9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6dae9-104">Syntax</span></span>

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a><span data-ttu-id="6dae9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6dae9-105">Parameters</span></span>

`ixUserString`\
<span data-ttu-id="6dae9-106">[in] Wartość indeksu, z którego będą pobierane ciągu ustalonych.</span><span class="sxs-lookup"><span data-stu-id="6dae9-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>

`pcbData`\
<span data-ttu-id="6dae9-107">[out] Wskaźnik do rozmiaru `ppData`.</span><span class="sxs-lookup"><span data-stu-id="6dae9-107">[out] A pointer to the size of `ppData`.</span></span>

`ppData`\
<span data-ttu-id="6dae9-108">[out] Wskaźnik do wskaźnika do zwracanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="6dae9-108">[out] A pointer to a pointer to the returned string.</span></span>

## <a name="requirements"></a><span data-ttu-id="6dae9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6dae9-109">Requirements</span></span>

<span data-ttu-id="6dae9-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dae9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="6dae9-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6dae9-111">**Header:** Cor.h</span></span>

<span data-ttu-id="6dae9-112">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6dae9-112">**Library:** Used as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="6dae9-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dae9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6dae9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6dae9-114">See also</span></span>

- [<span data-ttu-id="6dae9-115">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="6dae9-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="6dae9-116">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6dae9-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
