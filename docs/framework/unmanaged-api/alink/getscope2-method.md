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
ms.openlocfilehash: a5b080443be94d5a298cc67591914d87470e6f48
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447186"
---
# <a name="getscope2-method"></a><span data-ttu-id="06e70-102">GetScope2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="06e70-102">GetScope2 Method</span></span>
<span data-ttu-id="06e70-103">Pobiera zakres importu.</span><span class="sxs-lookup"><span data-stu-id="06e70-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06e70-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06e70-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="06e70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06e70-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="06e70-106">Identyfikator zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="06e70-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="06e70-107">Identyfikator pliku, z którego ma zostać zaimportowany.</span><span class="sxs-lookup"><span data-stu-id="06e70-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="06e70-108">Zakres od zera do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="06e70-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="06e70-109">Odbiera wskaźnik do interfejsu [interfejsu IMetaDataImport2](../metadata/imetadataimport2-interface.md) dla wskazanego zakresu.</span><span class="sxs-lookup"><span data-stu-id="06e70-109">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06e70-110">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="06e70-110">Return Value</span></span>  
 <span data-ttu-id="06e70-111">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="06e70-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06e70-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06e70-112">Requirements</span></span>  
 <span data-ttu-id="06e70-113">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="06e70-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e70-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06e70-114">See also</span></span>

- [<span data-ttu-id="06e70-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="06e70-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="06e70-116">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="06e70-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="06e70-117">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="06e70-117">ALink API</span></span>](index.md)
