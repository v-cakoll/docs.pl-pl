---
title: Narzędzie edytora konfiguracji (SvcConfigEditor.exe)
description: Dowiedz się, jak zarządzać ustawieniami powiązań, zachowań, usług i diagnostyki programu WCF przy użyciu edytora konfiguracji usługi WCF.
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: 258437ff616b969d40feabbfff364ad2cc6b25bc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247652"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a><span data-ttu-id="ea20d-103">Narzędzie edytora konfiguracji (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="ea20d-103">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>

<span data-ttu-id="ea20d-104">SvcConfigEditor.exe Edytor konfiguracji usługi Windows Communication Foundation (WCF) umożliwia administratorom i deweloperom tworzenie i modyfikowanie ustawień konfiguracji usług WCF przy użyciu graficznego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ea20d-104">The Windows Communication Foundation (WCF) Service Configuration Editor (SvcConfigEditor.exe) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="ea20d-105">Za pomocą tego narzędzia można zarządzać ustawieniami powiązań programu WCF, zachowań, usług i diagnostyki bez konieczności bezpośredniego edytowania plików konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="ea20d-105">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without having to directly edit XML configuration files.</span></span>

<span data-ttu-id="ea20d-106">Edytor konfiguracji usługi można znaleźć w folderze C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.</span><span class="sxs-lookup"><span data-stu-id="ea20d-106">Service Configuration Editor can be found in the C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin folder.</span></span>

## <a name="the-wcf-configuration-editor"></a><span data-ttu-id="ea20d-107">Edytor konfiguracji WCF</span><span class="sxs-lookup"><span data-stu-id="ea20d-107">The WCF Configuration Editor</span></span>

<span data-ttu-id="ea20d-108">Edytor konfiguracji usługi zawiera kreatora, który przeprowadzi Cię przez wszystkie kroki opisane w temacie Konfigurowanie usługi lub klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="ea20d-108">Service Configuration Editor comes with a wizard that guides you through all the steps in configuring a WCF service or client.</span></span> <span data-ttu-id="ea20d-109">Zdecydowanie zaleca się użycie Kreatora zamiast edytora bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="ea20d-109">You are strongly advised to use the wizard instead of the editor directly.</span></span>

<span data-ttu-id="ea20d-110">Jeśli masz już pewne pliki konfiguracji zgodne ze standardowym schematem System.Configwersja, możesz zarządzać określonymi ustawieniami powiązań, zachowań, usług i diagnostyki przy użyciu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ea20d-110">If you already have some configuration files that comply with the standard System.Configuration schema, you can manage specific settings for bindings, behavior, services, and diagnostics with the user interface.</span></span> <span data-ttu-id="ea20d-111">Edytor konfiguracji usługi umożliwia zarządzanie ustawieniami istniejących plików konfiguracji WCF oraz plikami wykonywalnymi, usługami COM+ i usługami hostowanymi w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ea20d-111">The Service Configuration Editor enables you to manage the settings for existing WCF configuration files as well as executable files, COM+ services, and Web-hosted services.</span></span> <span data-ttu-id="ea20d-112">Podczas otwierania usługi hostowanej w sieci Web za pomocą edytora konfiguracji usługi, są wyświetlane sekcje konfiguracja i dziedziczone konfiguracje usługi.</span><span class="sxs-lookup"><span data-stu-id="ea20d-112">When opening a Web-hosted service with Service Configuration Editor, both the service’s own configuration and inherited configurations sections of upper level nodes are shown.</span></span>

<span data-ttu-id="ea20d-113">Ponieważ ustawienia konfiguracji programu WCF znajdują się w `<system.serviceModel>` sekcji pliku konfiguracji, Edytor działa wyłącznie na zawartości tego elementu i nie uzyskuje dostępu do innych elementów w tym samym pliku.</span><span class="sxs-lookup"><span data-stu-id="ea20d-113">Because WCF configuration settings are located in the `<system.serviceModel>` section of the configuration file, the editor operates exclusively on the content of this element and does not access other elements in the same file.</span></span> <span data-ttu-id="ea20d-114">Możesz przejść do istniejących plików konfiguracji bezpośrednio lub wybrać zestaw, który zawiera usługę, katalog wirtualny lub usługę COM+.</span><span class="sxs-lookup"><span data-stu-id="ea20d-114">You can navigate to existing configuration files directly or you can select an assembly that contains a service, virtual directory, or COM+ service.</span></span> <span data-ttu-id="ea20d-115">Edytor ładuje plik konfiguracyjny dla danej usługi i zezwala użytkownikowi na dodawanie nowych elementów lub edytowanie istniejących elementów zagnieżdżonych w `<system.serviceModel>` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-115">The editor loads the configuration file for that particular service and allows the user to either add new elements or edit existing elements nested in the `<system.serviceModel>` section of the configuration file.</span></span>

<span data-ttu-id="ea20d-116">Edytor obsługuje funkcję IntelliSense i wymusza zgodność schematu.</span><span class="sxs-lookup"><span data-stu-id="ea20d-116">The editor supports IntelliSense and enforces schema compliance.</span></span> <span data-ttu-id="ea20d-117">Wynikowe dane wyjściowe są gwarantowane w celu zachowania zgodności ze schematem pliku konfiguracji i zawierają składniowo prawidłowe wartości danych.</span><span class="sxs-lookup"><span data-stu-id="ea20d-117">The resulting output is guaranteed to comply with the schema of the configuration file and to have syntactically correct data values.</span></span> <span data-ttu-id="ea20d-118">Jednak Edytor nie gwarantuje, że plik konfiguracji jest semantycznie prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ea20d-118">However, the editor does not guarantee that the configuration file is semantically valid.</span></span> <span data-ttu-id="ea20d-119">Innymi słowy, Edytor nie gwarantuje, że plik konfiguracji może współdziałać z usługą, którą konfiguruje.</span><span class="sxs-lookup"><span data-stu-id="ea20d-119">In other words, the editor does not guarantee that the configuration file can work with the service it configures.</span></span>

> [!CAUTION]
> <span data-ttu-id="ea20d-120">Edytor nie może przeczyścić elementu konfiguracji z pliku konfiguracji po zmodyfikowaniu elementu.</span><span class="sxs-lookup"><span data-stu-id="ea20d-120">The editor cannot purge a configuration element from the configuration file once you have modified the element.</span></span> <span data-ttu-id="ea20d-121">Na przykład, jeśli używasz edytora, aby ustawić nazwę punktu końcowego jako niepusty ciąg i zapisać go, plik konfiguracyjny ma następującą zawartość, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ea20d-121">For example, if you use the editor to set the endpoint name to a non-empty string and save it, the configuration file has the following content, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="somename" />`
>
> <span data-ttu-id="ea20d-122">Jeśli podjęto próbę usunięcia nazwy przez ustawienie jej jako pustego ciągu i zapisania pliku, plik konfiguracji nadal zawiera `name` atrybut, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ea20d-122">If you attempt to remove the name by setting it to an empty string and save the file, the configuration file still contains the `name` attribute, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="" />`
>
> <span data-ttu-id="ea20d-123">Aby przeczyścić atrybut, należy ręcznie edytować element przy użyciu innego edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="ea20d-123">To purge the attribute, you must manually edit the element using another text editor.</span></span>
>
> <span data-ttu-id="ea20d-124">W przypadku używania `issueToken` elementu zachowania punktu końcowego należy zachować szczególną ostrożność w przypadku tego problemu `clientCredential` .</span><span class="sxs-lookup"><span data-stu-id="ea20d-124">You should be especially careful with this issue when you use the `issueToken` element of the `clientCredential` Endpoint behavior.</span></span> <span data-ttu-id="ea20d-125">W przypadku `address` atrybutu jego `localIssuer` podelement nie może być pustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="ea20d-125">Specifically, the `address` attribute of its `localIssuer` sub-element must not be an empty string.</span></span> <span data-ttu-id="ea20d-126">Jeśli atrybut został zmodyfikowany `address` przy użyciu edytora konfiguracji i chcesz go całkowicie usunąć, należy to zrobić przy użyciu narzędzia innego niż Edytor.</span><span class="sxs-lookup"><span data-stu-id="ea20d-126">If you have modified the `address` attribute using the Configuration Editor and want to remove it completely, you should do so using a tool other than the Editor.</span></span> <span data-ttu-id="ea20d-127">W przeciwnym razie atrybut zawiera pusty ciąg, a aplikacja zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ea20d-127">Otherwise, the attribute contains an empty string and your application throws an exception.</span></span>

## <a name="using-the-configuration-editor"></a><span data-ttu-id="ea20d-128">Korzystanie z edytora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ea20d-128">Using the Configuration Editor</span></span>

<span data-ttu-id="ea20d-129">Edytor konfiguracji usługi można znaleźć w następującej Windows SDK lokalizacji instalacji:</span><span class="sxs-lookup"><span data-stu-id="ea20d-129">The Service Configuration Editor can be found at the following Windows SDK installation location:</span></span>

<span data-ttu-id="ea20d-130">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="ea20d-130">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span></span>

