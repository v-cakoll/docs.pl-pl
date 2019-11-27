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
ms.openlocfilehash: 5936ca837c9ab452e992fcb09aacb476ab37316a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431436"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="fdb9e-102">IMetaDataTables::GetUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="fdb9e-102">IMetaDataTables::GetUserString Method</span></span>

<span data-ttu-id="fdb9e-103">Pobiera zakodowany ciąg o określonym indeksie w kolumnie ciąg w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="fdb9e-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="fdb9e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdb9e-104">Syntax</span></span>

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a><span data-ttu-id="fdb9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdb9e-105">Parameters</span></span>

`ixUserString`\
<span data-ttu-id="fdb9e-106">podczas Wartość indeksu, z której zostanie pobrany zakodowany ciąg.</span><span class="sxs-lookup"><span data-stu-id="fdb9e-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>

`pcbData`\
<span data-ttu-id="fdb9e-107">określoną Wskaźnik do rozmiaru `ppData`.</span><span class="sxs-lookup"><span data-stu-id="fdb9e-107">[out] A pointer to the size of `ppData`.</span></span>

`ppData`\
<span data-ttu-id="fdb9e-108">określoną Wskaźnik do wskaźnika do zwracanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="fdb9e-108">[out] A pointer to a pointer to the returned string.</span></span>

## <a name="requirements"></a><span data-ttu-id="fdb9e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fdb9e-109">Requirements</span></span>

<span data-ttu-id="fdb9e-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdb9e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="fdb9e-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fdb9e-111">**Header:** Cor.h</span></span>

<span data-ttu-id="fdb9e-112">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fdb9e-112">**Library:** Used as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="fdb9e-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdb9e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fdb9e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdb9e-114">See also</span></span>

- [<span data-ttu-id="fdb9e-115">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="fdb9e-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="fdb9e-116">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fdb9e-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
