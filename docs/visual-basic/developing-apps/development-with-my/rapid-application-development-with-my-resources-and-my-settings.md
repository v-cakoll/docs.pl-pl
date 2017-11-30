---
title: "Szybkie opracowywanie aplikacji przy użyciu My.Resources i My.Settings (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1657febf935560ff4c8dd2f54b10fdcb2254891f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="4ee98-102">Szybkie opracowywanie aplikacji przy użyciu My.Resources i My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ee98-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>
<span data-ttu-id="4ee98-103">`My.Resources` Obiekt zapewnia dostęp do zasobów aplikacji i pozwala dynamicznie pobrać zasobów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ee98-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="4ee98-104">Pobieranie zasobów</span><span class="sxs-lookup"><span data-stu-id="4ee98-104">Retrieving Resources</span></span>  
 <span data-ttu-id="4ee98-105">Liczba zasobów, takich jak pliki dźwiękowe, ikony, obrazy i ciągi mogą zostać pobrane za pośrednictwem `My.Resources` obiektu.</span><span class="sxs-lookup"><span data-stu-id="4ee98-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="4ee98-106">Na przykład można uzyskać dostępu do plików specyficzne dla kultury zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ee98-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="4ee98-107">Poniższy przykład przedstawia ikonę w postaci ikony o nazwie `Form1Icon` przechowywane w pliku zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ee98-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 <span data-ttu-id="4ee98-108">`My.Resources` Obiekt ujawnia tylko zasoby globalne.</span><span class="sxs-lookup"><span data-stu-id="4ee98-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="4ee98-109">Nie ma dostępu do plików zasobów skojarzonych z formularzami.</span><span class="sxs-lookup"><span data-stu-id="4ee98-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="4ee98-110">W formularzu musi uzyskiwać dostęp do zasobów formularza.</span><span class="sxs-lookup"><span data-stu-id="4ee98-110">You must access the form resources from the form.</span></span> <span data-ttu-id="4ee98-111">Aby uzyskać więcej informacji, zobacz [wskazówki: Lokalizowanie formularzy systemu Windows](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).</span><span class="sxs-lookup"><span data-stu-id="4ee98-111">For more information, see [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).</span></span>  
  
 <span data-ttu-id="4ee98-112">Podobnie `My.Settings` obiektu zapewnia dostęp do ustawień aplikacji i pozwala na dynamicznie przechowywać i pobierać ustawienia właściwości i inne informacje dotyczące aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ee98-112">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="4ee98-113">Aby uzyskać więcej informacji, zobacz [My.resources — obiekt](../../../visual-basic/language-reference/objects/my-resources-object.md) i [My.Settings — obiekt](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="4ee98-113">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ee98-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ee98-114">See Also</span></span>  
 [<span data-ttu-id="4ee98-115">My.resources — obiekt</span><span class="sxs-lookup"><span data-stu-id="4ee98-115">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [<span data-ttu-id="4ee98-116">My.Settings — obiekt</span><span class="sxs-lookup"><span data-stu-id="4ee98-116">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="4ee98-117">Uzyskiwanie dostępu do ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="4ee98-117">Accessing Application Settings</span></span>](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