<span data-ttu-id="ea20d-131">Po uruchomieniu edytora konfiguracji usługi możesz użyć menu **plik/Otwórz** , aby przeglądać w poszukiwaniu usługi lub zestawu, którym chcesz zarządzać.</span><span class="sxs-lookup"><span data-stu-id="ea20d-131">After you launch the Service Configuration Editor, you can use the **File/Open** menu to browse for the service or assembly you want to manage.</span></span> <span data-ttu-id="ea20d-132">Pliki konfiguracji można otwierać bezpośrednio, przeglądać w poszukiwaniu usług WCF/COM + usługi i otwierać pliki konfiguracji dla usług hostowanych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ea20d-132">You can open configuration files directly, browse for WCF /COM+ services, and open configuration files for Web-hosted services.</span></span>

<span data-ttu-id="ea20d-133">Interfejs użytkownika edytora konfiguracji usługi jest podzielony na następujące obszary:</span><span class="sxs-lookup"><span data-stu-id="ea20d-133">The Service Configuration Editor's user interface is divided into the following areas:</span></span>

- <span data-ttu-id="ea20d-134">Okienko widoku drzewa, które wyświetla elementy konfiguracji w strukturze drzewa po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="ea20d-134">Tree View Pane, which displays configuration elements in a tree structure on the left.</span></span> <span data-ttu-id="ea20d-135">Aby wykonać operacje w drzewie, kliknij prawym przyciskiem myszy węzły.</span><span class="sxs-lookup"><span data-stu-id="ea20d-135">You can perform operations in the tree by right-clicking the nodes.</span></span>

- <span data-ttu-id="ea20d-136">Okienko zadań, które wyświetla typowe zadania dla bieżących elementów w lewym dolnym rogu okna</span><span class="sxs-lookup"><span data-stu-id="ea20d-136">Task Pane, which displays common tasks for current elements on the lower-left of the window</span></span>

- <span data-ttu-id="ea20d-137">Okienko szczegółów, w którym są wyświetlane szczegółowe ustawienia węzła konfiguracji wybranego w widoku drzewa po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="ea20d-137">Detail Pane, which displays detailed settings of the configuration node selected in the Tree View on the right.</span></span>

### <a name="opening-a-configuration-file"></a><span data-ttu-id="ea20d-138">Otwieranie pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ea20d-138">Opening a Configuration File</span></span>

1. <span data-ttu-id="ea20d-139">Uruchom Edytor konfiguracji usługi przy użyciu okna wiersza polecenia, aby przejść do lokalizacji instalacji programu WCF, a następnie wpisz polecenie `SvcConfigEditor.exe` .</span><span class="sxs-lookup"><span data-stu-id="ea20d-139">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="ea20d-140">Z menu **plik** wybierz polecenie **Otwórz** , a następnie kliknij typ pliku, którym chcesz zarządzać.</span><span class="sxs-lookup"><span data-stu-id="ea20d-140">From the **File** menu, select **Open** and click the type of file you want to manage.</span></span>

3. <span data-ttu-id="ea20d-141">W oknie dialogowym **otwieranie** przejdź do określonego pliku, który chcesz zarządzać, a następnie kliknij go dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="ea20d-141">In the **Open** dialog box, navigate to the specific file you want to manage and double-click it.</span></span>

<span data-ttu-id="ea20d-142">Przeglądarka automatycznie postępuje zgodnie ze ścieżką scalania konfiguracji i tworzy widok Scalonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-142">The viewer automatically follows the configuration merge path and creates a view of the merged configuration.</span></span> <span data-ttu-id="ea20d-143">Na przykład rzeczywista konfiguracja usługi niehostowanej to kombinacja Machine.config i App.config. Wszystkie zmiany są stosowane do aktywnego pliku w SvcConfigEditor.</span><span class="sxs-lookup"><span data-stu-id="ea20d-143">For example, the actual configuration of a non-hosted service is a combination of Machine.config and App.config. Any changes are applied to the active file in the SvcConfigEditor.</span></span> <span data-ttu-id="ea20d-144">Jeśli chcesz edytować konkretny plik w ścieżce scalania konfiguracji, należy otworzyć go bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="ea20d-144">If you want to edit a specific file in the configuration merge path, you should open it directly.</span></span>

> [!NOTE]
> <span data-ttu-id="ea20d-145">Edytor konfiguracji ponownie ładuje aktualnie otwarty plik konfiguracji, gdy ten ostatni został zmodyfikowany poza edytorem.</span><span class="sxs-lookup"><span data-stu-id="ea20d-145">Configuration Editor reloads the currently opened configuration file when the latter has been modified outside the Editor.</span></span> <span data-ttu-id="ea20d-146">W takim przypadku wszystkie zmiany, które nie zostały trwale zapisane w edytorze, zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="ea20d-146">When this happens, all the changes that are not durably saved inside the Editor are lost.</span></span> <span data-ttu-id="ea20d-147">Jeśli ponowne ładowanie odbywa się konsekwentnie, najbardziej prawdopodobną przyczyną jest usługa, która stale uzyskuje dostęp do pliku konfiguracji, na przykład oprogramowania antywirusowego działającego w tle.</span><span class="sxs-lookup"><span data-stu-id="ea20d-147">If reloading happens consistently, the most likely cause is a service that constantly accesses the configuration file, for example, an antivirus software running in the background.</span></span> <span data-ttu-id="ea20d-148">Aby rozwiązać ten problem, upewnij się, że Edytor konfiguracji jest jedynym procesem, który ma dostęp do pliku po jego otwarciu.</span><span class="sxs-lookup"><span data-stu-id="ea20d-148">To resolve this, ensure that Configuration Editor is the only process that can access the file when it is opened.</span></span>

### <a name="services"></a><span data-ttu-id="ea20d-149">Usługi</span><span class="sxs-lookup"><span data-stu-id="ea20d-149">Services</span></span>

<span data-ttu-id="ea20d-150">W węźle **usługi** są wyświetlane wszystkie usługi aktualnie przypisane w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-150">The **Services** node displays all of the services currently assigned in the configuration file.</span></span> <span data-ttu-id="ea20d-151">Każdy podwęzeł w drzewie odnosi się do podrzędnego elementu <`services`> elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-151">Each sub-node in the tree corresponds to a sub-element of the <`services`> element in the configuration file.</span></span>

<span data-ttu-id="ea20d-152">Po kliknięciu węzła **usługi** można wyświetlić lub wykonać zadania na stronie Podsumowanie usługi w okienku **szczegółów** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-152">When you click the **Services** node, you can view or perform tasks on the service Summary Page in the **Detail** Pane.</span></span>

#### <a name="creating-a-new-service-configuration"></a><span data-ttu-id="ea20d-153">Tworzenie nowej konfiguracji usługi</span><span class="sxs-lookup"><span data-stu-id="ea20d-153">Creating a new Service Configuration</span></span>

<span data-ttu-id="ea20d-154">Nową konfigurację usługi można utworzyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ea20d-154">You can create a new service configuration in the following ways:</span></span>

- <span data-ttu-id="ea20d-155">Korzystanie z kreatora: kliknij link **Utwórz nową usługę...**</span><span class="sxs-lookup"><span data-stu-id="ea20d-155">Using a Wizard: Click the link **Create a New Service…**</span></span> <span data-ttu-id="ea20d-156">Aby uruchomić kreatora, w okienku zadań lub stronie podsumowania.</span><span class="sxs-lookup"><span data-stu-id="ea20d-156">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="ea20d-157">Można to również zrobić w menu **plik** — > **dodać nowy element**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-157">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="ea20d-158">Utwórz ręcznie: możesz kliknąć prawym przyciskiem myszy węzeł **usługi** i wybrać polecenie **Nowa usługa**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-158">Create manually: You can right-click the **Services** node and choose **New Service**.</span></span>

#### <a name="creating-a-new-service-endpoint-configuration"></a><span data-ttu-id="ea20d-159">Tworzenie nowej konfiguracji punktu końcowego usługi</span><span class="sxs-lookup"><span data-stu-id="ea20d-159">Creating a new Service Endpoint Configuration</span></span>

<span data-ttu-id="ea20d-160">Nową konfigurację punktu końcowego usługi można utworzyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ea20d-160">You can create a new service endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="ea20d-161">Utwórz za pomocą kreatora: kliknij link **Utwórz nowy punkt końcowy usługi...**</span><span class="sxs-lookup"><span data-stu-id="ea20d-161">Create using a Wizard: click the link **Create a New Service Endpoint…**</span></span> <span data-ttu-id="ea20d-162">Aby uruchomić kreatora, w okienku zadań lub stronie podsumowania.</span><span class="sxs-lookup"><span data-stu-id="ea20d-162">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="ea20d-163">Można to również zrobić w menu **plik** — > **dodać nowy element**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-163">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="ea20d-164">Utwórz ręcznie: po utworzeniu usługi można kliknąć prawym przyciskiem myszy węzeł **punkty końcowe** i wybrać pozycję "**nowy punkt końcowy usługi**".</span><span class="sxs-lookup"><span data-stu-id="ea20d-164">Create manually: Once you created a Service, you can right-click the **Endpoints** node and choose "**New Service Endpoint**".</span></span>

#### <a name="editing-a-service-configuration"></a><span data-ttu-id="ea20d-165">Edytowanie konfiguracji usługi</span><span class="sxs-lookup"><span data-stu-id="ea20d-165">Editing a Service Configuration</span></span>

