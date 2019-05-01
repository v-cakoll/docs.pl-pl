---
title: Storeadm.exe (Narzędzie wydzielonej pamięci masowej)
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 906d9d4dfd1c1082a4b49b7143f590967dcc7fd0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61919378"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="ad79c-102">Storeadm.exe (Narzędzie wydzielonej pamięci masowej)</span><span class="sxs-lookup"><span data-stu-id="ad79c-102">Storeadm.exe (Isolated Storage Tool)</span></span>
<span data-ttu-id="ad79c-103">Narzędzie Isolated Storage obsługujące izolowane magazyny wyświetla lub usuwa wszystkie istniejące magazyny bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ad79c-103">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="ad79c-104">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ad79c-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="ad79c-105">Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7).</span><span class="sxs-lookup"><span data-stu-id="ad79c-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="ad79c-106">Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="ad79c-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="ad79c-107">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ad79c-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad79c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad79c-108">Syntax</span></span>  
  
```  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad79c-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad79c-109">Parameters</span></span>  
  
|<span data-ttu-id="ad79c-110">Opcja</span><span class="sxs-lookup"><span data-stu-id="ad79c-110">Option</span></span>|<span data-ttu-id="ad79c-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ad79c-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ad79c-112">**/ h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="ad79c-112">**/h**[**elp**]</span></span>|<span data-ttu-id="ad79c-113">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="ad79c-113">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="ad79c-114">**/ list**</span><span class="sxs-lookup"><span data-stu-id="ad79c-114">**/list**</span></span>|<span data-ttu-id="ad79c-115">Wyświetla wszystkie istniejące magazyny bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ad79c-115">Displays all existing stores for the current user.</span></span> <span data-ttu-id="ad79c-116">W tym magazyny dla wszystkich aplikacji lub zespołów wykonanych przez tego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ad79c-116">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="ad79c-117">**/ machine**</span><span class="sxs-lookup"><span data-stu-id="ad79c-117">**/machine**</span></span>|<span data-ttu-id="ad79c-118">Wybiera magazyn komputera.</span><span class="sxs-lookup"><span data-stu-id="ad79c-118">Selects the machine store.</span></span> <span data-ttu-id="ad79c-119">Użyj tej opcji z **/list** lub **/usunąć** opcję, aby określić, czy akcja ma mieć zastosowanie do magazynu komputera.</span><span class="sxs-lookup"><span data-stu-id="ad79c-119">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="ad79c-120">Nowość w programie .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="ad79c-120">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="ad79c-121">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="ad79c-121">**/quiet**</span></span>|<span data-ttu-id="ad79c-122">Określa tryb cichy; pomija informacyjne dane wyjściowe, tak aby były wyświetlane tylko komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="ad79c-122">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="ad79c-123">**/remove**</span><span class="sxs-lookup"><span data-stu-id="ad79c-123">**/remove**</span></span>|<span data-ttu-id="ad79c-124">Trwale usuwa wszystkie istniejące magazyny bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ad79c-124">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="ad79c-125">**/ roaming**</span><span class="sxs-lookup"><span data-stu-id="ad79c-125">**/roaming**</span></span>|<span data-ttu-id="ad79c-126">Wybiera mobilny magazyn.</span><span class="sxs-lookup"><span data-stu-id="ad79c-126">Selects the roaming store.</span></span> <span data-ttu-id="ad79c-127">Użyj tej opcji z **/list** lub **/usunąć** opcji, aby określić, czy akcja ma mieć zastosowanie do mobilnego magazynu.</span><span class="sxs-lookup"><span data-stu-id="ad79c-127">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="ad79c-128">**/?**</span><span class="sxs-lookup"><span data-stu-id="ad79c-128">**/?**</span></span>|<span data-ttu-id="ad79c-129">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="ad79c-129">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad79c-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad79c-130">Remarks</span></span>  
 <span data-ttu-id="ad79c-131">Uruchamianie Storeadm.exe z wiersza polecenia bez określenia opcji wyświetla składnię i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="ad79c-131">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="ad79c-132">**/List** i **/usunąć** opcje są zwykle używane pojedynczo; Jednakże, jeśli nie określono dwie lub więcej opcji one wykonywane w kolejności, w jakiej są wyświetlane w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="ad79c-132">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="ad79c-133">Aplikacje można zapisać do jednego z dwóch magazynów użytkownika lub do magazynu komputera:</span><span class="sxs-lookup"><span data-stu-id="ad79c-133">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
- <span data-ttu-id="ad79c-134">Magazyn lokalny istnieje w lokalizacji, która może się nie korzystać z roamingu (w systemie operacyjnym Windows 2000 i nowszych), nawet jeśli roaming danych jest włączone dla danego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ad79c-134">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
- <span data-ttu-id="ad79c-135">Mobilny magazyn istnieje w lokalizacji, która jest w stanie korzystać z roamingu, ale tylko w przypadku, gdy roaming jest włączony dla użytkownika za pośrednictwem administracji systemu Windows NT.</span><span class="sxs-lookup"><span data-stu-id="ad79c-135">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
- <span data-ttu-id="ad79c-136">Magazyn komputera jest wspólny dla wszystkich użytkowników komputera i jest przechowywany we wspólnym katalogu na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ad79c-136">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad79c-137">Magazyn komputera jest nowy w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="ad79c-137">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="ad79c-138">To, czy roaming jest faktycznie włączony dla użytkownika, nie wpływa na administrację Storeadm.exe.</span><span class="sxs-lookup"><span data-stu-id="ad79c-138">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="ad79c-139">Uruchomienie narzędzia bez żadnych opcji zastosuje wszystkie akcje do magazynu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="ad79c-139">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="ad79c-140">Uruchomienie narzędzia z **/ roaming** opcji zastosuje wszystkie akcje do magazynu który może korzystać z roamingu.</span><span class="sxs-lookup"><span data-stu-id="ad79c-140">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="ad79c-141">Uruchomienie narzędzia z **/machine** opcji zastosuje wszystkie akcje do magazynu komputera.</span><span class="sxs-lookup"><span data-stu-id="ad79c-141">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad79c-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad79c-142">See also</span></span>

- [<span data-ttu-id="ad79c-143">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="ad79c-143">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="ad79c-144">Wydzielona pamięć masowa</span><span class="sxs-lookup"><span data-stu-id="ad79c-144">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
- [<span data-ttu-id="ad79c-145">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="ad79c-145">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
