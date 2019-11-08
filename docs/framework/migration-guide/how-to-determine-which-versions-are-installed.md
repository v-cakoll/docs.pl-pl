---
title: Ustal, które wersje .NET Framework są zainstalowane
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: b860aac01780acb67c53e822eff478b78198996b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738193"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="ba310-102">Instrukcje: Określanie, które wersje .NET Framework są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="ba310-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="ba310-103">Użytkownicy mogą [instalować](../install/index.md) i uruchamiać wiele wersji .NET Framework na swoich komputerach.</span><span class="sxs-lookup"><span data-stu-id="ba310-103">Users can [install](../install/index.md) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="ba310-104">Podczas opracowywania lub wdrażania aplikacji może być konieczne, aby wiedzieć, które wersje .NET Framework są zainstalowane na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ba310-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span>

<span data-ttu-id="ba310-105">.NET Framework składa się z dwóch głównych składników, które są osobno dla wersji:</span><span class="sxs-lookup"><span data-stu-id="ba310-105">The .NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="ba310-106">Zestaw zestawów, które są kolekcjami typów i zasobów zapewniających funkcje dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ba310-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="ba310-107">.NET Framework i zestawy mają ten sam numer wersji.</span><span class="sxs-lookup"><span data-stu-id="ba310-107">The .NET Framework and assemblies share the same version number.</span></span>

