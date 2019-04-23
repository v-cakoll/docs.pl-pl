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
ms.openlocfilehash: f14822a58f3982d6f9fee1328c10b960657c056f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098471"
---
# <a name="importtypes2-method"></a><span data-ttu-id="8fef0-102">ImportTypes2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="8fef0-102">ImportTypes2 Method</span></span>
<span data-ttu-id="8fef0-103">Inicjuje importowania typów.</span><span class="sxs-lookup"><span data-stu-id="8fef0-103">Initiates the import of types.</span></span> <span data-ttu-id="8fef0-104">Wywołaj tę metodę ma się zacząć importowanie typów z każdym zakresem importowane za pośrednictwem [importfile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="8fef0-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fef0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8fef0-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8fef0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fef0-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8fef0-107">Identyfikator zestawu, do którego chcesz zaimportować.</span><span class="sxs-lookup"><span data-stu-id="8fef0-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8fef0-108">Identyfikator pliku do, z którego chcesz zaimportować.</span><span class="sxs-lookup"><span data-stu-id="8fef0-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="8fef0-109">Liczony od zera zakres, z którego chcesz zaimportować.</span><span class="sxs-lookup"><span data-stu-id="8fef0-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="8fef0-110">Odbiera uchwytu modułu wyliczającego dla typów w danym zakresie.</span><span class="sxs-lookup"><span data-stu-id="8fef0-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="8fef0-111">Opcjonalnie odbiera [imetadataimport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8fef0-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="8fef0-112">Opcjonalnie odbiera liczba typów w określonym zakresie.</span><span class="sxs-lookup"><span data-stu-id="8fef0-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8fef0-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8fef0-113">Return Value</span></span>  
 <span data-ttu-id="8fef0-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8fef0-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fef0-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8fef0-115">Requirements</span></span>  
 <span data-ttu-id="8fef0-116">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="8fef0-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fef0-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8fef0-117">See also</span></span>

- [<span data-ttu-id="8fef0-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8fef0-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="8fef0-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="8fef0-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="8fef0-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="8fef0-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
