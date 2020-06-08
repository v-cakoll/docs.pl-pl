---
title: ICorProfilerInfo::GetAppDomainInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 5e5510ec098b2c1aa3b768830b812328287fd31a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503032"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="de5df-102">ICorProfilerInfo::GetAppDomainInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="de5df-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="de5df-103">Akceptuje identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de5df-103">Accepts an application domain ID.</span></span> <span data-ttu-id="de5df-104">Zwraca nazwę domeny aplikacji i identyfikator procesu, który go zawiera.</span><span class="sxs-lookup"><span data-stu-id="de5df-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de5df-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="de5df-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de5df-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="de5df-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="de5df-107">podczas Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de5df-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="de5df-108">podczas Długość (w znakach) `szName` buforu powrotu.</span><span class="sxs-lookup"><span data-stu-id="de5df-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="de5df-109">określoną Wskaźnik do łącznej długości znaku nazwy domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de5df-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="de5df-110">określoną Bufor znaków udostępniany przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="de5df-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="de5df-111">Gdy metoda zwraca, `szName` będzie zawierać pełną lub częściową nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de5df-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="de5df-112">określoną Wskaźnik do identyfikatora procesu, który zawiera domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de5df-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de5df-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de5df-113">Remarks</span></span>  
 <span data-ttu-id="de5df-114">Po powrocie tej metody należy sprawdzić, czy `szName` bufor jest wystarczająco duży, aby pomieścić pełną nazwę domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de5df-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="de5df-115">W tym celu należy porównać wartość wskazującą wartość `pcchName` `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="de5df-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="de5df-116">Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName` , Przydziel większy `szName` bufor, zaktualizuj `cchName` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetAppDomainInfo` .</span><span class="sxs-lookup"><span data-stu-id="de5df-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="de5df-117">Alternatywnie, można najpierw wywołać `GetAppDomainInfo` z buforem o zerowej długości, `szName` Aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="de5df-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="de5df-118">Następnie można ustawić rozmiar buforu na wartość zwracaną w `pcchName` i `GetAppDomainInfo` ponownie wywołać.</span><span class="sxs-lookup"><span data-stu-id="de5df-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de5df-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de5df-119">Requirements</span></span>  
 <span data-ttu-id="de5df-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de5df-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de5df-121">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="de5df-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="de5df-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="de5df-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de5df-123">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de5df-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de5df-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de5df-124">See also</span></span>

- [<span data-ttu-id="de5df-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="de5df-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="de5df-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="de5df-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="de5df-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="de5df-127">Profiling</span></span>](index.md)
