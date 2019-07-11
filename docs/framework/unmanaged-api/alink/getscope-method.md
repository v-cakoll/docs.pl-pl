---
title: GetScope — Metoda
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f3c3142ca12789b086bcd8b5a9c00c943264ae7b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741852"
---
# <a name="getscope-method"></a><span data-ttu-id="0bd20-102">GetScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="0bd20-102">GetScope Method</span></span>
<span data-ttu-id="0bd20-103">Pobiera zakres importu.</span><span class="sxs-lookup"><span data-stu-id="0bd20-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bd20-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0bd20-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bd20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bd20-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0bd20-106">Unikatowy identyfikator zestawu, aby zaimportować.</span><span class="sxs-lookup"><span data-stu-id="0bd20-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="0bd20-107">Unikatowy identyfikator pliku do zaimportowania z.</span><span class="sxs-lookup"><span data-stu-id="0bd20-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="0bd20-108">Liczony od zera zakres do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="0bd20-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="0bd20-109">Odbiera [imetadataimport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejs dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="0bd20-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0bd20-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0bd20-110">Return Value</span></span>  
 <span data-ttu-id="0bd20-111">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="0bd20-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bd20-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0bd20-112">Requirements</span></span>  
 <span data-ttu-id="0bd20-113">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="0bd20-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd20-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0bd20-114">See also</span></span>

- [<span data-ttu-id="0bd20-115">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="0bd20-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="0bd20-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0bd20-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="0bd20-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="0bd20-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
