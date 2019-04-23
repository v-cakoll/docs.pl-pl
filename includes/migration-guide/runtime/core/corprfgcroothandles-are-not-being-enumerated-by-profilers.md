---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981650"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="98205-101">Nie są wyliczane COR_PRF_GC_ROOT_HANDLEs przez profilery</span><span class="sxs-lookup"><span data-stu-id="98205-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="98205-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="98205-102">Details</span></span>|<span data-ttu-id="98205-103">W v4.5.1 .NET Framework, interfejsie API profilowania <code>RootReferences2()</code> niepoprawnie nigdy nie zwraca <code>COR_PRF_GC_ROOT_HANDLE</code> (są zwracane w postaci <code>COR_PRF_GC_ROOT_OTHER</code> zamiast).</span><span class="sxs-lookup"><span data-stu-id="98205-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="98205-104">Ten problem jest rozwiązany, począwszy od programu .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="98205-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="98205-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="98205-105">Suggestion</span></span>|<span data-ttu-id="98205-106">Ten problem został rozwiązany w .NET Framework 4.6 i może zostać zlikwidowane przez uaktualnienie do wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="98205-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="98205-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="98205-107">Scope</span></span>|<span data-ttu-id="98205-108">Mały</span><span class="sxs-lookup"><span data-stu-id="98205-108">Minor</span></span>|
|<span data-ttu-id="98205-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="98205-109">Version</span></span>|<span data-ttu-id="98205-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="98205-110">4.5.1</span></span>|
|<span data-ttu-id="98205-111">Typ</span><span class="sxs-lookup"><span data-stu-id="98205-111">Type</span></span>|<span data-ttu-id="98205-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="98205-112">Runtime</span></span>|
