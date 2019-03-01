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
ms.openlocfilehash: c5798fc488cf4453b6abcf00a7169b1ec0b529ec
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965374"
---
# <a name="getscope-method"></a><span data-ttu-id="c3972-102">GetScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="c3972-102">GetScope Method</span></span>
<span data-ttu-id="c3972-103">Pobiera zakres importu.</span><span class="sxs-lookup"><span data-stu-id="c3972-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3972-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3972-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3972-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3972-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c3972-106">Unikatowy identyfikator zestawu, aby zaimportować.</span><span class="sxs-lookup"><span data-stu-id="c3972-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c3972-107">Unikatowy identyfikator pliku do zaimportowania z.</span><span class="sxs-lookup"><span data-stu-id="c3972-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="c3972-108">Liczony od zera zakres do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="c3972-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="c3972-109">Odbiera [imetadataimport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejs dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="c3972-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3972-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c3972-110">Return Value</span></span>  
 <span data-ttu-id="c3972-111">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c3972-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3972-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3972-112">Requirements</span></span>  
 <span data-ttu-id="c3972-113">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="c3972-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3972-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3972-114">See also</span></span>
- [<span data-ttu-id="c3972-115">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="c3972-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c3972-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c3972-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c3972-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="c3972-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