1. <span data-ttu-id="ea20d-166">Kliknij węzeł **usługi** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-166">Click a **Service** node.</span></span>

2. <span data-ttu-id="ea20d-167">Edytuj ustawienia w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="ea20d-167">Edit the settings in the property grids.</span></span>

#### <a name="editing-a-service-endpoint-configuration"></a><span data-ttu-id="ea20d-168">Edytowanie konfiguracji punktu końcowego usługi</span><span class="sxs-lookup"><span data-stu-id="ea20d-168">Editing a Service Endpoint Configuration</span></span>

1. <span data-ttu-id="ea20d-169">Kliknij węzeł **punktu końcowego usługi** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-169">Click a **Service Endpoint** node.</span></span>

2. <span data-ttu-id="ea20d-170">Edytuj ustawienia w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="ea20d-170">Edit the settings in the property grids.</span></span>

#### <a name="adding-a-base-address"></a><span data-ttu-id="ea20d-171">Dodawanie adresu podstawowego</span><span class="sxs-lookup"><span data-stu-id="ea20d-171">Adding a Base Address</span></span>

1. <span data-ttu-id="ea20d-172">Kliknij węzeł **hosta** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-172">Click the **Host** node.</span></span>

2. <span data-ttu-id="ea20d-173">Kliknij **Nowy...**</span><span class="sxs-lookup"><span data-stu-id="ea20d-173">Click the **New…**</span></span> <span data-ttu-id="ea20d-174">w sekcji **adresy podstawowe** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-174">button in the **Base Addresses** section.</span></span>

3. <span data-ttu-id="ea20d-175">W oknie dialogowym wpisz adres URI adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="ea20d-175">Type in the base address URI in the dialog box.</span></span>

4. <span data-ttu-id="ea20d-176">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-176">Click **OK**.</span></span>

> [!NOTE]
> <span data-ttu-id="ea20d-177">Nie można edytować wartości [\<baseAddressPrefixFilters>](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) wewnątrz tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="ea20d-177">You cannot edit the value of [\<baseAddressPrefixFilters>](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) inside this tool.</span></span> <span data-ttu-id="ea20d-178">Aby dodać lub zmodyfikować ten element, należy użyć edytora tekstu lub programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ea20d-178">To add or modify this element, you should use a text editor or Visual Studio.</span></span>

### <a name="client"></a><span data-ttu-id="ea20d-179">Klient</span><span class="sxs-lookup"><span data-stu-id="ea20d-179">Client</span></span>

<span data-ttu-id="ea20d-180">W węźle **klienta** są wyświetlane wszystkie punkty końcowe klienta w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-180">The **Client** node displays all of the client endpoints in the configuration file.</span></span> <span data-ttu-id="ea20d-181">Każdy podwęzeł w drzewie odnosi się do podrzędnego elementu <`client`> elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-181">Every sub-node in the tree corresponds to a sub-element of the <`client`> element in the configuration file.</span></span>

<span data-ttu-id="ea20d-182">Po kliknięciu węzła **klienta** można wyświetlić lub wykonać zadania na **stronie Podsumowanie** klienta w **okienku szczegółów**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-182">When you click the **Client** node, you can view or perform tasks on the client **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-client-endpoint-configuration"></a><span data-ttu-id="ea20d-183">Tworzenie nowej konfiguracji punktu końcowego klienta</span><span class="sxs-lookup"><span data-stu-id="ea20d-183">Creating a new Client Endpoint Configuration</span></span>

<span data-ttu-id="ea20d-184">Nową konfigurację punktu końcowego klienta można utworzyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ea20d-184">You can create a new client endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="ea20d-185">Utwórz przez kreatora: kliknij link **Utwórz nowego klienta...**</span><span class="sxs-lookup"><span data-stu-id="ea20d-185">Create by Wizard: Click the link **Create a New Client…**</span></span> <span data-ttu-id="ea20d-186">w **okienku zadań** w dolnej części okna lub **stronie podsumowania** , aby uruchomić kreatora.</span><span class="sxs-lookup"><span data-stu-id="ea20d-186">on the **Task Pane** on the lower-left of the window, or **Summary Page** to launch the wizard.</span></span> <span data-ttu-id="ea20d-187">Można to również zrobić w menu **plik** — > **dodać nowy element**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-187">You can also do so in the **File** menu -> **Add New Item**.</span></span> <span data-ttu-id="ea20d-188">Kreator poprosi o wskazanie lokalizacji konfiguracji usługi, z której jest generowana konfiguracja klienta.</span><span class="sxs-lookup"><span data-stu-id="ea20d-188">The wizard prompts you to point to the location of the service configuration, from which the client configuration is generated.</span></span> <span data-ttu-id="ea20d-189">Następnie można wybrać punkt końcowy usługi, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="ea20d-189">You can then choose the service endpoint to connect to.</span></span>

- <span data-ttu-id="ea20d-190">Utwórz ręcznie: kliknij prawym przyciskiem myszy węzeł **punkty końcowe** w obszarze **Klient**, a następnie wybierz polecenie **nowy punkt końcowy klienta**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-190">Create manually: Right-click the **Endpoints** node under **Client**, and choose **New Client Endpoint**.</span></span>

#### <a name="editing-a-client-endpoint-configuration"></a><span data-ttu-id="ea20d-191">Edytowanie konfiguracji punktu końcowego klienta</span><span class="sxs-lookup"><span data-stu-id="ea20d-191">Editing a Client Endpoint Configuration</span></span>

1. <span data-ttu-id="ea20d-192">Kliknij węzeł **punktu końcowego klienta** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-192">Click a **Client Endpoint** node.</span></span>

2. <span data-ttu-id="ea20d-193">Edytuj ustawienia w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="ea20d-193">Edit the settings in the property grids.</span></span>

### <a name="standard-endpoint"></a><span data-ttu-id="ea20d-194">Standardowy punkt końcowy</span><span class="sxs-lookup"><span data-stu-id="ea20d-194">Standard Endpoint</span></span>

<span data-ttu-id="ea20d-195">Standardowe punkty końcowe to wyspecjalizowane punkty końcowe, które mają co najmniej jeden aspekt adresu, kontraktu i powiązania ustawione na wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="ea20d-195">Standard endpoints are specialized endpoints that have one or more aspects of the address, contract and binding set to default values.</span></span>

<span data-ttu-id="ea20d-196">Takie ustawienia konfiguracji są przechowywane w **standardowym węźle punktu końcowego** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-196">Such configuration settings are stored in the **Standard Endpoint** node.</span></span> <span data-ttu-id="ea20d-197">**Standardowy węzeł punktu końcowego** wyświetla wszystkie standardowe ustawienia punktu końcowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-197">The **Standard Endpoint** node displays all of the standard endpoint settings in the configuration file.</span></span> <span data-ttu-id="ea20d-198">Każdy podwęzeł w drzewie odnosi się do elementu podrzędnego w `<standardEndpoints>` elemencie w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-198">Every sub-node in the tree corresponds to a sub-element in the `<standardEndpoints>` element in the configuration file.</span></span>

<span data-ttu-id="ea20d-199">Po kliknięciu węzła **standardowego punktu końcowego** można wyświetlić lub wykonać zadania na **stronie Podsumowanie** standardowego punktu końcowego w **okienku szczegółów**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-199">When you click the **Standard Endpoint** node, you can view or perform tasks on the standard endpoint **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-standard-endpoint-configuration"></a><span data-ttu-id="ea20d-200">Tworzenie nowej konfiguracji standardowego punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="ea20d-200">Creating a New Standard Endpoint Configuration</span></span>

<span data-ttu-id="ea20d-201">Nową konfigurację standardowego punktu końcowego można utworzyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ea20d-201">You can create a new standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="ea20d-202">Kliknij prawym przyciskiem myszy **Standardowy węzeł punktu końcowego** i wybierz pozycję **Nowa Standardowa konfiguracja punktu końcowego...**</span><span class="sxs-lookup"><span data-stu-id="ea20d-202">Right-click the **Standard Endpoint** node and select **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="ea20d-203">W oknie dialogowym Wybierz typ powiązania i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-203">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="ea20d-204">Wybierz węzeł **standardowego punktu końcowego** , a następnie kliknij pozycję **Nowa Standardowa konfiguracja punktu końcowego...**</span><span class="sxs-lookup"><span data-stu-id="ea20d-204">Select the **Standard Endpoint** node and click **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="ea20d-205">w **okienku zadań** w lewym dolnym rogu okna.</span><span class="sxs-lookup"><span data-stu-id="ea20d-205">in the **Task Pane** on the lower-left of the window.</span></span>

<span data-ttu-id="ea20d-206">W oknie dialogowym **Tworzenie nowego standardowego punktu końcowego** zostaną wyświetlone wszystkie zarejestrowane standardowe typy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ea20d-206">The **Creating a New Standard Endpoint** dialog box displays and lists all registered standard endpoint types.</span></span>

#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a><span data-ttu-id="ea20d-207">Wyświetlanie i edytowanie standardowej konfiguracji punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="ea20d-207">Viewing and Editing a Standard Endpoint Configuration</span></span>

