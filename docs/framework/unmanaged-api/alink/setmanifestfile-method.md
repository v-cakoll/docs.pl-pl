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
ms.openlocfilehash: df97f4c37d8f335ce183685debd7c0933be910ed
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445563"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="6f36b-102">SetManifestFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="6f36b-102">SetManifestFile Method</span></span>
<span data-ttu-id="6f36b-103">Umożliwia określenie lub zresetowanie pliku manifestu używanego przez konsolidatora podczas tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="6f36b-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f36b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f36b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f36b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f36b-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="6f36b-106">Nazwa pliku manifestu, którego zawartość jest umieszczana w obiekcie blob zasobów Win32.</span><span class="sxs-lookup"><span data-stu-id="6f36b-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f36b-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="6f36b-107">Return Value</span></span>  
 <span data-ttu-id="6f36b-108">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6f36b-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f36b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f36b-109">Remarks</span></span>  
 <span data-ttu-id="6f36b-110">Wywołaj to przed pytaniem o Win32ResBlob.</span><span class="sxs-lookup"><span data-stu-id="6f36b-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="6f36b-111">Wartość parametru `pszFile` jest nazwą pliku manifestu, którego zawartość jest odczytywana i umieszczana w zasobach Win32 z IDENTYFIKATORem RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="6f36b-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="6f36b-112">Gdy wywoływana przy użyciu parametru o wartości NULL, każdy poprzednio odczytany manifest jest czyszczony.</span><span class="sxs-lookup"><span data-stu-id="6f36b-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="6f36b-113">Umożliwia to jednemu resetowaniu stanu konsolidatora do czasu inicjacji.</span><span class="sxs-lookup"><span data-stu-id="6f36b-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f36b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6f36b-114">Requirements</span></span>  
 <span data-ttu-id="6f36b-115">Wymaga aLink. h</span><span class="sxs-lookup"><span data-stu-id="6f36b-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f36b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f36b-116">See also</span></span>

- [<span data-ttu-id="6f36b-117">IALink3, interfejs</span><span class="sxs-lookup"><span data-stu-id="6f36b-117">IALink3 Interface</span></span>](ialink3-interface.md)
- [<span data-ttu-id="6f36b-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="6f36b-118">ALink API</span></span>](index.md)
- [<span data-ttu-id="6f36b-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="6f36b-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6f36b-120">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="6f36b-120">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
