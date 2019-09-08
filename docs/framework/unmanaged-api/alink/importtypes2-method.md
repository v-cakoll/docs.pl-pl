---
title: ImportTypes2 — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce09eca30e1edb9e1afc02216a07955a5fed4fd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787255"
---
# <a name="importtypes2-method"></a><span data-ttu-id="f6ae6-102">ImportTypes2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="f6ae6-102">ImportTypes2 Method</span></span>
<span data-ttu-id="f6ae6-103">Inicjuje importowanie typów.</span><span class="sxs-lookup"><span data-stu-id="f6ae6-103">Initiates the import of types.</span></span> <span data-ttu-id="f6ae6-104">Wywołaj tę metodę, aby rozpocząć importowanie typów z każdego zakresu zaimportowanego za pomocą [metody ImportFile —](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="f6ae6-104">Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6ae6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6ae6-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6ae6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6ae6-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f6ae6-107">Identyfikator zestawu do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="f6ae6-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f6ae6-108">Identyfikator pliku, z którego ma zostać zaimportowany.</span><span class="sxs-lookup"><span data-stu-id="f6ae6-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="f6ae6-109">Zakres od zera, z którego ma zostać zaimportowany.</span><span class="sxs-lookup"><span data-stu-id="f6ae6-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="f6ae6-110">Odbiera dojście modułu wyliczającego dla typów w danym zakresie.</span><span class="sxs-lookup"><span data-stu-id="f6ae6-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="f6ae6-111">Opcjonalnie odbiera Interfejs [interfejsu IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f6ae6-111">Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="f6ae6-112">Opcjonalnie otrzymuje liczbę typów w określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="f6ae6-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6ae6-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f6ae6-113">Return Value</span></span>  
 <span data-ttu-id="f6ae6-114">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6ae6-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6ae6-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6ae6-115">Requirements</span></span>  
 <span data-ttu-id="f6ae6-116">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="f6ae6-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6ae6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6ae6-117">See also</span></span>

- [<span data-ttu-id="f6ae6-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f6ae6-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="f6ae6-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="f6ae6-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="f6ae6-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="f6ae6-120">ALink API</span></span>](index.md)