<span data-ttu-id="ea20d-208">Konfigurację standardowego punktu końcowego można otworzyć do wyświetlania i edytowania w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ea20d-208">You can open a standard endpoint configuration for viewing and editing in the following ways:</span></span>

- <span data-ttu-id="ea20d-209">Kliknij, aby rozwinąć węzeł **standardowego punktu końcowego** , a następnie kliknij odpowiedni podwęzeł punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ea20d-209">Click to expand the **Standard Endpoint** node and click the respective endpoint sub-node.</span></span>

- <span data-ttu-id="ea20d-210">Kliknij węzeł **standardowego punktu końcowego** , a następnie kliknij odpowiedni punkt końcowy w okienku szczegółów.</span><span class="sxs-lookup"><span data-stu-id="ea20d-210">Click the **Standard Endpoint** node and click the respective endpoint on the Detail pane.</span></span>

<span data-ttu-id="ea20d-211">Atrybuty punktu końcowego są wyświetlane w okienku po prawej stronie do edycji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-211">Attributes for the endpoint are shown in the right pane for editing.</span></span>

#### <a name="deleting-a-standard-endpoint-configuration"></a><span data-ttu-id="ea20d-212">Usuwanie standardowej konfiguracji punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="ea20d-212">Deleting a Standard Endpoint Configuration</span></span>

<span data-ttu-id="ea20d-213">Konfigurację standardowego punktu końcowego można usunąć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ea20d-213">You can delete a standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="ea20d-214">Kliknij, aby rozwinąć węzeł **standardowego punktu końcowego** , a następnie kliknij prawym przyciskiem myszy odpowiedni podwęzeł punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ea20d-214">Click to expand the **Standard Endpoint** node and right-click the respective endpoint sub-node.</span></span> <span data-ttu-id="ea20d-215">Użyj polecenia kontekstowego **Usuń konfigurację standardowego punktu końcowego** , aby usunąć punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="ea20d-215">Use the context command **Delete Standard Endpoint Configuration** to delete the endpoint.</span></span>

- <span data-ttu-id="ea20d-216">Kliknij węzeł **standardowego punktu końcowego** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-216">Click the **Standard Endpoint** node.</span></span> <span data-ttu-id="ea20d-217">W okienku **zadań** kliknij pozycję **Usuń konfigurację standardowego punktu końcowego**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-217">In the **Task** pane, click **Delete Standard Endpoint Configuration**.</span></span>

<span data-ttu-id="ea20d-218">Jeśli standardowy punkt końcowy jest używany, podczas próby usunięcia zostanie wyświetlony komunikat ostrzegawczy: **Standardowy punkt końcowy jest w użyciu. Jeśli usuniesz ją teraz, pamiętaj, aby usunąć wszystkie odwołania do innych części konfiguracji (na przykład w punkcie końcowym usługi lub w punkcie końcowym klienta). W przeciwnym razie konfiguracja będzie nieprawidłowa i nie będzie można jej otworzyć następnym razem. Czy na pewno chcesz usunąć standardowy punkt końcowy? "**</span><span class="sxs-lookup"><span data-stu-id="ea20d-218">If the standard endpoint is in used, a warning message is displayed when you attempt to delete it: **The standard endpoint is in use. If you delete it now, please be sure to delete all of its references in other parts of the configuration (for example, in the service endpoint or client endpoint). Otherwise, the configuration will be invalid and cannot be opened next time. Are you sure you want to delete the standard endpoint?"**</span></span>

### <a name="binding"></a><span data-ttu-id="ea20d-219">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="ea20d-219">Binding</span></span>

<span data-ttu-id="ea20d-220">Konfiguracje powiązań są używane do konfigurowania powiązań dla punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ea20d-220">Binding configurations are used to configure bindings on endpoints.</span></span> <span data-ttu-id="ea20d-221">Takie ustawienia konfiguracji są przechowywane w węźle **powiązania** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-221">Such configuration settings are stored in the **Binding** node.</span></span> <span data-ttu-id="ea20d-222">Odniesienia do konfiguracji powiązań odwołań według nazwy i wielu punktów końcowych mogą odwoływać się do konfiguracji pojedynczego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ea20d-222">Endpoints reference binding configurations by name and multiple endpoints can reference a single binding configuration.</span></span>

<span data-ttu-id="ea20d-223">W węźle **powiązania** są wyświetlane wszystkie ustawienia powiązań w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-223">The **Bindings** node displays all of the binding settings in the configuration file.</span></span> <span data-ttu-id="ea20d-224">Każdy podwęzeł w drzewie odnosi się do elementu podrzędnego w <`bindings`> elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-224">Every sub-node in the tree corresponds to a sub-element in the <`bindings`> element in the configuration file.</span></span>

<span data-ttu-id="ea20d-225">Po kliknięciu węzła **powiązania** można wyświetlić lub wykonać zadania na **stronie Podsumowanie** powiązań w **okienku szczegółów**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-225">When you click the **Bindings** node, you can view or perform tasks on the binding **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-binding-configuration"></a><span data-ttu-id="ea20d-226">Tworzenie nowej konfiguracji powiązania</span><span class="sxs-lookup"><span data-stu-id="ea20d-226">Creating a New Binding Configuration</span></span>

<span data-ttu-id="ea20d-227">Nową konfigurację powiązania można utworzyć w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ea20d-227">You can create a new binding configuration in the following ways.</span></span>

- <span data-ttu-id="ea20d-228">Kliknij prawym przyciskiem myszy węzeł **powiązania** i wybierz pozycję **Nowa konfiguracja powiązania**...</span><span class="sxs-lookup"><span data-stu-id="ea20d-228">Right-click the **Bindings** node and select **New Binding Configuration**…</span></span> <span data-ttu-id="ea20d-229">W oknie dialogowym Wybierz typ powiązania i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-229">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="ea20d-230">Wybierz węzeł **powiązania** , a następnie kliknij pozycję **Nowa konfiguracja powiązania**...</span><span class="sxs-lookup"><span data-stu-id="ea20d-230">Select the **Bindings** node and click **New Binding Configuration**…</span></span> <span data-ttu-id="ea20d-231">w **okienku zadań** w lewym dolnym rogu okna.</span><span class="sxs-lookup"><span data-stu-id="ea20d-231">in the **Task Pane** on the lower-left of the window.</span></span>

- <span data-ttu-id="ea20d-232">Na stronie Podsumowanie usługi lub klienta kliknij przycisk **kliknij, aby utworzyć** w polu **Konfiguracja powiązania** , aby utworzyć konfigurację powiązania dla odpowiedniego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ea20d-232">In the service or client summary page, click **Click to Create** in the **Binding Configuration** field to create a binding configuration for the corresponding endpoint.</span></span>

#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a><span data-ttu-id="ea20d-233">Dodawanie rozszerzeń elementu wiązania do niestandardowego powiązania</span><span class="sxs-lookup"><span data-stu-id="ea20d-233">Adding Binding Element Extensions to a Custom Binding</span></span>

1. <span data-ttu-id="ea20d-234">Wybierz powiązanie, do którego chcesz dodać element rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="ea20d-234">Select the binding you want to add an extension element to.</span></span>

2. <span data-ttu-id="ea20d-235">Kliknij pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-235">Click **Add**.</span></span>

3. <span data-ttu-id="ea20d-236">Z listy dostępnych rozszerzeń wybierz rozszerzenie elementu powiązania, które chcesz dodać.</span><span class="sxs-lookup"><span data-stu-id="ea20d-236">From the list of available extensions, select the binding element extension you want to add.</span></span> <span data-ttu-id="ea20d-237">Aby zaznaczyć wiele elementów, naciśnij jednocześnie klawisz CTRL.</span><span class="sxs-lookup"><span data-stu-id="ea20d-237">To select multiple items, press the CTRL key simultaneously.</span></span>

4. <span data-ttu-id="ea20d-238">Kliknij pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-238">Click **Add**.</span></span>

#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a><span data-ttu-id="ea20d-239">Dopasowanie położenia rozszerzenia w niestandardowym powiązaniu</span><span class="sxs-lookup"><span data-stu-id="ea20d-239">Adjusting the Extension Position in a Custom Binding</span></span>

<span data-ttu-id="ea20d-240">Niestandardowe powiązanie to kolekcja elementów powiązania, które tworzą stos.</span><span class="sxs-lookup"><span data-stu-id="ea20d-240">A custom binding is a collection of binding elements that form a stack.</span></span> <span data-ttu-id="ea20d-241">Każdy element powiązania na stosie ma własne ustawienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-241">Each binding element on the stack has its own configuration settings.</span></span> <span data-ttu-id="ea20d-242">Kolejność rozszerzeń elementu powiązania w niestandardowym powiązaniu wskazuje ich położenie w stosie.</span><span class="sxs-lookup"><span data-stu-id="ea20d-242">The order of the binding element extensions in a custom binding indicates their positions in the stack.</span></span> <span data-ttu-id="ea20d-243">Elementy w górnej części stosu są stosowane najpierw.</span><span class="sxs-lookup"><span data-stu-id="ea20d-243">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="ea20d-244">Aby zmienić kolejność:</span><span class="sxs-lookup"><span data-stu-id="ea20d-244">To change the ordering:</span></span>

1. <span data-ttu-id="ea20d-245">Wybierz węzeł niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ea20d-245">Select the custom binding node.</span></span>

