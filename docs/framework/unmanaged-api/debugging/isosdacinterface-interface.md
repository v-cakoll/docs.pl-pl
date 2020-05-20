---
title: ISOSDacInterface, interfejs
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c9b4e6e5b36fe38b6c0ea78f6d1848d155008bcc
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420971"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="32fa7-102">ISOSDacInterface, interfejs</span><span class="sxs-lookup"><span data-stu-id="32fa7-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="32fa7-103">Zapewnia metody pomocnika do uzyskiwania dostępu do danych `SOS` .</span><span class="sxs-lookup"><span data-stu-id="32fa7-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="32fa7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="32fa7-104">Methods</span></span>

| <span data-ttu-id="32fa7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="32fa7-105">Method</span></span>                                                                                                               | <span data-ttu-id="32fa7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="32fa7-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="32fa7-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="32fa7-107">GetMethodDescData</span></span>](isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="32fa7-108">Pobiera dane dla danego wskaźnika MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="32fa7-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="32fa7-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="32fa7-109">GetMethodDescPtrFromIP</span></span>](isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="32fa7-110">Pobiera wskaźnik MethodDesc odpowiadającego metodzie zawierającej podanego adresu instrukcji macierzystej.</span><span class="sxs-lookup"><span data-stu-id="32fa7-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="32fa7-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="32fa7-111">GetModuleData</span></span>](isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="32fa7-112">Pobiera dane odpowiadające modułowi załadowanemu pod danym adresem.</span><span class="sxs-lookup"><span data-stu-id="32fa7-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="32fa7-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32fa7-113">Remarks</span></span>

<span data-ttu-id="32fa7-114">Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek.</span><span class="sxs-lookup"><span data-stu-id="32fa7-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="32fa7-115">Jest to jednak interfejs COM pochodzący z `IUnknown` identyfikatora GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` , który można uzyskać za pomocą zwykłych mechanizmów com.</span><span class="sxs-lookup"><span data-stu-id="32fa7-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="32fa7-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32fa7-116">Requirements</span></span>

<span data-ttu-id="32fa7-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32fa7-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="32fa7-118">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="32fa7-118">**Header:** None</span></span>  
<span data-ttu-id="32fa7-119">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="32fa7-119">**Library:** None</span></span>  
<span data-ttu-id="32fa7-120">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="32fa7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="32fa7-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32fa7-121">See also</span></span>

- [<span data-ttu-id="32fa7-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="32fa7-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="32fa7-123">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="32fa7-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
