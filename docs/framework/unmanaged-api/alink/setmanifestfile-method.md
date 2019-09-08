---
title: SetManifestFile — Metoda
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b293c30060107d18c6b609efc82c4128a73cc1c7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787208"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="4fd86-102">SetManifestFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="4fd86-102">SetManifestFile Method</span></span>
<span data-ttu-id="4fd86-103">Umożliwia określenie lub zresetowanie pliku manifestu używanego przez konsolidatora podczas tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="4fd86-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fd86-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4fd86-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fd86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4fd86-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="4fd86-106">Nazwa pliku manifestu, którego zawartość jest umieszczana w obiekcie blob zasobów Win32.</span><span class="sxs-lookup"><span data-stu-id="4fd86-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4fd86-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4fd86-107">Return Value</span></span>  
 <span data-ttu-id="4fd86-108">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4fd86-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fd86-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4fd86-109">Remarks</span></span>  
 <span data-ttu-id="4fd86-110">Wywołaj to przed pytaniem o Win32ResBlob.</span><span class="sxs-lookup"><span data-stu-id="4fd86-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="4fd86-111">Wartość `pszFile` parametru jest nazwą pliku manifestu, którego zawartość jest odczytywana i umieszczana w zasobach Win32 o identyfikatorze RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="4fd86-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="4fd86-112">Gdy wywoływana przy użyciu parametru o wartości NULL, każdy poprzednio odczytany manifest jest czyszczony.</span><span class="sxs-lookup"><span data-stu-id="4fd86-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="4fd86-113">Umożliwia to jednemu resetowaniu stanu konsolidatora do czasu inicjacji.</span><span class="sxs-lookup"><span data-stu-id="4fd86-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fd86-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4fd86-114">Requirements</span></span>  
 <span data-ttu-id="4fd86-115">Wymaga aLink. h</span><span class="sxs-lookup"><span data-stu-id="4fd86-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd86-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4fd86-116">See also</span></span>

- [<span data-ttu-id="4fd86-117">IALink3, interfejs</span><span class="sxs-lookup"><span data-stu-id="4fd86-117">IALink3 Interface</span></span>](ialink3-interface.md)
- [<span data-ttu-id="4fd86-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="4fd86-118">ALink API</span></span>](index.md)
- [<span data-ttu-id="4fd86-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="4fd86-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4fd86-120">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="4fd86-120">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