2. <span data-ttu-id="ea20d-246">Wybierz jeden element rozszerzenia powiązania w sekcji **pozycja rozszerzenia elementu powiązania** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-246">Select one binding extension element in the **Binding Element Extension Position** section.</span></span>

3. <span data-ttu-id="ea20d-247">Użyj przycisku w **górę** lub w **dół** z lewej strony listy, aby zmienić pozycję wybranego elementu.</span><span class="sxs-lookup"><span data-stu-id="ea20d-247">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a><span data-ttu-id="ea20d-248">Edytowanie konfiguracji rozszerzeń elementu powiązania w niestandardowym powiązaniu</span><span class="sxs-lookup"><span data-stu-id="ea20d-248">Editing the Configuration of Binding Element Extensions in a Custom Binding</span></span>

1. <span data-ttu-id="ea20d-249">Wybierz węzeł powiązanie w drzewie.</span><span class="sxs-lookup"><span data-stu-id="ea20d-249">Select the binding node in the tree.</span></span>

2. <span data-ttu-id="ea20d-250">Wybierz niestandardowe powiązanie, które zawiera element, który chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="ea20d-250">Select the custom binding that contains the element you want to edit.</span></span>

3. <span data-ttu-id="ea20d-251">Wybierz rozszerzenie elementu powiązania, które chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="ea20d-251">Select the binding element extension you want to edit.</span></span> <span data-ttu-id="ea20d-252">Ustawienia elementu są wyświetlane w okienku po prawej stronie, gdzie mogą być edytowane.</span><span class="sxs-lookup"><span data-stu-id="ea20d-252">The settings of the element appear in the right pane, where they can be edited.</span></span>

### <a name="diagnostics"></a><span data-ttu-id="ea20d-253">Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="ea20d-253">Diagnostics</span></span>

<span data-ttu-id="ea20d-254">W węźle **Diagnostyka** są wyświetlane wszystkie ustawienia diagnostyczne w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-254">The **Diagnostics** node displays all of the diagnostic settings in the configuration file.</span></span> <span data-ttu-id="ea20d-255">Umożliwia włączenie lub wyłączenie liczników wydajności, włączenie lub wyłączenie Instrumentacja zarządzania Windows (WMI), skonfigurowanie śledzenia WCF i skonfigurowanie rejestrowania komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="ea20d-255">It enables you to turn performance counters on or off, enable or disable Windows Management Instrumentation (WMI), configure WCF tracing, and configure WCF message logging.</span></span> <span data-ttu-id="ea20d-256">Ustawienia w węźle **Diagnostyka** odpowiadają `system.diagnostics` sekcji <> i `<diagnostics>` sekcji w `<system.serviceModel>` pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-256">The settings in the **Diagnostics** node correspond to the <`system.diagnostics`> section, and `<diagnostics>` section in `<system.serviceModel>` in the configuration file.</span></span>

<span data-ttu-id="ea20d-257">Po kliknięciu węzła **Diagnostyka** można wyświetlić lub wykonać zadania na **stronie podsumowania** diagnostyki w **okienku szczegółów**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-257">When you click the **Diagnostics** node, you can view or perform tasks on the diagnostics **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="configuring-performance-counters-and-wmi"></a><span data-ttu-id="ea20d-258">Konfigurowanie liczników wydajności i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="ea20d-258">Configuring performance counters and WMI</span></span>

1. <span data-ttu-id="ea20d-259">Kliknij węzeł **Diagnostyka** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-259">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="ea20d-260">Kliknij pozycję **Przełącz liczniki wydajności**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-260">Click **Toggle Performance Counters**.</span></span> <span data-ttu-id="ea20d-261">Licznik wydajności ma trzy stany: wyłączone (wartość domyślna), tylko serviceI ALL.</span><span class="sxs-lookup"><span data-stu-id="ea20d-261">The performance counter has three states: Off (default), ServiceOnly, and All.</span></span> <span data-ttu-id="ea20d-262">Kliknięcie linku powoduje przełączenie tego ustawienia między tymi trzema stanami.</span><span class="sxs-lookup"><span data-stu-id="ea20d-262">Clicking the link toggles the setting among these three states.</span></span>

#### <a name="configuring-wmi-provider"></a><span data-ttu-id="ea20d-263">Konfigurowanie dostawcy WMI</span><span class="sxs-lookup"><span data-stu-id="ea20d-263">Configuring WMI Provider</span></span>

1. <span data-ttu-id="ea20d-264">Kliknij węzeł **Diagnostyka** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-264">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="ea20d-265">Aby włączyć dostawcę usługi WMI, kliknij link **Włącz dostawcę WMI** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-265">To enable WMI provider, click the **Enable WMI Provider** link.</span></span>

#### <a name="enabling-wcf-tracing"></a><span data-ttu-id="ea20d-266">Włączanie śledzenia WCF</span><span class="sxs-lookup"><span data-stu-id="ea20d-266">Enabling WCF Tracing</span></span>

<span data-ttu-id="ea20d-267">Można utworzyć plik śledzenia WCF ze standardowymi właściwościami lub skonfigurować niestandardowy plik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ea20d-267">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="ea20d-268">Kliknij węzeł **Diagnostyka** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-268">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="ea20d-269">Kliknij pozycję **Włącz śledzenie**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-269">Click **Enable Tracing**.</span></span>

3. <span data-ttu-id="ea20d-270">Kliknij link **poziom śledzenia** , aby dostosować poziom śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ea20d-270">Click the **Trace Level** link to adjust the trace level.</span></span> <span data-ttu-id="ea20d-271">Istnieje sześć poziomów śledzenia: wyłączone, krytyczne, błąd, ostrzeżenie, informacje i pełne.</span><span class="sxs-lookup"><span data-stu-id="ea20d-271">There are six trace levels: Off, Critical, Error, Warning, Information, and Verbose.</span></span> <span data-ttu-id="ea20d-272">Opcja **śledzenie działań** i **propagowanie** działań umożliwia korzystanie z funkcji śledzenia działań programu WCF.</span><span class="sxs-lookup"><span data-stu-id="ea20d-272">The **Activity Tracing** and **Propagate Activity** option enable you to use the WCF activity tracing feature.</span></span>

4. <span data-ttu-id="ea20d-273">Kliknij nazwę odbiornika śledzenia, aby określić plik śledzenia i opcje.</span><span class="sxs-lookup"><span data-stu-id="ea20d-273">Click the trace listener name to specify the trace file and options.</span></span>

#### <a name="enabling-wcf-logging"></a><span data-ttu-id="ea20d-274">Włączanie rejestrowania WCF</span><span class="sxs-lookup"><span data-stu-id="ea20d-274">Enabling WCF Logging</span></span>

<span data-ttu-id="ea20d-275">Można utworzyć plik śledzenia WCF ze standardowymi właściwościami lub skonfigurować niestandardowy plik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ea20d-275">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="ea20d-276">Kliknij węzeł **Diagnostyka** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-276">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="ea20d-277">Kliknij pozycję **Włącz rejestrowanie komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-277">Click **Enable Message Logging**.</span></span>

3. <span data-ttu-id="ea20d-278">Kliknij link **poziom rejestrowania** , aby dostosować poziom rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="ea20d-278">Click the **Log Level** link to adjust the log level.</span></span> <span data-ttu-id="ea20d-279">Istnieją trzy poziomy dziennika: źle sformułowane, usługa i transport.</span><span class="sxs-lookup"><span data-stu-id="ea20d-279">There are three log levels: Malformed, Service, and Transport.</span></span>

4. <span data-ttu-id="ea20d-280">Kliknij nazwę odbiornika, aby określić plik dziennika i opcje.</span><span class="sxs-lookup"><span data-stu-id="ea20d-280">Click the listener name to specify the log file and options.</span></span>

> [!NOTE]
> <span data-ttu-id="ea20d-281">Jeśli chcesz, aby dzienniki śledzenia i komunikatów były opróżniane automatycznie po zamknięciu aplikacji, Włącz opcję **automatycznego opróżniania** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-281">If you want the trace and message logs to be flushed automatically when your application is closed, enable the **Auto Flush** option.</span></span>

<span data-ttu-id="ea20d-282">**Strona podsumowania** **diagnostyki** umożliwia wykonywanie najbardziej typowych zadań związanych z konfigurowaniem diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="ea20d-282">The **Diagnostics** **Summary Page** enables you to accomplish the most common tasks in configuring diagnostics.</span></span> <span data-ttu-id="ea20d-283">Jeśli jednak chcesz ręcznie edytować ustawienia odbiorników i źródeł, należy rozwinąć węzeł **Diagnostyka** i edytować ustawienia w węźle **Rejestrowanie komunikatów**, **odbiorniki** i **źródła** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-283">However, if you want to manually edit the Listeners and Sources settings, you must expand the **Diagnostics** node and edit settings in **Message Logging**, **Listeners** and **Sources** node.</span></span>

#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a><span data-ttu-id="ea20d-284">Włączanie śledzenia niestandardowego programu WCF lub rejestrowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="ea20d-284">Enabling WCF Custom Tracing or Message Logging</span></span>

