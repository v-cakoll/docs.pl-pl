---
title: 'Porady: dodawanie lub usuwanie obrazów ImageList przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: cdc7b563a0ee4f8779b99b4e9a6786e78f8d500f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628725"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="de603-102">Porady: dodawanie lub usuwanie obrazów ImageList przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="de603-102">How to: Add or Remove ImageList Images with the Designer</span></span>

<span data-ttu-id="de603-103">Do składnika <xref:System.Windows.Forms.ImageList> można dodawać obrazy na kilka różnych sposobów.</span><span class="sxs-lookup"><span data-stu-id="de603-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="de603-104">Obrazy można dodawać bardzo szybko przy użyciu tagu inteligentnego skojarzonego z <xref:System.Windows.Forms.ImageList>lub jeśli ustawiasz kilka innych właściwości na <xref:System.Windows.Forms.ImageList>, może być wygodniejsze Dodawanie obrazów z okno Właściwości.</span><span class="sxs-lookup"><span data-stu-id="de603-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="de603-105">Możesz również dodawać obrazy za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="de603-105">You can also add images by using code.</span></span> <span data-ttu-id="de603-106">Aby uzyskać więcej informacji na temat dodawania obrazów przy użyciu kodu, zobacz [How to: Dodawanie lub usuwanie obrazów za pomocą składnika Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="de603-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="de603-107">Zwykle wypełniany jest składnik <xref:System.Windows.Forms.ImageList> z obrazami, zanim zostanie on skojarzony z kontrolką, ale nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="de603-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="de603-108">Aby dodać lub usunąć obrazy przy użyciu okno Właściwości</span><span class="sxs-lookup"><span data-stu-id="de603-108">To add or remove images by using the Properties window</span></span>

1. <span data-ttu-id="de603-109">Wybierz składnik <xref:System.Windows.Forms.ImageList> lub Dodaj go do formularza.</span><span class="sxs-lookup"><span data-stu-id="de603-109">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="de603-110">W okno Właściwości kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno Właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.ImageList.Images%2A>.</span><span class="sxs-lookup"><span data-stu-id="de603-110">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>

3. <span data-ttu-id="de603-111">W **edytorze kolekcji obrazów**kliknij pozycję **Dodaj** lub **Usuń** , aby dodać lub usunąć obrazy z listy.</span><span class="sxs-lookup"><span data-stu-id="de603-111">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>

### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="de603-112">Aby dodać lub usunąć obrazy przy użyciu tagu inteligentnego</span><span class="sxs-lookup"><span data-stu-id="de603-112">To add or remove images using the smart tag</span></span>

1. <span data-ttu-id="de603-113">Wybierz składnik <xref:System.Windows.Forms.ImageList> lub Dodaj go do formularza.</span><span class="sxs-lookup"><span data-stu-id="de603-113">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="de603-114">Kliknij symbol akcji projektanta (</span><span class="sxs-lookup"><span data-stu-id="de603-114">Click the designer actions glyph (</span></span>![Mała czarna strzałka](./media/designer-actions-glyph.gif)<span data-ttu-id="de603-116">)</span><span class="sxs-lookup"><span data-stu-id="de603-116">)</span></span>

3. <span data-ttu-id="de603-117">W oknie dialogowym **ImageList Tasks (zadania** ) wybierz pozycję **Wybierz obrazy**.</span><span class="sxs-lookup"><span data-stu-id="de603-117">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>

4. <span data-ttu-id="de603-118">W **edytorze kolekcji obrazów** kliknij pozycję **Dodaj** lub **Usuń** , aby dodać lub usunąć obrazy z listy.</span><span class="sxs-lookup"><span data-stu-id="de603-118">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>

## <a name="see-also"></a><span data-ttu-id="de603-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de603-119">See also</span></span>

- [<span data-ttu-id="de603-120">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="de603-120">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="de603-121">Przewodnik: wykonywanie typowych zadań przy użyciu akcji projektanta</span><span class="sxs-lookup"><span data-stu-id="de603-121">Walkthrough: Perform common tasks using designer actions</span></span>](perform-common-tasks-design-actions.md)
- [<span data-ttu-id="de603-122">ImageList, składnik</span><span class="sxs-lookup"><span data-stu-id="de603-122">ImageList Component</span></span>](imagelist-component-windows-forms.md)
