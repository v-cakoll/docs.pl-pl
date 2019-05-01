---
title: Pakowanie i wdrażanie niestandardowych rozszerzeń My (Visual Basic)
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 4212f58c39f63be6ba20c3b79e5d9c98d0615c5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014209"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a><span data-ttu-id="b16f9-102">Pakowanie i wdrażanie niestandardowych rozszerzeń My (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b16f9-102">Package and deploy custom My extensions (Visual Basic)</span></span>

<span data-ttu-id="b16f9-103">Visual Basic zapewnia łatwy sposób można wdrażać niestandardowe `My` rozszerzenia nazw przy użyciu szablonów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b16f9-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="b16f9-104">Jeśli tworzysz szablon projektu, dla którego Twoja `My` rozszerzenia są integralną częścią nowy typ projektu, możesz po prostu dołączyć niestandardowe `My` rozszerzenia kodu z projektem podczas eksportowania szablonu.</span><span class="sxs-lookup"><span data-stu-id="b16f9-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="b16f9-105">Aby uzyskać więcej informacji na temat eksportowania szablonów projektu, zobacz [jak: Tworzenie szablonów projektów](/visualstudio/ide/how-to-create-project-templates).</span><span class="sxs-lookup"><span data-stu-id="b16f9-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>

<span data-ttu-id="b16f9-106">Jeśli niestandardowe `My` rozszerzenia znajduje się w pliku pojedynczego kodu, możesz wyeksportować plik jako szablon elementu, który użytkownicy mogą dodawać do dowolnego typu projektu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b16f9-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="b16f9-107">Następnie można dostosować szablon elementu, aby włączyć dodatkowe funkcje i działanie dla niestandardowych `My` rozszerzeń w projekcie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b16f9-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="b16f9-108">Te możliwości są następujące:</span><span class="sxs-lookup"><span data-stu-id="b16f9-108">Those capabilities include the following:</span></span>

- <span data-ttu-id="b16f9-109">Zezwalanie użytkownikom na zarządzanie niestandardowe `My` rozszerzenie z **Moje rozszerzenia** strony w Projektancie projektu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b16f9-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>

- <span data-ttu-id="b16f9-110">Automatyczne dodawanie niestandardowych `My` rozszerzenia, gdy odwołanie do określonego zestawu został dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="b16f9-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>

- <span data-ttu-id="b16f9-111">Ukrywanie `My` szablon elementu rozszerzenia w **elementu Dodawanie** okno dialogowe, tak aby nie znajduje się na liście elementów projektu.</span><span class="sxs-lookup"><span data-stu-id="b16f9-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>

<span data-ttu-id="b16f9-112">W tym temacie omówiono sposób pakowania niestandardowego `My` rozszerzenia jako szablon ukryty element, który można zarządzać przy użyciu **Moje rozszerzenia** strony w Projektancie projektu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b16f9-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="b16f9-113">Niestandardowy `My` rozszerzenia mogą być również dodawane automatycznie po dodaniu do projektu odwołanie do określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b16f9-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>

## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="b16f9-114">Utwórz moje rozszerzenie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="b16f9-114">Create a My namespace extension</span></span>

<span data-ttu-id="b16f9-115">Pierwszym krokiem w tworzeniu pakietu wdrożeniowego dla niestandardowego `My` rozszerzenia polega na utworzeniu rozszerzenia jako plik pojedynczego kodu.</span><span class="sxs-lookup"><span data-stu-id="b16f9-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="b16f9-116">Aby uzyskać szczegółowe informacje i wskazówki dotyczące sposobu tworzenia niestandardowego `My` rozszerzenia, zobacz [rozszerzanie My Namespace w języku Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b16f9-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>

## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="b16f9-117">Eksportuj Moje rozszerzenie przestrzeni nazw jako szablon elementu</span><span class="sxs-lookup"><span data-stu-id="b16f9-117">Export a My namespace extension as an item template</span></span>