1. <span data-ttu-id="ea20d-285">Kliknij węzeł **Diagnostyka** i rozwiń go.</span><span class="sxs-lookup"><span data-stu-id="ea20d-285">Click the **Diagnostics** node, and expand it.</span></span>

2. <span data-ttu-id="ea20d-286">Kliknij prawym przyciskiem myszy węzeł **detektory** i wybierz pozycję **Nowy odbiornik**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-286">Right-click the **Listeners** node and select **New Listener**.</span></span>

3. <span data-ttu-id="ea20d-287">Wpisz nazwę pliku śledzenia w polu **InitData** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-287">Type in the trace file name in the **InitData** field.</span></span> <span data-ttu-id="ea20d-288">Możesz kliknąć przycisk "..." przycisk, aby przejść do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="ea20d-288">You can click the "…" button to browse to a path.</span></span>

4. <span data-ttu-id="ea20d-289">Kliknięcie wiersza **TypeName** powoduje wyświetlenie "..." przycisk.</span><span class="sxs-lookup"><span data-stu-id="ea20d-289">Clicking the **TypeName** line displays a "…" button.</span></span> <span data-ttu-id="ea20d-290">Kliknij ten przycisk, aby otworzyć **przeglądarkę śledzenia typów odbiorników**, której można użyć do znajdowania wstępnie skonfigurowanych detektorów śledzenia, które są już zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="ea20d-290">Click this button to open the **Trace Listener Type Browser**, which you can use to find pre-configured trace listeners that are already installed.</span></span>

5. <span data-ttu-id="ea20d-291">Zwróć uwagę na sekcję **źródłową** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-291">Note the **Source** section.</span></span> <span data-ttu-id="ea20d-292">Kliknij przycisk **Dodaj** w tej sekcji, aby otworzyć okno dialogowe z menu rozwijanym zawierającym listę dostępnych źródeł śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ea20d-292">Click **Add** in this section to open a dialog box with a drop-down menu, which lists available tracing sources.</span></span> <span data-ttu-id="ea20d-293">Wybierz źródło śledzenia i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-293">Select a tracing source and click **OK**.</span></span>

6. <span data-ttu-id="ea20d-294">Aby edytować ustawienia rejestrowania komunikatów, kliknij węzeł **Rejestrowanie komunikatów** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-294">To edit Message Logging settings, click the **Message Logging** node.</span></span> <span data-ttu-id="ea20d-295">Ustawienia można edytować w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="ea20d-295">You can edit the settings in the property grid.</span></span>

### <a name="advanced"></a><span data-ttu-id="ea20d-296">Zaawansowany</span><span class="sxs-lookup"><span data-stu-id="ea20d-296">Advanced</span></span>

#### <a name="behaviors"></a><span data-ttu-id="ea20d-297">Zachowania</span><span class="sxs-lookup"><span data-stu-id="ea20d-297">Behaviors</span></span>

<span data-ttu-id="ea20d-298">W węźle **zachowań** są wyświetlane zachowania, które są obecnie zdefiniowane w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-298">The **Behaviors** node displays the behaviors that are currently defined in the configuration file.</span></span>

<span data-ttu-id="ea20d-299">Konfiguracje zachowań są używane do konfigurowania zachowań punktów końcowych i usług.</span><span class="sxs-lookup"><span data-stu-id="ea20d-299">Behavior configurations are used to configure behaviors of endpoints and services.</span></span> <span data-ttu-id="ea20d-300">Takie ustawienia konfiguracji są przechowywane w węźle **Zaawansowane** w obszarze **zachowania usługi** i **zachowania punktów końcowych**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-300">Such configuration settings are stored in the **Advanced** node under **Service Behaviors** and **Endpoint Behaviors**.</span></span> <span data-ttu-id="ea20d-301">Zachowania usługi są używane przez usługi; zachowania punktu końcowego dla punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ea20d-301">Service behaviors are used by services; whereas endpoint behaviors by endpoints.</span></span>

<span data-ttu-id="ea20d-302">Zachowania są kolekcją elementów rozszerzenia, które stosują stos.</span><span class="sxs-lookup"><span data-stu-id="ea20d-302">Behaviors are a collection of extension elements that for a stack.</span></span> <span data-ttu-id="ea20d-303">Element w górnej części stosu jest stosowany najpierw.</span><span class="sxs-lookup"><span data-stu-id="ea20d-303">The element at the top of the stack is applied first.</span></span> <span data-ttu-id="ea20d-304">Każdy element rozszerzenia może mieć własną konfigurację.</span><span class="sxs-lookup"><span data-stu-id="ea20d-304">Each extension element can have its own configuration.</span></span>

##### <a name="creating-a-new-behavior-configuration"></a><span data-ttu-id="ea20d-305">Tworzenie nowej konfiguracji zachowania</span><span class="sxs-lookup"><span data-stu-id="ea20d-305">Creating a new Behavior Configuration</span></span>

<span data-ttu-id="ea20d-306">Nową konfigurację zachowania można utworzyć na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="ea20d-306">You can create a new behavior configuration in two ways.</span></span>

- <span data-ttu-id="ea20d-307">Kliknij prawym przyciskiem myszy jeden z węzłów zachowań i wybierz polecenie "**Nowa konfiguracja zachowań...**</span><span class="sxs-lookup"><span data-stu-id="ea20d-307">Right-click one of the behavior nodes and select "**New Behavior Configuration…**</span></span>

- <span data-ttu-id="ea20d-308">Wybierz jeden z węzłów zachowań i kliknij **nową konfigurację zachowań**...</span><span class="sxs-lookup"><span data-stu-id="ea20d-308">Select one of the behavior nodes and click the **New Behavior Configuration**…</span></span> <span data-ttu-id="ea20d-309">w **okienku zadań** w lewym dolnym rogu okna.</span><span class="sxs-lookup"><span data-stu-id="ea20d-309">in the **Task Pane** on the lower-left of the window.</span></span>

##### <a name="adding-behavior-element-extensions-to-a-behavior"></a><span data-ttu-id="ea20d-310">Dodawanie rozszerzeń elementu zachowania do zachowania</span><span class="sxs-lookup"><span data-stu-id="ea20d-310">Adding Behavior Element Extensions to a Behavior</span></span>

1. <span data-ttu-id="ea20d-311">Wybierz jeden z węzłów zachowań.</span><span class="sxs-lookup"><span data-stu-id="ea20d-311">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="ea20d-312">Wybierz zachowanie, które chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="ea20d-312">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="ea20d-313">Kliknij pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-313">Click **Add**.</span></span>

4. <span data-ttu-id="ea20d-314">Z listy dostępnych rozszerzeń wybierz rozszerzenie elementu zachowania, które chcesz dodać.</span><span class="sxs-lookup"><span data-stu-id="ea20d-314">From the list of available extensions, select the behavior element extension you want to add.</span></span>

5. <span data-ttu-id="ea20d-315">Kliknij pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-315">Click **Add**.</span></span>

##### <a name="adjusting-the-extension-position-in-a-behavior"></a><span data-ttu-id="ea20d-316">Dopasowanie położenia rozszerzenia w ramach zachowania</span><span class="sxs-lookup"><span data-stu-id="ea20d-316">Adjusting the Extension Position in a Behavior</span></span>

<span data-ttu-id="ea20d-317">Zachowania są kolekcjami elementów tworzących stos.</span><span class="sxs-lookup"><span data-stu-id="ea20d-317">Behaviors are collections of elements that form a stack.</span></span> <span data-ttu-id="ea20d-318">Każdy element na stosie ma własną konfigurację.</span><span class="sxs-lookup"><span data-stu-id="ea20d-318">Each element on the stack has its own configuration.</span></span> <span data-ttu-id="ea20d-319">Kolejność rozszerzeń elementów zachowań w zachowaniu wskazuje ich położenie w stosie.</span><span class="sxs-lookup"><span data-stu-id="ea20d-319">The order of the behavior element extensions in a behavior indicates their positions in the stack.</span></span> <span data-ttu-id="ea20d-320">Elementy w górnej części stosu są stosowane najpierw.</span><span class="sxs-lookup"><span data-stu-id="ea20d-320">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="ea20d-321">Aby zmienić kolejność:</span><span class="sxs-lookup"><span data-stu-id="ea20d-321">To change the ordering:</span></span>

1. <span data-ttu-id="ea20d-322">Wybierz jeden z węzłów zachowań.</span><span class="sxs-lookup"><span data-stu-id="ea20d-322">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="ea20d-323">Wybierz zachowanie, które chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="ea20d-323">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="ea20d-324">Zaznacz element rozszerzenia zachowań w sekcji **pozycja rozszerzenia elementu zachowania** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-324">Select a behavior extension element in the **Behavior Element Extension Position** section.</span></span>

4. <span data-ttu-id="ea20d-325">Użyj przycisku w **górę** lub w **dół** z lewej strony listy, aby zmienić pozycję wybranego elementu.</span><span class="sxs-lookup"><span data-stu-id="ea20d-325">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

##### <a name="editing-the-configuration-of-behavior-element-extensions"></a><span data-ttu-id="ea20d-326">Edytowanie konfiguracji rozszerzeń elementów zachowań</span><span class="sxs-lookup"><span data-stu-id="ea20d-326">Editing the Configuration of Behavior Element Extensions</span></span>

