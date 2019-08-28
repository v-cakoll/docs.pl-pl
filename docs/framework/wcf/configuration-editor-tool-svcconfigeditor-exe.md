---
title: Narzędzie edytora konfiguracji (SvcConfigEditor.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: 8123a504e83164f2ae842755da8ff4d8850141d2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046033"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a><span data-ttu-id="8ecfc-102">Narzędzie edytora konfiguracji (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="8ecfc-102">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>

<span data-ttu-id="8ecfc-103">Edytor konfiguracji usługi Windows Communication Foundation (WCF) (SvcConfigEditor. exe) umożliwia administratorom i deweloperom tworzenie i modyfikowanie ustawień konfiguracji usług WCF przy użyciu graficznego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-103">The Windows Communication Foundation (WCF) Service Configuration Editor (SvcConfigEditor.exe) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="8ecfc-104">Za pomocą tego narzędzia można zarządzać ustawieniami powiązań programu WCF, zachowań, usług i diagnostyki bez konieczności bezpośredniego edytowania plików konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-104">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without having to directly edit XML configuration files.</span></span>

<span data-ttu-id="8ecfc-105">Edytor konfiguracji usługi można znaleźć w folderze C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-105">Service Configuration Editor can be found in the C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin folder.</span></span>

## <a name="the-wcf-configuration-editor"></a><span data-ttu-id="8ecfc-106">Edytor konfiguracji WCF</span><span class="sxs-lookup"><span data-stu-id="8ecfc-106">The WCF Configuration Editor</span></span>

<span data-ttu-id="8ecfc-107">Edytor konfiguracji usługi zawiera kreatora, który przeprowadzi Cię przez wszystkie kroki opisane w temacie Konfigurowanie usługi lub klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-107">Service Configuration Editor comes with a wizard that guides you through all the steps in configuring a WCF service or client.</span></span> <span data-ttu-id="8ecfc-108">Zdecydowanie zaleca się użycie Kreatora zamiast edytora bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-108">You are strongly advised to use the wizard instead of the editor directly.</span></span>

<span data-ttu-id="8ecfc-109">Jeśli masz już pewne pliki konfiguracji zgodne ze standardowym schematem system. Configuration, możesz zarządzać określonymi ustawieniami powiązań, zachowań, usług i diagnostyki przy użyciu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-109">If you already have some configuration files that comply with the standard System.Configuration schema, you can manage specific settings for bindings, behavior, services, and diagnostics with the user interface.</span></span> <span data-ttu-id="8ecfc-110">Edytor konfiguracji usługi umożliwia zarządzanie ustawieniami istniejących plików konfiguracji WCF oraz plikami wykonywalnymi, usługami COM+ i usługami hostowanymi w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-110">The Service Configuration Editor enables you to manage the settings for existing WCF configuration files as well as executable files, COM+ services, and Web-hosted services.</span></span> <span data-ttu-id="8ecfc-111">Podczas otwierania usługi hostowanej w sieci Web za pomocą edytora konfiguracji usługi, są wyświetlane sekcje konfiguracja i dziedziczone konfiguracje usługi.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-111">When opening a Web-hosted service with Service Configuration Editor, both the service’s own configuration and inherited configurations sections of upper level nodes are shown.</span></span>

<span data-ttu-id="8ecfc-112">Ponieważ ustawienia konfiguracji programu WCF znajdują się `<system.serviceModel>` w sekcji pliku konfiguracji, Edytor działa wyłącznie na zawartości tego elementu i nie uzyskuje dostępu do innych elementów w tym samym pliku.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-112">Because WCF configuration settings are located in the `<system.serviceModel>` section of the configuration file, the editor operates exclusively on the content of this element and does not access other elements in the same file.</span></span> <span data-ttu-id="8ecfc-113">Możesz przejść do istniejących plików konfiguracji bezpośrednio lub wybrać zestaw, który zawiera usługę, katalog wirtualny lub usługę COM+.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-113">You can navigate to existing configuration files directly or you can select an assembly that contains a service, virtual directory, or COM+ service.</span></span> <span data-ttu-id="8ecfc-114">Edytor ładuje plik konfiguracyjny dla danej usługi i zezwala użytkownikowi na dodawanie nowych elementów lub edytowanie istniejących elementów zagnieżdżonych w `<system.serviceModel>` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-114">The editor loads the configuration file for that particular service and allows the user to either add new elements or edit existing elements nested in the `<system.serviceModel>` section of the configuration file.</span></span>

<span data-ttu-id="8ecfc-115">Edytor obsługuje funkcję IntelliSense i wymusza zgodność schematu.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-115">The editor supports IntelliSense and enforces schema compliance.</span></span> <span data-ttu-id="8ecfc-116">Wynikowe dane wyjściowe są gwarantowane w celu zachowania zgodności ze schematem pliku konfiguracji i zawierają składniowo prawidłowe wartości danych.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-116">The resulting output is guaranteed to comply with the schema of the configuration file and to have syntactically correct data values.</span></span> <span data-ttu-id="8ecfc-117">Jednak Edytor nie gwarantuje, że plik konfiguracji jest semantycznie prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-117">However, the editor does not guarantee that the configuration file is semantically valid.</span></span> <span data-ttu-id="8ecfc-118">Innymi słowy, Edytor nie gwarantuje, że plik konfiguracji może współdziałać z usługą, którą konfiguruje.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-118">In other words, the editor does not guarantee that the configuration file can work with the service it configures.</span></span>

> [!CAUTION]
> <span data-ttu-id="8ecfc-119">Edytor nie może przeczyścić elementu konfiguracji z pliku konfiguracji po zmodyfikowaniu elementu.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-119">The editor cannot purge a configuration element from the configuration file once you have modified the element.</span></span> <span data-ttu-id="8ecfc-120">Na przykład, jeśli używasz edytora, aby ustawić nazwę punktu końcowego jako niepusty ciąg i zapisać go, plik konfiguracyjny ma następującą zawartość, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-120">For example, if you use the editor to set the endpoint name to a non-empty string and save it, the configuration file has the following content, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="somename" />`
>
> <span data-ttu-id="8ecfc-121">Jeśli podjęto próbę usunięcia nazwy przez ustawienie jej jako pustego ciągu i zapisania pliku, plik konfiguracji nadal zawiera `name` atrybut, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-121">If you attempt to remove the name by setting it to an empty string and save the file, the configuration file still contains the `name` attribute, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="" />`
>
> <span data-ttu-id="8ecfc-122">Aby przeczyścić atrybut, należy ręcznie edytować element przy użyciu innego edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-122">To purge the attribute, you must manually edit the element using another text editor.</span></span>
>
> <span data-ttu-id="8ecfc-123">W przypadku używania `issueToken` elementu `clientCredential` zachowania punktu końcowego należy zachować szczególną ostrożność w przypadku tego problemu.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-123">You should be especially careful with this issue when you use the `issueToken` element of the `clientCredential` Endpoint behavior.</span></span> <span data-ttu-id="8ecfc-124">W `address` przypadku atrybutu jego `localIssuer` podelement nie może być pustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-124">Specifically, the `address` attribute of its `localIssuer` sub-element must not be an empty string.</span></span> <span data-ttu-id="8ecfc-125">Jeśli `address` atrybut został zmodyfikowany przy użyciu edytora konfiguracji i chcesz go całkowicie usunąć, należy to zrobić przy użyciu narzędzia innego niż Edytor.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-125">If you have modified the `address` attribute using the Configuration Editor and want to remove it completely, you should do so using a tool other than the Editor.</span></span> <span data-ttu-id="8ecfc-126">W przeciwnym razie atrybut zawiera pusty ciąg, a aplikacja zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-126">Otherwise, the attribute contains an empty string and your application throws an exception.</span></span>

## <a name="using-the-configuration-editor"></a><span data-ttu-id="8ecfc-127">Korzystanie z edytora konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8ecfc-127">Using the Configuration Editor</span></span>

<span data-ttu-id="8ecfc-128">Edytor konfiguracji usługi można znaleźć w następującej Windows SDK lokalizacji instalacji:</span><span class="sxs-lookup"><span data-stu-id="8ecfc-128">The Service Configuration Editor can be found at the following Windows SDK installation location:</span></span>

<span data-ttu-id="8ecfc-129">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="8ecfc-129">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span></span>

<span data-ttu-id="8ecfc-130">Po uruchomieniu edytora konfiguracji usługi możesz użyć menu **plik/Otwórz** , aby przeglądać w poszukiwaniu usługi lub zestawu, którym chcesz zarządzać.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-130">After you launch the Service Configuration Editor, you can use the **File/Open** menu to browse for the service or assembly you want to manage.</span></span> <span data-ttu-id="8ecfc-131">Pliki konfiguracji można otwierać bezpośrednio, przeglądać w poszukiwaniu usług WCF/COM + usługi i otwierać pliki konfiguracji dla usług hostowanych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-131">You can open configuration files directly, browse for WCF /COM+ services, and open configuration files for Web-hosted services.</span></span>

<span data-ttu-id="8ecfc-132">Interfejs użytkownika edytora konfiguracji usługi jest podzielony na następujące obszary:</span><span class="sxs-lookup"><span data-stu-id="8ecfc-132">The Service Configuration Editor's user interface is divided into the following areas:</span></span>

- <span data-ttu-id="8ecfc-133">Okienko widoku drzewa, które wyświetla elementy konfiguracji w strukturze drzewa po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-133">Tree View Pane, which displays configuration elements in a tree structure on the left.</span></span> <span data-ttu-id="8ecfc-134">Aby wykonać operacje w drzewie, kliknij prawym przyciskiem myszy węzły.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-134">You can perform operations in the tree by right-clicking the nodes.</span></span>

- <span data-ttu-id="8ecfc-135">Okienko zadań, które wyświetla typowe zadania dla bieżących elementów w lewym dolnym rogu okna</span><span class="sxs-lookup"><span data-stu-id="8ecfc-135">Task Pane, which displays common tasks for current elements on the lower-left of the window</span></span>

- <span data-ttu-id="8ecfc-136">Okienko szczegółów, w którym są wyświetlane szczegółowe ustawienia węzła konfiguracji wybranego w widoku drzewa po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-136">Detail Pane, which displays detailed settings of the configuration node selected in the Tree View on the right.</span></span>

### <a name="opening-a-configuration-file"></a><span data-ttu-id="8ecfc-137">Otwieranie pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8ecfc-137">Opening a Configuration File</span></span>

1. <span data-ttu-id="8ecfc-138">Uruchom Edytor konfiguracji usługi przy użyciu okna wiersza polecenia, aby przejść do lokalizacji instalacji programu WCF, a następnie `SvcConfigEditor.exe`wpisz polecenie.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-138">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="8ecfc-139">Z menu **plik** wybierz polecenie **Otwórz** , a następnie kliknij typ pliku, którym chcesz zarządzać.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-139">From the **File** menu, select **Open** and click the type of file you want to manage.</span></span>

3. <span data-ttu-id="8ecfc-140">W oknie dialogowym **otwieranie** przejdź do określonego pliku, który chcesz zarządzać, a następnie kliknij go dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-140">In the **Open** dialog box, navigate to the specific file you want to manage and double-click it.</span></span>

<span data-ttu-id="8ecfc-141">Przeglądarka automatycznie postępuje zgodnie ze ścieżką scalania konfiguracji i tworzy widok Scalonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-141">The viewer automatically follows the configuration merge path and creates a view of the merged configuration.</span></span> <span data-ttu-id="8ecfc-142">Na przykład rzeczywista konfiguracja usługi niehostowanej jest kombinacją Machine. config i App. config. Wszystkie zmiany są stosowane do aktywnego pliku w SvcConfigEditor.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-142">For example, the actual configuration of a non-hosted service is a combination of Machine.config and App.config. Any changes are applied to the active file in the SvcConfigEditor.</span></span> <span data-ttu-id="8ecfc-143">Jeśli chcesz edytować konkretny plik w ścieżce scalania konfiguracji, należy otworzyć go bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-143">If you want to edit a specific file in the configuration merge path, you should open it directly.</span></span>

> [!NOTE]
> <span data-ttu-id="8ecfc-144">Edytor konfiguracji ponownie ładuje aktualnie otwarty plik konfiguracji, gdy ten ostatni został zmodyfikowany poza edytorem.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-144">Configuration Editor reloads the currently opened configuration file when the latter has been modified outside the Editor.</span></span> <span data-ttu-id="8ecfc-145">W takim przypadku wszystkie zmiany, które nie zostały trwale zapisane w edytorze, zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-145">When this happens, all the changes that are not durably saved inside the Editor are lost.</span></span> <span data-ttu-id="8ecfc-146">Jeśli ponowne ładowanie odbywa się konsekwentnie, najbardziej prawdopodobną przyczyną jest usługa, która stale uzyskuje dostęp do pliku konfiguracji, na przykład oprogramowania antywirusowego działającego w tle.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-146">If reloading happens consistently, the most likely cause is a service that constantly accesses the configuration file, for example, an antivirus software running in the background.</span></span> <span data-ttu-id="8ecfc-147">Aby rozwiązać ten problem, upewnij się, że Edytor konfiguracji jest jedynym procesem, który ma dostęp do pliku po jego otwarciu.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-147">To resolve this, ensure that Configuration Editor is the only process that can access the file when it is opened.</span></span>

### <a name="services"></a><span data-ttu-id="8ecfc-148">Usługi</span><span class="sxs-lookup"><span data-stu-id="8ecfc-148">Services</span></span>

<span data-ttu-id="8ecfc-149">W węźle **usługi** są wyświetlane wszystkie usługi aktualnie przypisane w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-149">The **Services** node displays all of the services currently assigned in the configuration file.</span></span> <span data-ttu-id="8ecfc-150">Każdy podwęzeł w drzewie odnosi się do podrzędnego elementu <`services`> elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-150">Each sub-node in the tree corresponds to a sub-element of the <`services`> element in the configuration file.</span></span>

<span data-ttu-id="8ecfc-151">Po kliknięciu węzła **usługi** można wyświetlić lub wykonać zadania na stronie Podsumowanie usługi w okienku **szczegółów** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-151">When you click the **Services** node, you can view or perform tasks on the service Summary Page in the **Detail** Pane.</span></span>

#### <a name="creating-a-new-service-configuration"></a><span data-ttu-id="8ecfc-152">Tworzenie nowej konfiguracji usługi</span><span class="sxs-lookup"><span data-stu-id="8ecfc-152">Creating a new Service Configuration</span></span>

<span data-ttu-id="8ecfc-153">Nową konfigurację usługi można utworzyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8ecfc-153">You can create a new service configuration in the following ways:</span></span>

- <span data-ttu-id="8ecfc-154">Korzystanie z kreatora: Kliknij link **Utwórz nową usługę...**</span><span class="sxs-lookup"><span data-stu-id="8ecfc-154">Using a Wizard: Click the link **Create a New Service…**</span></span> <span data-ttu-id="8ecfc-155">Aby uruchomić kreatora, w okienku zadań lub stronie podsumowania.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-155">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="8ecfc-156">Można to również zrobić w menu **plik** — > **dodać nowy element**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-156">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="8ecfc-157">Utwórz ręcznie: Możesz kliknąć prawym przyciskiem myszy węzeł **usługi** i wybrać polecenie **Nowa usługa**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-157">Create manually: You can right-click the **Services** node and choose **New Service**.</span></span>

#### <a name="creating-a-new-service-endpoint-configuration"></a><span data-ttu-id="8ecfc-158">Tworzenie nowej konfiguracji punktu końcowego usługi</span><span class="sxs-lookup"><span data-stu-id="8ecfc-158">Creating a new Service Endpoint Configuration</span></span>

<span data-ttu-id="8ecfc-159">Nową konfigurację punktu końcowego usługi można utworzyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8ecfc-159">You can create a new service endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="8ecfc-160">Utwórz za pomocą kreatora: kliknij link **Utwórz nowy punkt końcowy usługi...**</span><span class="sxs-lookup"><span data-stu-id="8ecfc-160">Create using a Wizard: click the link **Create a New Service Endpoint…**</span></span> <span data-ttu-id="8ecfc-161">Aby uruchomić kreatora, w okienku zadań lub stronie podsumowania.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-161">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="8ecfc-162">Można to również zrobić w menu **plik** — > **dodać nowy element**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-162">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="8ecfc-163">Utwórz ręcznie: Po utworzeniu usługi można kliknąć prawym przyciskiem myszy węzeł **punkty końcowe** i wybrać pozycję "**nowy punkt końcowy usługi**".</span><span class="sxs-lookup"><span data-stu-id="8ecfc-163">Create manually: Once you created a Service, you can right-click the **Endpoints** node and choose "**New Service Endpoint**".</span></span>

#### <a name="editing-a-service-configuration"></a><span data-ttu-id="8ecfc-164">Edytowanie konfiguracji usługi</span><span class="sxs-lookup"><span data-stu-id="8ecfc-164">Editing a Service Configuration</span></span>

1. <span data-ttu-id="8ecfc-165">Kliknij węzeł **usługi** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-165">Click a **Service** node.</span></span>

2. <span data-ttu-id="8ecfc-166">Edytuj ustawienia w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-166">Edit the settings in the property grids.</span></span>

#### <a name="editing-a-service-endpoint-configuration"></a><span data-ttu-id="8ecfc-167">Edytowanie konfiguracji punktu końcowego usługi</span><span class="sxs-lookup"><span data-stu-id="8ecfc-167">Editing a Service Endpoint Configuration</span></span>

1. <span data-ttu-id="8ecfc-168">Kliknij węzeł **punktu końcowego usługi** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-168">Click a **Service Endpoint** node.</span></span>

2. <span data-ttu-id="8ecfc-169">Edytuj ustawienia w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-169">Edit the settings in the property grids.</span></span>

#### <a name="adding-a-base-address"></a><span data-ttu-id="8ecfc-170">Dodawanie adresu podstawowego</span><span class="sxs-lookup"><span data-stu-id="8ecfc-170">Adding a Base Address</span></span>

1. <span data-ttu-id="8ecfc-171">Kliknij węzeł **hosta** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-171">Click the **Host** node.</span></span>

2. <span data-ttu-id="8ecfc-172">Kliknij **Nowy...**</span><span class="sxs-lookup"><span data-stu-id="8ecfc-172">Click the **New…**</span></span> <span data-ttu-id="8ecfc-173">w sekcji **adresy podstawowe** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-173">button in the **Base Addresses** section.</span></span>

3. <span data-ttu-id="8ecfc-174">W oknie dialogowym wpisz adres URI adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-174">Type in the base address URI in the dialog box.</span></span>

4. <span data-ttu-id="8ecfc-175">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-175">Click **OK**.</span></span>

> [!NOTE]
> <span data-ttu-id="8ecfc-176">Nie można edytować wartości [ \<baseAddressPrefixFilters >](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) wewnątrz tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-176">You cannot edit the value of [\<baseAddressPrefixFilters>](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) inside this tool.</span></span> <span data-ttu-id="8ecfc-177">Aby dodać lub zmodyfikować ten element, należy użyć edytora tekstu lub programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-177">To add or modify this element, you should use a text editor or Visual Studio.</span></span>

### <a name="client"></a><span data-ttu-id="8ecfc-178">Klient</span><span class="sxs-lookup"><span data-stu-id="8ecfc-178">Client</span></span>

<span data-ttu-id="8ecfc-179">W węźle **klienta** są wyświetlane wszystkie punkty końcowe klienta w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-179">The **Client** node displays all of the client endpoints in the configuration file.</span></span> <span data-ttu-id="8ecfc-180">Każdy podwęzeł w drzewie odnosi się do podrzędnego elementu <`client`> elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-180">Every sub-node in the tree corresponds to a sub-element of the <`client`> element in the configuration file.</span></span>

<span data-ttu-id="8ecfc-181">Po kliknięciu węzła **klienta** można wyświetlić lub wykonać zadania na **stronie Podsumowanie** klienta w **okienku szczegółów**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-181">When you click the **Client** node, you can view or perform tasks on the client **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-client-endpoint-configuration"></a><span data-ttu-id="8ecfc-182">Tworzenie nowej konfiguracji punktu końcowego klienta</span><span class="sxs-lookup"><span data-stu-id="8ecfc-182">Creating a new Client Endpoint Configuration</span></span>

<span data-ttu-id="8ecfc-183">Nową konfigurację punktu końcowego klienta można utworzyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8ecfc-183">You can create a new client endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="8ecfc-184">Kreator tworzenia przez: Kliknij link **Utwórz nowego klienta...**</span><span class="sxs-lookup"><span data-stu-id="8ecfc-184">Create by Wizard: Click the link **Create a New Client…**</span></span> <span data-ttu-id="8ecfc-185">w **okienku zadań** w dolnej części okna lub **stronie podsumowania** , aby uruchomić kreatora.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-185">on the **Task Pane** on the lower-left of the window, or **Summary Page** to launch the wizard.</span></span> <span data-ttu-id="8ecfc-186">Można to również zrobić w menu **plik** — > **dodać nowy element**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-186">You can also do so in the **File** menu -> **Add New Item**.</span></span> <span data-ttu-id="8ecfc-187">Kreator poprosi o wskazanie lokalizacji konfiguracji usługi, z której jest generowana konfiguracja klienta.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-187">The wizard prompts you to point to the location of the service configuration, from which the client configuration is generated.</span></span> <span data-ttu-id="8ecfc-188">Następnie można wybrać punkt końcowy usługi, z którym ma zostać nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-188">You can then choose the service endpoint to connect to.</span></span>

- <span data-ttu-id="8ecfc-189">Utwórz ręcznie: Kliknij prawym przyciskiem myszy węzeł **punkty końcowe** w obszarze **Klient**, a następnie wybierz polecenie **nowy punkt końcowy klienta**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-189">Create manually: Right-click the **Endpoints** node under **Client**, and choose **New Client Endpoint**.</span></span>

#### <a name="editing-a-client-endpoint-configuration"></a><span data-ttu-id="8ecfc-190">Edytowanie konfiguracji punktu końcowego klienta</span><span class="sxs-lookup"><span data-stu-id="8ecfc-190">Editing a Client Endpoint Configuration</span></span>

1. <span data-ttu-id="8ecfc-191">Kliknij węzeł **punktu końcowego klienta** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-191">Click a **Client Endpoint** node.</span></span>

2. <span data-ttu-id="8ecfc-192">Edytuj ustawienia w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-192">Edit the settings in the property grids.</span></span>

### <a name="standard-endpoint"></a><span data-ttu-id="8ecfc-193">Standardowy punkt końcowy</span><span class="sxs-lookup"><span data-stu-id="8ecfc-193">Standard Endpoint</span></span>

<span data-ttu-id="8ecfc-194">Standardowe punkty końcowe to wyspecjalizowane punkty końcowe, które mają co najmniej jeden aspekt adresu, kontraktu i powiązania ustawione na wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-194">Standard endpoints are specialized endpoints that have one or more aspects of the address, contract and binding set to default values.</span></span>

<span data-ttu-id="8ecfc-195">Takie ustawienia konfiguracji są przechowywane w standardowym węźle **punktu końcowego** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-195">Such configuration settings are stored in the **Standard Endpoint** node.</span></span> <span data-ttu-id="8ecfc-196">**Standardowy węzeł punktu końcowego** wyświetla wszystkie standardowe ustawienia punktu końcowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-196">The **Standard Endpoint** node displays all of the standard endpoint settings in the configuration file.</span></span> <span data-ttu-id="8ecfc-197">Każdy podwęzeł w drzewie odnosi się do elementu podrzędnego w `<standardEndpoints>` elemencie w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-197">Every sub-node in the tree corresponds to a sub-element in the `<standardEndpoints>` element in the configuration file.</span></span>

<span data-ttu-id="8ecfc-198">Po kliknięciu węzła **standardowego punktu końcowego** można wyświetlić lub wykonać zadania na **stronie Podsumowanie** standardowego punktu końcowego w **okienku szczegółów**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-198">When you click the **Standard Endpoint** node, you can view or perform tasks on the standard endpoint **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-standard-endpoint-configuration"></a><span data-ttu-id="8ecfc-199">Tworzenie nowej konfiguracji standardowego punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="8ecfc-199">Creating a New Standard Endpoint Configuration</span></span>

<span data-ttu-id="8ecfc-200">Nową konfigurację standardowego punktu końcowego można utworzyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8ecfc-200">You can create a new standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="8ecfc-201">Kliknij prawym przyciskiem myszy **Standardowy węzeł punktu końcowego** i wybierz pozycję **Nowa Standardowa konfiguracja punktu końcowego...**</span><span class="sxs-lookup"><span data-stu-id="8ecfc-201">Right-click the **Standard Endpoint** node and select **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="8ecfc-202">W oknie dialogowym Wybierz typ powiązania i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-202">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="8ecfc-203">Wybierz węzeł **standardowego punktu końcowego** , a następnie kliknij pozycję **Nowa Standardowa konfiguracja punktu końcowego...**</span><span class="sxs-lookup"><span data-stu-id="8ecfc-203">Select the **Standard Endpoint** node and click **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="8ecfc-204">w **okienku zadań** w lewym dolnym rogu okna.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-204">in the **Task Pane** on the lower-left of the window.</span></span>

<span data-ttu-id="8ecfc-205">W oknie dialogowym **Tworzenie nowego standardowego punktu końcowego** zostaną wyświetlone wszystkie zarejestrowane standardowe typy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-205">The **Creating a New Standard Endpoint** dialog box displays and lists all registered standard endpoint types.</span></span>

#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a><span data-ttu-id="8ecfc-206">Wyświetlanie i edytowanie standardowej konfiguracji punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="8ecfc-206">Viewing and Editing a Standard Endpoint Configuration</span></span>

<span data-ttu-id="8ecfc-207">Konfigurację standardowego punktu końcowego można otworzyć do wyświetlania i edytowania w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8ecfc-207">You can open a standard endpoint configuration for viewing and editing in the following ways:</span></span>

- <span data-ttu-id="8ecfc-208">Kliknij, aby rozwinąć węzeł **standardowego punktu końcowego** , a następnie kliknij odpowiedni podwęzeł punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-208">Click to expand the **Standard Endpoint** node and click the respective endpoint sub-node.</span></span>

- <span data-ttu-id="8ecfc-209">Kliknij węzeł **standardowego punktu końcowego** , a następnie kliknij odpowiedni punkt końcowy w okienku szczegółów.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-209">Click the **Standard Endpoint** node and click the respective endpoint on the Detail pane.</span></span>

<span data-ttu-id="8ecfc-210">Atrybuty punktu końcowego są wyświetlane w okienku po prawej stronie do edycji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-210">Attributes for the endpoint are shown in the right pane for editing.</span></span>

#### <a name="deleting-a-standard-endpoint-configuration"></a><span data-ttu-id="8ecfc-211">Usuwanie standardowej konfiguracji punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="8ecfc-211">Deleting a Standard Endpoint Configuration</span></span>

<span data-ttu-id="8ecfc-212">Konfigurację standardowego punktu końcowego można usunąć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8ecfc-212">You can delete a standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="8ecfc-213">Kliknij, aby rozwinąć węzeł **standardowego punktu końcowego** , a następnie kliknij prawym przyciskiem myszy odpowiedni podwęzeł punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-213">Click to expand the **Standard Endpoint** node and right-click the respective endpoint sub-node.</span></span> <span data-ttu-id="8ecfc-214">Użyj polecenia kontekstowego **Usuń konfigurację standardowego punktu końcowego** , aby usunąć punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-214">Use the context command **Delete Standard Endpoint Configuration** to delete the endpoint.</span></span>

- <span data-ttu-id="8ecfc-215">Kliknij węzeł **standardowego punktu końcowego** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-215">Click the **Standard Endpoint** node.</span></span> <span data-ttu-id="8ecfc-216">W okienku **zadań** kliknij pozycję **Usuń konfigurację standardowego punktu końcowego**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-216">In the **Task** pane, click **Delete Standard Endpoint Configuration**.</span></span>

<span data-ttu-id="8ecfc-217">Jeśli standardowy punkt końcowy jest używany, podczas próby usunięcia zostanie wyświetlony komunikat ostrzegawczy: **Standardowy punkt końcowy jest używany. Jeśli usuniesz ją teraz, pamiętaj, aby usunąć wszystkie odwołania do innych części konfiguracji (na przykład w punkcie końcowym usługi lub w punkcie końcowym klienta). W przeciwnym razie konfiguracja będzie nieprawidłowa i nie będzie można jej otworzyć następnym razem. Czy na pewno chcesz usunąć standardowy punkt końcowy? "**</span><span class="sxs-lookup"><span data-stu-id="8ecfc-217">If the standard endpoint is in used, a warning message is displayed when you attempt to delete it: **The standard endpoint is in use. If you delete it now, please be sure to delete all of its references in other parts of the configuration (for example, in the service endpoint or client endpoint). Otherwise, the configuration will be invalid and cannot be opened next time. Are you sure you want to delete the standard endpoint?"**</span></span>

### <a name="binding"></a><span data-ttu-id="8ecfc-218">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="8ecfc-218">Binding</span></span>

<span data-ttu-id="8ecfc-219">Konfiguracje powiązań są używane do konfigurowania powiązań dla punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-219">Binding configurations are used to configure bindings on endpoints.</span></span> <span data-ttu-id="8ecfc-220">Takie ustawienia konfiguracji są przechowywane w węźle **powiązania** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-220">Such configuration settings are stored in the **Binding** node.</span></span> <span data-ttu-id="8ecfc-221">Odniesienia do konfiguracji powiązań odwołań według nazwy i wielu punktów końcowych mogą odwoływać się do konfiguracji pojedynczego powiązania.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-221">Endpoints reference binding configurations by name and multiple endpoints can reference a single binding configuration.</span></span>

<span data-ttu-id="8ecfc-222">W węźle **powiązania** są wyświetlane wszystkie ustawienia powiązań w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-222">The **Bindings** node displays all of the binding settings in the configuration file.</span></span> <span data-ttu-id="8ecfc-223">Każdy podwęzeł w drzewie odnosi się do elementu podrzędnego w <`bindings`> elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-223">Every sub-node in the tree corresponds to a sub-element in the <`bindings`> element in the configuration file.</span></span>

<span data-ttu-id="8ecfc-224">Po kliknięciu węzła **powiązania** można wyświetlić lub wykonać zadania na **stronie Podsumowanie** powiązań w **okienku szczegółów**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-224">When you click the **Bindings** node, you can view or perform tasks on the binding **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-binding-configuration"></a><span data-ttu-id="8ecfc-225">Tworzenie nowej konfiguracji powiązania</span><span class="sxs-lookup"><span data-stu-id="8ecfc-225">Creating a New Binding Configuration</span></span>

<span data-ttu-id="8ecfc-226">Nową konfigurację powiązania można utworzyć w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-226">You can create a new binding configuration in the following ways.</span></span>

- <span data-ttu-id="8ecfc-227">Kliknij prawym przyciskiem myszy węzeł **powiązania** i wybierz pozycję **Nowa konfiguracja powiązania**...</span><span class="sxs-lookup"><span data-stu-id="8ecfc-227">Right-click the **Bindings** node and select **New Binding Configuration**…</span></span> <span data-ttu-id="8ecfc-228">W oknie dialogowym Wybierz typ powiązania i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-228">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="8ecfc-229">Wybierz węzeł **powiązania** , a następnie kliknij pozycję **Nowa konfiguracja powiązania**...</span><span class="sxs-lookup"><span data-stu-id="8ecfc-229">Select the **Bindings** node and click **New Binding Configuration**…</span></span> <span data-ttu-id="8ecfc-230">w **okienku zadań** w lewym dolnym rogu okna.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-230">in the **Task Pane** on the lower-left of the window.</span></span>

- <span data-ttu-id="8ecfc-231">Na stronie Podsumowanie usługi lub klienta kliknij przycisk **kliknij, aby utworzyć** w polu **Konfiguracja powiązania** , aby utworzyć konfigurację powiązania dla odpowiedniego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-231">In the service or client summary page, click **Click to Create** in the **Binding Configuration** field to create a binding configuration for the corresponding endpoint.</span></span>

#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a><span data-ttu-id="8ecfc-232">Dodawanie rozszerzeń elementu wiązania do niestandardowego powiązania</span><span class="sxs-lookup"><span data-stu-id="8ecfc-232">Adding Binding Element Extensions to a Custom Binding</span></span>

1. <span data-ttu-id="8ecfc-233">Wybierz powiązanie, do którego chcesz dodać element rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-233">Select the binding you want to add an extension element to.</span></span>

2. <span data-ttu-id="8ecfc-234">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-234">Click **Add**.</span></span>

3. <span data-ttu-id="8ecfc-235">Z listy dostępnych rozszerzeń wybierz rozszerzenie elementu powiązania, które chcesz dodać.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-235">From the list of available extensions, select the binding element extension you want to add.</span></span> <span data-ttu-id="8ecfc-236">Aby zaznaczyć wiele elementów, naciśnij jednocześnie klawisz CTRL.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-236">To select multiple items, press the CTRL key simultaneously.</span></span>

4. <span data-ttu-id="8ecfc-237">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-237">Click **Add**.</span></span>

#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a><span data-ttu-id="8ecfc-238">Dopasowanie położenia rozszerzenia w niestandardowym powiązaniu</span><span class="sxs-lookup"><span data-stu-id="8ecfc-238">Adjusting the Extension Position in a Custom Binding</span></span>

<span data-ttu-id="8ecfc-239">Niestandardowe powiązanie to kolekcja elementów powiązania, które tworzą stos.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-239">A custom binding is a collection of binding elements that form a stack.</span></span> <span data-ttu-id="8ecfc-240">Każdy element powiązania na stosie ma własne ustawienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-240">Each binding element on the stack has its own configuration settings.</span></span> <span data-ttu-id="8ecfc-241">Kolejność rozszerzeń elementu powiązania w niestandardowym powiązaniu wskazuje ich położenie w stosie.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-241">The order of the binding element extensions in a custom binding indicates their positions in the stack.</span></span> <span data-ttu-id="8ecfc-242">Elementy w górnej części stosu są stosowane najpierw.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-242">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="8ecfc-243">Aby zmienić kolejność:</span><span class="sxs-lookup"><span data-stu-id="8ecfc-243">To change the ordering:</span></span>

1. <span data-ttu-id="8ecfc-244">Wybierz węzeł niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-244">Select the custom binding node.</span></span>

2. <span data-ttu-id="8ecfc-245">Wybierz jeden element rozszerzenia powiązania w sekcji **pozycja rozszerzenia elementu powiązania** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-245">Select one binding extension element in the **Binding Element Extension Position** section.</span></span>

3. <span data-ttu-id="8ecfc-246">Użyj przycisku w **górę** lub w **dół** z lewej strony listy, aby zmienić pozycję wybranego elementu.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-246">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a><span data-ttu-id="8ecfc-247">Edytowanie konfiguracji rozszerzeń elementu powiązania w niestandardowym powiązaniu</span><span class="sxs-lookup"><span data-stu-id="8ecfc-247">Editing the Configuration of Binding Element Extensions in a Custom Binding</span></span>

1. <span data-ttu-id="8ecfc-248">Wybierz węzeł powiązanie w drzewie.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-248">Select the binding node in the tree.</span></span>

2. <span data-ttu-id="8ecfc-249">Wybierz niestandardowe powiązanie, które zawiera element, który chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-249">Select the custom binding that contains the element you want to edit.</span></span>

3. <span data-ttu-id="8ecfc-250">Wybierz rozszerzenie elementu powiązania, które chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-250">Select the binding element extension you want to edit.</span></span> <span data-ttu-id="8ecfc-251">Ustawienia elementu są wyświetlane w okienku po prawej stronie, gdzie mogą być edytowane.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-251">The settings of the element appear in the right pane, where they can be edited.</span></span>

### <a name="diagnostics"></a><span data-ttu-id="8ecfc-252">Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="8ecfc-252">Diagnostics</span></span>

<span data-ttu-id="8ecfc-253">W węźle **Diagnostyka** są wyświetlane wszystkie ustawienia diagnostyczne w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-253">The **Diagnostics** node displays all of the diagnostic settings in the configuration file.</span></span> <span data-ttu-id="8ecfc-254">Umożliwia włączenie lub wyłączenie liczników wydajności, włączenie lub wyłączenie Instrumentacja zarządzania Windows (WMI), skonfigurowanie śledzenia WCF i skonfigurowanie rejestrowania komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-254">It enables you to turn performance counters on or off, enable or disable Windows Management Instrumentation (WMI), configure WCF tracing, and configure WCF message logging.</span></span> <span data-ttu-id="8ecfc-255">Ustawienia w węźle **Diagnostyka** odpowiadają sekcji <`system.diagnostics`> i `<diagnostics>` sekcji w `<system.serviceModel>` pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-255">The settings in the **Diagnostics** node correspond to the <`system.diagnostics`> section, and `<diagnostics>` section in `<system.serviceModel>` in the configuration file.</span></span>

<span data-ttu-id="8ecfc-256">Po kliknięciu węzła **Diagnostyka** można wyświetlić lub wykonać zadania na **stronie podsumowania** diagnostyki w **okienku szczegółów**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-256">When you click the **Diagnostics** node, you can view or perform tasks on the diagnostics **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="configuring-performance-counters-and-wmi"></a><span data-ttu-id="8ecfc-257">Konfigurowanie liczników wydajności i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="8ecfc-257">Configuring performance counters and WMI</span></span>

1. <span data-ttu-id="8ecfc-258">Kliknij węzeł **Diagnostyka** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-258">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="8ecfc-259">Kliknij pozycję **Przełącz liczniki wydajności**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-259">Click **Toggle Performance Counters**.</span></span> <span data-ttu-id="8ecfc-260">Licznik wydajności ma trzy stany: Wyłączone (wartość domyślna), tylko serviceI ALL.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-260">The performance counter has three states: Off (default), ServiceOnly, and All.</span></span> <span data-ttu-id="8ecfc-261">Kliknięcie linku powoduje przełączenie tego ustawienia między tymi trzema stanami.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-261">Clicking the link toggles the setting among these three states.</span></span>

#### <a name="configuring-wmi-provider"></a><span data-ttu-id="8ecfc-262">Konfigurowanie dostawcy WMI</span><span class="sxs-lookup"><span data-stu-id="8ecfc-262">Configuring WMI Provider</span></span>

1. <span data-ttu-id="8ecfc-263">Kliknij węzeł **Diagnostyka** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-263">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="8ecfc-264">Aby włączyć dostawcę usługi WMI, kliknij link **Włącz dostawcę WMI** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-264">To enable WMI provider, click the **Enable WMI Provider** link.</span></span>

#### <a name="enabling-wcf-tracing"></a><span data-ttu-id="8ecfc-265">Włączanie śledzenia WCF</span><span class="sxs-lookup"><span data-stu-id="8ecfc-265">Enabling WCF Tracing</span></span>

<span data-ttu-id="8ecfc-266">Można utworzyć plik śledzenia WCF ze standardowymi właściwościami lub skonfigurować niestandardowy plik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-266">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="8ecfc-267">Kliknij węzeł **Diagnostyka** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-267">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="8ecfc-268">Kliknij pozycję **Włącz śledzenie**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-268">Click **Enable Tracing**.</span></span>

3. <span data-ttu-id="8ecfc-269">Kliknij link **poziom śledzenia** , aby dostosować poziom śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-269">Click the **Trace Level** link to adjust the trace level.</span></span> <span data-ttu-id="8ecfc-270">Istnieje sześć poziomów śledzenia: Wyłączone, krytyczne, błąd, ostrzeżenie, informacje i pełne.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-270">There are six trace levels: Off, Critical, Error, Warning, Information, and Verbose.</span></span> <span data-ttu-id="8ecfc-271">Opcja **śledzenie działań** i **propagowanie** działań umożliwia korzystanie z funkcji śledzenia działań programu WCF.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-271">The **Activity Tracing** and **Propagate Activity** option enable you to use the WCF activity tracing feature.</span></span>

4. <span data-ttu-id="8ecfc-272">Kliknij nazwę odbiornika śledzenia, aby określić plik śledzenia i opcje.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-272">Click the trace listener name to specify the trace file and options.</span></span>

#### <a name="enabling-wcf-logging"></a><span data-ttu-id="8ecfc-273">Włączanie rejestrowania WCF</span><span class="sxs-lookup"><span data-stu-id="8ecfc-273">Enabling WCF Logging</span></span>

<span data-ttu-id="8ecfc-274">Można utworzyć plik śledzenia WCF ze standardowymi właściwościami lub skonfigurować niestandardowy plik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-274">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="8ecfc-275">Kliknij węzeł **Diagnostyka** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-275">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="8ecfc-276">Kliknij pozycję **Włącz rejestrowanie komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-276">Click **Enable Message Logging**.</span></span>

3. <span data-ttu-id="8ecfc-277">Kliknij link **poziom rejestrowania** , aby dostosować poziom rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-277">Click the **Log Level** link to adjust the log level.</span></span> <span data-ttu-id="8ecfc-278">Istnieją trzy poziomy dziennika: Źle sformułowane, usługa i transport.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-278">There are three log levels: Malformed, Service, and Transport.</span></span>

4. <span data-ttu-id="8ecfc-279">Kliknij nazwę odbiornika, aby określić plik dziennika i opcje.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-279">Click the listener name to specify the log file and options.</span></span>

> [!NOTE]
> <span data-ttu-id="8ecfc-280">Jeśli chcesz, aby dzienniki śledzenia i komunikatów były opróżniane automatycznie po zamknięciu aplikacji, Włącz opcję **automatycznego opróżniania** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-280">If you want the trace and message logs to be flushed automatically when your application is closed, enable the **Auto Flush** option.</span></span>

<span data-ttu-id="8ecfc-281">**Strona podsumowania** **diagnostyki** umożliwia wykonywanie najbardziej typowych zadań związanych z konfigurowaniem diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-281">The **Diagnostics** **Summary Page** enables you to accomplish the most common tasks in configuring diagnostics.</span></span> <span data-ttu-id="8ecfc-282">Jeśli jednak chcesz ręcznie edytować ustawienia odbiorników i źródeł, należy rozwinąć węzeł **Diagnostyka** i edytować ustawienia w węźle **Rejestrowanie komunikatów**, **odbiorniki** i **źródła** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-282">However, if you want to manually edit the Listeners and Sources settings, you must expand the **Diagnostics** node and edit settings in **Message Logging**, **Listeners** and **Sources** node.</span></span>

#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a><span data-ttu-id="8ecfc-283">Włączanie śledzenia niestandardowego programu WCF lub rejestrowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="8ecfc-283">Enabling WCF Custom Tracing or Message Logging</span></span>

1. <span data-ttu-id="8ecfc-284">Kliknij węzeł **Diagnostyka** i rozwiń go.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-284">Click the **Diagnostics** node, and expand it.</span></span>

2. <span data-ttu-id="8ecfc-285">Kliknij prawym przyciskiem myszy węzeł detektory i wybierz pozycję **Nowy odbiornik**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-285">Right-click the **Listeners** node and select **New Listener**.</span></span>

3. <span data-ttu-id="8ecfc-286">Wpisz nazwę pliku śledzenia w polu **InitData** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-286">Type in the trace file name in the **InitData** field.</span></span> <span data-ttu-id="8ecfc-287">Możesz kliknąć przycisk "..." przycisk, aby przejść do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-287">You can click the "…" button to browse to a path.</span></span>

4. <span data-ttu-id="8ecfc-288">Kliknięcie wiersza **TypeName** powoduje wyświetlenie "..." przycisk.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-288">Clicking the **TypeName** line displays a "…" button.</span></span> <span data-ttu-id="8ecfc-289">Kliknij ten przycisk, aby otworzyć **przeglądarkę śledzenia typów odbiorników**, której można użyć do znajdowania wstępnie skonfigurowanych detektorów śledzenia, które są już zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-289">Click this button to open the **Trace Listener Type Browser**, which you can use to find pre-configured trace listeners that are already installed.</span></span>

5. <span data-ttu-id="8ecfc-290">Zwróć uwagę na sekcję źródłową.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-290">Note the **Source** section.</span></span> <span data-ttu-id="8ecfc-291">Kliknij przycisk **Dodaj** w tej sekcji, aby otworzyć okno dialogowe z menu rozwijanym zawierającym listę dostępnych źródeł śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-291">Click **Add** in this section to open a dialog box with a drop-down menu, which lists available tracing sources.</span></span> <span data-ttu-id="8ecfc-292">Wybierz źródło śledzenia i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-292">Select a tracing source and click **OK**.</span></span>

6. <span data-ttu-id="8ecfc-293">Aby edytować ustawienia rejestrowania komunikatów, kliknij węzeł **Rejestrowanie komunikatów** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-293">To edit Message Logging settings, click the **Message Logging** node.</span></span> <span data-ttu-id="8ecfc-294">Ustawienia można edytować w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-294">You can edit the settings in the property grid.</span></span>

### <a name="advanced"></a><span data-ttu-id="8ecfc-295">Zaawansowane</span><span class="sxs-lookup"><span data-stu-id="8ecfc-295">Advanced</span></span>

#### <a name="behaviors"></a><span data-ttu-id="8ecfc-296">Zachowania</span><span class="sxs-lookup"><span data-stu-id="8ecfc-296">Behaviors</span></span>

<span data-ttu-id="8ecfc-297">W węźle **zachowań** są wyświetlane zachowania, które są obecnie zdefiniowane w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-297">The **Behaviors** node displays the behaviors that are currently defined in the configuration file.</span></span>

<span data-ttu-id="8ecfc-298">Konfiguracje zachowań są używane do konfigurowania zachowań punktów końcowych i usług.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-298">Behavior configurations are used to configure behaviors of endpoints and services.</span></span> <span data-ttu-id="8ecfc-299">Takie ustawienia konfiguracji są przechowywane w węźle **Zaawansowane** w obszarze **zachowania usługi** i **zachowania punktów końcowych**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-299">Such configuration settings are stored in the **Advanced** node under **Service Behaviors** and **Endpoint Behaviors**.</span></span> <span data-ttu-id="8ecfc-300">Zachowania usługi są używane przez usługi; zachowania punktu końcowego dla punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-300">Service behaviors are used by services; whereas endpoint behaviors by endpoints.</span></span>

<span data-ttu-id="8ecfc-301">Zachowania są kolekcją elementów rozszerzenia, które stosują stos.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-301">Behaviors are a collection of extension elements that for a stack.</span></span> <span data-ttu-id="8ecfc-302">Element w górnej części stosu jest stosowany najpierw.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-302">The element at the top of the stack is applied first.</span></span> <span data-ttu-id="8ecfc-303">Każdy element rozszerzenia może mieć własną konfigurację.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-303">Each extension element can have its own configuration.</span></span>

##### <a name="creating-a-new-behavior-configuration"></a><span data-ttu-id="8ecfc-304">Tworzenie nowej konfiguracji zachowania</span><span class="sxs-lookup"><span data-stu-id="8ecfc-304">Creating a new Behavior Configuration</span></span>

<span data-ttu-id="8ecfc-305">Nową konfigurację zachowania można utworzyć na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-305">You can create a new behavior configuration in two ways.</span></span>

- <span data-ttu-id="8ecfc-306">Kliknij prawym przyciskiem myszy jeden z węzłów zachowań i wybierz polecenie "**Nowa konfiguracja zachowań...**</span><span class="sxs-lookup"><span data-stu-id="8ecfc-306">Right-click one of the behavior nodes and select "**New Behavior Configuration…**</span></span>

- <span data-ttu-id="8ecfc-307">Wybierz jeden z węzłów zachowań i kliknij **nową konfigurację zachowań**...</span><span class="sxs-lookup"><span data-stu-id="8ecfc-307">Select one of the behavior nodes and click the **New Behavior Configuration**…</span></span> <span data-ttu-id="8ecfc-308">w **okienku zadań** w lewym dolnym rogu okna.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-308">in the **Task Pane** on the lower-left of the window.</span></span>

##### <a name="adding-behavior-element-extensions-to-a-behavior"></a><span data-ttu-id="8ecfc-309">Dodawanie rozszerzeń elementu zachowania do zachowania</span><span class="sxs-lookup"><span data-stu-id="8ecfc-309">Adding Behavior Element Extensions to a Behavior</span></span>

1. <span data-ttu-id="8ecfc-310">Wybierz jeden z węzłów zachowań.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-310">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="8ecfc-311">Wybierz zachowanie, które chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-311">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="8ecfc-312">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-312">Click **Add**.</span></span>

4. <span data-ttu-id="8ecfc-313">Z listy dostępnych rozszerzeń wybierz rozszerzenie elementu zachowania, które chcesz dodać.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-313">From the list of available extensions, select the behavior element extension you want to add.</span></span>

5. <span data-ttu-id="8ecfc-314">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-314">Click **Add**.</span></span>

##### <a name="adjusting-the-extension-position-in-a-behavior"></a><span data-ttu-id="8ecfc-315">Dopasowanie położenia rozszerzenia w ramach zachowania</span><span class="sxs-lookup"><span data-stu-id="8ecfc-315">Adjusting the Extension Position in a Behavior</span></span>

<span data-ttu-id="8ecfc-316">Zachowania są kolekcjami elementów tworzących stos.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-316">Behaviors are collections of elements that form a stack.</span></span> <span data-ttu-id="8ecfc-317">Każdy element na stosie ma własną konfigurację.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-317">Each element on the stack has its own configuration.</span></span> <span data-ttu-id="8ecfc-318">Kolejność rozszerzeń elementów zachowań w zachowaniu wskazuje ich położenie w stosie.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-318">The order of the behavior element extensions in a behavior indicates their positions in the stack.</span></span> <span data-ttu-id="8ecfc-319">Elementy w górnej części stosu są stosowane najpierw.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-319">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="8ecfc-320">Aby zmienić kolejność:</span><span class="sxs-lookup"><span data-stu-id="8ecfc-320">To change the ordering:</span></span>

1. <span data-ttu-id="8ecfc-321">Wybierz jeden z węzłów zachowań.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-321">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="8ecfc-322">Wybierz zachowanie, które chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-322">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="8ecfc-323">Zaznacz element rozszerzenia zachowań w sekcji **pozycja rozszerzenia elementu zachowania** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-323">Select a behavior extension element in the **Behavior Element Extension Position** section.</span></span>

4. <span data-ttu-id="8ecfc-324">Użyj przycisku w **górę** lub w **dół** z lewej strony listy, aby zmienić pozycję wybranego elementu.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-324">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

##### <a name="editing-the-configuration-of-behavior-element-extensions"></a><span data-ttu-id="8ecfc-325">Edytowanie konfiguracji rozszerzeń elementów zachowań</span><span class="sxs-lookup"><span data-stu-id="8ecfc-325">Editing the Configuration of Behavior Element Extensions</span></span>

1. <span data-ttu-id="8ecfc-326">Wybierz jeden z węzłów zachowań w drzewie.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-326">Select one of the behavior nodes in the tree.</span></span>

2. <span data-ttu-id="8ecfc-327">Wybierz zachowanie, które zawiera element, który chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-327">Select the behavior that contains the element you want to edit.</span></span>

3. <span data-ttu-id="8ecfc-328">Wybierz rozszerzenie elementu zachowania, które chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-328">Select the behavior element extension you want to edit.</span></span> <span data-ttu-id="8ecfc-329">Ustawienia elementu są wyświetlane w okienku po prawej stronie, w którym można je edytować.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-329">The settings of the element appear in the right pane where they can be edited.</span></span>

#### <a name="protocolmapping"></a><span data-ttu-id="8ecfc-330">ProtocolMapping</span><span class="sxs-lookup"><span data-stu-id="8ecfc-330">ProtocolMapping</span></span>

<span data-ttu-id="8ecfc-331">Ta sekcja umożliwia ustawienie domyślnych typów powiązań dla różnych protokołów, takich jak http, TCP, MSMQ lub net. pipe przez zdefiniowane mapowanie między schematami adresów protokołu a możliwymi powiązaniami.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-331">This section allows you to set default binding types for different protocols such as http, tcp, MSMQ or net.pipe through defined mapping between protocol address schemes and the possible bindings.</span></span> <span data-ttu-id="8ecfc-332">Możesz również dodać nowe mapowania do innych protokołów.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-332">You can also add new mappings to other protocols.</span></span>

#### <a name="extensions"></a><span data-ttu-id="8ecfc-333">Rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="8ecfc-333">Extensions</span></span>

<span data-ttu-id="8ecfc-334">Nowe rozszerzenia powiązań, rozszerzenia elementów powiązania, standardowe rozszerzenia punktów końcowych i rozszerzenia zachowań mogą być zarejestrowane do użycia w konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-334">New binding extensions, binding element extensions, standard endpoint extensions and behavior extensions can be registered for use in WCF configuration.</span></span> <span data-ttu-id="8ecfc-335">Rozszerzeniami są pary nazwa/typ.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-335">Extensions are name/type pairs.</span></span> <span data-ttu-id="8ecfc-336">Nazwa definiuje nazwę rozszerzenia w konfiguracji, podczas gdy typ implementuje rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-336">The name defines the name of the extension in configuration, whereas the type implements the extension.</span></span> <span data-ttu-id="8ecfc-337">Istnieją cztery typy rozszerzeń:</span><span class="sxs-lookup"><span data-stu-id="8ecfc-337">There are four types of extensions:</span></span>

- <span data-ttu-id="8ecfc-338">Rozszerzenia powiązań definiują cały typ powiązania.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-338">Binding extensions define an entire binding type.</span></span> <span data-ttu-id="8ecfc-339">Przykład: `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-339">Example: `basicHttpBinding`.</span></span>

- <span data-ttu-id="8ecfc-340">Rozszerzenia elementów powiązania definiują element powiązania.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-340">Binding element extensions define an element of a binding.</span></span> <span data-ttu-id="8ecfc-341">Przykład: `textMessageEncoding`.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-341">Example: `textMessageEncoding`.</span></span>

- <span data-ttu-id="8ecfc-342">Standardowe rozszerzenia punktów końcowych definiują cały standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-342">Standard endpoint extensions define an entire standard endpoint.</span></span> <span data-ttu-id="8ecfc-343">Przykład: `discoveryEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-343">Example: `discoveryEndpoint`.</span></span>

- <span data-ttu-id="8ecfc-344">Rozszerzenia elementów zachowań definiują element zachowania.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-344">Behavior element extensions define an element of a behavior.</span></span> <span data-ttu-id="8ecfc-345">Przykład: `clientVia`.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-345">Example: `clientVia`.</span></span>

 <span data-ttu-id="8ecfc-346">Rozszerzenia, które zostały zarejestrowane w konfiguracji, mogą być używane jak każdy inny składnik WCF tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-346">Extensions that have been registered in configuration can be used like any other WCF component of the same type.</span></span>

##### <a name="adding-a-new-extension"></a><span data-ttu-id="8ecfc-347">Dodawanie nowego rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="8ecfc-347">Adding a new extension</span></span>

<span data-ttu-id="8ecfc-348">Wybierz jeden z węzłów rozszerzeń w węzłach zaawansowanych:</span><span class="sxs-lookup"><span data-stu-id="8ecfc-348">Select one of the extension nodes in the advanced nodes:</span></span>

1. <span data-ttu-id="8ecfc-349">Kliknij przycisk **Nowy**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-349">Click **New**.</span></span>

2. <span data-ttu-id="8ecfc-350">Wprowadź nazwę i typ.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-350">Enter a name and type.</span></span>

3. <span data-ttu-id="8ecfc-351">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-351">Click **OK**.</span></span>

4. <span data-ttu-id="8ecfc-352">Rozszerzenie jest teraz widoczne w odpowiednim miejscu w edytorze.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-352">The extension now appears in the appropriate place in the Editor.</span></span> <span data-ttu-id="8ecfc-353">Na przykład, jeśli dodasz rozszerzenie elementu zachowania, pojawia się ono na liście dostępnych rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-353">For example, if you add a behavior element extension, it appears in the list of available extensions.</span></span>

#### <a name="hosting-environment"></a><span data-ttu-id="8ecfc-354">Środowisko hostingu</span><span class="sxs-lookup"><span data-stu-id="8ecfc-354">Hosting Environment</span></span>

<span data-ttu-id="8ecfc-355">Ta sekcja umożliwia zdefiniowanie ustawień tworzenia wystąpienia dla środowiska hostingu usługi.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-355">This section allows you to define instantiation settings for the service hosting environment.</span></span>

### <a name="creating-a-configuration-file-using-the-wizard"></a><span data-ttu-id="8ecfc-356">Tworzenie pliku konfiguracji przy użyciu kreatora</span><span class="sxs-lookup"><span data-stu-id="8ecfc-356">Creating a Configuration File Using the Wizard</span></span>

<span data-ttu-id="8ecfc-357">Jednym ze sposobów tworzenia nowego pliku konfiguracji jest użycie Kreatora nowego elementu usługi.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-357">One way to create a new configuration file is to use the New Service Element Wizard.</span></span> <span data-ttu-id="8ecfc-358">Kreator odnajduje zainstalowane typy usług i inne elementy zgodne z programem WCF na komputerze, w tym katalogi wirtualne COM+ i hostowane w sieci Web, i ładuje je w celu znacznie usprawnienia tworzenia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-358">The wizard finds the installed service types and other elements compatible with WCF on the computer, including COM+ and Web-hosted virtual directories, and loads them to make creating the configuration much more streamlined.</span></span>

#### <a name="creating-a-configuration-file"></a><span data-ttu-id="8ecfc-359">Tworzenie pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8ecfc-359">Creating a Configuration File</span></span>

1. <span data-ttu-id="8ecfc-360">Uruchom Edytor konfiguracji usługi przy użyciu okna wiersza polecenia, aby przejść do lokalizacji instalacji programu WCF, a następnie `SvcConfigEditor.exe`wpisz polecenie.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-360">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="8ecfc-361">W menu **plik** wybierz pozycję **Otwórz** , a następnie kliknij pozycję plik wykonywalny, **Usługa com+** lub **Usługa**webhosted, w zależności od typu pliku konfiguracji, który chcesz utworzyć.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-361">From the **File** menu, select **Open** and click **Executable**, **COM+ Service**, or **WebHosted Service**, depending on the type of configuration file you want to create.</span></span>

3. <span data-ttu-id="8ecfc-362">W oknie dialogowym **Otwórz** przejdź do określonego pliku, dla którego chcesz utworzyć plik konfiguracji, a następnie kliknij go dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-362">In the **Open** dialog box, navigate to the specific file you want to create a configuration file for and double-click it.</span></span>

4. <span data-ttu-id="8ecfc-363">W menu **plik** wskaż polecenie **Dodaj nowy element** , a następnie kliknij pozycję **Usługa**.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-363">In the **File** menu, point to **Add New Item** and click **Service**.</span></span> <span data-ttu-id="8ecfc-364">Zostanie otwarty Kreator nowego elementu usługi.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-364">The New Service Element Wizard opens.</span></span>

5. <span data-ttu-id="8ecfc-365">Postępuj zgodnie z instrukcjami w kreatorze, aby utworzyć nową usługę.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-365">Follow the steps in the wizard to create the new service.</span></span>

> [!NOTE]
> <span data-ttu-id="8ecfc-366">Jeśli chcesz użyć NetPeerTcpBinding z pliku konfiguracji wygenerowanego przez kreatora, musisz ręcznie dodać element konfiguracji powiązania i zmodyfikować `mode` atrybut jego `security` elementu na wartość "none".</span><span class="sxs-lookup"><span data-stu-id="8ecfc-366">If you want to use the NetPeerTcpBinding from the configuration file generated by the Wizard, you have to manually add a binding configuration element and modify the `mode` attribute of its `security` element to "None".</span></span>

## <a name="configuring-com"></a><span data-ttu-id="8ecfc-367">Konfigurowanie modelu COM+</span><span class="sxs-lookup"><span data-stu-id="8ecfc-367">Configuring COM+</span></span>

<span data-ttu-id="8ecfc-368">Edytor konfiguracji usługi umożliwia utworzenie nowego pliku konfiguracji dla istniejącej aplikacji modelu COM+ lub edytowanie istniejącej konfiguracji modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-368">The Service Configuration Editor enables you to create a new configuration file for an existing COM+ application, or edit an existing COM+ configuration.</span></span> <span data-ttu-id="8ecfc-369">Węzeł **kontraktu com** jest widoczny tylko wtedy, gdy sekcja`comContract`> < istnieje w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-369">The **COM Contract** node is only visible when the <`comContract`> section exists in the configuration file.</span></span>

### <a name="creating-a-new-com-configuration"></a><span data-ttu-id="8ecfc-370">Tworzenie nowej konfiguracji modelu COM+</span><span class="sxs-lookup"><span data-stu-id="8ecfc-370">Creating a New COM+ Configuration</span></span>

<span data-ttu-id="8ecfc-371">Przed utworzeniem nowej konfiguracji modelu COM+ upewnij się, że aplikacja modelu COM+ jest zainstalowana w usługach składników i zarejestrowana w globalnej pamięci podręcznej zestawów (GAC).</span><span class="sxs-lookup"><span data-stu-id="8ecfc-371">Before creating a new COM+ configuration, make sure that your COM+ application is installed in Component Services, and registered in the Global Assembly Cache (GAC).</span></span>

1. <span data-ttu-id="8ecfc-372">Wybierz menu **plik** — > **Zintegruj** -> **aplikację com+.**</span><span class="sxs-lookup"><span data-stu-id="8ecfc-372">Select **File** menu -> **Integrate** -> **COM+ Application.**</span></span> <span data-ttu-id="8ecfc-373">Ta operacja zamyka bieżący otwarty plik.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-373">This operation closes the current opened file.</span></span> <span data-ttu-id="8ecfc-374">Jeśli w bieżącym pliku znajdują się niezapisane dane, zostanie wyświetlone okno dialogowe Zapisz.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-374">If there is unsaved data in the current file, a Save dialog appears.</span></span> <span data-ttu-id="8ecfc-375">Następnie zostanie uruchomiony **Kreator integracji modelu COM+** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-375">The **COM+ Integration Wizard** is then launched.</span></span>

2. <span data-ttu-id="8ecfc-376">Na pierwszej stronie wybierz aplikację COM+ z drzewa.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-376">In the first page, select the COM+ application from the tree.</span></span> <span data-ttu-id="8ecfc-377">Jeśli nie możesz znaleźć aplikacji modelu COM+ w drzewie, sprawdź, czy jest ona zainstalowana w usługach składników i zarejestrowana w globalnej pamięci podręcznej zestawów (GAC).</span><span class="sxs-lookup"><span data-stu-id="8ecfc-377">If you cannot find your COM+ application in the tree, verify that it is installed in the Component Services and registered in the Global Assembly Cache (GAC).</span></span>

3. <span data-ttu-id="8ecfc-378">Na następnej stronie Wybierz metody, które chcesz uwidocznić jako usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-378">In the next page, select which method(s) you want to expose as WCF services.</span></span> <span data-ttu-id="8ecfc-379">Wszystkie obsługiwane metody w aplikacji COM+ są domyślnie wyświetlane i wybierane.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-379">All the supported methods in the COM+ application are displayed and selected by default.</span></span>

4. <span data-ttu-id="8ecfc-380">Wybierz metodę hostingu.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-380">Choose a hosting method.</span></span>

5. <span data-ttu-id="8ecfc-381">Skonfiguruj inne ustawienia zgodnie z przewodnikami w kreatorze.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-381">Configure other settings according to the guides in the wizard.</span></span>

6. <span data-ttu-id="8ecfc-382">Edytor konfiguracji usługi używa programu ComSvcConfig. exe w tle do generowania pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-382">Service Configuration Editor utilizes ComSvcConfig.exe in the background to generate configuration file.</span></span> <span data-ttu-id="8ecfc-383">Po zakończeniu tej operacji można wyświetlić podsumowanie i zakończyć pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-383">After this is completed, you can view a summary and exit the wizard.</span></span> <span data-ttu-id="8ecfc-384">Wygenerowany plik konfiguracji zostanie otwarty, aby można go było edytować bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-384">The generated configuration file is opened so that you can edit it directly.</span></span>

### <a name="editing-an-existing-com-configuration"></a><span data-ttu-id="8ecfc-385">Edytowanie istniejącej konfiguracji modelu COM+</span><span class="sxs-lookup"><span data-stu-id="8ecfc-385">Editing an Existing COM+ Configuration</span></span>

1. <span data-ttu-id="8ecfc-386">Wybierz menu **plik** > **Otwórz** -> **usługę com+** ...</span><span class="sxs-lookup"><span data-stu-id="8ecfc-386">Select **File** menu -> **Open** -> **COM+ Service**…</span></span>

2. <span data-ttu-id="8ecfc-387">Wybierz z listy usługę COM+, którą chcesz edytować.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-387">Select the COM+ Service you want to edit from the list.</span></span>

3. <span data-ttu-id="8ecfc-388">Edytuj ustawienia konfiguracji w węźle **kontrakty com** .</span><span class="sxs-lookup"><span data-stu-id="8ecfc-388">Edit configuration settings in the **COM Contracts** node.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8ecfc-389">Można również bezpośrednio otworzyć i edytować plik konfiguracji, który zawiera kontrakty COM.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-389">You can also directly open and edit a configuration file that contains COM contracts.</span></span>

## <a name="security"></a><span data-ttu-id="8ecfc-390">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="8ecfc-390">Security</span></span>

<span data-ttu-id="8ecfc-391">Nie ma gwarancji, że plik konfiguracji usługi wygenerowany przez Edytor konfiguracji jest bezpieczny.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-391">A service configuration file generated by the Configuration Editor is not guaranteed to be secure.</span></span> <span data-ttu-id="8ecfc-392">Zapoznaj się z dokumentacją [zabezpieczeń](../../../docs/framework/wcf/feature-details/security.md) , aby dowiedzieć się, jak zabezpieczyć usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-392">Please refer to the [Security](../../../docs/framework/wcf/feature-details/security.md) documentation to find out how to secure your WCF services.</span></span>

<span data-ttu-id="8ecfc-393">Ponadto edytor konfiguracji może być używany tylko do odczytu i zapisu prawidłowych elementów konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-393">In addition, the Configuration Editor can only be used to read and write valid WCF configuration elements.</span></span> <span data-ttu-id="8ecfc-394">Narzędzie ignoruje elementy zdefiniowane przez użytkownika, które są zgodne ze schematem.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-394">The tool ignores schema-compliant, user-defined elements.</span></span> <span data-ttu-id="8ecfc-395">Nie powoduje to również usunięcia tych elementów z pliku konfiguracyjnego ani określania ich wpływu na znane elementy programu WCF.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-395">It also does not attempt remove these elements from the configuration file or determine their effects on the known WCF elements.</span></span> <span data-ttu-id="8ecfc-396">Użytkownik jest odpowiedzialny za określenie, czy te elementy stanowią zagrożenie dla aplikacji lub systemu.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-396">It is the user’s responsibility to determine whether these elements pose a threat to the application or the system.</span></span>
