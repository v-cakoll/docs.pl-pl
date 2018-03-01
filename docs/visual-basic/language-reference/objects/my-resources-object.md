---
title: "My.Resources — Obiekt"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96e5b909d9945ed631cebe07e4cfc7d5dc2e019f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="myresources-object"></a><span data-ttu-id="d72fe-102">My.Resources — Obiekt</span><span class="sxs-lookup"><span data-stu-id="d72fe-102">My.Resources Object</span></span>
<span data-ttu-id="d72fe-103">Udostępnia właściwości i klasy do uzyskiwania dostępu do zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d72fe-103">Provides properties and classes for accessing the application's resources.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d72fe-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d72fe-104">Remarks</span></span>  
 <span data-ttu-id="d72fe-105">`My.Resources` Obiektu zapewnia dostęp do zasobów aplikacji i pozwala dynamicznie pobrać zasobów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d72fe-105">The `My.Resources` object provides access to the application's resources and lets you dynamically retrieve resources for your application.</span></span> <span data-ttu-id="d72fe-106">Aby uzyskać więcej informacji, zobacz [zarządzanie zasobami aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="d72fe-106">For more information, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
 <span data-ttu-id="d72fe-107">`My.Resources` Obiekt ujawnia tylko zasoby globalne.</span><span class="sxs-lookup"><span data-stu-id="d72fe-107">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="d72fe-108">Nie ma dostępu do plików zasobów skojarzonych z formularzami.</span><span class="sxs-lookup"><span data-stu-id="d72fe-108">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="d72fe-109">W formularzu musi uzyskiwać dostęp do zasobów formularza.</span><span class="sxs-lookup"><span data-stu-id="d72fe-109">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="d72fe-110">Dostępne pliki specyficzne dla kultury zasobów aplikacji z `My.Resources` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d72fe-110">You can access the application's culture-specific resource files from the `My.Resources` object.</span></span> <span data-ttu-id="d72fe-111">Domyślnie `My.Resources` obiekt odwołuje się do zasobów z pliku zasobów zgodny kultury w <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d72fe-111">By default, the `My.Resources` object looks up resources from the resource file that matches the culture in the <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> property.</span></span> <span data-ttu-id="d72fe-112">Można jednak zmienić to zachowanie i określić określonej kultury dla zasobów.</span><span class="sxs-lookup"><span data-stu-id="d72fe-112">However, you can override this behavior and specify a particular culture to use for the resources.</span></span> <span data-ttu-id="d72fe-113">Aby uzyskać więcej informacji, zobacz [zasobów w aplikacjach pulpitu](../../../framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="d72fe-113">For more information, see [Resources in Desktop Apps](../../../framework/resources/index.md).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d72fe-114">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d72fe-114">Properties</span></span>  
 <span data-ttu-id="d72fe-115">Właściwości `My.Resources` obiektu umożliwiają dostęp tylko do odczytu do zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d72fe-115">The properties of the `My.Resources` object provide read-only access to your application's resources.</span></span> <span data-ttu-id="d72fe-116">Aby dodać lub usunąć zasoby, używać **projektanta projektu**.</span><span class="sxs-lookup"><span data-stu-id="d72fe-116">To add or remove resources, use the **Project Designer**.</span></span> <span data-ttu-id="d72fe-117">Dostępne zasoby dodane za pośrednictwem **projektanta projektu** przy użyciu `My.Resources.``resourceName`.</span><span class="sxs-lookup"><span data-stu-id="d72fe-117">You can access resources added through the **Project Designer** by using `My.Resources.``resourceName`.</span></span>  
  
 <span data-ttu-id="d72fe-118">Możesz również dodać lub usunąć pliki zasobów, zaznaczając projektu w **Eksploratora rozwiązań** i klikając **Dodaj nowy element** lub **Dodaj istniejący element** z  **Projekt** menu.</span><span class="sxs-lookup"><span data-stu-id="d72fe-118">You can also add or remove resource files by selecting your project in **Solution Explorer** and clicking **Add New Item** or **Add Existing Item** from the **Project** menu.</span></span> <span data-ttu-id="d72fe-119">Dostępne zasoby dodane w ten sposób za pomocą `My.Resources.``resourceFileName`.`resourceName`.</span><span class="sxs-lookup"><span data-stu-id="d72fe-119">You can access resources added in this manner by using `My.Resources.``resourceFileName`.`resourceName`.</span></span>  
  
 <span data-ttu-id="d72fe-120">Każdy zasób ma nazwę, kategorii i wartość, a tych ustawień zasobu określenia sposobu wyświetlania właściwości dostępu do zasobu w `My.Resources` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d72fe-120">Each resource has a name, category, and value, and these resource settings determine how the property to access the resource appears in the `My.Resources` object.</span></span> <span data-ttu-id="d72fe-121">Dla zasobów dodane w **projektanta projektu**:</span><span class="sxs-lookup"><span data-stu-id="d72fe-121">For resources added in the **Project Designer**:</span></span>  
  
-   <span data-ttu-id="d72fe-122">Nazwa właściwości, określa nazwę</span><span class="sxs-lookup"><span data-stu-id="d72fe-122">The name determines the name of the property,</span></span>  
  
-   <span data-ttu-id="d72fe-123">Dane zasobu są wartości właściwości,</span><span class="sxs-lookup"><span data-stu-id="d72fe-123">The resource data is the value of the property,</span></span>  
  
-   <span data-ttu-id="d72fe-124">Kategoria określa typ właściwości:</span><span class="sxs-lookup"><span data-stu-id="d72fe-124">The category determines the type of the property:</span></span>  
  
|<span data-ttu-id="d72fe-125">Kategoria</span><span class="sxs-lookup"><span data-stu-id="d72fe-125">Category</span></span>|<span data-ttu-id="d72fe-126">Typ danych właściwości</span><span class="sxs-lookup"><span data-stu-id="d72fe-126">Property data type</span></span>|  
|---|---|  
|<span data-ttu-id="d72fe-127">**Ciągi**</span><span class="sxs-lookup"><span data-stu-id="d72fe-127">**Strings**</span></span>|[<span data-ttu-id="d72fe-128">Ciąg</span><span class="sxs-lookup"><span data-stu-id="d72fe-128">String</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|<span data-ttu-id="d72fe-129">**Obrazy**</span><span class="sxs-lookup"><span data-stu-id="d72fe-129">**Images**</span></span>|<xref:System.Drawing.Bitmap>|  
|<span data-ttu-id="d72fe-130">**Ikony**</span><span class="sxs-lookup"><span data-stu-id="d72fe-130">**Icons**</span></span>|<xref:System.Drawing.Icon>|  
|<span data-ttu-id="d72fe-131">**Audio**</span><span class="sxs-lookup"><span data-stu-id="d72fe-131">**Audio**</span></span>|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <span data-ttu-id="d72fe-132"><xref:System.IO.UnmanagedMemoryStream> Pochodną klasy <xref:System.IO.Stream> klasy, więc można go użyć z metod, które przyjmują strumieni, takie jak <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d72fe-132">The <xref:System.IO.UnmanagedMemoryStream> class derives from the <xref:System.IO.Stream> class, so it can be used with methods that take streams, such as the <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> method.</span></span>|  
|<span data-ttu-id="d72fe-133">**Pliki**</span><span class="sxs-lookup"><span data-stu-id="d72fe-133">**Files**</span></span>|<span data-ttu-id="d72fe-134">-   [Ciąg](../../../visual-basic/language-reference/data-types/string-data-type.md) w przypadku plików tekstowych.</span><span class="sxs-lookup"><span data-stu-id="d72fe-134">-   [String](../../../visual-basic/language-reference/data-types/string-data-type.md) for text files.</span></span><br /><span data-ttu-id="d72fe-135">-   <xref:System.Drawing.Bitmap>w przypadku plików obrazu.</span><span class="sxs-lookup"><span data-stu-id="d72fe-135">-   <xref:System.Drawing.Bitmap> for image files.</span></span><br /><span data-ttu-id="d72fe-136">-   <xref:System.Drawing.Icon>Ikona plików.</span><span class="sxs-lookup"><span data-stu-id="d72fe-136">-   <xref:System.Drawing.Icon> for icon files.</span></span><br /><span data-ttu-id="d72fe-137">-   <xref:System.IO.UnmanagedMemoryStream>w przypadku plików dźwięku.</span><span class="sxs-lookup"><span data-stu-id="d72fe-137">-   <xref:System.IO.UnmanagedMemoryStream> for sound files.</span></span>|  
|<span data-ttu-id="d72fe-138">**Inne**</span><span class="sxs-lookup"><span data-stu-id="d72fe-138">**Other**</span></span>|<span data-ttu-id="d72fe-139">Zależą od informacji w Projektancie **typu** kolumny.</span><span class="sxs-lookup"><span data-stu-id="d72fe-139">Determined by the information in the designer's **Type** column.</span></span>|  
  
## <a name="classes"></a><span data-ttu-id="d72fe-140">Klasy</span><span class="sxs-lookup"><span data-stu-id="d72fe-140">Classes</span></span>  
 <span data-ttu-id="d72fe-141">`My.Resources` Obiekt udostępnia każdy plik zasobu jako klasa z właściwości udostępnionych.</span><span class="sxs-lookup"><span data-stu-id="d72fe-141">The `My.Resources` object exposes each resource file as a class with shared properties.</span></span> <span data-ttu-id="d72fe-142">Nazwa klasy jest taka sama jak nazwa pliku zasobu.</span><span class="sxs-lookup"><span data-stu-id="d72fe-142">The class name is the same as the name of the resource file.</span></span> <span data-ttu-id="d72fe-143">Zgodnie z opisem w poprzedniej sekcji, zasobów w pliku zasobów są widoczne jako właściwości w klasie.</span><span class="sxs-lookup"><span data-stu-id="d72fe-143">As described in the previous section, the resources in a resource file are exposed as properties in the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d72fe-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="d72fe-144">Example</span></span>  
 <span data-ttu-id="d72fe-145">W tym przykładzie tytuł formularza zasobu ciągu o nazwie `Form1Title` w pliku zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d72fe-145">This example sets the title of a form to the string resource named `Form1Title` in the application resource file.</span></span> <span data-ttu-id="d72fe-146">Na przykład do pracy, aplikacja musi mieć ciągu o nazwie `Form1Title` w pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="d72fe-146">For the example to work, the application must have a string named `Form1Title` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="d72fe-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="d72fe-147">Example</span></span>  
 <span data-ttu-id="d72fe-148">W tym przykładzie ikonę w postaci ikony o nazwie `Form1Icon` jest przechowywana w pliku zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d72fe-148">This example sets the icon of the form to the icon named `Form1Icon` that is stored in the application's resource file.</span></span> <span data-ttu-id="d72fe-149">Na przykład do pracy, aplikacja musi mieć ikony o nazwie `Form1Icon` w pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="d72fe-149">For the example to work, the application must have an icon named `Form1Icon` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="d72fe-150">Przykład</span><span class="sxs-lookup"><span data-stu-id="d72fe-150">Example</span></span>  
 <span data-ttu-id="d72fe-151">W tym przykładzie obraz tła formularza zasobu obrazu o nazwie `Form1Background`, która znajduje się w pliku zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d72fe-151">This example sets the background image of a form to the image resource named `Form1Background`, which is in the application resource file.</span></span> <span data-ttu-id="d72fe-152">W tym przykładzie działała, aplikacja musi mieć zasób obrazu o nazwie `Form1Background` w pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="d72fe-152">For this example to work, the application must have an image resource named `Form1Background` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="d72fe-153">Przykład</span><span class="sxs-lookup"><span data-stu-id="d72fe-153">Example</span></span>  
 <span data-ttu-id="d72fe-154">W tym przykładzie odtwarza dźwięk, który jest przechowywany jako audio zasób o nazwie `Form1Greeting` w pliku zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d72fe-154">This example plays the sound that is stored as an audio resource named `Form1Greeting` in the application's resource file.</span></span> <span data-ttu-id="d72fe-155">Na przykład do pracy, aplikacja musi mieć audio zasób o nazwie `Form1Greeting` w pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="d72fe-155">For the example to work, the application must have an audio resource named `Form1Greeting` in its resource file.</span></span> <span data-ttu-id="d72fe-156">`My.Computer.Audio.Play` Metoda jest dostępna tylko dla aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d72fe-156">The `My.Computer.Audio.Play` method is available only for Windows Forms applications.</span></span>  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="d72fe-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="d72fe-157">Example</span></span>  
 <span data-ttu-id="d72fe-158">W tym przykładzie pobierana wersja kultury francuski zasób ciągu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d72fe-158">This example retrieves the French-culture version of a  string resource of the application.</span></span> <span data-ttu-id="d72fe-159">Nosi nazwę zasobu `Message`.</span><span class="sxs-lookup"><span data-stu-id="d72fe-159">The resource is named `Message`.</span></span> <span data-ttu-id="d72fe-160">Aby zmienić kulturę który `My.Resources` używa obiektu, w przykładzie użyto <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</span><span class="sxs-lookup"><span data-stu-id="d72fe-160">To change the culture that the `My.Resources` object uses, the example uses <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</span></span>  
  
 <span data-ttu-id="d72fe-161">W tym przykładzie działała, aplikacja musi mieć ciągu o nazwie `Message` w jego zasobów plików i aplikacji powinny mieć wersję kultury francuski tego pliku zasobu Resources.fr FR.resx.</span><span class="sxs-lookup"><span data-stu-id="d72fe-161">For this example to work, the application must have a string named `Message` in its resource file, and the application should have the French-culture version of that resource file, Resources.fr-FR.resx.</span></span> <span data-ttu-id="d72fe-162">Jeśli aplikacja nie ma wersji kultury francuski pliku zasobu `My.Resource` obiektu pobiera zasobu z pliku zasobu kultury domyślnej.</span><span class="sxs-lookup"><span data-stu-id="d72fe-162">If the application does not have the French-culture version of the resource file, the `My.Resource` object retrieves the resource from the default-culture resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d72fe-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d72fe-163">See Also</span></span>  
 [<span data-ttu-id="d72fe-164">Zarządzanie zasobami aplikacji (.NET)</span><span class="sxs-lookup"><span data-stu-id="d72fe-164">Managing Application Resources (.NET)</span></span>](/visualstudio/ide/managing-application-resources-dotnet)  
 [<span data-ttu-id="d72fe-165">Zasoby w aplikacjach klasycznych</span><span class="sxs-lookup"><span data-stu-id="d72fe-165">Resources in Desktop Apps</span></span>](../../../framework/resources/index.md)  

