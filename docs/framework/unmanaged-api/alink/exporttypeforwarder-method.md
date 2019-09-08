---
title: ExportTypeForwarder — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ae4ddd07a2a3d3ab9b5d024eceb43329db96915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787510"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="33129-102">ExportTypeForwarder — Metoda</span><span class="sxs-lookup"><span data-stu-id="33129-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="33129-103">Dodaje usługę przesyłania dalej typu do tabeli typów danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="33129-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33129-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33129-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="33129-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33129-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="33129-106">Odwołanie do zestawu, do którego odwołuje się usługa przesyłania dalej typu.</span><span class="sxs-lookup"><span data-stu-id="33129-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="33129-107">W pełni kwalifikowana nazwa typu do eksportowania.</span><span class="sxs-lookup"><span data-stu-id="33129-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="33129-108">`ComType`flagi takie jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="33129-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="33129-109">Ta wartość może zostać przeniesiona do [metody DefineExportedType —](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="33129-109">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="33129-110">Odbiera token wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="33129-110">Receives the token of the exported type.</span></span> <span data-ttu-id="33129-111">Jest to konieczne tylko w przypadku emitowania typów zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="33129-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33129-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="33129-112">Return Value</span></span>  
 <span data-ttu-id="33129-113">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="33129-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33129-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33129-114">Requirements</span></span>  
 <span data-ttu-id="33129-115">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="33129-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33129-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33129-116">See also</span></span>

- [<span data-ttu-id="33129-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="33129-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="33129-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="33129-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="33129-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="33129-119">ALink API</span></span>](index.md)