- <span data-ttu-id="ba310-108">Środowisko uruchomieniowe języka wspólnego (CLR), które zarządza kodem aplikacji i go wykonuje.</span><span class="sxs-lookup"><span data-stu-id="ba310-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="ba310-109">Środowisko CLR jest identyfikowane za pomocą własnego numeru wersji (zobacz [wersje i zależności](versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="ba310-109">The CLR is identified by its own version number (see [Versions and dependencies](versions-and-dependencies.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="ba310-110">Każda nowa wersja programu .NET Framework zachowuje funkcje z poprzednich wersji i dodaje nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="ba310-110">Each new version of the .NET Framework retains features from the previous versions and adds new features.</span></span> <span data-ttu-id="ba310-111">Możesz ładować wiele wersji .NET Framework na jednym komputerze w tym samym czasie, co oznacza, że można zainstalować .NET Framework bez konieczności odinstalowywania poprzednich wersji.</span><span class="sxs-lookup"><span data-stu-id="ba310-111">You can load multiple versions of the .NET Framework on a single computer at the same time, which means that you can install the .NET Framework without having to uninstall previous versions.</span></span> <span data-ttu-id="ba310-112">Ogólnie rzecz biorąc nie należy odinstalowywać poprzednich wersji .NET Framework, ponieważ używana aplikacja może zależeć od określonej wersji i może zostać przerwana, jeśli ta wersja zostanie usunięta.</span><span class="sxs-lookup"><span data-stu-id="ba310-112">In general, you shouldn't uninstall previous versions of the .NET Framework, because an application you use may depend on a specific version and may break if that version is removed.</span></span>
>
> <span data-ttu-id="ba310-113">Istnieje różnica między wersją .NET Framework i wersją środowiska CLR:</span><span class="sxs-lookup"><span data-stu-id="ba310-113">There is a difference between the .NET Framework version and the CLR version:</span></span>
>
> - <span data-ttu-id="ba310-114">Wersja .NET Framework jest oparta na zestawie zestawów, które tworzą bibliotekę klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba310-114">The .NET Framework version is based on the set of assemblies that form the .NET Framework class library.</span></span> <span data-ttu-id="ba310-115">Na przykład .NET Framework wersje obejmują 4,5, 4.6.1 i 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="ba310-115">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>
> - <span data-ttu-id="ba310-116">Wersja środowiska CLR jest oparta na czasie wykonywania, w którym wykonywane są .NET Framework aplikacje.</span><span class="sxs-lookup"><span data-stu-id="ba310-116">The CLR version is based on the runtime on which .NET Framework applications execute.</span></span> <span data-ttu-id="ba310-117">Jedna wersja środowiska CLR obsługuje zazwyczaj wiele wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba310-117">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="ba310-118">Na przykład środowisko CLR w wersji 4.0.30319. *XXXXX* obsługuje .NET Framework wersje od 4 do 4.5.2, gdzie *XXXXX* jest mniejszy niż 42000, a środowisko CLR w wersji 4.0.30319.42000 obsługuje wersje .NET Framework, które zaczynają się od .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="ba310-118">For example, CLR version 4.0.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2, where *xxxxx* is less than 42000, and CLR version 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>
>
> <span data-ttu-id="ba310-119">Aby uzyskać więcej informacji na temat wersji, zobacz [.NET Framework wersje i zależności](versions-and-dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="ba310-119">For more information about versions, see [.NET Framework versions and dependencies](versions-and-dependencies.md).</span></span>

<span data-ttu-id="ba310-120">Rejestr zawiera listę wersji .NET Framework zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ba310-120">The registry contains a list of the .NET Framework versions installed on a computer.</span></span> <span data-ttu-id="ba310-121">Możesz użyć Edytora rejestru, aby wyświetlić rejestr lub zbadać go za pomocą kodu:</span><span class="sxs-lookup"><span data-stu-id="ba310-121">You can either use the Registry Editor to view the registry or query it with code:</span></span>

- <span data-ttu-id="ba310-122">Znajdź nowsze wersje .NET Framework (4,5 i nowsze):</span><span class="sxs-lookup"><span data-stu-id="ba310-122">Find newer .NET Framework versions (4.5 and later):</span></span>

  - [<span data-ttu-id="ba310-123">Znajdź .NET Framework wersje przy użyciu Edytora rejestru</span><span class="sxs-lookup"><span data-stu-id="ba310-123">Use the Registry Editor to find .NET Framework versions</span></span>](#net_b)
  - [<span data-ttu-id="ba310-124">Używanie kodu do wysyłania zapytań do rejestru w przypadku wersji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ba310-124">Use code to query the registry for .NET Framework versions</span></span>](#net_d)
  - [<span data-ttu-id="ba310-125">Używanie programu PowerShell do wykonywania zapytań dotyczących rejestru w przypadku wersji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ba310-125">Use PowerShell to query the registry for .NET Framework versions</span></span>](#ps_a)

- <span data-ttu-id="ba310-126">Znajdź starsze wersje .NET Framework (od 1 do 4):</span><span class="sxs-lookup"><span data-stu-id="ba310-126">Find older .NET Framework versions (1 through 4):</span></span>

  - [<span data-ttu-id="ba310-127">Znajdź .NET Framework wersje przy użyciu Edytora rejestru</span><span class="sxs-lookup"><span data-stu-id="ba310-127">Use the Registry Editor to find .NET Framework versions</span></span>](#net_a)
  - [<span data-ttu-id="ba310-128">Używanie kodu do wysyłania zapytań do rejestru w przypadku wersji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ba310-128">Use code to query the registry for .NET Framework versions</span></span>](#net_c)

<span data-ttu-id="ba310-129">Aby uzyskać listę wersji środowiska CLR zainstalowanych na komputerze, użyj narzędzia lub kodu:</span><span class="sxs-lookup"><span data-stu-id="ba310-129">To get a list of the CLR versions installed on a computer, use a tool or code:</span></span>

- [<span data-ttu-id="ba310-130">Korzystanie z narzędzia Clrver</span><span class="sxs-lookup"><span data-stu-id="ba310-130">Use the Clrver tool</span></span>](#clr_a)
- [<span data-ttu-id="ba310-131">Użyj kodu, aby wykonać zapytanie dotyczące klasy środowiska</span><span class="sxs-lookup"><span data-stu-id="ba310-131">Use code to query the Environment class</span></span>](#clr_b)

<span data-ttu-id="ba310-132">Aby uzyskać informacje dotyczące wykrywania zainstalowanych aktualizacji dla każdej wersji .NET Framework, zobacz [How to: Określanie, które aktualizacje .NET Framework są zainstalowane](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="ba310-132">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="find-newer-net-framework-versions-45-and-later"></a><span data-ttu-id="ba310-133">Znajdź nowsze wersje .NET Framework (4,5 i nowsze)</span><span class="sxs-lookup"><span data-stu-id="ba310-133">Find newer .NET Framework versions (4.5 and later)</span></span>

<span data-ttu-id="ba310-134">Aby znaleźć informacje o wersji w rejestrze, można użyć Edytora rejestru lub programowo zbadać rejestr.</span><span class="sxs-lookup"><span data-stu-id="ba310-134">You can use Registry Editor to find version information in the registry, or you can query the registry programmatically.</span></span>

<a name="net_b"></a>

### <a name="use-registry-editor"></a><span data-ttu-id="ba310-135">Korzystanie z edytora rejestru</span><span class="sxs-lookup"><span data-stu-id="ba310-135">Use Registry Editor</span></span>

1. <span data-ttu-id="ba310-136">Z menu **Start** wybierz polecenie **Uruchom**, wpisz polecenie *regedit*, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ba310-136">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

     <span data-ttu-id="ba310-137">Musisz mieć poświadczenia administracyjne, aby uruchomić regedit.</span><span class="sxs-lookup"><span data-stu-id="ba310-137">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="ba310-138">W Edytorze rejestru Otwórz następujący podklucz: **rejestrze Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="ba310-138">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span></span> <span data-ttu-id="ba310-139">Jeśli **pełny** podklucz nie jest obecny, nie masz zainstalowanego .NET Framework 4,5 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="ba310-139">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ba310-140">Folder **instalacji programu .NET Framework** w rejestrze *nie rozpoczyna się* kropką.</span><span class="sxs-lookup"><span data-stu-id="ba310-140">The **NET Framework Setup** folder in the registry does *not* begin with a period.</span></span>

3. <span data-ttu-id="ba310-141">Wyszukaj wpis DWORD o nazwie **Release**.</span><span class="sxs-lookup"><span data-stu-id="ba310-141">Check for a DWORD entry named **Release**.</span></span> <span data-ttu-id="ba310-142">Jeśli istnieje, jest zainstalowana .NET Framework 4,5 lub nowsza.</span><span class="sxs-lookup"><span data-stu-id="ba310-142">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="ba310-143">Wartość jest kluczem wydania, który odpowiada określonej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba310-143">Its value is a release key that corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="ba310-144">Na przykład, wartość wpisu **zlecenia** to 378389, który jest kluczem wydania dla .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="ba310-144">In the following figure, for example, the value of the **Release** entry is 378389, which is the release key for .NET Framework 4.5.</span></span>

   <span data-ttu-id="ba310-145">![Wpis rejestru dla .NET Framework 4,5](./media/clr-installdir.png "Wpis rejestru dla .NET Framework 4,5")</span><span class="sxs-lookup"><span data-stu-id="ba310-145">![Registry entry for the .NET Framework 4.5](./media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

<span data-ttu-id="ba310-146">W poniższej tabeli wymieniono wartości DWORD **wydania** w poszczególnych systemach operacyjnych dla .NET Framework 4,5 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="ba310-146">The following table lists the value of the **Release** DWORD on individual operating systems for .NET Framework 4.5 and later versions.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|<span data-ttu-id="ba310-147">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ba310-147">.NET Framework version</span></span>|<span data-ttu-id="ba310-148">Wartość DWORD dotycząca wersji</span><span class="sxs-lookup"><span data-stu-id="ba310-148">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="ba310-149">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="ba310-149">.NET Framework 4.5</span></span>|<span data-ttu-id="ba310-150">Wszystkie systemy operacyjne Windows: 378389</span><span class="sxs-lookup"><span data-stu-id="ba310-150">All Windows operating systems: 378389</span></span>|
|<span data-ttu-id="ba310-151">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="ba310-151">.NET Framework 4.5.1</span></span>|<span data-ttu-id="ba310-152">W systemach Windows 8.1 i Windows Server 2012 R2:378675</span><span class="sxs-lookup"><span data-stu-id="ba310-152">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="ba310-153">We wszystkich innych systemach operacyjnych Windows: 378758</span><span class="sxs-lookup"><span data-stu-id="ba310-153">On all other Windows operating systems: 378758</span></span>|
|<span data-ttu-id="ba310-154">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="ba310-154">.NET Framework 4.5.2</span></span>|<span data-ttu-id="ba310-155">Wszystkie systemy operacyjne Windows: 379893</span><span class="sxs-lookup"><span data-stu-id="ba310-155">All Windows operating systems: 379893</span></span>|
|<span data-ttu-id="ba310-156">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="ba310-156">.NET Framework 4.6</span></span>|<span data-ttu-id="ba310-157">W systemie Windows 10:393295</span><span class="sxs-lookup"><span data-stu-id="ba310-157">On Windows 10: 393295</span></span><br /><span data-ttu-id="ba310-158">We wszystkich innych systemach operacyjnych Windows: 393297</span><span class="sxs-lookup"><span data-stu-id="ba310-158">On all other Windows operating systems: 393297</span></span>|
|<span data-ttu-id="ba310-159">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="ba310-159">.NET Framework 4.6.1</span></span>|<span data-ttu-id="ba310-160">W systemach aktualizacji systemu Windows 10 listopad: 394254</span><span class="sxs-lookup"><span data-stu-id="ba310-160">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="ba310-161">We wszystkich innych systemach operacyjnych Windows (w tym Windows 10): 394271</span><span class="sxs-lookup"><span data-stu-id="ba310-161">On all other Windows operating systems (including Windows 10): 394271</span></span>|
|<span data-ttu-id="ba310-162">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="ba310-162">.NET Framework 4.6.2</span></span>|<span data-ttu-id="ba310-163">W rocznicowej aktualizacji systemu Windows 10 i Windows Server 2016:394802</span><span class="sxs-lookup"><span data-stu-id="ba310-163">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="ba310-164">Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 394806</span><span class="sxs-lookup"><span data-stu-id="ba310-164">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span>|
|<span data-ttu-id="ba310-165">.NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="ba310-165">.NET Framework 4.7</span></span>|<span data-ttu-id="ba310-166">Aktualizacja systemu Windows 10 dla twórców: 460798</span><span class="sxs-lookup"><span data-stu-id="ba310-166">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="ba310-167">Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 460805</span><span class="sxs-lookup"><span data-stu-id="ba310-167">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span>|
|<span data-ttu-id="ba310-168">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="ba310-168">.NET Framework 4.7.1</span></span>|<span data-ttu-id="ba310-169">W przypadku aktualizacji systemu Windows 10 dla twórców i systemu Windows Server w wersji 1709:461308</span><span class="sxs-lookup"><span data-stu-id="ba310-169">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="ba310-170">Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 461310</span><span class="sxs-lookup"><span data-stu-id="ba310-170">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span>|
|<span data-ttu-id="ba310-171">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="ba310-171">.NET Framework 4.7.2</span></span>|<span data-ttu-id="ba310-172">W systemie Windows 10 kwiecień 2018 Update i Windows Server w wersji 1803:461808</span><span class="sxs-lookup"><span data-stu-id="ba310-172">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="ba310-173">We wszystkich systemach operacyjnych Windows innych niż Windows 10 kwiecień 2018 Update i Windows Server w wersji 1803:461814</span><span class="sxs-lookup"><span data-stu-id="ba310-173">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span>|
|<span data-ttu-id="ba310-174">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="ba310-174">.NET Framework 4.8</span></span>|<span data-ttu-id="ba310-175">W systemie Windows 10 maja 2019 Update i aktualizacja Windows 10 listopad 2019:528040</span><span class="sxs-lookup"><span data-stu-id="ba310-175">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="ba310-176">Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 528049</span><span class="sxs-lookup"><span data-stu-id="ba310-176">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span>|

#### <a name="specific-version"></a><span data-ttu-id="ba310-177">Określona wersja</span><span class="sxs-lookup"><span data-stu-id="ba310-177">Specific version</span></span>

<span data-ttu-id="ba310-178">Aby określić, czy *określona* wersja .NET Framework jest zainstalowana w określonej wersji systemu operacyjnego Windows, należy sprawdzić, czy wartość DWORD **wersji** jest *równa* wartości wymienionej w tabeli.</span><span class="sxs-lookup"><span data-stu-id="ba310-178">To determine whether a *specific* version of the .NET Framework is installed on a particular version of the Windows operating system, test whether the **Release** DWORD value is *equal to* the value listed in the table.</span></span> <span data-ttu-id="ba310-179">Na przykład aby określić, czy .NET Framework 4,6 jest obecny w systemie Windows 10, należy sprawdzić wartość **wersji** , która jest *równa* 393295.</span><span class="sxs-lookup"><span data-stu-id="ba310-179">For example, to determine whether .NET Framework 4.6 is present on a Windows 10 system, test for the a **Release** value that is *equal to* 393295.</span></span>

#### <a name="minimum-version"></a><span data-ttu-id="ba310-180">Wersja minimalna</span><span class="sxs-lookup"><span data-stu-id="ba310-180">Minimum version</span></span>

<span data-ttu-id="ba310-181">Aby określić, czy jest dostępna *minimalna* wersja .NET Framework, użyj najmniejszej wartości DWORD **wersji** dla tej wersji z poprzedniej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ba310-181">To determine whether a *minimum* version of the .NET Framework is present, use the smallest **RELEASE** DWORD value for that version from the previous table.</span></span> <span data-ttu-id="ba310-182">(W przypadku wygody wartości minimalne są również wymienione w poniższej tabeli).</span><span class="sxs-lookup"><span data-stu-id="ba310-182">(For convenience, the minimum values are also listed in the table that follows.)</span></span>

<span data-ttu-id="ba310-183">Na przykład, jeśli aplikacja działa w .NET Framework 4,8 lub nowszej wersji, należy przetestować wartość typu DWORD **zlecenia** , która jest *większa lub równa* 528040.</span><span class="sxs-lookup"><span data-stu-id="ba310-183">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **RELEASE** DWORD value that is *greater than or equal to* 528040.</span></span>

|<span data-ttu-id="ba310-184">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ba310-184">.NET Framework version</span></span>|<span data-ttu-id="ba310-185">Minimalna wartość wartości DWORD zlecenia</span><span class="sxs-lookup"><span data-stu-id="ba310-185">Minimum value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="ba310-186">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="ba310-186">.NET Framework 4.5</span></span>|<span data-ttu-id="ba310-187">378389</span><span class="sxs-lookup"><span data-stu-id="ba310-187">378389</span></span>|
|<span data-ttu-id="ba310-188">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="ba310-188">.NET Framework 4.5.1</span></span>|<span data-ttu-id="ba310-189">378675</span><span class="sxs-lookup"><span data-stu-id="ba310-189">378675</span></span>|
|<span data-ttu-id="ba310-190">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="ba310-190">.NET Framework 4.5.2</span></span>|<span data-ttu-id="ba310-191">379893</span><span class="sxs-lookup"><span data-stu-id="ba310-191">379893</span></span>|
|<span data-ttu-id="ba310-192">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="ba310-192">.NET Framework 4.6</span></span>|<span data-ttu-id="ba310-193">393295</span><span class="sxs-lookup"><span data-stu-id="ba310-193">393295</span></span>|
|<span data-ttu-id="ba310-194">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="ba310-194">.NET Framework 4.6.1</span></span>|<span data-ttu-id="ba310-195">394254</span><span class="sxs-lookup"><span data-stu-id="ba310-195">394254</span></span>|
|<span data-ttu-id="ba310-196">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="ba310-196">.NET Framework 4.6.2</span></span>|<span data-ttu-id="ba310-197">394802</span><span class="sxs-lookup"><span data-stu-id="ba310-197">394802</span></span>|
|<span data-ttu-id="ba310-198">.NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="ba310-198">.NET Framework 4.7</span></span>|<span data-ttu-id="ba310-199">460798</span><span class="sxs-lookup"><span data-stu-id="ba310-199">460798</span></span>|
|<span data-ttu-id="ba310-200">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="ba310-200">.NET Framework 4.7.1</span></span>|<span data-ttu-id="ba310-201">461308</span><span class="sxs-lookup"><span data-stu-id="ba310-201">461308</span></span>|
|<span data-ttu-id="ba310-202">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="ba310-202">.NET Framework 4.7.2</span></span>|<span data-ttu-id="ba310-203">461808</span><span class="sxs-lookup"><span data-stu-id="ba310-203">461808</span></span>|
|<span data-ttu-id="ba310-204">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="ba310-204">.NET Framework 4.8</span></span>|<span data-ttu-id="ba310-205">528040</span><span class="sxs-lookup"><span data-stu-id="ba310-205">528040</span></span>|

#### <a name="multiple-versions"></a><span data-ttu-id="ba310-206">Wiele wersji</span><span class="sxs-lookup"><span data-stu-id="ba310-206">Multiple versions</span></span>

<span data-ttu-id="ba310-207">Aby przetestować dla wielu wersji, Zacznij od sprawdzenia wartości, która jest *większa niż lub równa* mniejszej wartości DWORD dla najnowszej wersji .NET Framework, a następnie porównaj wartość z mniejszą wartością DWORD dla każdej kolejnej wersji.</span><span class="sxs-lookup"><span data-stu-id="ba310-207">To test for multiple versions, begin by testing for a value that is *greater than or equal to* the smaller DWORD value for the latest .NET Framework version, and then compare the value with the smaller DWORD value for each successive earlier version.</span></span> <span data-ttu-id="ba310-208">Na przykład, jeśli aplikacja wymaga .NET Framework 4,7 lub nowszego, a chcesz określić konkretną wersję .NET Framework obecny, Zacznij od testowania dla wartości typu DWORD o **wersji** , która jest *większa lub równa* 461808 (mniejsza wartość DWORD wartość .NET Framework 4.7.2).</span><span class="sxs-lookup"><span data-stu-id="ba310-208">For example, if your application requires .NET Framework 4.7 or later and you want to determine the specific version of .NET Framework present, start by testing for a **RELEASE** DWORD value that is *great than or equal to* to 461808 (the smaller DWORD value for .NET Framework 4.7.2).</span></span> <span data-ttu-id="ba310-209">Następnie porównaj wartość DWORD **wersji** z mniejszą wartością dla każdej późniejszej .NET Framework wersji.</span><span class="sxs-lookup"><span data-stu-id="ba310-209">Then compare the **RELEASE** DWORD value with the smaller value for each later .NET Framework version.</span></span>

<a name="net_d"></a>

### <a name="query-the-registry-using-code"></a><span data-ttu-id="ba310-210">Tworzenie zapytań dotyczących rejestru przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="ba310-210">Query the registry using code</span></span>

1. <span data-ttu-id="ba310-211">Użyj metod <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> i <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType>, aby uzyskać dostęp do podklucza **rejestrze Framework Setup\NDP\v4\Full** w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ba310-211">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey in the Windows registry.</span></span>

   <span data-ttu-id="ba310-212">Obecność wpisu DWORD **Release** w podkluczu **rejestrze Framework Setup\NDP\v4\Full** wskazuje, że na komputerze jest zainstalowana .NET Framework 4,5 lub nowsza.</span><span class="sxs-lookup"><span data-stu-id="ba310-212">The existence of the **Release** DWORD entry in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey indicates that the .NET Framework 4.5 or a later version is installed on a computer.</span></span>

2. <span data-ttu-id="ba310-213">Sprawdź wartość wpisu **Zwolnij** , aby określić zainstalowaną wersję.</span><span class="sxs-lookup"><span data-stu-id="ba310-213">Check the value of the **Release** entry to determine the installed version.</span></span> <span data-ttu-id="ba310-214">Aby można było przesłać dalej, sprawdź, czy wartość jest większa niż lub równa wartości wymienionej w [tabeli wersji .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="ba310-214">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="ba310-215">Poniższy przykład sprawdza wartość wpisu **Release** w rejestrze, aby znaleźć .NET Framework 4,5 i nowsze wersje, które są zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="ba310-215">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="ba310-216">Ten przykład jest zgodny z zalecaną metodą sprawdzania wersji:</span><span class="sxs-lookup"><span data-stu-id="ba310-216">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="ba310-217">Sprawdza, czy wartość wpisu **wydania** jest *większa niż lub równa* wartości znanych kluczy wydania.</span><span class="sxs-lookup"><span data-stu-id="ba310-217">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="ba310-218">Sprawdza w kolejności od najnowszej wersji do najwcześniejszej wersji.</span><span class="sxs-lookup"><span data-stu-id="ba310-218">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a>

### <a name="use-powershell-to-check-for-a-minimum-required-version"></a><span data-ttu-id="ba310-219">Użyj programu PowerShell, aby sprawdzić wersję minimalną wymaganą</span><span class="sxs-lookup"><span data-stu-id="ba310-219">Use PowerShell to check for a minimum-required version</span></span>

<span data-ttu-id="ba310-220">Użyj poleceń programu PowerShell, aby sprawdzić wartość wpisu **Release** w podkluczu **rejestrze Framework Setup\NDP\v4\Full** .</span><span class="sxs-lookup"><span data-stu-id="ba310-220">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey.</span></span>

<span data-ttu-id="ba310-221">Poniższe przykłady umożliwiają sprawdzenie wartości wpisu **wydania** , aby określić, czy .NET Framework 4.6.2 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ba310-221">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="ba310-222">Ten kod zwraca `True`, jeśli jest zainstalowany i `False` w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="ba310-222">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

<span data-ttu-id="ba310-223">Aby sprawdzić, czy jest wymagana inna wersja .NET Framework, Zastąp `394802` w przykładzie wartością z [tabeli .NET Framework wersji](#version_table).</span><span class="sxs-lookup"><span data-stu-id="ba310-223">To check for a different minimum-required .NET Framework version, replace `394802` in the example with a value from the [.NET Framework version table](#version_table).</span></span> <span data-ttu-id="ba310-224">Użyj najmniejszej wartości wyświetlanej dla tej wersji.</span><span class="sxs-lookup"><span data-stu-id="ba310-224">Use the smallest value shown for that version.</span></span>

## <a name="find-older-net-framework-versions-1-through-4"></a><span data-ttu-id="ba310-225">Znajdź starsze wersje .NET Framework (od 1 do 4)</span><span class="sxs-lookup"><span data-stu-id="ba310-225">Find older .NET Framework versions (1 through 4)</span></span>

<a name="net_a"></a>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="ba310-226">Użyj edytora rejestru (starsze wersje Framework)</span><span class="sxs-lookup"><span data-stu-id="ba310-226">Use Registry Editor (older framework versions)</span></span>

1. <span data-ttu-id="ba310-227">Z menu **Start** wybierz polecenie **Uruchom**, wpisz polecenie *regedit*, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ba310-227">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="ba310-228">Musisz mieć poświadczenia administracyjne, aby uruchomić regedit.</span><span class="sxs-lookup"><span data-stu-id="ba310-228">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="ba310-229">W Edytorze rejestru Otwórz następujący podklucz: **rejestrze Framework Setup\NDP**:</span><span class="sxs-lookup"><span data-stu-id="ba310-229">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span></span>

    - <span data-ttu-id="ba310-230">W przypadku .NET Framework wersje 1,1 do 3,5 każda zainstalowana wersja jest wymieniona jako podklucz w podkluczu **rejestrze Framework Setup\NDP** .</span><span class="sxs-lookup"><span data-stu-id="ba310-230">For .NET Framework versions 1.1 through 3.5, each installed version is listed as a subkey under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** subkey.</span></span> <span data-ttu-id="ba310-231">Na przykład **rejestrze Framework Setup\NDP\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="ba310-231">For example, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span></span> <span data-ttu-id="ba310-232">Numer wersji jest przechowywany jako wartość w wpisie **wersji** podklucza wersji.</span><span class="sxs-lookup"><span data-stu-id="ba310-232">The version number is stored as a value in the version subkey's **Version** entry.</span></span>

    - <span data-ttu-id="ba310-233">W przypadku .NET Framework 4, wpis **wersji** znajduje się w podkluczu **rejestrze Framework Setup\NDP\v4.0\Client** , **rejestrze Framework Setup\NDP\v4.0\Full** podklucz lub w obu podkluczach.</span><span class="sxs-lookup"><span data-stu-id="ba310-233">For .NET Framework 4, the **Version** entry is under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** subkey, the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ba310-234">Folder **instalacji programu .NET Framework** w rejestrze nie rozpoczyna się kropką.</span><span class="sxs-lookup"><span data-stu-id="ba310-234">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="ba310-235">Na poniższej ilustracji przedstawiono podklucz i jego **wersję** wpisu dla .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="ba310-235">The following figure shows the subkey and its **Version** entry for the .NET Framework 3.5.</span></span>

    <span data-ttu-id="ba310-236">![Wpis rejestru dla .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 i wcześniejsze wersje")</span><span class="sxs-lookup"><span data-stu-id="ba310-236">![The registry entry for the .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

<a name="net_c"></a>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="ba310-237">Wykonywanie zapytania dotyczącego rejestru przy użyciu kodu (starsze wersje Framework)</span><span class="sxs-lookup"><span data-stu-id="ba310-237">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="ba310-238">Użyj klasy <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType>, aby uzyskać dostęp do podklucza **rejestrze Framework Setup\NDP** w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ba310-238">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** subkey in the Windows registry.</span></span>

<span data-ttu-id="ba310-239">Poniższy przykład umożliwia znalezienie zainstalowanych wersji .NET Framework od 1 do 4:</span><span class="sxs-lookup"><span data-stu-id="ba310-239">The following example finds the .NET Framework 1 through 4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a><span data-ttu-id="ba310-240">Znajdź wersje środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="ba310-240">Find CLR versions</span></span>

<a name="clr_a"></a>

### <a name="use-clrverexe"></a><span data-ttu-id="ba310-241">Użyj Clrver. exe</span><span class="sxs-lookup"><span data-stu-id="ba310-241">Use Clrver.exe</span></span>

<span data-ttu-id="ba310-242">Użyj [Narzędzia wersji środowiska CLR (Clrver. exe)](../tools/clrver-exe-clr-version-tool.md) , aby określić, które wersje środowiska CLR są zainstalowane na komputerze:</span><span class="sxs-lookup"><span data-stu-id="ba310-242">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer:</span></span>

- <span data-ttu-id="ba310-243">W [wiersz polecenia dla deweloperów dla programu Visual Studio](../tools/developer-command-prompt-for-vs.md)wprowadź `clrver`.</span><span class="sxs-lookup"><span data-stu-id="ba310-243">From a [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), enter `clrver`.</span></span>

    <span data-ttu-id="ba310-244">Przykładowe dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ba310-244">Sample output:</span></span>

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="use-the-environment-class"></a><span data-ttu-id="ba310-245">Korzystanie z klasy Environment</span><span class="sxs-lookup"><span data-stu-id="ba310-245">Use the Environment class</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba310-246">W przypadku .NET Framework 4,5 i nowszych wersje nie należy używać właściwości <xref:System.Environment.Version%2A?displayProperty=nameWithType> do wykrywania wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ba310-246">For the .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="ba310-247">Zamiast tego należy wykonać zapytanie dotyczące rejestru zgodnie z opisem w artykule [znajdowanie .NET Framework wersje 4,5 i nowsze z kodem](#net_d).</span><span class="sxs-lookup"><span data-stu-id="ba310-247">Instead, query the registry as described in [Find .NET Framework versions 4.5 and later with code](#net_d).</span></span>

1. <span data-ttu-id="ba310-248">Zbadaj Właściwość <xref:System.Environment.Version?displayProperty=nameWithType>, aby pobrać obiekt <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="ba310-248">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

    <span data-ttu-id="ba310-249">Zwrócony obiekt `System.Version` identyfikuje wersję środowiska uruchomieniowego, które aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="ba310-249">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="ba310-250">Nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogły zostać zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ba310-250">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

    <span data-ttu-id="ba310-251">W przypadku .NET Framework w wersji 4, 4,5, 4.5.1 i 4.5.2 ciąg reprezentujący zwrócony obiekt <xref:System.Version> ma postać 4.0.30319. *XXXXX*, gdzie *XXXXX* jest mniejszy niż 42000.</span><span class="sxs-lookup"><span data-stu-id="ba310-251">For the .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="ba310-252">W przypadku .NET Framework 4,6 i nowszych wersje ma postać 4.0.30319.42000.</span><span class="sxs-lookup"><span data-stu-id="ba310-252">For the .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

2. <span data-ttu-id="ba310-253">Po utworzeniu obiektu `Version` wykonaj zapytanie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ba310-253">After you have the `Version` object, query it as follows:</span></span>

   - <span data-ttu-id="ba310-254">Aby uzyskać informacje o głównym identyfikatorze wydania (na przykład *4* dla wersji 4,0), użyj właściwości <xref:System.Version.Major%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ba310-254">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="ba310-255">W przypadku pomocniczego identyfikatora wydania (na przykład *0* w przypadku wersji 4,0) użyj właściwości <xref:System.Version.Minor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ba310-255">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="ba310-256">Dla całego ciągu wersji (na przykład *4.0.30319.18010*) użyj metody <xref:System.Version.ToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ba310-256">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ba310-257">Ta metoda zwraca pojedynczą wartość odzwierciedlającą wersję środowiska uruchomieniowego, które wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="ba310-257">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="ba310-258">Nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogą być zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ba310-258">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

<span data-ttu-id="ba310-259">W poniższym przykładzie zastosowano Właściwość <xref:System.Environment.Version%2A?displayProperty=nameWithType> do pobrania informacji o wersji środowiska CLR:</span><span class="sxs-lookup"><span data-stu-id="ba310-259">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="ba310-260">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba310-260">See also</span></span>

- [<span data-ttu-id="ba310-261">Instrukcje: Określanie, które aktualizacje .NET Framework są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="ba310-261">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="ba310-262">Zainstaluj .NET Framework dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="ba310-262">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="ba310-263">.NET Framework wersje i zależności</span><span class="sxs-lookup"><span data-stu-id="ba310-263">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
