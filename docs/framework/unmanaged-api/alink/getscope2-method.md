---
title: GetScope2 — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c0abc63610f3f1ed6e8a556c44ee15edc1ea20b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741843"
---
# <a name="getscope2-method"></a><span data-ttu-id="2223a-102">GetScope2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="2223a-102">GetScope2 Method</span></span>
<span data-ttu-id="2223a-103">Pobiera zakres importu.</span><span class="sxs-lookup"><span data-stu-id="2223a-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2223a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2223a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="2223a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2223a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2223a-106">Identyfikator zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="2223a-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="2223a-107">Identyfikator pliku, z którego chcesz zaimportować.</span><span class="sxs-lookup"><span data-stu-id="2223a-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="2223a-108">Liczony od zera zakres do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="2223a-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="2223a-109">Otrzymuje wskaźnik do [imetadataimport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interfejsu dla wskazanego zakresu.</span><span class="sxs-lookup"><span data-stu-id="2223a-109">Receives pointer to [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2223a-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2223a-110">Return Value</span></span>  
 <span data-ttu-id="2223a-111">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="2223a-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2223a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2223a-112">Requirements</span></span>  
 <span data-ttu-id="2223a-113">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="2223a-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2223a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2223a-114">See also</span></span>

- [<span data-ttu-id="2223a-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2223a-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="2223a-116">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="2223a-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="2223a-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="2223a-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
