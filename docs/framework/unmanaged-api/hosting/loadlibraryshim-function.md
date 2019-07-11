---
title: LoadLibraryShim — Funkcja
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03bc5584d24efa790989f93426251f9f38e65904
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768524"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="eb70c-102">LoadLibraryShim — Funkcja</span><span class="sxs-lookup"><span data-stu-id="eb70c-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="eb70c-103">Ładuje określoną wersję biblioteki dll, który znajduje się w pakiet redystrybucyjny programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb70c-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="eb70c-104">Ta funkcja jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="eb70c-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="eb70c-105">Użyj [iclrruntimeinfo::LoadLibrary —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="eb70c-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb70c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb70c-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb70c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb70c-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="eb70c-108">[in] Ciąg zakończony zerem, który reprezentuje nazwę biblioteki DLL, należy załadować z biblioteki programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb70c-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="eb70c-109">[in] Ciąg zakończony zerem, który reprezentuje wersję biblioteki DLL do załadowania.</span><span class="sxs-lookup"><span data-stu-id="eb70c-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="eb70c-110">Jeśli `szVersion` jest null, wersja wybrane do ładowania jest najnowsza wersja określonej biblioteki dll, która jest mniejsza niż w wersji 4.</span><span class="sxs-lookup"><span data-stu-id="eb70c-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="eb70c-111">Oznacza to, że wszystkie wersje, równa lub większa niż w wersji 4 są ignorowane w przypadku `szVersion` ma wartość null, a jeśli nie wersji mniejsze niż w wersji 4 jest zainstalowana, biblioteki DLL nie można załadować.</span><span class="sxs-lookup"><span data-stu-id="eb70c-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="eb70c-112">To, aby upewnić się, że instalacja programu .NET Framework 4 nie ma wpływu na istniejące aplikacje lub składniki.</span><span class="sxs-lookup"><span data-stu-id="eb70c-112">This is to ensure that installation of the .NET Framework 4 does not affect pre-existing applications or components.</span></span> <span data-ttu-id="eb70c-113">Zobacz wpis [SxS In-Proc i migracji — Szybki Start](https://go.microsoft.com/fwlink/?LinkId=200329) w blogu zespołu programu CLR.</span><span class="sxs-lookup"><span data-stu-id="eb70c-113">See the entry [In-Proc SxS and Migration Quick Start](https://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="eb70c-114">Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="eb70c-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="eb70c-115">[out] Wskaźnik do uchwytu modułu.</span><span class="sxs-lookup"><span data-stu-id="eb70c-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb70c-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="eb70c-116">Return Value</span></span>  
 <span data-ttu-id="eb70c-117">Ta metoda zwraca standardowe kody błędów Component Object Model (COM), zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="eb70c-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="eb70c-118">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="eb70c-118">Return code</span></span>|<span data-ttu-id="eb70c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="eb70c-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="eb70c-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="eb70c-120">S_OK</span></span>|<span data-ttu-id="eb70c-121">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="eb70c-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="eb70c-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="eb70c-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="eb70c-123">Trwa ładowanie `szDllName` wymaga ładowania, środowisko uruchomieniowe języka wspólnego (CLR) i wymaganej wersji środowiska CLR nie może zostać załadowany.</span><span class="sxs-lookup"><span data-stu-id="eb70c-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb70c-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb70c-124">Remarks</span></span>  
 <span data-ttu-id="eb70c-125">Ta funkcja jest używana do ładowania bibliotek DLL, które znajdują się w pakiet redystrybucyjny programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb70c-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="eb70c-126">Nie ładuje dll wygenerowaną przez użytkowników.</span><span class="sxs-lookup"><span data-stu-id="eb70c-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb70c-127">Począwszy od programu .NET Framework w wersji 2.0, ładowanie Fusion.dll powoduje, że CLR do załadowania.</span><span class="sxs-lookup"><span data-stu-id="eb70c-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="eb70c-128">Jest to spowodowane funkcje w Fusion.dll są teraz otoki, którego implementacje są dostarczane przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="eb70c-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb70c-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb70c-129">Requirements</span></span>  
 <span data-ttu-id="eb70c-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb70c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb70c-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eb70c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb70c-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb70c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb70c-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb70c-133">See also</span></span>

- [<span data-ttu-id="eb70c-134">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="eb70c-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
