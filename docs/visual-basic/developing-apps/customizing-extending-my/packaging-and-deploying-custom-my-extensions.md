---
title: Pakowanie i wdrażanie niestandardowych rozszerzeń my
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: a2e2a6705fb3d8d4424d46d96bbf49b41e1414af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330259"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a><span data-ttu-id="36903-102">Pakowanie i wdrażanie niestandardowych rozszerzeń my (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36903-102">Package and deploy custom My extensions (Visual Basic)</span></span>

<span data-ttu-id="36903-103">Visual Basic zapewnia łatwy sposób wdrażania rozszerzeń niestandardowej przestrzeni nazw `My` przy użyciu szablonów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36903-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="36903-104">Jeśli tworzysz szablon projektu, dla którego rozszerzenia `My` są integralną częścią nowego typu projektu, możesz po prostu dołączyć kod niestandardowego rozszerzenia `My` do projektu podczas eksportowania szablonu.</span><span class="sxs-lookup"><span data-stu-id="36903-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="36903-105">Aby uzyskać więcej informacji na temat eksportowania szablonów projektów, zobacz [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span><span class="sxs-lookup"><span data-stu-id="36903-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>

<span data-ttu-id="36903-106">Jeśli niestandardowe rozszerzenie `My` znajduje się w pojedynczym pliku kodu, można wyeksportować plik jako szablon elementu, który użytkownicy mogą dodać do dowolnego typu Visual Basic projektu.</span><span class="sxs-lookup"><span data-stu-id="36903-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="36903-107">Następnie można dostosować szablon elementu, aby umożliwić dodatkowe możliwości i zachowanie dla niestandardowego rozszerzenia `My` w projekcie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="36903-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="36903-108">Dostępne są następujące możliwości:</span><span class="sxs-lookup"><span data-stu-id="36903-108">Those capabilities include the following:</span></span>

- <span data-ttu-id="36903-109">Umożliwienie użytkownikom zarządzania rozszerzeniem niestandardowego `My` na stronie **Moje rozszerzenia** projektanta projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="36903-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>

- <span data-ttu-id="36903-110">Automatyczne dodanie niestandardowego rozszerzenia `My`, gdy odwołanie do określonego zestawu zostanie dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="36903-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>

- <span data-ttu-id="36903-111">Ukrywanie szablonu `My` elementu rozszerzenia w oknie dialogowym **Dodaj element** , tak aby nie było ono zawarte na liście elementów projektu.</span><span class="sxs-lookup"><span data-stu-id="36903-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>

<span data-ttu-id="36903-112">W tym temacie omówiono sposób pakowania niestandardowego rozszerzenia `My` jako szablonu ukrytego elementu, którym można zarządzać za pomocą strony **Moje rozszerzenia** w programie Visual Basic Designer projektanta.</span><span class="sxs-lookup"><span data-stu-id="36903-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="36903-113">Niestandardowe rozszerzenie `My` można również dodać automatycznie, gdy odwołanie do określonego zestawu zostanie dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="36903-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>

## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="36903-114">Tworzenie rozszerzenia my Namespace</span><span class="sxs-lookup"><span data-stu-id="36903-114">Create a My namespace extension</span></span>

<span data-ttu-id="36903-115">Pierwszym krokiem tworzenia pakietu wdrożeniowego dla niestandardowego rozszerzenia `My` jest utworzenie rozszerzenia jako pojedynczego pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="36903-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="36903-116">Aby uzyskać szczegółowe informacje i wskazówki dotyczące sposobu tworzenia niestandardowego rozszerzenia `My`, zobacz [rozszerzanie przestrzeni nazw my w Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="36903-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>

## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="36903-117">Eksportowanie rozszerzenia my Namespace jako szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="36903-117">Export a My namespace extension as an item template</span></span>

<span data-ttu-id="36903-118">Po utworzeniu pliku z kodem, który zawiera rozszerzenie przestrzeni nazw `My`, można wyeksportować plik kodu jako szablon elementu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36903-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="36903-119">Aby uzyskać instrukcje dotyczące sposobu eksportowania pliku jako szablonu elementu programu Visual Studio, zobacz [How to: Create Item templates](/visualstudio/ide/how-to-create-item-templates).</span><span class="sxs-lookup"><span data-stu-id="36903-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>

