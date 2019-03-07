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
ms.openlocfilehash: e3c11eeeb4eece495a7ccbe51c7e04d077e497ce
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494574"
---
# <a name="getscope2-method"></a><span data-ttu-id="3ae12-102">GetScope2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="3ae12-102">GetScope2 Method</span></span>
<span data-ttu-id="3ae12-103">Pobiera zakres importu.</span><span class="sxs-lookup"><span data-stu-id="3ae12-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ae12-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ae12-104">Syntax</span></span>  
  
```  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="3ae12-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ae12-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3ae12-106">Identyfikator zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3ae12-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3ae12-107">Identyfikator pliku, z którego chcesz zaimportować.</span><span class="sxs-lookup"><span data-stu-id="3ae12-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="3ae12-108">Liczony od zera zakres do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="3ae12-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="3ae12-109">Otrzymuje wskaźnik do [imetadataimport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interfejsu dla wskazanego zakresu.</span><span class="sxs-lookup"><span data-stu-id="3ae12-109">Receives pointer to [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ae12-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3ae12-110">Return Value</span></span>  
 <span data-ttu-id="3ae12-111">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="3ae12-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ae12-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ae12-112">Requirements</span></span>  
 <span data-ttu-id="3ae12-113">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="3ae12-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae12-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ae12-114">See also</span></span>
- [<span data-ttu-id="3ae12-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3ae12-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="3ae12-116">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="3ae12-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="3ae12-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="3ae12-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
