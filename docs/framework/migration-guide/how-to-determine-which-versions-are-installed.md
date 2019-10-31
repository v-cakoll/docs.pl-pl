---
title: 'Instrukcje: Określanie, które wersje .NET Framework są zainstalowane'
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: e339767b981cea80b1b804db7360961dc42f2102
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126324"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="0dbe1-102">Instrukcje: Określanie, które wersje .NET Framework są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="0dbe1-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="0dbe1-103">Użytkownicy mogą [instalować](../install/index.md) i uruchamiać wiele wersji .NET Framework na swoich komputerach.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-103">Users can [install](../install/index.md) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="0dbe1-104">Podczas opracowywania lub wdrażania aplikacji może być konieczne, aby wiedzieć, które wersje .NET Framework są zainstalowane na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span>

<span data-ttu-id="0dbe1-105">.NET Framework składa się z dwóch głównych składników, które są osobno dla wersji:</span><span class="sxs-lookup"><span data-stu-id="0dbe1-105">The .NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="0dbe1-106">Zestaw zestawów, które są kolekcjami typów i zasobów zapewniających funkcje dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="0dbe1-107">.NET Framework i zestawy mają ten sam numer wersji.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-107">The .NET Framework and assemblies share the same version number.</span></span>

- <span data-ttu-id="0dbe1-108">Środowisko uruchomieniowe języka wspólnego (CLR), które zarządza kodem aplikacji i go wykonuje.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="0dbe1-109">Środowisko CLR jest identyfikowane za pomocą własnego numeru wersji (zobacz [wersje i zależności](versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="0dbe1-109">The CLR is identified by its own version number (see [Versions and dependencies](versions-and-dependencies.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="0dbe1-110">Każda nowa wersja programu .NET Framework zachowuje funkcje z poprzednich wersji i dodaje nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-110">Each new version of the .NET Framework retains features from the previous versions and adds new features.</span></span> <span data-ttu-id="0dbe1-111">Możesz ładować wiele wersji .NET Framework na jednym komputerze w tym samym czasie, co oznacza, że można zainstalować .NET Framework bez konieczności odinstalowywania poprzednich wersji.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-111">You can load multiple versions of the .NET Framework on a single computer at the same time, which means that you can install the .NET Framework without having to uninstall previous versions.</span></span> <span data-ttu-id="0dbe1-112">Ogólnie rzecz biorąc nie należy odinstalowywać poprzednich wersji .NET Framework, ponieważ używana aplikacja może zależeć od określonej wersji i może zostać przerwana, jeśli ta wersja zostanie usunięta.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-112">In general, you shouldn't uninstall previous versions of the .NET Framework, because an application you use may depend on a specific version and may break if that version is removed.</span></span>
>
> <span data-ttu-id="0dbe1-113">Istnieje różnica między wersją .NET Framework i wersją środowiska CLR:</span><span class="sxs-lookup"><span data-stu-id="0dbe1-113">There is a difference between the .NET Framework version and the CLR version:</span></span>
>
> - <span data-ttu-id="0dbe1-114">Wersja .NET Framework jest oparta na zestawie zestawów, które tworzą bibliotekę klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-114">The .NET Framework version is based on the set of assemblies that form the .NET Framework class library.</span></span> <span data-ttu-id="0dbe1-115">Na przykład .NET Framework wersje obejmują 4,5, 4.6.1 i 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-115">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>
> - <span data-ttu-id="0dbe1-116">Wersja środowiska CLR jest oparta na czasie wykonywania, w którym wykonywane są .NET Framework aplikacje.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-116">The CLR version is based on the runtime on which .NET Framework applications execute.</span></span> <span data-ttu-id="0dbe1-117">Jedna wersja środowiska CLR obsługuje zazwyczaj wiele wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-117">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="0dbe1-118">Na przykład środowisko CLR w wersji 4.0.30319. *XXXXX* obsługuje .NET Framework wersje od 4 do 4.5.2, gdzie *XXXXX* jest mniejszy niż 42000, a środowisko CLR w wersji 4.0.30319.42000 obsługuje wersje .NET Framework, które zaczynają się od .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-118">For example, CLR version 4.0.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2, where *xxxxx* is less than 42000, and CLR version 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>
>
> <span data-ttu-id="0dbe1-119">Aby uzyskać więcej informacji na temat wersji, zobacz [.NET Framework wersje i zależności](versions-and-dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="0dbe1-119">For more information about versions, see [.NET Framework versions and dependencies](versions-and-dependencies.md).</span></span>

<span data-ttu-id="0dbe1-120">Aby uzyskać listę wersji .NET Framework zainstalowanych na komputerze, można uzyskać dostęp do rejestru.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-120">To get a list of the .NET Framework versions installed on a computer, you access the registry.</span></span> <span data-ttu-id="0dbe1-121">Możesz użyć Edytora rejestru, aby wyświetlić rejestr lub użyć kodu, aby wykonać zapytanie:</span><span class="sxs-lookup"><span data-stu-id="0dbe1-121">You can either use the Registry Editor to view the registry or use code to query it:</span></span>

- <span data-ttu-id="0dbe1-122">Znajdź nowsze wersje .NET Framework (4,5 i nowsze):</span><span class="sxs-lookup"><span data-stu-id="0dbe1-122">Find newer .NET Framework versions (4.5 and later):</span></span>
  - [<span data-ttu-id="0dbe1-123">Znajdź .NET Framework wersje przy użyciu Edytora rejestru</span><span class="sxs-lookup"><span data-stu-id="0dbe1-123">Use the Registry Editor to find .NET Framework versions</span></span>](#net_b)
  - [<span data-ttu-id="0dbe1-124">Używanie kodu do wysyłania zapytań do rejestru w przypadku wersji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0dbe1-124">Use code to query the registry for .NET Framework versions</span></span>](#net_d)
  - [<span data-ttu-id="0dbe1-125">Używanie programu PowerShell do wykonywania zapytań dotyczących rejestru w przypadku wersji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0dbe1-125">Use PowerShell to query the registry for .NET Framework versions</span></span>](#ps_a)
- <span data-ttu-id="0dbe1-126">Znajdź starsze wersje .NET Framework (1&#8211;4):</span><span class="sxs-lookup"><span data-stu-id="0dbe1-126">Find older .NET Framework versions (1&#8211;4):</span></span>
  - [<span data-ttu-id="0dbe1-127">Znajdź .NET Framework wersje przy użyciu Edytora rejestru</span><span class="sxs-lookup"><span data-stu-id="0dbe1-127">Use the Registry Editor to find .NET Framework versions</span></span>](#net_a)
  - [<span data-ttu-id="0dbe1-128">Używanie kodu do wysyłania zapytań do rejestru w przypadku wersji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0dbe1-128">Use code to query the registry for .NET Framework versions</span></span>](#net_c)

<span data-ttu-id="0dbe1-129">Aby uzyskać listę wersji środowiska CLR zainstalowanych na komputerze, użyj narzędzia lub kodu:</span><span class="sxs-lookup"><span data-stu-id="0dbe1-129">To get a list of the CLR versions installed on a computer, use a tool or code:</span></span>

- [<span data-ttu-id="0dbe1-130">Korzystanie z narzędzia Clrver</span><span class="sxs-lookup"><span data-stu-id="0dbe1-130">Use the Clrver tool</span></span>](#clr_a)
- [<span data-ttu-id="0dbe1-131">Użyj kodu, aby wykonać zapytanie dotyczące klasy środowiska</span><span class="sxs-lookup"><span data-stu-id="0dbe1-131">Use code to query the Environment class</span></span>](#clr_b)

<span data-ttu-id="0dbe1-132">Aby uzyskać informacje dotyczące wykrywania zainstalowanych aktualizacji dla każdej wersji .NET Framework, zobacz [How to: Określanie, które aktualizacje .NET Framework są zainstalowane](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="0dbe1-132">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="find-newer-net-framework-versions-45-and-later"></a><span data-ttu-id="0dbe1-133">Znajdź nowsze wersje .NET Framework (4,5 i nowsze)</span><span class="sxs-lookup"><span data-stu-id="0dbe1-133">Find newer .NET Framework versions (4.5 and later)</span></span>

<a name="net_b"></a>

### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a><span data-ttu-id="0dbe1-134">Znajdź .NET Framework w wersji 4,5 i nowszych w rejestrze</span><span class="sxs-lookup"><span data-stu-id="0dbe1-134">Find .NET Framework versions 4.5 and later in the registry</span></span>

1. <span data-ttu-id="0dbe1-135">Z menu **Start** wybierz polecenie **Uruchom**, wpisz polecenie *regedit*, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-135">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

     <span data-ttu-id="0dbe1-136">Musisz mieć poświadczenia administracyjne, aby uruchomić regedit.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-136">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="0dbe1-137">W Edytorze rejestru Otwórz następujący podklucz: **rejestrze Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-137">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span></span> <span data-ttu-id="0dbe1-138">Jeśli **pełny** podklucz nie jest obecny, nie masz zainstalowanego .NET Framework 4,5 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-138">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0dbe1-139">Folder **instalacji programu .NET Framework** w rejestrze *nie rozpoczyna się* kropką.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-139">The **NET Framework Setup** folder in the registry does *not* begin with a period.</span></span>

3. <span data-ttu-id="0dbe1-140">Wyszukaj wpis DWORD o nazwie **Release**.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-140">Check for a DWORD entry named **Release**.</span></span> <span data-ttu-id="0dbe1-141">Jeśli istnieje, masz zainstalowaną .NET Framework 4,5 lub nowszą wersję.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-141">If it exists, then you have .NET Framework 4.5 or later versions installed.</span></span> <span data-ttu-id="0dbe1-142">Wartość jest kluczem wydania, który odpowiada określonej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-142">Its value is a release key that corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="0dbe1-143">Na przykład, wartość wpisu **zlecenia** to *378389*, który jest kluczem wydania dla .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-143">In the following figure, for example, the value of the **Release** entry is *378389*, which is the release key for .NET Framework 4.5.</span></span>

     <span data-ttu-id="0dbe1-144">![Wpis rejestru dla .NET Framework 4,5](./media/clr-installdir.png "Wpis rejestru dla .NET Framework 4,5")</span><span class="sxs-lookup"><span data-stu-id="0dbe1-144">![Registry entry for the .NET Framework 4.5](./media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

<span data-ttu-id="0dbe1-145">W poniższej tabeli wymieniono wartości DWORD **wydania** w poszczególnych systemach operacyjnych dla .NET Framework 4,5 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-145">The following table lists the value of the **Release** DWORD on individual operating systems for .NET Framework 4.5 and later versions.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|<span data-ttu-id="0dbe1-146">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0dbe1-146">.NET Framework version</span></span>|<span data-ttu-id="0dbe1-147">Wartość DWORD dotycząca wersji</span><span class="sxs-lookup"><span data-stu-id="0dbe1-147">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="0dbe1-148">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="0dbe1-148">.NET Framework 4.5</span></span>|<span data-ttu-id="0dbe1-149">Wszystkie systemy operacyjne Windows: 378389</span><span class="sxs-lookup"><span data-stu-id="0dbe1-149">All Windows operating systems: 378389</span></span>|
|<span data-ttu-id="0dbe1-150">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="0dbe1-150">.NET Framework 4.5.1</span></span>|<span data-ttu-id="0dbe1-151">W systemach Windows 8.1 i Windows Server 2012 R2:378675</span><span class="sxs-lookup"><span data-stu-id="0dbe1-151">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="0dbe1-152">We wszystkich innych systemach operacyjnych Windows: 378758</span><span class="sxs-lookup"><span data-stu-id="0dbe1-152">On all other Windows operating systems: 378758</span></span>|
|<span data-ttu-id="0dbe1-153">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="0dbe1-153">.NET Framework 4.5.2</span></span>|<span data-ttu-id="0dbe1-154">Wszystkie systemy operacyjne Windows: 379893</span><span class="sxs-lookup"><span data-stu-id="0dbe1-154">All Windows operating systems: 379893</span></span>|
|<span data-ttu-id="0dbe1-155">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="0dbe1-155">.NET Framework 4.6</span></span>|<span data-ttu-id="0dbe1-156">W systemie Windows 10:393295</span><span class="sxs-lookup"><span data-stu-id="0dbe1-156">On Windows 10: 393295</span></span><br /><span data-ttu-id="0dbe1-157">We wszystkich innych systemach operacyjnych Windows: 393297</span><span class="sxs-lookup"><span data-stu-id="0dbe1-157">On all other Windows operating systems: 393297</span></span>|
|<span data-ttu-id="0dbe1-158">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="0dbe1-158">.NET Framework 4.6.1</span></span>|<span data-ttu-id="0dbe1-159">W systemach aktualizacji systemu Windows 10 listopad: 394254</span><span class="sxs-lookup"><span data-stu-id="0dbe1-159">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="0dbe1-160">We wszystkich innych systemach operacyjnych Windows (w tym Windows 10): 394271</span><span class="sxs-lookup"><span data-stu-id="0dbe1-160">On all other Windows operating systems (including Windows 10): 394271</span></span>|
|<span data-ttu-id="0dbe1-161">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="0dbe1-161">.NET Framework 4.6.2</span></span>|<span data-ttu-id="0dbe1-162">W rocznicowej aktualizacji systemu Windows 10 i Windows Server 2016:394802</span><span class="sxs-lookup"><span data-stu-id="0dbe1-162">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="0dbe1-163">Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 394806</span><span class="sxs-lookup"><span data-stu-id="0dbe1-163">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span>|
|<span data-ttu-id="0dbe1-164">.NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="0dbe1-164">.NET Framework 4.7</span></span>|<span data-ttu-id="0dbe1-165">Aktualizacja systemu Windows 10 dla twórców: 460798</span><span class="sxs-lookup"><span data-stu-id="0dbe1-165">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="0dbe1-166">Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 460805</span><span class="sxs-lookup"><span data-stu-id="0dbe1-166">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span>|
|<span data-ttu-id="0dbe1-167">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="0dbe1-167">.NET Framework 4.7.1</span></span>|<span data-ttu-id="0dbe1-168">W przypadku aktualizacji systemu Windows 10 dla twórców i systemu Windows Server w wersji 1709:461308</span><span class="sxs-lookup"><span data-stu-id="0dbe1-168">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="0dbe1-169">Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 461310</span><span class="sxs-lookup"><span data-stu-id="0dbe1-169">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span>|
|<span data-ttu-id="0dbe1-170">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="0dbe1-170">.NET Framework 4.7.2</span></span>|<span data-ttu-id="0dbe1-171">W systemie Windows 10 kwiecień 2018 Update i Windows Server w wersji 1803:461808</span><span class="sxs-lookup"><span data-stu-id="0dbe1-171">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="0dbe1-172">We wszystkich systemach operacyjnych Windows innych niż Windows 10 kwiecień 2018 Update i Windows Server w wersji 1803:461814</span><span class="sxs-lookup"><span data-stu-id="0dbe1-172">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span>|
|<span data-ttu-id="0dbe1-173">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="0dbe1-173">.NET Framework 4.8</span></span>|<span data-ttu-id="0dbe1-174">W systemie Windows 10 maja 2019 Update i aktualizacja Windows 10 listopad 2019:528040</span><span class="sxs-lookup"><span data-stu-id="0dbe1-174">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="0dbe1-175">Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 528049</span><span class="sxs-lookup"><span data-stu-id="0dbe1-175">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span>|

<span data-ttu-id="0dbe1-176">Możesz użyć następujących wartości w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0dbe1-176">You can use these values as follows:</span></span>

- <span data-ttu-id="0dbe1-177">Aby określić, czy określona wersja .NET Framework jest zainstalowana w określonej wersji systemu operacyjnego Windows, należy sprawdzić, czy wartość DWORD **wersji** jest *równa* wartości wymienionej w tabeli.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-177">To determine whether a specific version of the .NET Framework is installed on a particular version of the Windows operating system, test whether the **Release** DWORD value is *equal to* the value listed in the table.</span></span> <span data-ttu-id="0dbe1-178">Na przykład aby określić, czy .NET Framework 4,6 jest obecny w systemie Windows 10, należy sprawdzić wartość **wersji** , która jest *równa* 393295.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-178">For example, to determine whether .NET Framework 4.6 is present on a Windows 10 system, test for the a **Release** value that is *equal to* 393295.</span></span>

- <span data-ttu-id="0dbe1-179">Aby określić, czy jest dostępna minimalna wersja .NET Framework, Użyj mniejszej wartości DWORD **Release** dla tej wersji.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-179">To determine whether a minimum version of the .NET Framework is present, use the smaller **RELEASE** DWORD value for that version.</span></span> <span data-ttu-id="0dbe1-180">Na przykład, jeśli aplikacja działa w .NET Framework 4,6 lub nowszej wersji, należy przetestować wartość typu DWORD **zlecenia** , która jest *większa lub równa* 393295.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-180">For example, if your application runs under .NET Framework 4.6 or a later version, test for a **RELEASE** DWORD value that is *greater than or equal to* 393295.</span></span> <span data-ttu-id="0dbe1-181">W przypadku tabeli, która zawiera tylko minimalną wartość **typu DWORD dla każdej wersji .NET Framework** , zobacz [minimalne wartości w polu dword wydania dla .NET Framework 4,5 i nowszych wersji](minimum-release-dword.md).</span><span class="sxs-lookup"><span data-stu-id="0dbe1-181">For a table that lists only the minimum **RELEASE** DWORD value for each .NET Framework version, see [The minimum values of the Release DWORD for .NET Framework 4.5 and later versions](minimum-release-dword.md).</span></span>

- <span data-ttu-id="0dbe1-182">Aby przetestować dla wielu wersji, Zacznij od sprawdzenia wartości, która jest *większa niż lub równa* mniejszej wartości DWORD dla najnowszej wersji .NET Framework, a następnie porównaj wartość z mniejszą wartością DWORD dla każdej kolejnej wersji.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-182">To test for multiple versions, begin by testing for a value that is *greater than or equal to* the smaller DWORD value for the latest .NET Framework version, and then compare the value with the smaller DWORD value for each successive earlier version.</span></span> <span data-ttu-id="0dbe1-183">Na przykład, jeśli aplikacja wymaga .NET Framework 4,7 lub nowszego, a chcesz określić konkretną wersję .NET Framework obecny, Zacznij od testowania dla wartości typu DWORD o **wersji** , która jest *większa lub równa* 461808 (mniejsza wartość DWORD wartość .NET Framework 4.7.2).</span><span class="sxs-lookup"><span data-stu-id="0dbe1-183">For example, if your application requires .NET Framework 4.7 or later and you want to determine the specific version of .NET Framework present, start by testing for a **RELEASE** DWORD value that is *great than or equal to* to 461808 (the smaller DWORD value for .NET Framework 4.7.2).</span></span> <span data-ttu-id="0dbe1-184">Następnie porównaj wartość DWORD **wersji** z mniejszą wartością dla każdej późniejszej .NET Framework wersji.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-184">Then compare the **RELEASE** DWORD value with the smaller value for each later .NET Framework version.</span></span> <span data-ttu-id="0dbe1-185">W przypadku tabeli, która zawiera tylko minimalną wartość **typu DWORD dla każdej wersji .NET Framework** , zobacz [minimalne wartości w polu dword wydania dla .NET Framework 4,5 i nowszych wersji](minimum-release-dword.md).</span><span class="sxs-lookup"><span data-stu-id="0dbe1-185">For a table that lists only the minimum **RELEASE** DWORD value for each .NET Framework version, see [The minimum values of the Release DWORD for .NET Framework 4.5 and later versions](minimum-release-dword.md).</span></span>

<a name="net_d"></a>

### <a name="find-net-framework-versions-45-and-later-with-code"></a><span data-ttu-id="0dbe1-186">Znajdź .NET Framework wersje 4,5 i nowsze z kodem</span><span class="sxs-lookup"><span data-stu-id="0dbe1-186">Find .NET Framework versions 4.5 and later with code</span></span>

1. <span data-ttu-id="0dbe1-187">Użyj metod <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> i <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType>, aby uzyskać dostęp do podklucza **rejestrze Framework Setup\NDP\v4\Full** w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-187">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey in the Windows registry.</span></span>

    <span data-ttu-id="0dbe1-188">Obecność wpisu DWORD **Release** w podkluczu **rejestrze Framework Setup\NDP\v4\Full** wskazuje, że na komputerze jest zainstalowana .NET Framework 4,5 lub nowsza.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-188">The existence of the **Release** DWORD entry in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey indicates that the .NET Framework 4.5 or a later version is installed on a computer.</span></span>

2. <span data-ttu-id="0dbe1-189">Sprawdź wartość wpisu **Zwolnij** , aby określić zainstalowaną wersję.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-189">Check the value of the **Release** entry to determine the installed version.</span></span> <span data-ttu-id="0dbe1-190">Aby można było przesłać dalej, sprawdź, czy wartość jest większa niż lub równa wartości wymienionej w [tabeli wersji .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="0dbe1-190">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="0dbe1-191">Poniższy przykład sprawdza wartość wpisu **Release** w rejestrze, aby znaleźć .NET Framework 4,5 i nowsze wersje, które są zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="0dbe1-191">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="0dbe1-192">Ten przykład jest zgodny z zalecaną metodą sprawdzania wersji:</span><span class="sxs-lookup"><span data-stu-id="0dbe1-192">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="0dbe1-193">Sprawdza, czy wartość wpisu **wydania** jest *większa niż lub równa* wartości znanych kluczy wydania.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-193">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="0dbe1-194">Sprawdza w kolejności od najnowszej wersji do najwcześniejszej wersji.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-194">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a>

### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a><span data-ttu-id="0dbe1-195">Sprawdzanie minimalnej wymaganej wersji .NET Framework (4,5 i nowszych) przy użyciu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="0dbe1-195">Check for a minimum-required .NET Framework version (4.5 and later) with PowerShell</span></span>

- <span data-ttu-id="0dbe1-196">Użyj poleceń programu PowerShell, aby sprawdzić wartość wpisu **Release** w podkluczu **rejestrze Framework Setup\NDP\v4\Full** .</span><span class="sxs-lookup"><span data-stu-id="0dbe1-196">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey.</span></span>

<span data-ttu-id="0dbe1-197">Poniższe przykłady umożliwiają sprawdzenie wartości wpisu **wydania** , aby określić, czy .NET Framework 4.6.2 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-197">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="0dbe1-198">Ten kod zwraca `True`, jeśli jest zainstalowany i `False` w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-198">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

<span data-ttu-id="0dbe1-199">Aby sprawdzić, czy wersja .NET Framework wymaga innej minimalnej wersji, Zastąp *394802* w poniższych przykładach wartością **wydania** z [tabeli .NET Framework wersji](#version_table).</span><span class="sxs-lookup"><span data-stu-id="0dbe1-199">To check for a different minimum-required .NET Framework version, replace *394802* in these examples with a **Release** value from the [.NET Framework version table](#version_table).</span></span>

## <a name="find-older-net-framework-versions-182114"></a><span data-ttu-id="0dbe1-200">Znajdź starsze wersje .NET Framework (1&#8211;4)</span><span class="sxs-lookup"><span data-stu-id="0dbe1-200">Find older .NET Framework versions (1&#8211;4)</span></span>

<a name="net_a"></a>

### <a name="find-net-framework-versions-182114-in-the-registry"></a><span data-ttu-id="0dbe1-201">Znajdź .NET Framework wersji 1&#8211;4 w rejestrze</span><span class="sxs-lookup"><span data-stu-id="0dbe1-201">Find .NET Framework versions 1&#8211;4 in the registry</span></span>

1. <span data-ttu-id="0dbe1-202">Z menu **Start** wybierz polecenie **Uruchom**, wpisz polecenie *regedit*, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-202">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="0dbe1-203">Musisz mieć poświadczenia administracyjne, aby uruchomić regedit.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-203">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="0dbe1-204">W Edytorze rejestru Otwórz następujący podklucz: **rejestrze Framework Setup\NDP**:</span><span class="sxs-lookup"><span data-stu-id="0dbe1-204">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span></span>

    - <span data-ttu-id="0dbe1-205">W przypadku .NET Framework wersje 1,1 do 3,5 każda zainstalowana wersja jest wymieniona jako podklucz w podkluczu **rejestrze Framework Setup\NDP** .</span><span class="sxs-lookup"><span data-stu-id="0dbe1-205">For .NET Framework versions 1.1 through 3.5, each installed version is listed as a subkey under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** subkey.</span></span> <span data-ttu-id="0dbe1-206">Na przykład **rejestrze Framework Setup\NDP\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-206">For example, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span></span> <span data-ttu-id="0dbe1-207">Numer wersji jest przechowywany jako wartość w wpisie **wersji** podklucza wersji.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-207">The version number is stored as a value in the version subkey's **Version** entry.</span></span>

    - <span data-ttu-id="0dbe1-208">W przypadku .NET Framework 4, wpis **wersji** znajduje się w podkluczu **rejestrze Framework Setup\NDP\v4.0\Client** , **rejestrze Framework Setup\NDP\v4.0\Full** podklucz lub w obu podkluczach.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-208">For .NET Framework 4, the **Version** entry is under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** subkey, the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0dbe1-209">Folder **instalacji programu .NET Framework** w rejestrze nie rozpoczyna się kropką.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-209">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="0dbe1-210">Na poniższej ilustracji przedstawiono podklucz i jego **wersję** wpisu dla .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-210">The following figure shows the subkey and its **Version** entry for the .NET Framework 3.5.</span></span>

    <span data-ttu-id="0dbe1-211">![Wpis rejestru dla .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 i wcześniejsze wersje")</span><span class="sxs-lookup"><span data-stu-id="0dbe1-211">![The registry entry for the .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

<a name="net_c"></a>

### <a name="find-net-framework-versions-182114-with-code"></a><span data-ttu-id="0dbe1-212">Znajdź .NET Framework wersje 1&#8211;4 z kodem</span><span class="sxs-lookup"><span data-stu-id="0dbe1-212">Find .NET Framework versions 1&#8211;4 with code</span></span>

- <span data-ttu-id="0dbe1-213">Użyj klasy <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType>, aby uzyskać dostęp do podklucza **rejestrze Framework Setup\NDP** w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-213">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** subkey in the Windows registry.</span></span>

<span data-ttu-id="0dbe1-214">Poniższy przykład umożliwia znalezienie zainstalowanych wersji .NET Framework&#8211;1 4:</span><span class="sxs-lookup"><span data-stu-id="0dbe1-214">The following example finds the .NET Framework 1&#8211;4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a><span data-ttu-id="0dbe1-215">Znajdź wersje środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="0dbe1-215">Find CLR versions</span></span>

<a name="clr_a"></a>

### <a name="find-the-current-clr-version-with-clrverexe"></a><span data-ttu-id="0dbe1-216">Znajdź bieżącą wersję środowiska CLR za pomocą Clrver. exe</span><span class="sxs-lookup"><span data-stu-id="0dbe1-216">Find the current CLR version with Clrver.exe</span></span>

<span data-ttu-id="0dbe1-217">Użyj [Narzędzia wersji środowiska CLR (Clrver. exe)](../tools/clrver-exe-clr-version-tool.md) , aby określić, które wersje środowiska CLR są zainstalowane na komputerze:</span><span class="sxs-lookup"><span data-stu-id="0dbe1-217">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer:</span></span>

- <span data-ttu-id="0dbe1-218">W [wiersz polecenia dla deweloperów dla programu Visual Studio](../tools/developer-command-prompt-for-vs.md)wprowadź `clrver`.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-218">From a [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), enter `clrver`.</span></span>

    <span data-ttu-id="0dbe1-219">Przykładowe dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0dbe1-219">Sample output:</span></span>

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="find-the-current-clr-version-with-the-environment-class"></a><span data-ttu-id="0dbe1-220">Znajdź bieżącą wersję środowiska CLR z klasą środowiska</span><span class="sxs-lookup"><span data-stu-id="0dbe1-220">Find the current CLR version with the Environment class</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0dbe1-221">W przypadku .NET Framework 4,5 i nowszych wersje nie należy używać właściwości <xref:System.Environment.Version%2A?displayProperty=nameWithType> do wykrywania wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-221">For the .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="0dbe1-222">Zamiast tego należy wykonać zapytanie dotyczące rejestru zgodnie z opisem w artykule [znajdowanie .NET Framework wersje 4,5 i nowsze z kodem](#net_d).</span><span class="sxs-lookup"><span data-stu-id="0dbe1-222">Instead, query the registry as described in [Find .NET Framework versions 4.5 and later with code](#net_d).</span></span>

1. <span data-ttu-id="0dbe1-223">Zbadaj Właściwość <xref:System.Environment.Version?displayProperty=nameWithType>, aby pobrać obiekt <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-223">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

    <span data-ttu-id="0dbe1-224">Zwrócony obiekt `System.Version` identyfikuje wersję środowiska uruchomieniowego, które aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-224">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="0dbe1-225">Nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogły zostać zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-225">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

    <span data-ttu-id="0dbe1-226">W przypadku .NET Framework w wersji 4, 4,5, 4.5.1 i 4.5.2 ciąg reprezentujący zwrócony obiekt <xref:System.Version> ma postać 4.0.30319. *XXXXX*, gdzie *XXXXX* jest mniejszy niż 42000.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-226">For the .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="0dbe1-227">W przypadku .NET Framework 4,6 i nowszych wersje ma postać 4.0.30319.42000.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-227">For the .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

2. <span data-ttu-id="0dbe1-228">Po utworzeniu obiektu `Version` wykonaj zapytanie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0dbe1-228">After you have the `Version` object, query it as follows:</span></span>

   - <span data-ttu-id="0dbe1-229">Aby uzyskać informacje o głównym identyfikatorze wydania (na przykład *4* dla wersji 4,0), użyj właściwości <xref:System.Version.Major%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-229">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="0dbe1-230">W przypadku pomocniczego identyfikatora wydania (na przykład *0* w przypadku wersji 4,0) użyj właściwości <xref:System.Version.Minor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-230">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="0dbe1-231">Dla całego ciągu wersji (na przykład *4.0.30319.18010*) użyj metody <xref:System.Version.ToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-231">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0dbe1-232">Ta metoda zwraca pojedynczą wartość odzwierciedlającą wersję środowiska uruchomieniowego, które wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-232">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="0dbe1-233">Nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogą być zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0dbe1-233">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

<span data-ttu-id="0dbe1-234">W poniższym przykładzie zastosowano Właściwość <xref:System.Environment.Version%2A?displayProperty=nameWithType> do pobrania informacji o wersji środowiska CLR:</span><span class="sxs-lookup"><span data-stu-id="0dbe1-234">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="0dbe1-235">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0dbe1-235">See also</span></span>

- [<span data-ttu-id="0dbe1-236">Instrukcje: Określanie, które aktualizacje .NET Framework są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="0dbe1-236">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="0dbe1-237">Zainstaluj .NET Framework dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="0dbe1-237">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="0dbe1-238">.NET Framework wersje i zależności</span><span class="sxs-lookup"><span data-stu-id="0dbe1-238">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
