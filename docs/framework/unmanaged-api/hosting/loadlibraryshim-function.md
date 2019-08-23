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
ms.openlocfilehash: 9ab44ce8f51620d83084d1dd16e98b2b310feb76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968937"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="3b3c1-102">LoadLibraryShim — Funkcja</span><span class="sxs-lookup"><span data-stu-id="3b3c1-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="3b3c1-103">Ładuje określoną wersję biblioteki DLL dołączoną do pakietu redystrybucyjnego .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="3b3c1-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="3b3c1-105">Zamiast tego użyj metody [ICLRRuntimeInfo:: LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3b3c1-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b3c1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b3c1-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b3c1-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b3c1-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="3b3c1-108">podczas Ciąg zakończony zerem, który reprezentuje nazwę biblioteki DLL, która ma zostać załadowana z biblioteki .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="3b3c1-109">podczas Ciąg zakończony zerem, który reprezentuje wersję biblioteki DLL, która ma zostać załadowana.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="3b3c1-110">Jeśli `szVersion` ma wartość null, wybrana wersja do załadowania to Najnowsza wersja określonej biblioteki DLL, która jest starsza niż wersja 4.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="3b3c1-111">Oznacza to, że wszystkie wersje, które są równe lub większe niż wersja 4 `szVersion` są ignorowane, jeśli ma wartość null, a jeśli nie jest zainstalowana wersja niższa niż 4, nie można załadować biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="3b3c1-112">Ma to na celu zapewnienie, że instalacja .NET Framework 4 nie ma wpływu na istniejące aplikacje lub składniki.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-112">This is to ensure that installation of the .NET Framework 4 does not affect pre-existing applications or components.</span></span> <span data-ttu-id="3b3c1-113">Zapoznaj się z wpisem [w procesie SxS i szybki start migracji](https://go.microsoft.com/fwlink/?LinkId=200329) w blogu zespołu CLR.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-113">See the entry [In-Proc SxS and Migration Quick Start](https://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="3b3c1-114">Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="3b3c1-115">określoną Wskaźnik do uchwytu modułu.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b3c1-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3b3c1-116">Return Value</span></span>  
 <span data-ttu-id="3b3c1-117">Ta metoda zwraca kody błędów standardowego Component Object Model (COM), jak zdefiniowano w WinError. h, oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="3b3c1-118">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="3b3c1-118">Return code</span></span>|<span data-ttu-id="3b3c1-119">Opis</span><span class="sxs-lookup"><span data-stu-id="3b3c1-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="3b3c1-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="3b3c1-120">S_OK</span></span>|<span data-ttu-id="3b3c1-121">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="3b3c1-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="3b3c1-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="3b3c1-123">Ładowanie `szDllName` wymaga załadowania środowiska uruchomieniowego języka wspólnego (CLR) i niezbędna wersja środowiska CLR nie może zostać załadowana.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b3c1-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b3c1-124">Remarks</span></span>  
 <span data-ttu-id="3b3c1-125">Ta funkcja służy do ładowania bibliotek DLL, które znajdują się w pakiecie redystrybucyjnym .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="3b3c1-126">Nie ładuje bibliotek DLL generowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b3c1-127">Począwszy od .NET Framework w wersji 2,0, wczytywanie pliku Fusion. dll powoduje załadowanie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="3b3c1-128">Jest to spowodowane tym, że funkcje w programie Fusion. dll są teraz otokami, których implementacje są udostępniane przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b3c1-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b3c1-129">Requirements</span></span>  
 <span data-ttu-id="3b3c1-130">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b3c1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b3c1-131">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3b3c1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3b3c1-132">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b3c1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b3c1-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b3c1-133">See also</span></span>

- [<span data-ttu-id="3b3c1-134">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="3b3c1-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
