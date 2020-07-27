---
title: Clrver.exe (Narzędzie wersji środowiska CLR)
description: Przejrzyj Clrver.exe, narzędzie wersji środowiska CLR. To narzędzie raportuje wszystkie zainstalowane wersje środowiska uruchomieniowego języka wspólnego (CLR) na komputerze.
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
ms.openlocfilehash: e914034819418df00438c454e209e6c86779ba3c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167279"
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="5db9c-104">Clrver.exe (Narzędzie wersji środowiska CLR)</span><span class="sxs-lookup"><span data-stu-id="5db9c-104">Clrver.exe (CLR Version Tool)</span></span>
<span data-ttu-id="5db9c-105">Narzędzia wersji środowiska CLR (Clrver.exe) raportuje wszystkie wersje środowiska uruchomieniowego języka wspólnego (CLR) zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5db9c-105">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="5db9c-106">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5db9c-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="5db9c-107">Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="5db9c-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="5db9c-108">Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="5db9c-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="5db9c-109">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="5db9c-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5db9c-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="5db9c-110">Syntax</span></span>  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="5db9c-111">Opcje</span><span class="sxs-lookup"><span data-stu-id="5db9c-111">Options</span></span>  
  
|<span data-ttu-id="5db9c-112">Opcja</span><span class="sxs-lookup"><span data-stu-id="5db9c-112">Option</span></span>|<span data-ttu-id="5db9c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="5db9c-113">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="5db9c-114">Wyświetla wszystkie procesy na komputerze używające środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5db9c-114">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="5db9c-115">*identyfikatora*</span><span class="sxs-lookup"><span data-stu-id="5db9c-115">*pid*</span></span>|<span data-ttu-id="5db9c-116">Wyświetla wersje środowiska CLR używane przez proces, który ma określony identyfikator procesu (PID).</span><span class="sxs-lookup"><span data-stu-id="5db9c-116">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="5db9c-117">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="5db9c-117">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5db9c-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5db9c-118">Remarks</span></span>  
 <span data-ttu-id="5db9c-119">Wywołanie procesu Clrver.exe bez opcji powoduje wyświetlenie wszystkich zainstalowanych wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5db9c-119">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="5db9c-120">Jeśli określisz PID dla innego użytkownika, musisz mieć uprawnienia administracyjne, aby uzyskać informacje o wersji.</span><span class="sxs-lookup"><span data-stu-id="5db9c-120">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5db9c-121">W systemie Windows Vista i nowszych Kontrola konta użytkownika (UAC) określa uprawnienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5db9c-121">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="5db9c-122">Jeśli jesteś członkiem wbudowanej grupy Administratorzy, masz przypisane dwa tokeny dostępu w czasie wykonywania: token dostępu użytkownika standardowego i token dostępu administratora.</span><span class="sxs-lookup"><span data-stu-id="5db9c-122">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="5db9c-123">Domyślnie jesteś w roli użytkownika standardowego.</span><span class="sxs-lookup"><span data-stu-id="5db9c-123">By default, you are in the standard user role.</span></span> <span data-ttu-id="5db9c-124">Aby wykonać kod wymagający uprawnień administracyjnych, musisz najpierw podwyższenie swoje uprawnienia z użytkownika standardowego do administratora.</span><span class="sxs-lookup"><span data-stu-id="5db9c-124">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="5db9c-125">Możesz to zrobić podczas uruchamiania wiersza polecenia, klikając prawym przyciskiem myszy ikonę wiersza polecenia i wskazując, że chcesz procować jako administrator.</span><span class="sxs-lookup"><span data-stu-id="5db9c-125">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="5db9c-126">Próba ustalenia wersji środowiska CLR dla procesów SYSTEM, USŁUGA LOKALNA i USŁUGA SIECIOWA powoduje wyświetlenie komunikatu, że PID nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="5db9c-126">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5db9c-127">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5db9c-127">Examples</span></span>  
 <span data-ttu-id="5db9c-128">Następujące polecenie wyświetla listę wszystkich wersji środowiska CLR zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5db9c-128">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="5db9c-129">Następujące polecenie wyświetla wersję środowiska CLR używanego przez proces 128.</span><span class="sxs-lookup"><span data-stu-id="5db9c-129">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="5db9c-130">Następujące polecenie wyświetla wszystkie zarządzane procesy i wersję używanego przez nie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5db9c-130">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="5db9c-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5db9c-131">See also</span></span>

- [<span data-ttu-id="5db9c-132">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="5db9c-132">Tools</span></span>](index.md)
- [<span data-ttu-id="5db9c-133">Wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="5db9c-133">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
