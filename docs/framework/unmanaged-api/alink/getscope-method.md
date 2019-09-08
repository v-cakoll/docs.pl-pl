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
ms.openlocfilehash: b3a0e42e9ffb99896bdd09dbbab65eafb40cafff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777209"
---
# <a name="getscope-method"></a><span data-ttu-id="9e355-102">GetScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="9e355-102">GetScope Method</span></span>
<span data-ttu-id="9e355-103">Pobiera zakres importu.</span><span class="sxs-lookup"><span data-stu-id="9e355-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e355-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e355-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e355-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e355-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9e355-106">Unikatowy identyfikator zestawu do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="9e355-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="9e355-107">Unikatowy identyfikator pliku do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="9e355-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="9e355-108">Zakres od zera do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="9e355-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="9e355-109">Odbiera Interfejs [interfejsu IMetaDataImport](../metadata/imetadataimport-interface.md) dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="9e355-109">Receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e355-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9e355-110">Return Value</span></span>  
 <span data-ttu-id="9e355-111">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9e355-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e355-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e355-112">Requirements</span></span>  
 <span data-ttu-id="9e355-113">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="9e355-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e355-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e355-114">See also</span></span>

- [<span data-ttu-id="9e355-115">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e355-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9e355-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e355-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9e355-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="9e355-117">ALink API</span></span>](index.md)
