---
title: ImportTypes — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92dfc2bec33501a5cd9ca6b4ec4c3629b6d89946
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487957"
---
# <a name="importtypes-method"></a><span data-ttu-id="99e21-102">ImportTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="99e21-102">ImportTypes Method</span></span>
<span data-ttu-id="99e21-103">Inicjuje importowania typów z każdym zakresem importowane za pośrednictwem [importfile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="99e21-103">Initiates the importing of types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99e21-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99e21-104">Syntax</span></span>  
  
```  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="99e21-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99e21-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="99e21-106">Identyfikator zestawu, aby zaimportować.</span><span class="sxs-lookup"><span data-stu-id="99e21-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="99e21-107">Identyfikator pliku do zaimportowania z.</span><span class="sxs-lookup"><span data-stu-id="99e21-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="99e21-108">Liczony od zera zakres do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="99e21-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="99e21-109">Odbiera uchwytu modułu wyliczającego dla typów, w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="99e21-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="99e21-110">Opcjonalnie odbiera [imetadataimport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="99e21-110">Optionally receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="99e21-111">Opcjonalnie odbiera liczba typów w zakresie wskazane.</span><span class="sxs-lookup"><span data-stu-id="99e21-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99e21-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="99e21-112">Return Value</span></span>  
 <span data-ttu-id="99e21-113">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="99e21-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99e21-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99e21-114">Requirements</span></span>  
 <span data-ttu-id="99e21-115">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="99e21-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99e21-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99e21-116">See also</span></span>
- [<span data-ttu-id="99e21-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="99e21-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="99e21-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="99e21-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="99e21-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="99e21-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