<span data-ttu-id="b16f9-118">Po utworzeniu pliku z kodem, który zawiera Twoje `My` rozszerzenie przestrzeni nazw, możesz wyeksportować plik kodu jako szablonu elementu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b16f9-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="b16f9-119">Aby uzyskać instrukcje dotyczące sposobu eksportowania pliku jako szablon elementu programu Visual Studio, zobacz [jak: Tworzenie szablonów elementu](/visualstudio/ide/how-to-create-item-templates).</span><span class="sxs-lookup"><span data-stu-id="b16f9-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>

> [!NOTE]
> <span data-ttu-id="b16f9-120">Jeśli Twoje `My` rozszerzenie przestrzeni nazw ma zależność od określonego zestawu, można dostosować szablon elementu, aby automatycznie zainstalować swoje `My` rozszerzenie przestrzeni nazw, po dodaniu odwołania do tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b16f9-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="b16f9-121">Co w efekcie można wykluczyć odwołanie do zestawu, eksportując plik kodu jako szablonu elementu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b16f9-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>

## <a name="customize-the-item-template"></a><span data-ttu-id="b16f9-122">Dostosowywanie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="b16f9-122">Customize the item template</span></span>

<span data-ttu-id="b16f9-123">Można włączyć usługi można zarządzać za pomocą szablonu elementu **Moje rozszerzenia** strony w Projektancie projektu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b16f9-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="b16f9-124">Można również włączyć szablon elementu, który ma zostać dodana automatycznie, gdy odwołanie do określonego zestawu zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="b16f9-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="b16f9-125">Aby włączyć te modyfikacje, będzie Dodaj nowy plik o nazwie pliku CustomData do szablonu, a następnie dodaj nowy element do pliku XML w pliku .vstemplate.</span><span class="sxs-lookup"><span data-stu-id="b16f9-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>

### <a name="add-the-customdata-file"></a><span data-ttu-id="b16f9-126">Dodaj plik CustomData</span><span class="sxs-lookup"><span data-stu-id="b16f9-126">Add the CustomData file</span></span>

<span data-ttu-id="b16f9-127">Plik CustomData jest plik tekstowy, który ma rozszerzenie nazwy pliku. CustomData (nazwa pliku można ustawić dowolną wartość zrozumiałe dla szablonu) i która zawiera kod XML.</span><span class="sxs-lookup"><span data-stu-id="b16f9-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="b16f9-128">Kod XML w pliku CustomData powoduje, że Visual Basic, aby dołączyć swoje `My` rozszerzenia, gdy użytkownicy korzystają **Moje rozszerzenia** strony w Projektancie projektu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b16f9-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="b16f9-129">Możesz opcjonalnie dodać <`AssemblyFullName>` atrybutu CustomData pliku XML.</span><span class="sxs-lookup"><span data-stu-id="b16f9-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="b16f9-130">To powoduje, że Visual Basic, aby automatycznie zainstalować niestandardowe `My` rozszerzenia, gdy odwołanie do konkretnego zestawu jest dodawany do projektu.</span><span class="sxs-lookup"><span data-stu-id="b16f9-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="b16f9-131">Można użyć dowolnego edytora tekstu lub edytorze XML, aby utworzyć plik CustomData, a następnie dodaj go do szablonu elementu skompresowany folder (plik zip).</span><span class="sxs-lookup"><span data-stu-id="b16f9-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>

<span data-ttu-id="b16f9-132">Na przykład, następujący kody XML pokazuje zawartość pliku CustomData, który doda element szablonu do folderu rozszerzeń mój projekt Visual Basic, gdy odwołanie do zestawu Microsoft.VisualBasic.PowerPacks.Vs.dll zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="b16f9-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

<span data-ttu-id="b16f9-133">Zawiera plik CustomData <`VBMyExtensionTemplate>` element, który zawiera atrybuty wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="b16f9-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>

