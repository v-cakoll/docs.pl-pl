---
title: Szybkie opracowywanie aplikacji przy użyciu My.Resources i My.Settings (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 1d5fe35ea491c2c2d3de82ef208fec59a6079a25
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976074"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="7e379-102">Szybkie opracowywanie aplikacji przy użyciu My.Resources i My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e379-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>
<span data-ttu-id="7e379-103">`My.Resources` Obiekt zapewnia dostęp do zasobów aplikacji i pozwala dynamicznie pobrać zasobów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e379-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="7e379-104">Pobieranie zasobów</span><span class="sxs-lookup"><span data-stu-id="7e379-104">Retrieving Resources</span></span>  
 <span data-ttu-id="7e379-105">Liczba zasobów, takich jak pliki audio, ikony, obrazy i ciągi mogą być pobierane za pośrednictwem `My.Resources` obiektu.</span><span class="sxs-lookup"><span data-stu-id="7e379-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="7e379-106">Na przykład można uzyskać dostęp do plików specyficzne dla kultury zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e379-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="7e379-107">W poniższym przykładzie ustawiono ikony w postaci ikony o nazwie `Form1Icon` przechowywane w pliku zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e379-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 <span data-ttu-id="7e379-108">`My.Resources` Obiekt udostępnia tylko zasoby globalne.</span><span class="sxs-lookup"><span data-stu-id="7e379-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="7e379-109">Zapewnia ona dostęp do plików zasobów skojarzonych z formularzami.</span><span class="sxs-lookup"><span data-stu-id="7e379-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="7e379-110">Należy uzyskać dostęp do zasobów formularza z formularza.</span><span class="sxs-lookup"><span data-stu-id="7e379-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="7e379-111">Podobnie `My.Settings` obiekt umożliwia dostęp do ustawień aplikacji i pozwala na dynamiczne przechowywanie i pobieranie ustawień właściwości i inne informacje dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e379-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="7e379-112">Aby uzyskać więcej informacji, zobacz [My.resources — obiekt](../../../visual-basic/language-reference/objects/my-resources-object.md) i [My.Settings — obiekt](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="7e379-112">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e379-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e379-113">See also</span></span>
- [<span data-ttu-id="7e379-114">My.Resources, obiekt</span><span class="sxs-lookup"><span data-stu-id="7e379-114">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [<span data-ttu-id="7e379-115">My.Settings, obiekt</span><span class="sxs-lookup"><span data-stu-id="7e379-115">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="7e379-116">Uzyskiwanie dostępu do ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="7e379-116">Accessing Application Settings</span></span>](../../../visual-basic/developing-apps/programming/app-settings/index.md)
