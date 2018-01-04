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
ms.openlocfilehash: 7339afdc35341739b592b2a327094754031c346c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="c62e4-102">Szybkie opracowywanie aplikacji przy użyciu My.Resources i My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c62e4-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>
<span data-ttu-id="c62e4-103">`My.Resources` Obiekt zapewnia dostęp do zasobów aplikacji i pozwala dynamicznie pobrać zasobów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c62e4-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="c62e4-104">Pobieranie zasobów</span><span class="sxs-lookup"><span data-stu-id="c62e4-104">Retrieving Resources</span></span>  
 <span data-ttu-id="c62e4-105">Liczba zasobów, takich jak pliki dźwiękowe, ikony, obrazy i ciągi mogą zostać pobrane za pośrednictwem `My.Resources` obiektu.</span><span class="sxs-lookup"><span data-stu-id="c62e4-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="c62e4-106">Na przykład można uzyskać dostępu do plików specyficzne dla kultury zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c62e4-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="c62e4-107">Poniższy przykład przedstawia ikonę w postaci ikony o nazwie `Form1Icon` przechowywane w pliku zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c62e4-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 <span data-ttu-id="c62e4-108">`My.Resources` Obiekt ujawnia tylko zasoby globalne.</span><span class="sxs-lookup"><span data-stu-id="c62e4-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="c62e4-109">Nie ma dostępu do plików zasobów skojarzonych z formularzami.</span><span class="sxs-lookup"><span data-stu-id="c62e4-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="c62e4-110">W formularzu musi uzyskiwać dostęp do zasobów formularza.</span><span class="sxs-lookup"><span data-stu-id="c62e4-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="c62e4-111">Podobnie `My.Settings` obiektu zapewnia dostęp do ustawień aplikacji i pozwala na dynamicznie przechowywać i pobierać ustawienia właściwości i inne informacje dotyczące aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c62e4-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="c62e4-112">Aby uzyskać więcej informacji, zobacz [My.resources — obiekt](../../../visual-basic/language-reference/objects/my-resources-object.md) i [My.Settings — obiekt](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="c62e4-112">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c62e4-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c62e4-113">See Also</span></span>  
 [<span data-ttu-id="c62e4-114">My.Resources, obiekt</span><span class="sxs-lookup"><span data-stu-id="c62e4-114">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [<span data-ttu-id="c62e4-115">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="c62e4-115">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="c62e4-116">Uzyskiwanie dostępu do ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="c62e4-116">Accessing Application Settings</span></span>](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
