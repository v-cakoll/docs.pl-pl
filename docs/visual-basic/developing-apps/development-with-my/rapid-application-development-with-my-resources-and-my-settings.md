---
title: Szybkie opracowywanie aplikacji przy użyciu My.Resources i My.Settings
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: fd1ec25582e919b84235502f5921edfbc6e1dade
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990203"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="c163f-102">Szybkie opracowywanie aplikacji przy użyciu My.Resources i My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c163f-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>

<span data-ttu-id="c163f-103">`My.Resources`Obiekt zapewnia dostęp do zasobów aplikacji i umożliwia dynamiczne pobieranie zasobów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c163f-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="c163f-104">Pobieranie zasobów</span><span class="sxs-lookup"><span data-stu-id="c163f-104">Retrieving Resources</span></span>  

 <span data-ttu-id="c163f-105">Wiele zasobów, takich jak pliki audio, ikony, obrazy i ciągi, można pobrać za pomocą `My.Resources` obiektu.</span><span class="sxs-lookup"><span data-stu-id="c163f-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="c163f-106">Można na przykład uzyskać dostęp do plików zasobów specyficznych dla kultury aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c163f-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="c163f-107">Poniższy przykład ustawia ikonę formularza na ikonę o nazwie `Form1Icon` przechowywanej w pliku zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c163f-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 <span data-ttu-id="c163f-108">`My.Resources`Obiekt uwidacznia tylko zasoby globalne.</span><span class="sxs-lookup"><span data-stu-id="c163f-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="c163f-109">Nie zapewnia dostępu do plików zasobów skojarzonych z formularzami.</span><span class="sxs-lookup"><span data-stu-id="c163f-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="c163f-110">Uzyskaj dostęp do formularzy zasoby z formularza.</span><span class="sxs-lookup"><span data-stu-id="c163f-110">Access the form resources from the form.</span></span>  
  
 <span data-ttu-id="c163f-111">Podobnie `My.Settings` obiekt zapewnia dostęp do ustawień aplikacji i umożliwia dynamiczne przechowywanie i pobieranie ustawień właściwości oraz innych informacji dotyczących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c163f-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="c163f-112">Aby uzyskać więcej informacji, zobacz [Moje obiekty Resources](../../language-reference/objects/my-resources-object.md) i [My. Settings](../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="c163f-112">For more information, see [My.Resources Object](../../language-reference/objects/my-resources-object.md) and [My.Settings Object](../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c163f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c163f-113">See also</span></span>

- [<span data-ttu-id="c163f-114">My.Resources — Obiekt</span><span class="sxs-lookup"><span data-stu-id="c163f-114">My.Resources Object</span></span>](../../language-reference/objects/my-resources-object.md)
- [<span data-ttu-id="c163f-115">My.Settings — Obiekt</span><span class="sxs-lookup"><span data-stu-id="c163f-115">My.Settings Object</span></span>](../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="c163f-116">Uzyskiwanie dostępu do ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="c163f-116">Accessing Application Settings</span></span>](../programming/app-settings/index.md)
