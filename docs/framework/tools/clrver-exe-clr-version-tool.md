---
title: Clrver.exe (Narzędzie wersji środowiska CLR)
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28ac90eadcc7a13fe946aabf17973ebc602c9d4a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084599"
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="bcc66-102">Clrver.exe (Narzędzie wersji środowiska CLR)</span><span class="sxs-lookup"><span data-stu-id="bcc66-102">Clrver.exe (CLR Version Tool)</span></span>
<span data-ttu-id="bcc66-103">Narzędzia wersji środowiska CLR (Clrver.exe) raportuje wszystkie wersje środowiska uruchomieniowego języka wspólnego (CLR) zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bcc66-103">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="bcc66-104">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bcc66-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="bcc66-105">Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7).</span><span class="sxs-lookup"><span data-stu-id="bcc66-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="bcc66-106">Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="bcc66-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="bcc66-107">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="bcc66-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc66-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="bcc66-108">Syntax</span></span>  
  
```  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="bcc66-109">Opcje</span><span class="sxs-lookup"><span data-stu-id="bcc66-109">Options</span></span>  
  
|<span data-ttu-id="bcc66-110">Opcja</span><span class="sxs-lookup"><span data-stu-id="bcc66-110">Option</span></span>|<span data-ttu-id="bcc66-111">Opis</span><span class="sxs-lookup"><span data-stu-id="bcc66-111">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="bcc66-112">Wyświetla wszystkie procesy na komputerze używające środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="bcc66-112">Displays all processes on the computer that are using the CLR.</span></span>|  
|*<span data-ttu-id="bcc66-113">Identyfikator PID</span><span class="sxs-lookup"><span data-stu-id="bcc66-113">pid</span></span>*|<span data-ttu-id="bcc66-114">Wyświetla wersje środowiska CLR używane przez proces, który ma określony identyfikator procesu (PID).</span><span class="sxs-lookup"><span data-stu-id="bcc66-114">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="bcc66-115">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="bcc66-115">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcc66-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bcc66-116">Remarks</span></span>  
 <span data-ttu-id="bcc66-117">Wywołanie procesu Clrver.exe bez opcji powoduje wyświetlenie wszystkich zainstalowanych wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="bcc66-117">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="bcc66-118">Jeśli określisz PID dla innego użytkownika, musisz mieć uprawnienia administracyjne, aby uzyskać informacje o wersji.</span><span class="sxs-lookup"><span data-stu-id="bcc66-118">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bcc66-119">W systemie Windows Vista i nowszych Kontrola konta użytkownika (UAC) określa uprawnienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bcc66-119">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="bcc66-120">Jeśli jesteś członkiem wbudowanej grupy Administratorzy, masz przypisane dwa tokeny dostępu w czasie wykonywania: token dostępu użytkownika standardowego i token dostępu administratora.</span><span class="sxs-lookup"><span data-stu-id="bcc66-120">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="bcc66-121">Domyślnie jesteś w roli użytkownika standardowego.</span><span class="sxs-lookup"><span data-stu-id="bcc66-121">By default, you are in the standard user role.</span></span> <span data-ttu-id="bcc66-122">Aby wykonać kod wymagający uprawnień administracyjnych, musisz najpierw podwyższenie swoje uprawnienia z użytkownika standardowego do administratora.</span><span class="sxs-lookup"><span data-stu-id="bcc66-122">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="bcc66-123">Możesz to zrobić podczas uruchamiania wiersza polecenia, klikając prawym przyciskiem myszy ikonę wiersza polecenia i wskazując, że chcesz procować jako administrator.</span><span class="sxs-lookup"><span data-stu-id="bcc66-123">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="bcc66-124">Próba ustalenia wersji środowiska CLR dla procesów SYSTEM, USŁUGA LOKALNA i USŁUGA SIECIOWA powoduje wyświetlenie komunikatu, że PID nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="bcc66-124">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bcc66-125">Przykłady</span><span class="sxs-lookup"><span data-stu-id="bcc66-125">Examples</span></span>  
 <span data-ttu-id="bcc66-126">Następujące polecenie wyświetla listę wszystkich wersji środowiska CLR zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bcc66-126">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="bcc66-127">Następujące polecenie wyświetla wersję środowiska CLR używanego przez proces 128.</span><span class="sxs-lookup"><span data-stu-id="bcc66-127">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="bcc66-128">Następujące polecenie wyświetla wszystkie zarządzane procesy i wersję używanego przez nie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="bcc66-128">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="bcc66-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bcc66-129">See also</span></span>

- [<span data-ttu-id="bcc66-130">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="bcc66-130">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="bcc66-131">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="bcc66-131">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
