---
title: "ImageList — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a913de1a6808c7e600a4f28ed58dedf93506466b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imagelist-component-overview-windows-forms"></a><span data-ttu-id="cd147-102">ImageList — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="cd147-102">ImageList Component Overview (Windows Forms)</span></span>
<span data-ttu-id="cd147-103">Formularze systemu Windows <xref:System.Windows.Forms.ImageList> składnik jest używany do przechowywania obrazów, które mogą być następnie wyświetlane przez formanty.</span><span class="sxs-lookup"><span data-stu-id="cd147-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is used to store images, which can then be displayed by controls.</span></span> <span data-ttu-id="cd147-104">Listy obrazów umożliwia pisanie kodu dla wykazu powinny być zawsze obrazów.</span><span class="sxs-lookup"><span data-stu-id="cd147-104">An image list allows you to write code for a single, consistent catalog of images.</span></span> <span data-ttu-id="cd147-105">Na przykład można obracać obrazów wyświetlanych przez <xref:System.Windows.Forms.Button> formantu, zmieniając po prostu przycisku <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> lub <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cd147-105">For example, you can rotate images displayed by a <xref:System.Windows.Forms.Button> control simply by changing the button's <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> or <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> property.</span></span> <span data-ttu-id="cd147-106">Można również kojarzyć tej samej listy obrazów z wielu formantów.</span><span class="sxs-lookup"><span data-stu-id="cd147-106">You can also associate the same image list with multiple controls.</span></span> <span data-ttu-id="cd147-107">Na przykład, jeśli używasz zarówno <xref:System.Windows.Forms.ListView> kontroli i <xref:System.Windows.Forms.TreeView> formantu, aby wyświetlić tę samą listę plików, zmieniając ikonę pliku na liście obrazów spowoduje, że nowa ikona pojawią się w obu widokach.</span><span class="sxs-lookup"><span data-stu-id="cd147-107">For example, if you are using both a <xref:System.Windows.Forms.ListView> control and a <xref:System.Windows.Forms.TreeView> control to display the same list of files, changing a file's icon in the image list will cause the new icon to appear in both views.</span></span>  
  
## <a name="using-imagelist-with-controls"></a><span data-ttu-id="cd147-108">Przy użyciu listy obrazów z formantami</span><span class="sxs-lookup"><span data-stu-id="cd147-108">Using ImageList with Controls</span></span>  
 <span data-ttu-id="cd147-109">Można użyć listy obrazów z żadnego formantu, który ma `ImageList` właściwości — lub w przypadku liczby <xref:System.Windows.Forms.ListView> kontroli, <xref:System.Windows.Forms.ListView.SmallImageList%2A> i <xref:System.Windows.Forms.ListView.LargeImageList%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cd147-109">You can use an image list with any control that has an `ImageList` property — or in the case of the <xref:System.Windows.Forms.ListView> control, <xref:System.Windows.Forms.ListView.SmallImageList%2A> and <xref:System.Windows.Forms.ListView.LargeImageList%2A> properties.</span></span> <span data-ttu-id="cd147-110">Formanty, które mogą być skojarzone z listy obrazów obejmują: <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, i <xref:System.Windows.Forms.Label> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="cd147-110">The controls that can be associated with an image list include: the <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, and <xref:System.Windows.Forms.Label> controls.</span></span> <span data-ttu-id="cd147-111">Aby skojarzyć listy obrazów z formantem, ustaw dla formantu `ImageList` właściwość na nazwę <xref:System.Windows.Forms.ImageList> składnika.</span><span class="sxs-lookup"><span data-stu-id="cd147-111">To associate the image list with a control, set the control's `ImageList` property to the name of the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="cd147-112">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="cd147-112">Key Properties</span></span>  
 <span data-ttu-id="cd147-113">Właściwość klucza <xref:System.Windows.Forms.ImageList> składnik jest <xref:System.Windows.Forms.ImageList.Images%2A>, zawierający obrazy, które mają być używane przez skojarzony formant.</span><span class="sxs-lookup"><span data-stu-id="cd147-113">The key property of the <xref:System.Windows.Forms.ImageList> component is <xref:System.Windows.Forms.ImageList.Images%2A>, which contains the pictures to be used by the associated control.</span></span> <span data-ttu-id="cd147-114">Każdy poszczególnych obraz jest dostępny przez jej wartość indeksu lub za pomocą klucza.</span><span class="sxs-lookup"><span data-stu-id="cd147-114">Each individual image can be accessed by its index value or by its key.</span></span> <span data-ttu-id="cd147-115"><xref:System.Windows.Forms.ImageList.ColorDepth%2A> Właściwość określa liczbę kolorów, które mają być renderowane obrazów z.</span><span class="sxs-lookup"><span data-stu-id="cd147-115">The <xref:System.Windows.Forms.ImageList.ColorDepth%2A> property determines the number of colors that the images are rendered with.</span></span> <span data-ttu-id="cd147-116">Obrazy wszystkie pojawi się w tym samym rozmiarze, ustawione przez <xref:System.Windows.Forms.ImageList.ImageSize%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cd147-116">The images will all be displayed at the same size, set by the <xref:System.Windows.Forms.ImageList.ImageSize%2A> property.</span></span> <span data-ttu-id="cd147-117">Obrazy, które są większe będą skalowane w celu dopasowania.</span><span class="sxs-lookup"><span data-stu-id="cd147-117">Images that are larger will be scaled to fit.</span></span>  
  
 <span data-ttu-id="cd147-118">Jeśli używasz [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], masz dostęp do dużych biblioteki standardowe obrazów, które można używać w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd147-118">If you are using [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], you have access to a large library of standard images that you can use in your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd147-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd147-119">See Also</span></span>  
 <xref:System.Windows.Forms.ImageList>  
 [<span data-ttu-id="cd147-120">Instrukcje: dodawanie lub usuwanie obrazów za pomocą składnika ImageList formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd147-120">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