|<span data-ttu-id="b16f9-134">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b16f9-134">Attribute</span></span>|<span data-ttu-id="b16f9-135">Opis</span><span class="sxs-lookup"><span data-stu-id="b16f9-135">Description</span></span>|
|---|---|
|`ID`|<span data-ttu-id="b16f9-136">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b16f9-136">Required.</span></span> <span data-ttu-id="b16f9-137">Unikatowy identyfikator dla rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="b16f9-137">A unique identifier for the extension.</span></span> <span data-ttu-id="b16f9-138">Jeśli rozszerzenie, które mają ten identyfikator został już dodany do projektu, użytkownik nie będzie monitowany ponownie dodać.</span><span class="sxs-lookup"><span data-stu-id="b16f9-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|
|`Version`|<span data-ttu-id="b16f9-139">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b16f9-139">Required.</span></span> <span data-ttu-id="b16f9-140">Numer wersji szablonu elementu.</span><span class="sxs-lookup"><span data-stu-id="b16f9-140">A version number for the item template.</span></span>|
|`AssemblyFullName`|<span data-ttu-id="b16f9-141">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="b16f9-141">Optional.</span></span> <span data-ttu-id="b16f9-142">Nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="b16f9-142">An assembly name.</span></span> <span data-ttu-id="b16f9-143">Po dodaniu do projektu odwołanie do tego zestawu użytkownika zostanie wyświetlony monit Dodaj `My` rozszerzenia za pomocą tego szablonu elementu.</span><span class="sxs-lookup"><span data-stu-id="b16f9-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="b16f9-144">Dodaj \<CustomDataSignature > element pliku .vstemplate</span><span class="sxs-lookup"><span data-stu-id="b16f9-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>

<span data-ttu-id="b16f9-145">Aby zidentyfikować szablonu elementu programu Visual Studio jako `My` rozszerzenie przestrzeni nazw, należy również zmodyfikować plik .vstemplate szablonu elementu.</span><span class="sxs-lookup"><span data-stu-id="b16f9-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="b16f9-146">Należy dodać `<CustomDataSignature>` elementu `<TemplateData>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b16f9-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="b16f9-147">`<CustomDataSignature>` Element musi zawierać tekst `Microsoft.VisualBasic.MyExtension`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b16f9-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

<span data-ttu-id="b16f9-148">Nie można bezpośrednio modyfikować pliki w skompresowanym folderze (pliku zip).</span><span class="sxs-lookup"><span data-stu-id="b16f9-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="b16f9-149">Należy skopiować plik .vstemplate ze skompresowanego folderu, go zmodyfikować, a następnie zastąp plik .vstemplate w skompresowanym folderze kopią zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="b16f9-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>

<span data-ttu-id="b16f9-150">W poniższym przykładzie pokazano zawartość pliku .vstemplate, który ma `<CustomDataSignature>` dodany element.</span><span class="sxs-lookup"><span data-stu-id="b16f9-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>

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

## <a name="install-the-template"></a><span data-ttu-id="b16f9-151">Zainstaluj szablonu</span><span class="sxs-lookup"><span data-stu-id="b16f9-151">Install the template</span></span>

<span data-ttu-id="b16f9-152">Aby zainstalować tego szablonu, należy skopiować skompresowany folder (*zip* plików) do folderu Szablony elementów Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b16f9-152">To install the template, you can copy the compressed folder (*.zip* file) to the Visual Basic item templates folder.</span></span> <span data-ttu-id="b16f9-153">Domyślnie, szablonów elementów użytkownika znajdują się w *%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ItemTemplates\Visual Basic*.</span><span class="sxs-lookup"><span data-stu-id="b16f9-153">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span></span> <span data-ttu-id="b16f9-154">Alternatywnie można opublikować szablon jako Instalator programu Visual Studio (*.vsi*) pliku.</span><span class="sxs-lookup"><span data-stu-id="b16f9-154">Alternatively, you can publish the template as a Visual Studio Installer (*.vsi*) file.</span></span>

## <a name="see-also"></a><span data-ttu-id="b16f9-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b16f9-155">See also</span></span>

- [<span data-ttu-id="b16f9-156">Rozszerzanie mojej Namespace w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b16f9-156">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [<span data-ttu-id="b16f9-157">Rozszerzanie modelu aplikacji Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b16f9-157">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [<span data-ttu-id="b16f9-158">Dostosowywanie, które obiekty są dostępne w My</span><span class="sxs-lookup"><span data-stu-id="b16f9-158">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [<span data-ttu-id="b16f9-159">Strona Moje rozszerzenia, Projektant projektu</span><span class="sxs-lookup"><span data-stu-id="b16f9-159">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