> [!NOTE]
> <span data-ttu-id="36903-120">Jeśli rozszerzenie przestrzeni nazw `My` ma zależność od określonego zestawu, można dostosować szablon elementu tak, aby automatycznie instalował rozszerzenie przestrzeni nazw `My` po dodaniu odwołania do tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="36903-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="36903-121">W związku z tym należy wykluczyć to odwołanie do zestawu podczas eksportowania pliku kodu jako szablonu elementu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36903-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>

## <a name="customize-the-item-template"></a><span data-ttu-id="36903-122">Dostosuj szablon elementu</span><span class="sxs-lookup"><span data-stu-id="36903-122">Customize the item template</span></span>

<span data-ttu-id="36903-123">Szablon elementu można włączyć jako zarządzany na stronie **Moje rozszerzenia** projektanta projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="36903-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="36903-124">Można również włączyć automatyczne Dodawanie szablonu elementu, gdy odwołanie do określonego zestawu zostanie dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="36903-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="36903-125">Aby włączyć te dostosowania, należy dodać nowy plik o nazwie plik CustomData, do szablonu, a następnie dodać nowy element do pliku XML w plik. vstemplate.</span><span class="sxs-lookup"><span data-stu-id="36903-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>

### <a name="add-the-customdata-file"></a><span data-ttu-id="36903-126">Dodaj plik CustomData</span><span class="sxs-lookup"><span data-stu-id="36903-126">Add the CustomData file</span></span>

<span data-ttu-id="36903-127">Plik CustomData jest plikiem tekstowym, który ma rozszerzenie nazwy pliku. CustomData (nazwa pliku może być ustawiona na dowolną wartość znaczącą dla szablonu), która zawiera kod XML.</span><span class="sxs-lookup"><span data-stu-id="36903-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="36903-128">KOD XML w pliku CustomData instruuje Visual Basic, aby dołączać `My` rozszerzenia, gdy użytkownicy korzystają z strony **Moje rozszerzenia** w projektancie projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="36903-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="36903-129">Opcjonalnie możesz dodać atrybut`AssemblyFullName>` < do pliku XML CustomData.</span><span class="sxs-lookup"><span data-stu-id="36903-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="36903-130">Powoduje to Visual Basic automatyczne zainstalowanie niestandardowego rozszerzenia `My`, gdy odwołanie do określonego zestawu zostanie dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="36903-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="36903-131">Możesz użyć dowolnego edytora tekstu lub edytora XML, aby utworzyć plik CustomData, a następnie dodać go do skompresowanego folderu szablonu elementu (plik. zip).</span><span class="sxs-lookup"><span data-stu-id="36903-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>

<span data-ttu-id="36903-132">Na przykład poniższy kod XML przedstawia zawartość pliku CustomData, który doda element szablonu do folderu Moje rozszerzenia projektu Visual Basic, gdy odwołanie do zestawu Microsoft. VisualBasic. PowerPacks. vs. dll zostanie dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="36903-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

<span data-ttu-id="36903-133">Plik CustomData zawiera element`VBMyExtensionTemplate>` <, który zawiera atrybuty wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="36903-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>

|<span data-ttu-id="36903-134">Atrybut</span><span class="sxs-lookup"><span data-stu-id="36903-134">Attribute</span></span>|<span data-ttu-id="36903-135">Opis</span><span class="sxs-lookup"><span data-stu-id="36903-135">Description</span></span>|
|---|---|
|`ID`|<span data-ttu-id="36903-136">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="36903-136">Required.</span></span> <span data-ttu-id="36903-137">Unikatowy identyfikator rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="36903-137">A unique identifier for the extension.</span></span> <span data-ttu-id="36903-138">Jeśli rozszerzenie, które ma ten identyfikator, zostało już dodane do projektu, użytkownik nie będzie monitowany o ponowne dodanie go.</span><span class="sxs-lookup"><span data-stu-id="36903-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|
|`Version`|<span data-ttu-id="36903-139">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="36903-139">Required.</span></span> <span data-ttu-id="36903-140">Numer wersji szablonu elementu.</span><span class="sxs-lookup"><span data-stu-id="36903-140">A version number for the item template.</span></span>|
|`AssemblyFullName`|<span data-ttu-id="36903-141">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="36903-141">Optional.</span></span> <span data-ttu-id="36903-142">Nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="36903-142">An assembly name.</span></span> <span data-ttu-id="36903-143">Gdy odwołanie do tego zestawu zostanie dodane do projektu, użytkownik zostanie poproszony o dodanie rozszerzenia `My` z tego szablonu elementu.</span><span class="sxs-lookup"><span data-stu-id="36903-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="36903-144">Dodaj element \<CustomDataSignature > do pliku vstemplate</span><span class="sxs-lookup"><span data-stu-id="36903-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>

