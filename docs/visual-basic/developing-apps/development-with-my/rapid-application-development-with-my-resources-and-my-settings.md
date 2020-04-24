---
title: Szybkie opracowywanie aplikacji przy użyciu My.Resources i My.Settings
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: ce9a5bf76ba3132f58aa40227a145d8b5bf1591d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349268"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="3a768-102">Szybkie opracowywanie aplikacji przy użyciu My.Resources i My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a768-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>

<span data-ttu-id="3a768-103">`My.Resources` Obiekt zapewnia dostęp do zasobów aplikacji i umożliwia dynamiczne pobieranie zasobów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a768-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="3a768-104">Pobieranie zasobów</span><span class="sxs-lookup"><span data-stu-id="3a768-104">Retrieving Resources</span></span>  

 <span data-ttu-id="3a768-105">Wiele zasobów, takich jak pliki audio, ikony, obrazy i ciągi, można pobrać za pomocą `My.Resources` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3a768-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="3a768-106">Można na przykład uzyskać dostęp do plików zasobów specyficznych dla kultury aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a768-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="3a768-107">Poniższy przykład ustawia ikonę formularza na ikonę o nazwie `Form1Icon` przechowywanej w pliku zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a768-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 <span data-ttu-id="3a768-108">`My.Resources` Obiekt uwidacznia tylko zasoby globalne.</span><span class="sxs-lookup"><span data-stu-id="3a768-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="3a768-109">Nie zapewnia dostępu do plików zasobów skojarzonych z formularzami.</span><span class="sxs-lookup"><span data-stu-id="3a768-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="3a768-110">Musisz uzyskać dostęp do zasobów formularza z formularza.</span><span class="sxs-lookup"><span data-stu-id="3a768-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="3a768-111">Podobnie `My.Settings` obiekt zapewnia dostęp do ustawień aplikacji i umożliwia dynamiczne przechowywanie i pobieranie ustawień właściwości oraz innych informacji dotyczących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a768-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="3a768-112">Aby uzyskać więcej informacji, zobacz [Moje obiekty Resources](../../../visual-basic/language-reference/objects/my-resources-object.md) i [My. Settings](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="3a768-112">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a768-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a768-113">See also</span></span>

- [<span data-ttu-id="3a768-114">My.Resources, obiekt</span><span class="sxs-lookup"><span data-stu-id="3a768-114">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [<span data-ttu-id="3a768-115">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="3a768-115">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="3a768-116">Uzyskiwanie dostępu do ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="3a768-116">Accessing Application Settings</span></span>](../../../visual-basic/developing-apps/programming/app-settings/index.md)
