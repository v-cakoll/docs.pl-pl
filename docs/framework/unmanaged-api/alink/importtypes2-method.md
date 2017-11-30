---
title: "ImportTypes2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportTypes2
api_location: alink.dll
api_type: COM
f1_keywords: ImportTypes2
helpviewer_keywords: ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 61d707cdd827b5e435c961a14e67170ab0e2bc90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="importtypes2-method"></a><span data-ttu-id="613df-102">ImportTypes2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="613df-102">ImportTypes2 Method</span></span>
<span data-ttu-id="613df-103">Inicjuje importowanie typów.</span><span class="sxs-lookup"><span data-stu-id="613df-103">Initiates the import of types.</span></span> <span data-ttu-id="613df-104">Wywołanie tej metody ma się zacząć importowanie typów z każdym zakresem importować za pomocą [ImportFile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="613df-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="613df-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="613df-105">Syntax</span></span>  
  
```  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="613df-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="613df-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="613df-107">Identyfikator zestawu, do których ma zostać zaimportowany.</span><span class="sxs-lookup"><span data-stu-id="613df-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="613df-108">Identyfikator pliku, z którego będą importowane.</span><span class="sxs-lookup"><span data-stu-id="613df-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="613df-109">Liczony od zera zakres, z którego będą importowane.</span><span class="sxs-lookup"><span data-stu-id="613df-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="613df-110">Odbiera uchwytu modułu wyliczającego dla typów w danym zakresie.</span><span class="sxs-lookup"><span data-stu-id="613df-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="613df-111">Opcjonalnie odbiera [IMetaDataImport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="613df-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="613df-112">Opcjonalnie odbiera liczba typy w podanym zakresie.</span><span class="sxs-lookup"><span data-stu-id="613df-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="613df-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="613df-113">Return Value</span></span>  
 <span data-ttu-id="613df-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="613df-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="613df-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="613df-115">Requirements</span></span>  
 <span data-ttu-id="613df-116">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="613df-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="613df-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="613df-117">See Also</span></span>  
 [<span data-ttu-id="613df-118">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="613df-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="613df-119">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="613df-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="613df-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="613df-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