1. <span data-ttu-id="ea20d-327">Wybierz jeden z węzłów zachowań w drzewie.</span><span class="sxs-lookup"><span data-stu-id="ea20d-327">Select one of the behavior nodes in the tree.</span></span>

2. <span data-ttu-id="ea20d-328">Wybierz zachowanie, które zawiera element, który chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="ea20d-328">Select the behavior that contains the element you want to edit.</span></span>

3. <span data-ttu-id="ea20d-329">Wybierz rozszerzenie elementu zachowania, które chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="ea20d-329">Select the behavior element extension you want to edit.</span></span> <span data-ttu-id="ea20d-330">Ustawienia elementu są wyświetlane w okienku po prawej stronie, w którym można je edytować.</span><span class="sxs-lookup"><span data-stu-id="ea20d-330">The settings of the element appear in the right pane where they can be edited.</span></span>

#### <a name="protocolmapping"></a><span data-ttu-id="ea20d-331">ProtocolMapping</span><span class="sxs-lookup"><span data-stu-id="ea20d-331">ProtocolMapping</span></span>

<span data-ttu-id="ea20d-332">Ta sekcja umożliwia ustawienie domyślnych typów powiązań dla różnych protokołów, takich jak http, TCP, MSMQ lub net. pipe przez zdefiniowane mapowanie między schematami adresów protokołu a możliwymi powiązaniami.</span><span class="sxs-lookup"><span data-stu-id="ea20d-332">This section allows you to set default binding types for different protocols such as http, tcp, MSMQ or net.pipe through defined mapping between protocol address schemes and the possible bindings.</span></span> <span data-ttu-id="ea20d-333">Możesz również dodać nowe mapowania do innych protokołów.</span><span class="sxs-lookup"><span data-stu-id="ea20d-333">You can also add new mappings to other protocols.</span></span>

#### <a name="extensions"></a><span data-ttu-id="ea20d-334">Rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="ea20d-334">Extensions</span></span>

<span data-ttu-id="ea20d-335">Nowe rozszerzenia powiązań, rozszerzenia elementów powiązania, standardowe rozszerzenia punktów końcowych i rozszerzenia zachowań mogą być zarejestrowane do użycia w konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="ea20d-335">New binding extensions, binding element extensions, standard endpoint extensions and behavior extensions can be registered for use in WCF configuration.</span></span> <span data-ttu-id="ea20d-336">Rozszerzeniami są pary nazwa/typ.</span><span class="sxs-lookup"><span data-stu-id="ea20d-336">Extensions are name/type pairs.</span></span> <span data-ttu-id="ea20d-337">Nazwa definiuje nazwę rozszerzenia w konfiguracji, podczas gdy typ implementuje rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="ea20d-337">The name defines the name of the extension in configuration, whereas the type implements the extension.</span></span> <span data-ttu-id="ea20d-338">Istnieją cztery typy rozszerzeń:</span><span class="sxs-lookup"><span data-stu-id="ea20d-338">There are four types of extensions:</span></span>

- <span data-ttu-id="ea20d-339">Rozszerzenia powiązań definiują cały typ powiązania.</span><span class="sxs-lookup"><span data-stu-id="ea20d-339">Binding extensions define an entire binding type.</span></span> <span data-ttu-id="ea20d-340">Przykład: `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="ea20d-340">Example: `basicHttpBinding`.</span></span>

- <span data-ttu-id="ea20d-341">Rozszerzenia elementów powiązania definiują element powiązania.</span><span class="sxs-lookup"><span data-stu-id="ea20d-341">Binding element extensions define an element of a binding.</span></span> <span data-ttu-id="ea20d-342">Przykład: `textMessageEncoding`.</span><span class="sxs-lookup"><span data-stu-id="ea20d-342">Example: `textMessageEncoding`.</span></span>

- <span data-ttu-id="ea20d-343">Standardowe rozszerzenia punktów końcowych definiują cały standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="ea20d-343">Standard endpoint extensions define an entire standard endpoint.</span></span> <span data-ttu-id="ea20d-344">Przykład: `discoveryEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="ea20d-344">Example: `discoveryEndpoint`.</span></span>

- <span data-ttu-id="ea20d-345">Rozszerzenia elementów zachowań definiują element zachowania.</span><span class="sxs-lookup"><span data-stu-id="ea20d-345">Behavior element extensions define an element of a behavior.</span></span> <span data-ttu-id="ea20d-346">Przykład: `clientVia`.</span><span class="sxs-lookup"><span data-stu-id="ea20d-346">Example: `clientVia`.</span></span>

 <span data-ttu-id="ea20d-347">Rozszerzenia, które zostały zarejestrowane w konfiguracji, mogą być używane jak każdy inny składnik WCF tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="ea20d-347">Extensions that have been registered in configuration can be used like any other WCF component of the same type.</span></span>

##### <a name="adding-a-new-extension"></a><span data-ttu-id="ea20d-348">Dodawanie nowego rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="ea20d-348">Adding a new extension</span></span>

<span data-ttu-id="ea20d-349">Wybierz jeden z węzłów rozszerzeń w węzłach zaawansowanych:</span><span class="sxs-lookup"><span data-stu-id="ea20d-349">Select one of the extension nodes in the advanced nodes:</span></span>

1. <span data-ttu-id="ea20d-350">Kliknij pozycję **Nowy**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-350">Click **New**.</span></span>

2. <span data-ttu-id="ea20d-351">Wprowadź nazwę i typ.</span><span class="sxs-lookup"><span data-stu-id="ea20d-351">Enter a name and type.</span></span>

3. <span data-ttu-id="ea20d-352">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-352">Click **OK**.</span></span>

4. <span data-ttu-id="ea20d-353">Rozszerzenie jest teraz widoczne w odpowiednim miejscu w edytorze.</span><span class="sxs-lookup"><span data-stu-id="ea20d-353">The extension now appears in the appropriate place in the Editor.</span></span> <span data-ttu-id="ea20d-354">Na przykład, jeśli dodasz rozszerzenie elementu zachowania, pojawia się ono na liście dostępnych rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="ea20d-354">For example, if you add a behavior element extension, it appears in the list of available extensions.</span></span>

#### <a name="hosting-environment"></a><span data-ttu-id="ea20d-355">Środowisko hostingu</span><span class="sxs-lookup"><span data-stu-id="ea20d-355">Hosting Environment</span></span>

<span data-ttu-id="ea20d-356">Ta sekcja umożliwia zdefiniowanie ustawień tworzenia wystąpienia dla środowiska hostingu usługi.</span><span class="sxs-lookup"><span data-stu-id="ea20d-356">This section allows you to define instantiation settings for the service hosting environment.</span></span>

### <a name="creating-a-configuration-file-using-the-wizard"></a><span data-ttu-id="ea20d-357">Tworzenie pliku konfiguracji przy użyciu kreatora</span><span class="sxs-lookup"><span data-stu-id="ea20d-357">Creating a Configuration File Using the Wizard</span></span>

<span data-ttu-id="ea20d-358">Jednym ze sposobów tworzenia nowego pliku konfiguracji jest użycie Kreatora nowego elementu usługi.</span><span class="sxs-lookup"><span data-stu-id="ea20d-358">One way to create a new configuration file is to use the New Service Element Wizard.</span></span> <span data-ttu-id="ea20d-359">Kreator odnajduje zainstalowane typy usług i inne elementy zgodne z programem WCF na komputerze, w tym katalogi wirtualne COM+ i hostowane w sieci Web, i ładuje je w celu znacznie usprawnienia tworzenia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-359">The wizard finds the installed service types and other elements compatible with WCF on the computer, including COM+ and Web-hosted virtual directories, and loads them to make creating the configuration much more streamlined.</span></span>

#### <a name="creating-a-configuration-file"></a><span data-ttu-id="ea20d-360">Tworzenie pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ea20d-360">Creating a Configuration File</span></span>

1. <span data-ttu-id="ea20d-361">Uruchom Edytor konfiguracji usługi przy użyciu okna wiersza polecenia, aby przejść do lokalizacji instalacji programu WCF, a następnie wpisz polecenie `SvcConfigEditor.exe` .</span><span class="sxs-lookup"><span data-stu-id="ea20d-361">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="ea20d-362">W menu **plik** wybierz pozycję **Otwórz** , a następnie kliknij pozycję plik **wykonywalny**, **Usługa com+** lub **Usługa webhosted**, w zależności od typu pliku konfiguracji, który chcesz utworzyć.</span><span class="sxs-lookup"><span data-stu-id="ea20d-362">From the **File** menu, select **Open** and click **Executable**, **COM+ Service**, or **WebHosted Service**, depending on the type of configuration file you want to create.</span></span>

3. <span data-ttu-id="ea20d-363">W oknie dialogowym **Otwórz** przejdź do określonego pliku, dla którego chcesz utworzyć plik konfiguracji, a następnie kliknij go dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="ea20d-363">In the **Open** dialog box, navigate to the specific file you want to create a configuration file for and double-click it.</span></span>

