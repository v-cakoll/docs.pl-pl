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
ms.openlocfilehash: 46e846eaf92835fb2a9130b85ed20749934ca5a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715712"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="4779e-102">Storeadm.exe (Narzędzie wydzielonej pamięci masowej)</span><span class="sxs-lookup"><span data-stu-id="4779e-102">Storeadm.exe (Isolated Storage Tool)</span></span>
<span data-ttu-id="4779e-103">Narzędzie Isolated Storage obsługujące izolowane magazyny wyświetla lub usuwa wszystkie istniejące magazyny bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4779e-103">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="4779e-104">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4779e-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="4779e-105">Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="4779e-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="4779e-106">Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="4779e-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="4779e-107">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4779e-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4779e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="4779e-108">Syntax</span></span>  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="4779e-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="4779e-109">Parameters</span></span>  
  
|<span data-ttu-id="4779e-110">Opcja</span><span class="sxs-lookup"><span data-stu-id="4779e-110">Option</span></span>|<span data-ttu-id="4779e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="4779e-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4779e-112">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="4779e-112">**/h**[**elp**]</span></span>|<span data-ttu-id="4779e-113">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="4779e-113">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="4779e-114">**/lista**</span><span class="sxs-lookup"><span data-stu-id="4779e-114">**/list**</span></span>|<span data-ttu-id="4779e-115">Wyświetla wszystkie istniejące magazyny bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4779e-115">Displays all existing stores for the current user.</span></span> <span data-ttu-id="4779e-116">W tym magazyny dla wszystkich aplikacji lub zespołów wykonanych przez tego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4779e-116">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="4779e-117">**/maszyna**</span><span class="sxs-lookup"><span data-stu-id="4779e-117">**/machine**</span></span>|<span data-ttu-id="4779e-118">Wybiera magazyn komputera.</span><span class="sxs-lookup"><span data-stu-id="4779e-118">Selects the machine store.</span></span> <span data-ttu-id="4779e-119">Użyj tej opcji z **/list** lub **/remove** opcji, aby określić, że akcja powinna mieć zastosowanie do magazynu komputera.</span><span class="sxs-lookup"><span data-stu-id="4779e-119">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="4779e-120">Nowość w programie .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="4779e-120">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="4779e-121">**/cichy**</span><span class="sxs-lookup"><span data-stu-id="4779e-121">**/quiet**</span></span>|<span data-ttu-id="4779e-122">Określa tryb cichy; pomija informacyjne dane wyjściowe, tak aby były wyświetlane tylko komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="4779e-122">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="4779e-123">**/usuń**</span><span class="sxs-lookup"><span data-stu-id="4779e-123">**/remove**</span></span>|<span data-ttu-id="4779e-124">Trwale usuwa wszystkie istniejące magazyny bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4779e-124">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="4779e-125">**/roaming**</span><span class="sxs-lookup"><span data-stu-id="4779e-125">**/roaming**</span></span>|<span data-ttu-id="4779e-126">Wybiera mobilny magazyn.</span><span class="sxs-lookup"><span data-stu-id="4779e-126">Selects the roaming store.</span></span> <span data-ttu-id="4779e-127">Użyj tej opcji z **/list** lub **/remove** opcje, aby określić, że akcja powinna mieć zastosowanie do magazynu mobilnego.</span><span class="sxs-lookup"><span data-stu-id="4779e-127">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="4779e-128">**/?**</span><span class="sxs-lookup"><span data-stu-id="4779e-128">**/?**</span></span>|<span data-ttu-id="4779e-129">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="4779e-129">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4779e-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4779e-130">Remarks</span></span>  
 <span data-ttu-id="4779e-131">Uruchamianie Storeadm.exe z wiersza polecenia bez określenia opcji wyświetla składnię i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="4779e-131">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="4779e-132">Opcje **/list** i **/remove** są zwykle używane po jednym naraz; jednak jeśli określono dwie lub więcej opcji, zostaną one wykonane w kolejności, w jakiej pojawiają się w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="4779e-132">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="4779e-133">Aplikacje można zapisać do jednego z dwóch magazynów użytkownika lub do magazynu komputera:</span><span class="sxs-lookup"><span data-stu-id="4779e-133">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
- <span data-ttu-id="4779e-134">Lokalny magazyn istnieje w lokalizacji, która jest gwarantowana, aby nie wędrować (w systemie Windows 2000 i nowszych), nawet jeśli roaming danych użytkownika jest włączony dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4779e-134">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
- <span data-ttu-id="4779e-135">Sklep mobilny istnieje w lokalizacji, która może się przemieszczać, ale może to zrobić tylko wtedy, gdy roaming jest włączony dla użytkownika za pośrednictwem administracji systemu Windows NT.</span><span class="sxs-lookup"><span data-stu-id="4779e-135">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
- <span data-ttu-id="4779e-136">Magazyn komputera jest wspólny dla wszystkich użytkowników komputera i jest przechowywany we wspólnym katalogu na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4779e-136">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4779e-137">Magazyn komputera jest nowy w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="4779e-137">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="4779e-138">To, czy roaming jest faktycznie włączony dla użytkownika, nie wpływa na administrację Storeadm.exe.</span><span class="sxs-lookup"><span data-stu-id="4779e-138">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="4779e-139">Uruchomienie narzędzia bez żadnych opcji zastosuje wszystkie akcje do magazynu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="4779e-139">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="4779e-140">Uruchomienie narzędzia z opcją **/roaming** stosuje wszystkie akcje do magazynu, który jest w stanie wędrować.</span><span class="sxs-lookup"><span data-stu-id="4779e-140">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="4779e-141">Uruchamianie narzędzia za pomocą opcji **/machine** powoduje zastosowanie wszystkich akcji do magazynu maszyn.</span><span class="sxs-lookup"><span data-stu-id="4779e-141">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4779e-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4779e-142">See also</span></span>

- [<span data-ttu-id="4779e-143">narzędzia</span><span class="sxs-lookup"><span data-stu-id="4779e-143">Tools</span></span>](index.md)
- [<span data-ttu-id="4779e-144">Izolowany magazyn</span><span class="sxs-lookup"><span data-stu-id="4779e-144">Isolated Storage</span></span>](../../standard/io/isolated-storage.md)
- [<span data-ttu-id="4779e-145">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="4779e-145">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