<span data-ttu-id="36903-145">Aby zidentyfikować szablon elementu programu Visual Studio jako rozszerzenie przestrzeni nazw `My`, należy również zmodyfikować plik vstemplate szablonu elementu.</span><span class="sxs-lookup"><span data-stu-id="36903-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="36903-146">Należy dodać element `<CustomDataSignature>` do elementu `<TemplateData>`.</span><span class="sxs-lookup"><span data-stu-id="36903-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="36903-147">Element `<CustomDataSignature>` musi zawierać `Microsoft.VisualBasic.MyExtension`tekstu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="36903-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

<span data-ttu-id="36903-148">Nie można bezpośrednio modyfikować plików w skompresowanym folderze (pliku. zip).</span><span class="sxs-lookup"><span data-stu-id="36903-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="36903-149">Należy skopiować plik. vstemplate z folderu skompresowanego, zmodyfikować go, a następnie zastąpić plik. vstemplate w folderze skompresowanym przy użyciu zaktualizowanej kopii.</span><span class="sxs-lookup"><span data-stu-id="36903-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>

<span data-ttu-id="36903-150">Poniższy przykład pokazuje zawartość pliku. vstemplate, który ma dodany element `<CustomDataSignature>`.</span><span class="sxs-lookup"><span data-stu-id="36903-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>

```xml
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
  <TemplateData>
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>
    <Name>MyPrinterInfo</Name>
    <Description>Custom My Extensions Item Template</Description>
    <ProjectType>VisualBasic</ProjectType>
    <SortOrder>10</SortOrder>
    <Icon>__TemplateIcon.ico</Icon>
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>
  </TemplateData>
  <TemplateContent>
    <References />
    <ProjectItem SubType="Code"
                 TargetFileName="$fileinputname$.vb"
                 ReplaceParameters="true"
     >MyCustomExtensionModule.vb</ProjectItem>
  </TemplateContent>
</VSTemplate>
```

## <a name="install-the-template"></a><span data-ttu-id="36903-151">Instalowanie szablonu</span><span class="sxs-lookup"><span data-stu-id="36903-151">Install the template</span></span>

<span data-ttu-id="36903-152">Aby zainstalować szablon, można skopiować skompresowany folder (plik*zip* ) do folderu szablonów elementów Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="36903-152">To install the template, you can copy the compressed folder (*.zip* file) to the Visual Basic item templates folder.</span></span> <span data-ttu-id="36903-153">Domyślnie szablony elementów użytkownika znajdują się w *%USERPROFILE%\Documents\Visual Studio \<wersja\>\Templates\ItemTemplates\Visual Basic*.</span><span class="sxs-lookup"><span data-stu-id="36903-153">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span></span> <span data-ttu-id="36903-154">Alternatywnie można opublikować szablon jako plik Instalator programu Visual Studio ( *. VSI*).</span><span class="sxs-lookup"><span data-stu-id="36903-154">Alternatively, you can publish the template as a Visual Studio Installer (*.vsi*) file.</span></span>

## <a name="see-also"></a><span data-ttu-id="36903-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36903-155">See also</span></span>

- [<span data-ttu-id="36903-156">Rozszerzanie przestrzeni nazw my w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="36903-156">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [<span data-ttu-id="36903-157">Rozszerzanie modelu aplikacji Visual Basic</span><span class="sxs-lookup"><span data-stu-id="36903-157">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [<span data-ttu-id="36903-158">Dostosowywanie, które obiekty są dostępne w My</span><span class="sxs-lookup"><span data-stu-id="36903-158">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [<span data-ttu-id="36903-159">Strona Moje rozszerzenia, Projektant projektu</span><span class="sxs-lookup"><span data-stu-id="36903-159">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