4. <span data-ttu-id="ea20d-364">W menu **plik** wskaż polecenie **Dodaj nowy element** , a następnie kliknij pozycję **Usługa**.</span><span class="sxs-lookup"><span data-stu-id="ea20d-364">In the **File** menu, point to **Add New Item** and click **Service**.</span></span> <span data-ttu-id="ea20d-365">Zostanie otwarty Kreator nowego elementu usługi.</span><span class="sxs-lookup"><span data-stu-id="ea20d-365">The New Service Element Wizard opens.</span></span>

5. <span data-ttu-id="ea20d-366">Postępuj zgodnie z instrukcjami w kreatorze, aby utworzyć nową usługę.</span><span class="sxs-lookup"><span data-stu-id="ea20d-366">Follow the steps in the wizard to create the new service.</span></span>

> [!NOTE]
> <span data-ttu-id="ea20d-367">Jeśli chcesz użyć NetPeerTcpBinding z pliku konfiguracji wygenerowanego przez kreatora, musisz ręcznie dodać element konfiguracji powiązania i zmodyfikować `mode` atrybut jego `security` elementu na wartość "none".</span><span class="sxs-lookup"><span data-stu-id="ea20d-367">If you want to use the NetPeerTcpBinding from the configuration file generated by the Wizard, you have to manually add a binding configuration element and modify the `mode` attribute of its `security` element to "None".</span></span>

## <a name="configuring-com"></a><span data-ttu-id="ea20d-368">Konfigurowanie modelu COM+</span><span class="sxs-lookup"><span data-stu-id="ea20d-368">Configuring COM+</span></span>

<span data-ttu-id="ea20d-369">Edytor konfiguracji usługi umożliwia utworzenie nowego pliku konfiguracji dla istniejącej aplikacji modelu COM+ lub edytowanie istniejącej konfiguracji modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="ea20d-369">The Service Configuration Editor enables you to create a new configuration file for an existing COM+ application, or edit an existing COM+ configuration.</span></span> <span data-ttu-id="ea20d-370">Węzeł **kontraktu com** jest widoczny tylko wtedy, gdy `comContract` sekcja> <istnieje w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-370">The **COM Contract** node is only visible when the <`comContract`> section exists in the configuration file.</span></span>

### <a name="creating-a-new-com-configuration"></a><span data-ttu-id="ea20d-371">Tworzenie nowej konfiguracji modelu COM+</span><span class="sxs-lookup"><span data-stu-id="ea20d-371">Creating a New COM+ Configuration</span></span>

<span data-ttu-id="ea20d-372">Przed utworzeniem nowej konfiguracji modelu COM+ upewnij się, że aplikacja modelu COM+ jest zainstalowana w usługach składników i zarejestrowana w globalnej pamięci podręcznej zestawów (GAC).</span><span class="sxs-lookup"><span data-stu-id="ea20d-372">Before creating a new COM+ configuration, make sure that your COM+ application is installed in Component Services, and registered in the Global Assembly Cache (GAC).</span></span>

1. <span data-ttu-id="ea20d-373">Wybierz menu **plik** — > **Zintegruj**  ->  **aplikację com+.**</span><span class="sxs-lookup"><span data-stu-id="ea20d-373">Select **File** menu -> **Integrate** -> **COM+ Application.**</span></span> <span data-ttu-id="ea20d-374">Ta operacja zamyka bieżący otwarty plik.</span><span class="sxs-lookup"><span data-stu-id="ea20d-374">This operation closes the current opened file.</span></span> <span data-ttu-id="ea20d-375">Jeśli w bieżącym pliku znajdują się niezapisane dane, zostanie wyświetlone okno dialogowe Zapisz.</span><span class="sxs-lookup"><span data-stu-id="ea20d-375">If there is unsaved data in the current file, a Save dialog appears.</span></span> <span data-ttu-id="ea20d-376">Następnie zostanie uruchomiony **Kreator integracji modelu COM+** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-376">The **COM+ Integration Wizard** is then launched.</span></span>

2. <span data-ttu-id="ea20d-377">Na pierwszej stronie wybierz aplikację COM+ z drzewa.</span><span class="sxs-lookup"><span data-stu-id="ea20d-377">In the first page, select the COM+ application from the tree.</span></span> <span data-ttu-id="ea20d-378">Jeśli nie możesz znaleźć aplikacji modelu COM+ w drzewie, sprawdź, czy jest ona zainstalowana w usługach składników i zarejestrowana w globalnej pamięci podręcznej zestawów (GAC).</span><span class="sxs-lookup"><span data-stu-id="ea20d-378">If you cannot find your COM+ application in the tree, verify that it is installed in the Component Services and registered in the Global Assembly Cache (GAC).</span></span>

3. <span data-ttu-id="ea20d-379">Na następnej stronie Wybierz metody, które chcesz uwidocznić jako usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="ea20d-379">In the next page, select which method(s) you want to expose as WCF services.</span></span> <span data-ttu-id="ea20d-380">Wszystkie obsługiwane metody w aplikacji COM+ są domyślnie wyświetlane i wybierane.</span><span class="sxs-lookup"><span data-stu-id="ea20d-380">All the supported methods in the COM+ application are displayed and selected by default.</span></span>

4. <span data-ttu-id="ea20d-381">Wybierz metodę hostingu.</span><span class="sxs-lookup"><span data-stu-id="ea20d-381">Choose a hosting method.</span></span>

5. <span data-ttu-id="ea20d-382">Skonfiguruj inne ustawienia zgodnie z przewodnikami w kreatorze.</span><span class="sxs-lookup"><span data-stu-id="ea20d-382">Configure other settings according to the guides in the wizard.</span></span>

6. <span data-ttu-id="ea20d-383">Edytor konfiguracji usługi używa ComSvcConfig.exe w tle do generowania pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea20d-383">Service Configuration Editor utilizes ComSvcConfig.exe in the background to generate configuration file.</span></span> <span data-ttu-id="ea20d-384">Po zakończeniu tej operacji można wyświetlić podsumowanie i zakończyć pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="ea20d-384">After this is completed, you can view a summary and exit the wizard.</span></span> <span data-ttu-id="ea20d-385">Wygenerowany plik konfiguracji zostanie otwarty, aby można go było edytować bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="ea20d-385">The generated configuration file is opened so that you can edit it directly.</span></span>

### <a name="editing-an-existing-com-configuration"></a><span data-ttu-id="ea20d-386">Edytowanie istniejącej konfiguracji modelu COM+</span><span class="sxs-lookup"><span data-stu-id="ea20d-386">Editing an Existing COM+ Configuration</span></span>

1. <span data-ttu-id="ea20d-387">Wybierz menu **plik** > **Otwórz**  ->  **usługę com+**...</span><span class="sxs-lookup"><span data-stu-id="ea20d-387">Select **File** menu -> **Open** -> **COM+ Service**…</span></span>

2. <span data-ttu-id="ea20d-388">Wybierz z listy usługę COM+, którą chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="ea20d-388">Select the COM+ Service you want to edit from the list.</span></span>

3. <span data-ttu-id="ea20d-389">Edytuj ustawienia konfiguracji w węźle **kontrakty com** .</span><span class="sxs-lookup"><span data-stu-id="ea20d-389">Edit configuration settings in the **COM Contracts** node.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ea20d-390">Można również bezpośrednio otworzyć i edytować plik konfiguracji, który zawiera kontrakty COM.</span><span class="sxs-lookup"><span data-stu-id="ea20d-390">You can also directly open and edit a configuration file that contains COM contracts.</span></span>

## <a name="security"></a><span data-ttu-id="ea20d-391">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="ea20d-391">Security</span></span>

<span data-ttu-id="ea20d-392">Nie ma gwarancji, że plik konfiguracji usługi wygenerowany przez Edytor konfiguracji jest bezpieczny.</span><span class="sxs-lookup"><span data-stu-id="ea20d-392">A service configuration file generated by the Configuration Editor is not guaranteed to be secure.</span></span> <span data-ttu-id="ea20d-393">Zapoznaj się z dokumentacją [zabezpieczeń](./feature-details/security.md) , aby dowiedzieć się, jak zabezpieczyć usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="ea20d-393">Please refer to the [Security](./feature-details/security.md) documentation to find out how to secure your WCF services.</span></span>

<span data-ttu-id="ea20d-394">Ponadto edytor konfiguracji może być używany tylko do odczytu i zapisu prawidłowych elementów konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="ea20d-394">In addition, the Configuration Editor can only be used to read and write valid WCF configuration elements.</span></span> <span data-ttu-id="ea20d-395">Narzędzie ignoruje elementy zdefiniowane przez użytkownika, które są zgodne ze schematem.</span><span class="sxs-lookup"><span data-stu-id="ea20d-395">The tool ignores schema-compliant, user-defined elements.</span></span> <span data-ttu-id="ea20d-396">Nie powoduje to również usunięcia tych elementów z pliku konfiguracyjnego ani określania ich wpływu na znane elementy programu WCF.</span><span class="sxs-lookup"><span data-stu-id="ea20d-396">It also does not attempt remove these elements from the configuration file or determine their effects on the known WCF elements.</span></span> <span data-ttu-id="ea20d-397">Użytkownik jest odpowiedzialny za określenie, czy te elementy stanowią zagrożenie dla aplikacji lub systemu.</span><span class="sxs-lookup"><span data-stu-id="ea20d-397">It is the user’s responsibility to determine whether these elements pose a threat to the application or the system.</span></span>
